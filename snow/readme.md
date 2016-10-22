# Notes
## Mutable and Immutable Object

- 官網的解釋:
  
  > The value of some objects can change. Objects whose value can change are said to be mutable; objects whose value is unchangeable once they are created are called immutable. (The value of an immutable container object that contains a reference to a mutable object can change when the latter’s value is changed; however the container is still considered immutable, because the collection of objects it contains cannot be changed. So, immutability is not strictly the same as having an unchangeable value, it is more subtle.) An object’s mutability is determined by its type; for instance, numbers, strings and tuples are immutable, while dictionaries and lists are mutable.
  - 簡言之，不能改變某一個index上的值的物件就是immutable object，反之則是mutable object。
  - 這串文字的後半段是在說明，若在immutable container(例如tuple)的成員當中有mutable object(例如list)，
  則mutable object的值仍然可以更改。舉例來說:
  
    ```python
    tupleWithList = (2,3,[5,6,7])
    tupleWithList[2][0] = 100
    print("tupleWithList=", tupleWithList)
    ```
    輸出結果:
    ```
    tupleWithList= (2,3,[100,6,7])
    ```

### Immutable Object
- Number(包含Integer和Float), String, Tuple
- Immutable objects雖然可以使用`+=`之類的運算，但實際上Python在這裡進行的動作和對mutable objects是不同的
  - 以下面這段程式碼為例:
    ```python
    myStr = "I am "
    myStr += "Snow"
    print("myStr=", myStr)
    ```
    輸出結果:
    ```
    myStr= "I am Snow"
    ```
    前兩行的動作實際上應該要拆成:
  
    1. 將`"I am"`這個string object指定給`myStr`
    2. 產生一個新的string object其值為`"Snow"`，然後和`"I am "`相加，產生一個新的string object值為`"I am Snow"`，
  然後指定給`myStr`
    也就是說`myStr`前後其實是指向不同的string object
- Number物件只要值一樣，一律都指到同一個物件。例:
    
  ```
  >>> a = 1
  >>> b = 2
  >>> a += 1
  >>> print("a is b=", a is b)
  a is b= True
  ```
  
  String和Tuple則*沒有*這個特性。

### Mutable Object
- List, Dictionary, Set

## Python的函式傳值機制: Call by assignment
- 改變函式傳入值會不會影響外部的變數，首先要看這個變數是屬於mutable還是immutable object
- 如果是immutable object，則函式內的改動不會影響外部的變數，例:
  
  ```python
  def foo(x):
    x += 1
    print("inner x=", x)
    
  a = 3 # Number是immutable object
  foo(a)
  print("outer a=", a)
  ```
  輸出結果:
  ```
  inner x= 4
  outer a= 3      <== 外部的a值不會變
  ```

- 如果是mutable object，那還要取決於你對它在函式內做了什麼處理。
  - 如果是「增加」、「減少」、「改變某一區間段的值」，則會影響外部變數的值。
  - 如果是「指定一個新的物件」(用`=`)，則在這個運算之後的所有運算都不再影響外部變數的值。
  
    ```python
    B = [x for x in range(10)]    # B是mutable物件

    def foo(L):
        for i in range(len(L)):
            L[i] = 100            # 更改第i項的值
            L = list(range(20))   # 指定一個新的list給L

    foo(B)
    print "B=", B
    ```
    輸出結果:
    ```
    B= [100, 1, 2, 3, 4, 5, 6, 7, 8, 9]
    ```

    像上面這例子，我們將`B`代入`foo()`中，一開始local variable `L`指向`B`，
    進入迴圈後，當`i=0`時，將`L[0]`改為100，由於這時的`L`和`B`仍然參照同一個物件，
    `B[0]`也會被改為100。而在下一行，我們把一個list object指定給`L`，
    這時`L`就會指向這個新的list object(即不再指向`B`)，
    之後函式當中雖然迴圈繼續進行且執行到`L[i]=100`來改值，但都不會再影響外層的`B`的內容。

## iterable, iterator, iteration, generator
- iterator: 
    - 當宣告類別有定義`__next__()`時，則這個物件可以當做iterator使用。
    - iterator可以使用內建函式`next()`來呼叫取得下一個reference的value，一旦下一個reference為invalid時就會raise `StopIteration` exception。
- iterable: 
    - 當宣告類別有定義`__iter__()`時，即表示這個類別為iterable object。
    - `__iter__()`必須回傳一個iterator。
        - 如果回傳值不是iterator則會產生`TypeError: iter() returned non-iterator of type 'Reverse'`。
- itertaion: 
    - 單純指對一個container做for loop運算。
    - 所以有iterable object都可以使用`for...in`運算。
- generator即為可以當作iterator使用的function object。
    - 只要function當中使用到`yield`關鍵字來回傳值，就會成為一個generator。當然，`__iter__()`和`__next__()`也會自動生成。
- 其它事項
    - 一個物件可以同時定義`__iter__()`和`__next__()`，這時候的`__iter__()`也可以指回傳`self`(因為含有`__next__()`，因此也是一個iterator)，
      像下面這樣：
    
      ```python
      class Reverse:
        """Iterator for looping over a sequence backwards."""
        def __init__(self, data):
            self.data = data
            self.index = len(data)

        def __iter__(self):
            return self

        def __next__(self):
            if self.index == 0:
                raise StopIteration
            self.index = self.index - 1
            return self.data[self.index]

      e = Reverse([3,4,5])
      e_iter = iter(e)
      print(next(e_iter))
      ```
      
      輸出結果:
      ```
      5
      ```
    - Python 2沒有`next()`方法，而是規定當物件有定義`next()`物件時即為iterator(和Python 3的`__next__()`也不同)
