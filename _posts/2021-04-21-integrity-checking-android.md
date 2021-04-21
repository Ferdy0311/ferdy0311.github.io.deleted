---
layout: post
title:  "Integrity Checking on Android"
date:   2021-04-21 09:12:00 +0700
categories: flask
---

Integrity Check Function by Comparing crc value of `classes.dex`
{% highlight kotlin %}
fun integrityCheck(): Boolean {
    var modified: Boolean = true
    var zf: ZipFile = ZipFile(this.applicationContext.packageCodePath)
    var ze: ZipEntry = zf.getEntry("classes.dex")

    var dexValue: String = this.applicationContext.getString(R.string.dex_value)

    if (ze.crc.toString() == dexValue) {
        modified = false
    }

    return modified
}
{% endhighlight %}

Insert `dex_value` into string.xml File
{% highlight xml %}
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <string name="dex_value">YOUR_DEX_VALUE</string>
</resources>
{% endhighlight %}

Getting `dex_value` in Java
{% highlight java %}
public static void main(String[] args) {
    try {
        System.out.print("Dex Value : ");
        ZipFile zipFile = new ZipFile("YOUR_APK_FILE.apk");
        ZipEntry zipEntry = zipFile.getEntry("classes.dex");
        System.out.println(zipEntry.getCrc());
    } catch (Exception e) {
        System.out.println(e);
    }
}
{% endhighlight %}