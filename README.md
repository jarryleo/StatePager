# StatePager
安卓状态页loading，empty，error，success等页面状态切换库

### 优点
> - 不需要修改项目布局，直接使用；
> - 延迟加载，不需要预先加载所有状态布局，切换状态后之前页面会被垃圾回收；

#### 举个栗子：
```
 mStatePager = StatePager.builder(mRecyclerView)
                .loadingViewLayout(R.layout.pager_loading)
                .emptyViewLayout(R.layout.pager_empty)
                .errorViewLayout(R.layout.pager_error)
                .addRetryButtonId(R.id.tv_tips)
                .addRetryButtonId(R.id.btn_retry)
                .setRetryClickListener(new StatePager.OnClickListener() {
                    @Override
                    public void onClick(StatePager statePager, View v) {
                        if (v.getId() == R.id.btn_retry) {
                            statePager.showSuccess();
                        } else {
                            statePager.showError()
                                    .setText(R.id.btn_retry, "哦哦，失败了，点击重试一下？");
                        }
                    }
                })
                .build();

        mStatePager.showLoading()
                .setText(R.id.tv_tips, "正在使出吃奶的力气加载");
```

#### usage:

复制类[StatePager.java](https://github.com/jarryleo/StatePager/blob/master/app/src/main/java/cn/leo/statepager/StatePager.java) 到项目中使用
