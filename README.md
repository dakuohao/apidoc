# apidoc

励志做Java届最好用的文档工具，工具解析Java代码自动生成api接口文档，不要人工写文档，写注释，写注解，统统不要，彻底解放后端开发人员，彻底告别写文档的烦恼

程序员都喜欢写代码，写文档总是大难题，我以前为了解决这个问题开发了apidoc第一版，地址在这里 https://gitee.com/lovepeng/api-doc ，类似swagger，但是写大量的Java注解/注释，超级恶心。所以我写了这个apidoc第二版。

## 项目地址  https://gitee.com/lovepeng/apidoc2


# 使用方式
> run ApidocApplication.class 的main方法即可看到预览版

将本项目打为jar包，引入你的项目

在你需要生成文档的controller上加一个注解`@Api("这里写模块名称")`

注意：如果一个模块由多个controller组成，只需要保证模块名称一样就行

例如：
```
@Api("测试请求参数类型")//同模块下多个controller时，保证模块名称一致即可
@RestController
@RequestMapping("/testRequestParamType")
public class TestRequestParamTypeController {

    @GetMapping(value = "/url")
    public Result url() {
        return Result.success();
    }
```
# 预览
![界面预览](https://images.gitee.com/uploads/images/2018/0830/132440_d99c53a5_929906.png "屏幕截图.png")
## 界面说明：
## 文档基本信息
点击可以编辑/保存

基本信息

![基本信息](https://images.gitee.com/uploads/images/2018/0830/132603_3a316a51_929906.png "屏幕截图.png")

基本信息编辑

![基本信息编辑](https://images.gitee.com/uploads/images/2018/0830/132642_02790f13_929906.png "屏幕截图.png")


## 目录
左侧为目录，一级目录为模块名称，二级目录为接口名称（默认读取controller的public方法的注释），目录双击可以修改，拖拽可以排序

目录

![目录](https://images.gitee.com/uploads/images/2018/0830/132540_e28c1596_929906.png "屏幕截图.png")

双击修改

![双击修改](https://images.gitee.com/uploads/images/2018/0830/132723_56d7b200_929906.png "屏幕截图.png")

拖拽排序

![拖拽排序](https://images.gitee.com/uploads/images/2018/0830/132814_128c90a4_929906.png "屏幕截图.png")

## 演示，自带mocke功能，用来替代测试postman等测试工具，方便文档使用人员
演示功能

![演示，自带mock功能](https://images.gitee.com/uploads/images/2018/0830/132858_e4463fe0_929906.png "屏幕截图.png")

## 接口信息
点击描述可以编辑/保存

接口信息

![接口信息](https://images.gitee.com/uploads/images/2018/0830/132945_9a705fb1_929906.png "屏幕截图.png")

编辑信息

![编辑](https://images.gitee.com/uploads/images/2018/0830/133020_b24ba4ef_929906.png "屏幕截图.png")

## 请求参数
可以在线编辑

请求参数

![请求参数](https://images.gitee.com/uploads/images/2018/0830/133040_95aa228c_929906.png "屏幕截图.png")

编辑界面

![编辑界面](https://images.gitee.com/uploads/images/2018/0830/133111_c5ba6cbf_929906.png "屏幕截图.png")

## 响应参数
点击可以编辑
响应参数

![响应参数](https://images.gitee.com/uploads/images/2018/0830/133127_677c0ffa_929906.png "屏幕截图.png")

编辑界面

![编辑界面](https://images.gitee.com/uploads/images/2018/0830/133148_9e388d0a_929906.png "屏幕截图.png")

## 示例
示例

![示例自动生成](https://images.gitee.com/uploads/images/2018/0830/133206_ddd14ab3_929906.png "屏幕截图.png")

### 兼容restful接口和普通接口，兼容json类型，兼容二进制流格式，兼容各种请求参数，from类型，json类型等等，请求参数/响应参数支持java对象的自嵌套，互相嵌套，而且会根据参数自动生成测试/演示参数，如果你设置了默认值，演示参数的默认值会自动更改

# 代码说明
技术架构：

- 标准的前后端分离开发模型
- 标准的RESTful接口风格
- 前端使用标准的“组件化”开发模式，技术架构为angualr6.x（最新版，目前组件化支持最好的前端框架）
- 后端使用标准的“模块化”开发模式，技术架构spring-boot（1.5版本，模块化最标准的java框架）
- 数据存储为json，实现了一个类似mongodb的小存储功能，目的是后期做离线文档方便，而且不引人mysql等数据库会让工具使用者更加方便
- 代码中使用的大量的递归，甚至我用html也写了一个递归，是个理解递归的不错案例
- 代码基于json构建的，是一个很好的json使用的案例
- 代码非常简洁，核心代码也就800行左右，了解源码的请关注com.apidoc.utis.GeneratorUtil这个类

项目结构：

```
-- apidoc                           项目名称
    --apidoc-angular                前端代码实现angular6
    --data                          数据存储目录
    --src                           后端代码实现
    --pom.xml                       pom文件
    --.gitignore                    git忽略文件
    -- readme.md                    项目说明
```
# 近期添加功能
1. springboot快速集成
2. 支持各大mvc框架
3. 文档可以离线
4. 增加权限
5. 增加版本控制，可以查看历史文档
6. 看时间安排吧

## 反馈建议
- 点击反馈 https://gitee.com/lovepeng/api-doc/issues
- QQ群：324133980

#### 支付宝扫码，你会获得2毛到99元现金，同时会给我捐赠几分钱，请我喝个茶吧，谢谢
![](https://images.gitee.com/uploads/images/2018/0830/135038_45d6b347_929906.png "屏幕截图.png")
