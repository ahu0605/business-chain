# business-chain
责任链衍化出的业务链，用于规范代码逻辑，第一版本中加入了异常捕获，后来发现这种设计并不可取，现已移除

目前二维火确认下单流程已经用该模型重构，这种结构适合判断逻辑非常多的情况，以二维火下单为例，我们的预付款流程、正常流程下又存在不同购物车的不同逻辑，用这个模型可以节省大量的if else 判断

之前出现过多线程问题，建议使用方式是：
1.各个businessNode一定不能为单例。（如果需要托管给spring的节点，一定要注入成prototype）
2.如果businessNode节点为单例，则需要把完整的channel提前构建出来。
