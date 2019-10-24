坑点1号SpanUtils
完全点击不到。原因这个工具里面的代码写的不够严谨导致的。
 tv.append(spanUtils.setSubscript().append("dasdadasd").setClickSpan(new ClickableSpan() {
            @Override
            public void onClick(View widget) {
                Toast.makeText(My23TextStyleActivity.this, "服了这都能点击", Toast.LENGTH_SHORT).show();
            }
        }).create());
        
  public SpanUtils setClickSpan(@NonNull final ClickableSpan clickSpan) {
        if (mTextView != null && mTextView.getMovementMethod() == null) {
            mTextView.setMovementMethod(LinkMovementMethod.getInstance());  //这里一直不执行mTextView 为null
        }
        this.clickSpan = clickSpan;
        return this;
    }
        
        修改方式  使用这个构造函数 即可  
public SpanUtils(TextView textView) {
        this();
        mTextView = textView;
    }
