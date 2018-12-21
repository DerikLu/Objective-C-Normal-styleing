# Objective-C-Normal-styling

Refer to https://github.com/NYTimes/objective-c-style-guide

## 屬性與方法

屬性使用`.`來呼叫，方法則使用中括號 `[ ]`

**For example**
```objc
view.backgroundColor = UIColor.orangeColor;
UIApplication.sharedApplication.delegate;
```

**Not**
```objc
[view setBackgroundColor:[UIColor orangeColor]];
[UIApplication sharedApplication].delegate;
```

## 方法

* 方法的宣告中，`-`與`+`前後需接一個空格，參數之間也接一個空格。
* 私有方法使用`_`為前綴字。
* 方法後之參數使用`the`為前綴字。

**For example**
```objc
// Public method
- (void)setExampleText:(NSString *)theText image:(UIImage *)theImage;

// Private method
- (void)_setupView;
```

## 關於換行

* `@synthesize` 及 `@dynamic` 每個都應該一個宣告一行。
* 方法與方法之間，需空一行，以便整理及視覺乾淨。

### 方法換行

方法之大括號 `{ }` 皆於新的一行

**For example**
```objc
- (void)_setupView
{
    // Do something
}
```

### 方法內換行

`if`/`else`/`switch`/`while` 大括號 `{ }`，起始於同一行，結束於下一行。

**For example**
```objc
if (user.isHappy) {
    // Do something
}
else {
    // Do something else
}
```

## 條件判斷

條件式的判斷必須用大括號來區分，不使用單行。

**For example**
```objc
if (!error) {
    return success;
}
```

**Not**
```objc
if (!error)
    return success;
    
if (!error) return success;
```

## 變數

變數命名使用首字小寫，駝峰式命名，以可立即看出變數意義為主，型態接於字串後方，且避免使用單一字母命名，除了`for`內之loop變數。

**For example**
* `NSString *title`: 可假設title為NSString型態。
* `NSString *titleHTML`: 可假設titleHTML為NSString型態。
* `NSAttributedString *titleAttributedString`
* `NSDate *now`: 可假設now為NSDate型態。
* `NSDate *lastModifiedDate`: 應明確定義出上次修改時間為NSDate型態。
* `NSURL *URL` vs. `NSString *URLString`
* `NSString *releaseDateString`: 命名為String可避免型態誤會的情形。

變數之指標與變數相關，因此應緊跟於變數

**For example**
```objc
NSString *text
```

**Not**
```objc
NSString* text 
NSString * text
```

#### 變數修飾詞

`__strong`, `__weak`, `__unsafe_unretained`, `__autoreleasing` 接於變數型態前面

**For example**
```objc
__weak NSString *text
```

## Categories

Categories命名以功能性為方向

**For example**

```objc
@interface UIViewController (NYTMediaPlaying)
@interface NSString (NSStringEncodingDetection)
```

**Not**

```objc
@interface NYTAdvertisement (private)
@interface NSString (NYTAdditions)
```

若增加方法或屬性於`Category`，其命名應使用app/organization做為前綴字，以避免與其他第三方`Category`相衝

**For example**

```objc
@interface NSArray (NYTAccessors)
- (id)nyt_objectOrNilAtIndex:(NSUInteger)index;
@end
```

**Not**

```objc
@interface NSArray (NYTAccessors)
- (id)objectOrNilAtIndex:(NSUInteger)index;
@end
```

## NSArray, NSDictionary

使用`@[]`及`@{}`來定義，Mutable則使用mutable copy方法

```objc
NSArray *array = @[@"1", @"2"];
NSDictionary *dict = @{@"key" : @"2"};

NSMutableArray *mutableArray = [@[@"1", @"2"] mutableCopy];
```
