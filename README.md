
 *  <Pre>
 * 自定义图片自动轮播控件，自定轮播指示器样式，支持点击，无限轮播，网络下载图片</br>
 * 可是使用XUtil的BitmapUtils也可是使用smart-image-view加载图片，支持轮播文字切换</br>
 * 此插件是基于viewpager实现的,需要导入android-support-v4.jar</br></br>
 *
 * 如果使用网络图片记得加权限。</br>
 * uses-permission android:name="android.permission.INTERNET"
 * uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"
 *
 * 主要功能:</br></br>
 * 1.支持设置文字提示</br>
 * 2.支持修改轮播指示器的样式及位置（修改view_cycle_image.xml样式,不能修改id）</br>
 * 3.支持修改文字提样式及位置（修改view_cycle_image.xml样式,不能修改id）</br>
 * 4.支持设置是否开启自动轮播</br>
 * 5.支持运行中启动和停止自动轮播</br>
 * 6.支持网络加载图片，资源图片id，sd卡图片</br>
 * 7.设置支持XUtil的BitmapUtils也可是使用smart-image-view加载图片</br>
 * 8.支持点击事件</br>
 * 9.默认是第一张</br></br>
 *
 * demo实例:</br> </br>
<pre>
* 	  mImageCycleView = (ImageCycleView) findViewById(R.id.icv_topView);
* 	 	//mImageCycleView.setAutoCycle(false); //关闭自动播放
* 		mImageCycleView.setCycleDelayed(2000);//设置自动轮播循环时间
* 
* 		mImageCycleView.setIndicationStyle(ImageCycleView.IndicationStyle.COLOR,
* 				Color.BLUE, Color.RED, 1f);
* 
* //		mImageCycleView.setIndicationStyle(ImageCycleView.IndicationStyle.IMAGE,
* //				R.drawable.dian_unfocus, R.drawable.dian_focus, 1f);
* 
* 
* 		List<ImageCycleView.ImageInfo> list=new ArrayList<ImageCycleView.ImageInfo>();
* //		list.add(new ImageCycleView.ImageInfo(R.drawable.a1,"111111111111",""));
* //		list.add(new ImageCycleView.ImageInfo(R.drawable.a2,"222222222222222",""));
* //		list.add(new ImageCycleView.ImageInfo(R.drawable.a3,"3333333333333",""));
* 
* 		//使用网络加载图片
* 		list.add(new ImageCycleView.ImageInfo("http://img.lakalaec.com/ad/57ab6dc2-43f2-4087-81e2-b5ab5681642d.jpg","11","eeee"));
* 		list.add(new ImageCycleView.ImageInfo("http://img.lakalaec.com/ad/cb56a1a6-6c33-41e4-9c3c-363f4ec6b728.jpg","222","rrrr"));
* 		list.add(new ImageCycleView.ImageInfo("http://img.lakalaec.com/ad/e4229e25-3906-4049-9fe8-e2b52a98f6d1.jpg", "333", "tttt"));
* 
* 		mImageCycleView.setOnPageClickListener(new ImageCycleView.OnPageClickListener() {
* 			@Override
* 			public void onClick(View imageView, ImageCycleView.ImageInfo imageInfo) {
* 				Toast.makeText(MainActivity.this, "你点击了" + imageInfo.value.toString(), Toast.LENGTH_SHORT).show();
* 			}
* 		});
* 
* 		mImageCycleView.loadData(list, new ImageCycleView.LoadImageCallBack() {
* 			@Override
* 			public ImageView loadAndDisplay(ImageCycleView.ImageInfo imageInfo) {
* 
* 				//本地图片
* //				ImageView imageView=new ImageView(MainActivity.this);
* //				imageView.setImageResource(Integer.parseInt(imageInfo.image.toString()));
* //				return imageView;
* 
* 				//使用SmartImageView，既可以使用网络图片也可以使用本地资源
* //				SmartImageView smartImageView=new SmartImageView(MainActivity.this);
* //				smartImageView.setImageResource(Integer.parseInt(imageInfo.image.toString()));
* //				return smartImageView;
* 
* 				//使用BitmapUtils,只能使用网络图片
* 				BitmapUtils bitmapUtils = new BitmapUtils(MainActivity.this);
* 				ImageView imageView = new ImageView(MainActivity.this);
* 				bitmapUtils.display(imageView, imageInfo.image.toString());
* 				return imageView;
* 
* 
* 			}
* 		});
* 		</pre>

