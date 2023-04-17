# Salesforce MarketingCloud Binding Project

### This is a native Salesforce MarketingCloud Binding Project for Xamarin Android

##### _SDKs (AAR):_
- com.salesforce.marketingcloud:marketingcloudsdk `v8.0.8`
- com.salesforce.marketingcloud:sfmcsdk `v1.0.2`
- org.altbeacon:android-beacon-library `v2.19.3`
- androidx.constraintlayout:constraintlayout `v2.1.4`


##### _Requirement (Xamarin Android):_
- Android requires a minimum API `v21`
- Xamarin.Firebase.Messaging `v123.1.1.1`
- Xamarin.GooglePlayServices.Gcm `v117.0.0.8`
- Xamarinn.AndroidX.ConstraintLayout `v2.1.4.3`
- File `google-service.json` set Build Action as GoogleServicesJson

##### _Example:_

```csharp

// Nessessary namespaces
using Com.Salesforce.Marketingcloud;
using Com.Salesforce.Marketingcloud.Sfmcsdk;
using Com.Salesforce.Marketingcloud.Notifications;

// Create a marketing cloud config
var marketingCloudConfig = Com.Salesforce.Marketingcloud.MarketingCloudConfig
      .InvokeBuilder()
      .SetApplicationId("xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx")
      .SetAccessToken("access token")
      .SetSenderId("xxxxxxxxxxxx")
      .SetMid("xxxxxxxxx")
      .SetNotificationCustomizationOptions(NotificationCustomizationOptions.Create(0)) // where 0 is resource id your icon
      .SetMarketingCloudServerUrl("https://xxxxxxxxxxxxxxxxxxx.device.marketingcloudapis.com/")
      .SetInboxEnabled(true)
      .SetAnalyticsEnabled(true)
      .SetPiAnalyticsEnabled(true)
      .SetGeofencingEnabled(true)
      .SetProximityEnabled(true)
      .Build(Application.Context);

// Init a SFMCSdk builder
var config = new SFMCSdkModuleConfig.Builder();

// Assign marketing cloud config to push mobile config
config.PushModuleConfig = marketingCloudConfig;

// Make a SFMCSdk builder
var builder = config.Build();

// Configure SFMCSdk
SFMCSdk.Configure(Application.Context, builder);

// Request listener as current class (ISFMCSdkReadyListener)
SFMCSdk.RequestSdk(this);

// SFMCSdk handler (here you can get a SDK status)
public void Ready(SFMCSdk sdk)
{
    // There is a push connection status
}
```

## Documents
- [Marketing Cloud SDK for Android](https://salesforce-marketingcloud.github.io/MarketingCloudSDK-Android/)
- [Binding a Java Library in Xamarin Android](https://learn.microsoft.com/en-us/xamarin/android/platform/binding-java-library/)

