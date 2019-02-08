# Appium-Test
Mobile Automaties Testing
##### unittest


##### 单元测试
##### 流程测试
```unnitest```里头的test数组存放的```TestCase```默认是以首字母来排序
正常的情况下是按照test1,test2,test3...testn来排序
可是test1,test11,test12,test2那就是按照首字母来排序那执行就是有问题的
顾需要进行定制化的修改。

情况1：case之间相互独立，独立运行
情况2：某些case建立在另一个case之上
先把异常都跑好，再跑正常
```python3
def test_case1()
def test_case2()
def test_case3()
```

```unittest.TextTestRuner()```
```unittest.TestSuite()```
##### 两种构造测试集封装
###### 实例1：
这是单独写在test_suite.py里头的，test_suite.py将所有模块的脚本都封装在这里头进行运行及其生成报告，下面是一个demo,这里使用的是```map()```函数进行构建测试集，可以很方便的选择性执行需要的用例，不需要全执行全部测试用例，这样很方便调试。
```
import unittest
from test_login import LoginTest
from test_register import RegisterTest

if __name__ == '__main__':
  test_runner= unittest.TextTestRunner()
  test_suite= unittest.TestSuite()
  test_suite.addTests(map(LoginTest,["test_login_wrongphone","test_login_wrongmail"]))
  test_suite.addTests(map(RegisterTest,["test_register_wrongphone","test_register_wrongmail"]))
  test_runner.run(test_suite)
```
###### 实例2：
不使用```map()```函数，直接封装运行所有的测试用例集。
```
import unittest
from test_login import LoginTest
from test_register import RegisterTest

if __name__ =='__main__':
  test_runner = unittest.TextTestRunner()
  test_suite = unittest.TestSuite()
  test_suite.addTest(unittest.TestLoader().unittest.loadTestsFromTestCase(LoginTest))
  test_suite.addTest(unittest.TestLoader().unittest.loadTestsFromTestCase(RegisterTest))
  test_runner.run(test_suite)
```
##### 联合HTMLTestRunner使用

