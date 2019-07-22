# Dialog 项目使用说明文档
### 使用步骤

#### 1. 引入第三方库

```groovy
 implementation 'com.liujc.util:jcdialog:1.0.1'
```



#### 2. 初始化 DialogUtils

```java
DialogUtils.init(mContext);
```

### 使用 PopupWindow

```java
private void initPopupWindow(View view){
        // 初始化 PopuWindowView
        final PopuWindowView popuWindowView = new PopuWindowView(this,
                LinearLayout.LayoutParams.WRAP_CONTENT);
        // 绑定数据和点击事件
        popuWindowView.initPupoData(new TdataListener() {
            @Override
            public void initPupoData(List<PopuBean> lists) {
                for (int i = 0; i < 5; i++) {
                    PopuBean popu = new PopuBean();
                    popu.setTitle("item"+i);
                    popu.setId(i);
                    lists.add(popu);
                }
            }

            @Override
            public void onItemClick(AdapterView<?> adapterView, View view, int position) {
                showToast(popuWindowView.getTitle(position));
                popuWindowView.dismiss();
            }
        });
        // 展示 PopuWindowView
        popuWindowView.showing(view);
    }
```

### 使用 LoadingDialog

#### 1. 横向 

```java
DialogUtils.showLoadingHorizontal(LoadingDialog.this, "加载中...").show();
```

#### 2. 竖向 

```java
DialogUtils.showLoadingVertical(LoadingDialog.this, "加载中...").show();
```

#### 3. 横向灰色

```java
DialogUtils.showLoadingHorizontal(LoadingDialog.this,"加载中...", false).show();
```

#### 4. 竖向灰色

```java
DialogUtils.showLoadingVertical(LoadingDialog.this, "加载中...", false).show();
```

#### 5. MD 风格的横向

```java
DialogUtils.showMdLoadingHorizontal(LoadingDialog.this,"加载中...").show();
```

#### 6. MD 风格的竖向

```java
DialogUtils.showMdLoadingVertical(LoadingDialog.this,"加载中...").show();
```

### 使用 Dialog

自定义文件 custom_dialog_layout.xml

#### 1. 自定义

```java
View rootView = View.inflate(DialogActivity.this,
                        R.layout.custom_dialog_layout, null);
                final Dialog dialog = DialogUtils
                        .showCustomAlert(DialogActivity.this,
                                rootView,
                                Gravity.CENTER,
                                true,
                                false)
                        .show();
                rootView
                        .findViewById(R.id.btn_ok)
                        .setOnClickListener(new View.OnClickListener() {
                            @Override
                            public void onClick(View v) {
                                DialogUtils.dismiss(dialog);
                            }
                        });
```

#### 2. 自定义底部

```java
 View rootViewB = View.inflate(DialogActivity.this,
                        R.layout.custom_dialog_layout,
                        null);
                DialogUtils.showCustomBottomAlert(DialogActivity.this,
                        rootViewB).show();
```

#### 3. MD 风格

```java
DialogUtils.showMdAlert(DialogActivity.this,
                        "标题",
                        "内容",
                        new DialogUIListener() {
                            @Override
                            public void onPositive() {
                                showToast("onPositive");
                            }

                            @Override
                            public void onNegative() {
                                showToast("onNegative");
                            }

                        }).show();
```

#### 4. 纯文本

```java
DialogUtils.showDialogTie(DialogActivity.this,
                        "纯文本 Dialog").show();
```

#### 5. 提示框

```java
DialogUtils.showAlert(DialogActivity.this,
                        "标题",
                        "提示框",
                        "aaa",
                        "bbb",
                        "确定",
                        "",
                        true,
                        new DialogUIListener() {
                            @Override
                            public void onPositive() {
                                showToast("onPositive");
                            }

                            @Override
                            public void onNegative() {
                                showToast("onNegative");
                            }

                        }).show();
```

#### 6. 水平

```java
DialogUtils.showAlert(DialogActivity.this,
                        "标题",
                        "内容",
                        "aaa",
                        "bbb",
                        "确定",
                        "取消",
                        false, new DialogUIListener() {
                            @Override
                            public void onPositive() {
                                showToast("onPositive");
                            }

                            @Override
                            public void onNegative() {
                                showToast("onNegative");
                            }

                        }).show();
```

#### 7. 竖向

```java
DialogUtils.showAlert(DialogActivity.this,
                        "标题",
                        "内容",
                        "aaa",
                        "bbb",
                        "确定",
                        "取消",
                        true,
                        new DialogUIListener() {
                            @Override
                            public void onPositive() {
                                showToast("onPositive");
                            }

                            @Override
                            public void onNegative() {
                                showToast("onNegative");
                            }

                        }).show();
```

#### 8. 输入框

```java
DialogUtils.showAlert(DialogActivity.this,
                        "登录",
                        "",
                        "请输入用户名",
                        "请输入密码",
                        "登录",
                        "取消",
                        false, new DialogUIListener() {
                            @Override
                            public void onPositive() {

                            }

                            @Override
                            public void onNegative() {

                            }

                            @Override
                            public void onGetInput(CharSequence input1, CharSequence input2) {
                                super.onGetInput(input1, input2);
                                showToast("input1:" + input1 + "--input2:" + input2);
                            }
                        }).show();
```
