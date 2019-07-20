---
title: Změna úrovní sdílení mezipaměti pro aktivity odesílání
ms.date: 03/30/2017
ms.assetid: 03926a64-753d-460e-ac06-2a4ff8e1bbf5
ms.openlocfilehash: ac4f2e4fe85d6b243999add6bda65f4fb202f79c
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363835"
---
# <a name="changing-the-cache-sharing-levels-for-send-activities"></a>Změna úrovní sdílení mezipaměti pro aktivity odesílání
Rozšíření umožňuje přizpůsobit úroveň sdílení mezipaměti, nastavení mezipaměti objektu pro vytváření kanálu a nastavení mezipaměti kanálu pro pracovní postupy, které odesílají zprávy do koncových bodů služby pomocí <xref:System.ServiceModel.Activities.Send> aktivit zasílání zpráv. <xref:System.ServiceModel.Activities.SendMessageChannelCache> Tyto pracovní postupy jsou obvykle pracovní postupy klienta, ale mohou být také služby pracovního postupu, které jsou hostovány v <xref:System.ServiceModel.WorkflowServiceHost>. Mezipaměť objektu pro vytváření kanálů obsahuje <xref:System.ServiceModel.ChannelFactory%601> objekty v mezipaměti. Mezipaměť kanálu obsahuje kanály v mezipaměti.  
  
> [!NOTE]
>  Pracovní postupy mohou <xref:System.ServiceModel.Activities.Send> používat aktivity zasílání zpráv k odeslání buď zpráv, nebo parametrů. Modul runtime pracovního postupu přidává do mezipaměti továrny kanálů, které vytvářejí kanály typu <xref:System.ServiceModel.Channels.IRequestChannel> při <xref:System.ServiceModel.Activities.ReceiveReply> použití aktivity s <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.Send> aktivitou a <xref:System.ServiceModel.Channels.IOutputChannel> při pouhém použití aktivity (ne <xref:System.ServiceModel.Activities.ReceiveReply>).  
  
## <a name="the-cache-sharing-levels"></a>Úrovně sdílení mezipaměti  
 Ve výchozím nastavení se v pracovním postupu hostovaném <xref:System.ServiceModel.WorkflowServiceHost> v mezipaměti <xref:System.ServiceModel.Activities.Send> používané aktivity zasílání zpráv sdílí mezi <xref:System.ServiceModel.WorkflowServiceHost> všemi instancemi pracovního postupu v (ukládání do mezipaměti na úrovni hostitele). Pro klienta pracovní postup, který není hostované <xref:System.ServiceModel.WorkflowServiceHost>, mezipaměť je k dispozici pouze pro instanci pracovního postupu (ukládání do mezipaměti na úrovni instance). Mezipaměť je k dispozici pouze <xref:System.ServiceModel.Activities.Send> pro aktivity, které nepoužívají koncové body definované v konfiguraci, pokud není povoleno zabezpečené ukládání do mezipaměti.  
  
 Níže jsou k dispozici různé úrovně sdílení mezipaměti pro <xref:System.ServiceModel.Activities.Send> aktivity v pracovním postupu a jejich Doporučené použití:  
  
- **Úroveň hostitele**: V úrovni sdílení hostitelů je mezipaměť dostupná jenom pro instance pracovních postupů hostované v hostiteli služby pracovního postupu. Mezipaměť lze také sdílet mezi hostiteli služby pracovního postupu v mezipaměti na úrovni procesu.  
  
- **Úroveň instance**: V úrovni sdílení instancí je mezipaměť k dispozici pro konkrétní instanci pracovního postupu po celou dobu své životnosti, ale mezipaměť není k dispozici pro jiné instance pracovního postupu.  
  
- **Žádná mezipaměť**: Mezipaměť je ve výchozím nastavení vypnuta v případě, že máte pracovní postup, který používá koncové body definované v konfiguraci. V takovém případě se taky doporučuje uchovávat mezipaměť, protože zapnutí této mezipaměti je nezabezpečené. Například pokud je pro každé odeslání vyžadována jiná identita (jiné přihlašovací údaje nebo použití zosobnění).  
  
## <a name="changing-the-cache-sharing-level-for-a-client-workflow"></a>Změna úrovně sdílení mezipaměti pro klientský pracovní postup  
 Chcete-li nastavit sdílení mezipaměti v klientském pracovním postupu, přidejte instanci <xref:System.ServiceModel.Activities.SendMessageChannelCache> třídy jako rozšíření do požadované sady instancí pracovního postupu. Výsledkem je sdílení mezipaměti napříč všemi instancemi pracovního postupu. Následující příklady kódu ukazují, jak provést tyto kroky.  
  
 Nejprve deklarujte instanci typu <xref:System.ServiceModel.Activities.SendMessageChannelCache>.  
  
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
  
## <a name="changing-the-cache-sharing-level-for-a-hosted-workflow-service"></a>Změna úrovně sdílení mezipaměti pro hostovanou službu pracovního postupu  
 Chcete-li nastavit sdílení mezipaměti ve službě hostovaného pracovního postupu, přidejte instanci <xref:System.ServiceModel.Activities.SendMessageChannelCache> třídy jako rozšíření do všech hostitelů služby pracovního postupu. Výsledkem je sdílení mezipaměti ve všech hostitelích služby pracovního postupu. Následující příklady kódu ukazují, jak provést tyto kroky.  
  
 Nejprve deklarujte instanci typu <xref:System.ServiceModel.Activities.SendMessageChannelCache> na úrovni třídy.  
  
```csharp  
// Create static instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension = new  
    SendMessageChannelCache();  
```  
  
 Dále přidejte rozšíření statické mezipaměti do každého hostitele služby pracovního postupu.  
  
```csharp  
WorkflowServiceHost host1 = new WorkflowServiceHost(new serviceWorkflow1(), new Uri(baseAddress1));  
WorkflowServiceHost host2 = new WorkflowServiceHost(new serviceWorkflow2(), new Uri(baseAddress2));  
  
// Share the static cache to get an AppDomain level cache.  
host1.WorkflowExtensions.Add(sharedChannelCacheExtension);  
host2.WorkflowExtensions.Add(sharedChannelCacheExtension);  
```  
  
 Chcete-li nastavit sdílení mezipaměti ve službě hostovaného pracovního postupu na úrovni instance, přidejte `Func<SendMessageChannelCache>` delegáta jako rozšíření do hostitele služby pracovního postupu a přiřaďte tohoto delegáta kódu, který vytvoří instanci nové instance <xref:System.ServiceModel.Activities.SendMessageChannelCache> třídy. Výsledkem je odlišná mezipaměť pro každou jednotlivou instanci pracovního postupu, a ne jednu mezipaměť sdílenou všemi instancemi pracovního postupu v hostiteli služby pracovního postupu. Následující příklad kódu ukazuje, jak toho dosáhnout pomocí výrazu lambda pro přímé definování <xref:System.ServiceModel.Activities.SendMessageChannelCache> rozšíření, na které tento delegát odkazuje.  
  
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
 Můžete přizpůsobit nastavení mezipaměti pro mezipaměť objektu pro vytváření kanálu a mezipaměť kanálu. Nastavení mezipaměti je definováno ve <xref:System.ServiceModel.Activities.ChannelCacheSettings> třídě. <xref:System.ServiceModel.Activities.SendMessageChannelCache> Třída definuje výchozí nastavení mezipaměti pro mezipaměť objektu pro vytváření kanálu a mezipaměť kanálu v jeho konstruktoru bez parametrů. Následující tabulka uvádí výchozí hodnoty těchto nastavení mezipaměti pro každý typ mezipaměti.  
  
|Nastavení|LeaseTimeout (min)|IdleTimeout (min)|MaxItemsInCache|  
|-|-|-|-|  
|Výchozí mezipaměť pro tovární nastavení|TimeSpan. MaxValue|2|16|  
|Výchozí nastavení mezipaměti kanálu|5|2|16|  
  
 Chcete-li přizpůsobit mezipaměť továrny a nastavení mezipaměti kanálu, vytvořte <xref:System.ServiceModel.Activities.SendMessageChannelCache> instanci třídy pomocí parametrizovaného konstruktoru <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> a předejte novou instanci <xref:System.ServiceModel.Activities.ChannelCacheSettings> s vlastními hodnotami do každého z těchto a `channelSettings` `factorySettings` ukazatelů. Dále přidejte novou instanci této třídy jako rozšíření hostitele služby pracovního postupu nebo instance pracovního postupu. Následující příklad kódu ukazuje, jak provést tyto kroky pro instanci pracovního postupu.  
  
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
  
 Pokud chcete povolit ukládání do mezipaměti, když má vaše služba pracovního postupu v konfiguraci definované <xref:System.ServiceModel.Activities.SendMessageChannelCache> koncové body, vytvořte instanci třídy <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> pomocí parametrizovaného konstruktoru s `true` `allowUnsafeCaching` parametrem nastaveným na. Dále přidejte novou instanci této třídy jako rozšíření hostitele služby pracovního postupu nebo instance pracovního postupu. Následující příklad kódu ukazuje, jak povolit ukládání do mezipaměti pro instanci pracovního postupu.  
  
```csharp  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache{ AllowUnsafeCaching = true };  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 Pokud chcete mezipaměť úplně zakázat pro továrny kanálů a kanály, zakažte mezipaměť objektu pro vytváření kanálů. Tím se také vypne mezipaměť kanálu, protože kanály vlastní odpovídající továrny kanálů. Chcete- `factorySettings` li zakázat mezipaměť objektu <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> pro vytváření kanálu, předejte parametr do konstruktoru inicializovanému <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> do <xref:System.ServiceModel.Activities.ChannelCacheSettings> instance s hodnotou 0. Následující příklad kódu ukazuje toto.  
  
```csharp  
// Disable the factory cache. This results in the channel cache to be turned off as well.  
ChannelCacheSettings factorySettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0 };  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings();  
  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache(factorySettings, channelSettings);   
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 Můžete zvolit, že se má použít pouze mezipaměť objektu pro vytváření kanálu, a zakázat mezipaměť kanálu `channelSettings` předáním parametru <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> do konstruktoru inicializovaného <xref:System.ServiceModel.Activities.ChannelCacheSettings> <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> do instance s hodnotou 0. Následující příklad kódu ukazuje toto.  
  
```csharp  
ChannelCacheSettings factorySettings = new ChannelCacheSettings();  
// Disable only the channel cache.  
ChannelCacheSettings channelSettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0};  
  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache(factorySettings, channelSettings);   
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 V služby hostované pracovního postupu můžete určit nastavení objekt pro vytváření mezipaměti a kanál mezipaměti v konfiguračním souboru aplikace. Chcete-li to provést, přidejte chování služby, který obsahuje nastavení mezipaměti pro objekt pro vytváření a kanál mezipaměti a ke službě Toto chování služby. Následující příklad ukazuje obsah konfiguračního souboru, který obsahuje `MyChannelCacheBehavior` chování služby s nastavením mezipaměti pro vlastní tovární nastavení a mezipamětí kanálu. Toto chování služby se do služby přidá prostřednictvím `behaviorConfiguration` atributu.  
  
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
