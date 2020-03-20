---
title: Změna úrovní sdílení mezipaměti pro aktivity odesílání
ms.date: 03/30/2017
ms.assetid: 03926a64-753d-460e-ac06-2a4ff8e1bbf5
ms.openlocfilehash: 101aab98a7d34ad45ad29efbe252cff0814ca290
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185397"
---
# <a name="changing-the-cache-sharing-levels-for-send-activities"></a>Změna úrovní sdílení mezipaměti pro aktivity odesílání
Rozšíření <xref:System.ServiceModel.Activities.SendMessageChannelCache> umožňuje přizpůsobit úrovně sdílení mezipaměti, nastavení mezipaměti kanálu a nastavení mezipaměti kanálu pro pracovní postupy, <xref:System.ServiceModel.Activities.Send> které odesílají zprávy koncovým bodům služby pomocí aktivit zasílání zpráv. Tyto pracovní postupy jsou obvykle pracovní postupy klienta, ale mohou být také služby pracovního postupu, které jsou hostovány v <xref:System.ServiceModel.WorkflowServiceHost>. Mezipaměť kanálu factory <xref:System.ServiceModel.ChannelFactory%601> obsahuje objekty uložené v mezipaměti. Mezipaměť kanálu obsahuje kanály uložené v mezipaměti.  
  
> [!NOTE]
> Pracovní postupy <xref:System.ServiceModel.Activities.Send> mohou používat aktivity zasílání zpráv k odesílání zpráv nebo parametrů. Za běhu pracovního postupu přidá továrny kanálu <xref:System.ServiceModel.Channels.IRequestChannel> do mezipaměti, které vytvářejí kanály typu <xref:System.ServiceModel.Activities.Send> při <xref:System.ServiceModel.Activities.ReceiveReply>použití <xref:System.ServiceModel.Activities.ReceiveReply> aktivity s aktivitou <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Channels.IOutputChannel> při použití pouze aktivity (ne).  
  
## <a name="the-cache-sharing-levels"></a>Úrovně sdílení mezipaměti  
 Ve výchozím nastavení je v <xref:System.ServiceModel.WorkflowServiceHost> pracovním postupu <xref:System.ServiceModel.Activities.Send> hostovaném mezipamětí používanou aktivitami zasílání zpráv sdílena ve všech instancích pracovního postupu v oblasti <xref:System.ServiceModel.WorkflowServiceHost> (ukládání do mezipaměti na úrovni hostitele). Pro klienta pracovní postup, který není hostované <xref:System.ServiceModel.WorkflowServiceHost>, mezipaměť je k dispozici pouze pro instanci pracovního postupu (ukládání do mezipaměti na úrovni instance). Mezipaměť je k <xref:System.ServiceModel.Activities.Send> dispozici pouze pro aktivity, které nepoužívají koncové body definované v konfiguraci, pokud není povoleno nebezpečné ukládání do mezipaměti.  
  
 Níže jsou uvedeny různé úrovně <xref:System.ServiceModel.Activities.Send> sdílení mezipaměti, které jsou k dispozici pro aktivity v pracovním postupu, a jejich doporučené použití:  
  
- **Úroveň hostitele**: Na úrovni sdílení hostitele je mezipaměť k dispozici pouze pro instance pracovního postupu hostované v hostiteli služby pracovního postupu. Mezipaměť lze také sdílet mezi hostiteli služby pracovního postupu v mezipaměti pro celý proces.  
  
- **Úroveň instance**: V úrovni sdílení instance je mezipaměť k dispozici pro konkrétní instanci pracovního postupu po celou dobu její životnosti, ale mezipaměť není k dispozici pro jiné instance pracovního postupu.  
  
- **Žádná mezipaměť**: Mezipaměť je ve výchozím nastavení vypnutá, pokud máte pracovní postup, který používá koncové body definované v konfiguraci. V tomto případě je také doporučeno ponechat mezipaměť vypnutou, protože její zapnutí může být nezabezpečené. Například pokud je pro každé odeslání vyžadována jiná identita (jiná pověření nebo použití zosobnění).  
  
## <a name="changing-the-cache-sharing-level-for-a-client-workflow"></a>Změna úrovně sdílení mezipaměti pro pracovní postup klienta  
 Chcete-li nastavit sdílení mezipaměti v pracovním <xref:System.ServiceModel.Activities.SendMessageChannelCache> postupu klienta, přidejte instanci třídy jako rozšíření požadované sady instancí pracovního postupu. Výsledkem je sdílení mezipaměti ve všech instancích pracovního postupu. Následující příklady kódu ukazují, jak provést tyto kroky.  
  
 Nejprve deklarujte <xref:System.ServiceModel.Activities.SendMessageChannelCache>instanci typu .  
  
```csharp  
// Create an instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension =  
    new SendMessageChannelCache();  
```  
  
 Dále přidejte rozšíření mezipaměti do každé instance pracovního postupu klienta.  
  
```csharp
WorkflowApplication clientInstance1 = new WorkflowApplication(new clientWorkflow1());  
WorkflowApplication clientInstance2 = new WorkflowApplication(new clientWorkflow2());  
  
// Share the cache extension object
  
clientInstance1.Extensions.Add(sharedChannelCacheExtension);  
clientInstance2.Extensions.Add(sharedChannelCacheExtension);  
```  
  
## <a name="changing-the-cache-sharing-level-for-a-hosted-workflow-service"></a>Změna úrovně sdílení mezipaměti pro hostovkou služby pracovního postupu  
 Chcete-li nastavit sdílení mezipaměti v hostované službě <xref:System.ServiceModel.Activities.SendMessageChannelCache> pracovního postupu, přidejte instanci třídy jako rozšíření ke všem hostitelům služby pracovního postupu. Výsledkem je sdílení mezipaměti mezi všemi hostiteli služby pracovního postupu. Následující příklady kódu ukazují provést tyto kroky.  
  
 Nejprve deklarujte <xref:System.ServiceModel.Activities.SendMessageChannelCache> instanci typu na úrovni třídy.  
  
```csharp  
// Create static instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension = new  
    SendMessageChannelCache();  
```  
  
 Dále přidejte rozšíření statické mezipaměti ke každému hostiteli služby pracovního postupu.  
  
```csharp  
WorkflowServiceHost host1 = new WorkflowServiceHost(new serviceWorkflow1(), new Uri(baseAddress1));  
WorkflowServiceHost host2 = new WorkflowServiceHost(new serviceWorkflow2(), new Uri(baseAddress2));  
  
// Share the static cache to get an AppDomain level cache.  
host1.WorkflowExtensions.Add(sharedChannelCacheExtension);  
host2.WorkflowExtensions.Add(sharedChannelCacheExtension);  
```  
  
 Chcete-li nastavit sdílení mezipaměti ve službě hostovaného `Func<SendMessageChannelCache>` pracovního postupu na úroveň instance, přidejte delegáta jako rozšíření k hostiteli služby pracovního postupu a přiřaďte tohoto delegáta ke kódu, který instancije novou instanci <xref:System.ServiceModel.Activities.SendMessageChannelCache> třídy. Výsledkem je jiná mezipaměť pro každou jednotlivé instance pracovního postupu namísto jedné mezipaměti sdílené všemi instancemi pracovního postupu v hostiteli služby pracovního postupu. Následující příklad kódu ukazuje, jak toho dosáhnout pomocí výrazu <xref:System.ServiceModel.Activities.SendMessageChannelCache> lambda k přímému definování rozšíření, na které delegát odkazuje.  
  
```csharp
serviceHost.WorkflowExtensions.Add(() => new SendMessageChannelCache  
{  
    // Use FactorySettings property to add custom factory cache settings.  
    FactorySettings = new ChannelCacheSettings
    { MaxItemsInCache = 5, },  
    // Use ChannelSettings property to add custom channel cache settings.  
    ChannelSettings = new ChannelCacheSettings
    { MaxItemsInCache = 10 },  
});  
```  
  
## <a name="customizing-cache-settings"></a>Přizpůsobení nastavení mezipaměti  
 Nastavení mezipaměti můžete přizpůsobit pro mezipaměť kanálu a mezipaměť kanálu. Nastavení mezipaměti jsou <xref:System.ServiceModel.Activities.ChannelCacheSettings> definovány ve třídě. Třída <xref:System.ServiceModel.Activities.SendMessageChannelCache> definuje výchozí nastavení mezipaměti pro vyrovnávací paměť kanálu a mezipaměť kanálu v jeho konstruktoru bez parametrů. V následující tabulce jsou uvedeny výchozí hodnoty těchto nastavení mezipaměti pro každý typ mezipaměti.  
  
|Nastavení|LeaseTimeout (min)|IdleTimeout (min)|MaxItemsv mezipaměti|  
|-|-|-|-|  
|Výchozí vyrovnávací paměť z výroby|Timespan.maxvalue|2|16|  
|Výchozí mezipaměť kanálu|5|2|16|  
  
 Chcete-li přizpůsobit nastavení mezipaměti výroby a <xref:System.ServiceModel.Activities.SendMessageChannelCache> mezipaměti kanálu, vytvořte instanci třídy pomocí parametrizovaného <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> konstruktoru a předejte novou instanci <xref:System.ServiceModel.Activities.ChannelCacheSettings> s vlastními hodnotami každému z parametrů `factorySettings` a. `channelSettings` Dále přidejte novou instanci této třídy jako rozšíření k hostiteli služby pracovního postupu nebo instanci pracovního postupu. Následující příklad kódu ukazuje, jak provést tyto kroky pro instanci pracovního postupu.  
  
```csharp  
ChannelCacheSettings factorySettings = new ChannelCacheSettings{  
                        MaxItemsInCache = 5,
                        IdleTimeout = TimeSpan.FromMinutes(5),
                        LeaseTimeout = TimeSpan.FromMinutes(20)};  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings{  
                        MaxItemsInCache = 5,
                        IdleTimeout = TimeSpan.FromMinutes(2),  
                        LeaseTimeout = TimeSpan.FromMinutes(10) };  
  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache(factorySettings, channelSettings);  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 Chcete-li povolit ukládání do mezipaměti, pokud má služba <xref:System.ServiceModel.Activities.SendMessageChannelCache> pracovního postupu koncové <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> body `allowUnsafeCaching` definované v `true`konfiguraci, vytvořte instanci třídy pomocí parametrizovaného konstruktoru s parametrem nastaveným na . Dále přidejte novou instanci této třídy jako rozšíření k hostiteli služby pracovního postupu nebo instanci pracovního postupu. Následující příklad kódu ukazuje, jak povolit ukládání do mezipaměti pro instanci pracovního postupu.  
  
```csharp  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache{ AllowUnsafeCaching = true };  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 Chcete-li mezipaměť zcela zakázat pro továrny kanálu a kanály, zakažte mezipaměť kanálu. Tím také vypnete mezipaměť kanálu, protože kanály jsou vlastněny jejich odpovídajícími továrnami kanálu. Chcete-li zakázat mezipaměť `factorySettings` kanálu <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> výroby, předajte parametr konstruktoru inicializovanému <xref:System.ServiceModel.Activities.ChannelCacheSettings> instanci s hodnotou <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> 0. Následující příklad kódu ukazuje toto.  
  
```csharp  
// Disable the factory cache. This results in the channel cache to be turned off as well.  
ChannelCacheSettings factorySettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0 };  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings();  
  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache(factorySettings, channelSettings);
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 Můžete použít pouze vyrovnávací paměť kanálu z výroby a `channelSettings` zakázat <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> mezipaměť kanálu předáním parametru konstruktoru inicializovanému <xref:System.ServiceModel.Activities.ChannelCacheSettings> instanci s hodnotou <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> 0. Následující příklad kódu ukazuje toto.  
  
```csharp  
ChannelCacheSettings factorySettings = new ChannelCacheSettings();  
// Disable only the channel cache.  
ChannelCacheSettings channelSettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0};  
  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache(factorySettings, channelSettings);
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 V služby hostované pracovního postupu můžete určit nastavení objekt pro vytváření mezipaměti a kanál mezipaměti v konfiguračním souboru aplikace. Chcete-li to provést, přidejte chování služby, který obsahuje nastavení mezipaměti pro objekt pro vytváření a kanál mezipaměti a ke službě Toto chování služby. Následující příklad ukazuje obsah konfiguračního `MyChannelCacheBehavior` souboru, který obsahuje chování služby s vlastním nastavením mezipaměti výroby a mezipaměti kanálů. Toto chování služby je `behaviorConfiguration` přidán do služby prostřednictvím atributu.  
  
```xml  
<configuration>
  <system.serviceModel>  
    <!-- List of other config sections here -->
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="MyChannelCacheBehavior">  
          <sendMessageChannelCache allowUnsafeCaching ="false" >  
            <!-- Control only the host level settings -->
            <factorySettings maxItemsInCache = "8" idleTimeout = "00:05:00" leaseTimeout="10:00:00" />  
            <channelSettings maxItemsInCache = "32" idleTimeout = "00:05:00" leaseTimeout="00:06:00" />  
          </sendMessageChannelCache>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service name="MyService" behaviorConfiguration="MyChannelCacheBehavior" />  
    </services>  
  </system.serviceModel>  
</configuration>  
```
