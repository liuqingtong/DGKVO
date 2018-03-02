# DGKVO
好用的kvo封装工具，一句代码，即可搞定，减少代码的耦合
使用方法：
将工具类 DGKVOTool 文件拖入即可（目前使用的是最新的swift语言）。
将使用观察的地方调用即可。
eg:
class ViewController: UIViewController {
    
    var scrollView: UIScrollView?
    
    override func viewDidLoad() {
        super.viewDidLoad()
        
        scrollView = UIScrollView()
        scrollView?.frame = CGRect(x: 20, y: 20, width: self.view.frame.size.width - 40, height: 200)
        scrollView?.backgroundColor = UIColor.blue
        scrollView?.contentSize = CGSize(width: self.view.frame.size.width - 40, height: 800)
        self.view.addSubview(scrollView!)
        weak var ws = self
        let str = "滑动了"
        scrollView?.observe(self, keyPath: "contentOffset", closure: {
            print(str + "\(ws!.scrollView!.contentOffset.y)")
        })
    }
}
滑动scrollView 时，会执行打印效果，是不是节省了很多代理方法。
打印结果： 滑动了397.0
          滑动了397.0
          滑动了397.333333333333
          滑动了397.666666666667
          滑动了398.0
          滑动了398.0
