# AppbarLayout联动RecyclerView不能展开问题
解决方案原文：http://blog.csdn.net/qq_23547831/article/details/52813145



解决方案:

```
recyclerView.addOnScrollListener(object : RecyclerView.OnScrollListener() {
            override fun onScrolled(recyclerView: RecyclerView?, dx: Int, dy: Int) {
            }

            override fun onScrollStateChanged(recyclerView: RecyclerView?, newState: Int) {
                if (newState == RecyclerView.SCROLL_STATE_IDLE) {
                    var visiblePosition = linearLayoutManager.findFirstCompletelyVisibleItemPosition()
                    if (visiblePosition == 0) {
                        barLayout.setExpanded(true, true)
                    }
                }
            }
        })
```