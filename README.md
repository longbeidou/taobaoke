# taobaoke for laravel #
> 关于taobaoke包的说明

taobaoke是专为laravel开发的淘宝客开发包，由阿里妈妈提供的淘宝客sdk修改而成。关于淘宝客的更多信息请查看[淘宝API的文档](http://open.taobao.com/api.htm?docId=24515&docType=2)。

> 安装包的步骤

步骤一：

    composer require "longbeidou/taobaoke:dev-master"

步骤二：

	composer dump-autoload

步骤三：

在config/app.php中的provider数组中加入

	Longbeidou\Taobaoke\TaobaokeServiceProvider::class,

在config/app.php中的aliases数组中加入

	'Taobaoke' => Longbeidou\Taobaoke\Facades\Taobaoke::class,

步骤四：

	php artisan vendor:publish --provider="Longbeidou\Taobaoke\TaobaokeServiceProvider"

> 使用包的步骤

在使用包以前需要先配置包的文件，位置在
	
	/config/taobaoke.php

配置文件中的appkey和secretKey为必填，填写的值请到[阿里妈妈淘宝联盟](http://www.alimama.com "阿里妈妈淘宝联盟")申请。


方法一：契约的使用方法

在文件开始加入

    use Longbeidou\Taobaoke\Contracts\Contract as Alimama;

通过构造函数注入

	public $alimama;

    public function __construct(Alimama $c)
    {
        $this->alimama = $c;
    }

在方法中使用

	public function test()
    {
        $info = $this->alimama->taobaoTbkDgItemCouponGet(['adzone_id'=>'1459254918']);
        dd($info);
    }

方法二：门面的使用方法

在文件开始加入

	use Taobaoke;

在方法中使用

	public function test()
    {
        $info2 = Taobaoke::taobaoTbkDgItemCouponGet(['adzone_id'=>'1459254918']);
        dd($info2);
    }


> 获取商品的方法（目前集成的方法，后续会继续更新）

	// 淘宝客基础API
	/**
	* 淘宝客商品查询
	*/
	public function taobaoTbkItemGet(Array $datas);

	/**
	* 淘宝客商品查询
	*/
	public function taobaoTbkItemRecommendGet(Array $datas);

	/**
	* 淘宝客商品详情（简版）
	*/
	public function taobaoTbkItemInfoGet(Array $datas);

	/**
	* 淘宝客店铺查询
	*/
	public function taobaoTbkShopGet(Array $datas);

	/**
	* 淘宝客店铺关联推荐查询
	*/
	public function taobaoTbkShopRecommendGet(Array $datas);

	/**
	* 枚举正在进行中的定向招商的活动列表
	*/
	public function taobaoTbkUatmEventGet(Array $datas);

	/**
	* 获取淘宝联盟定向招商的宝贝信息
	*/
	public function taobaoTbkUatmEventItemGet(Array $datas);

	/**
	* 获取淘宝联盟选品库的宝贝信息
	*/
	public function taobaotbkUatmFavoritesItemGet(Array $datas);

	/**
	* 获取淘宝联盟选品库列表
	*/
	public function taobaoTbkUatmFavoritesGet(Array $datas);

	/**
	* 淘抢购api
	*/
	public function taobaoTbkJuTqgGet(Array $datas);

	/**
	* 物料传播方式获取
	*/
	public function taobaoTbkSpreadGet(String $url);

	/**
	* 聚划算商品搜索接口
	*/
	public function taobaoJuItemsSearch(Array $datas);

	/**
	* 好券清单API【导购】
	*/
	public function taobaoTbkDgItemCouponGet(Array $datas);

	/**
	* 阿里妈妈推广券信息查询
	*/
	public function taobaoTbkCouponGet(Array $datas);

	/**
	* 淘宝客淘口令
	*/
	public function taobaoTbkTpwdCreate(Array $datas);

	/**
	* 淘宝客新用户订单API--导购
	*/
	public function taobaoTbkDgNewuserOrderGet(Array $datas);

	/**
	* 淘宝客新用户订单API--社交
	*/
	public function taobaoTbkScNewuserOrderGet(Array $datas);

	/**
	* 通用物料搜索API
	*/
	public function taobaoTbkScMaterialOptional(Array $datas);

	/**
	* 通用物料搜索API（导购）
	*/
	public function taobaoTbkDgMaterialOptional(Array $datas);

	/**
	* 拉新活动汇总API--导购
	*/
	public function taobaoTbkDgNewuserOrderSum(Array $datas);

	/**
	* 拉新活动汇总API--社交
	*/
	public function taobaoTbkScNewuserOrderSum(Array $datas);

	// 淘口令基础包
	/**
	* 生成淘口令
	*/
	public function taobaoWirelessShareTpwdCreate(Array $datas);

	/**
	* 查询解析淘口令
	*/
	public function taobaoWirelessShareTpwdQuery(String $tpwd);

	// 淘宝客-工具-超级搜索    注：已经存在
	/**
	* 通用物料搜索API
	*/
	// public function taobaoTbkScMaterialOptional(Array $datas);

	/**
	* 淘客媒体内容输出
	*/
	public function taobaoTbkContentGet(Array $datas);

	/**
	* 淘宝客擎天柱通用物料API
	*/
	public function taobaoTbkDgOptimusMaterial(Array $datas);

	/**
	* 淘宝客擎天柱通用物料API
	*/
	public function taobaoTbkScOptimusMaterial(Array $datas);

	// 淘宝客-媒体-单品券高效转链包
	/**
	* 【导购】链接转换
	*/
	public function taobaoTbkCouponConvert(Array $datas);

	// 淘宝客链接API
	/**
	* 淘宝客商品链接转换
	*/
	public function taobaoTbkItemConvert(Array $datas);

	/**
	* 淘宝客店铺链接转换
	*/
	public function taobaoTbkShopConvert(Array $datas);

	/**
	* 淘口令转链
	*/
	public function taobaoTbkTpwdConvert(Array $datas);

传递的参数说明：统一使用数组传递请求参数，具体请求参数见[淘宝API的文档](http://open.taobao.com/api.htm?docId=24515&docType=2)。如果数组中加入无效的参数，方法会忽略掉。

> 使用案例

[龙琴时代优惠券购物网站](http://www.52010000.cn)：PC端[http://www.52010000.cn](http://www.52010000.cn "龙琴时代优惠券购物网站")；WX端[http://m.52010000.cn](http://www.52010000.cn "龙琴时代优惠券购物网站")。