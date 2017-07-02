---
layout: post
title: Markdown and HTML
---

Jekyll supports the use of [Markdown](http://daringfireball.net/projects/markdown/syntax) with inline HTML tags which makes it easier to quickly write posts with Jekyll, without having to worry too much about text formatting. A sample of the formatting follows.

Tables have also been extended from Markdown:

First Header  | Second Header
------------- | -------------
Content Cell  | Content Cell
Content Cell  | Content Cell

Here's an example of an image, which is included using Markdown:

![Geometric pattern with fading gradient]({{ site.baseurl }}/img/sample_feature_img_2.png)

Highlighting for code in Jekyll is done using Pygments or Rouge. This theme makes use of Rouge by default.

{% highlight java %}

public class ApplicationSingleton extends Application {

    public static ApplicationSingleton ourInstance;

    public ApplicationSingleton() {}

    @Override
    public void onCreate(){
        super.onCreate();
        ourInstance = this;
        initFabric();
        initOneSignal();
        initRealm();
        initHawk();
        OneSignal.clearOneSignalNotifications();
    }

    public static ApplicationSingleton getContext() {
        return ourInstance;
    }

    private void initRealm(){
        Realm.init(this);
        RealmConfiguration config = new RealmConfiguration.Builder()
                .name(Realm.DEFAULT_REALM_NAME)
                .schemaVersion(22)
                .deleteRealmIfMigrationNeeded()
                .build();
        Realm.setDefaultConfiguration(config);
    }

    private void initOneSignal(){
        OneSignal.startInit(this)
                .inFocusDisplaying(OneSignal.OSInFocusDisplayOption.Notification)
                .setNotificationOpenedHandler(new PushMessagesHandler())
                .init();
    }

    private void initHawk(){
        Hawk.init(this).build();
    }

    private void initFabric(){
        Fabric.with(this, new Crashlytics());
    }

}
{% endhighlight %}

Type Theme uses KaTeX to display maths. Equations such as $$S_n = a \times \frac{1-r^n}{1-r}$$ can be displayed inline.

Alternatively, they can be shown on a new line:

$$ f(x) = \int \frac{2x^2+4x+6}{x-2} $$
