---
title: Změna úrovní sdílení mezipaměti pro aktivity odesílání
ms.date: 03/30/2017
ms.assetid: 03926a64-753d-460e-ac06-2a4ff8e1bbf5
ms.openlocfilehash: e439edc14183c2ba2bf9af67e177dddb52c43708
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53127053"
---
# <a name="changing-the-cache-sharing-levels-for-send-activities"></a>Změna úrovní sdílení mezipaměti pro aktivity odesílání
<xref:System.ServiceModel.Activities.SendMessageChannelCache> Rozšíření umožňuje do mezipaměti sdílení úrovně, nastavení mezipaměti kanálu objekt pro vytváření, přizpůsobení a nastavení kanálu do mezipaměti pro pracovní postupy, které odesílání zpráv do koncových bodů služby pomocí <xref:System.ServiceModel.Activities.Send> zasílání zpráv aktivity. Tyto pracovní postupy jsou obvykle pracovní postupy klienta, ale mohou být také služby pracovního postupu, které jsou hostovány v <xref:System.ServiceModel.WorkflowServiceHost>. Obsahuje objekt pro vytváření mezipaměti kanálu mezipaměti <xref:System.ServiceModel.ChannelFactory%601> objekty. Kanál mezipaměti obsahuje uložený v mezipaměti kanály.  
  
> [!NOTE]
>  Pracovní postupy můžete použít <xref:System.ServiceModel.Activities.Send> zasílání zpráv aktivity k odeslání zprávy nebo parametry. Modulu runtime pracovního postupu přidá do mezipaměti, která vytvářet kanály typu objektů pro vytváření kanálů <xref:System.ServiceModel.Channels.IRequestChannel> při použití <xref:System.ServiceModel.Activities.ReceiveReply> aktivita s <xref:System.ServiceModel.Activities.Send> aktivitu a <xref:System.ServiceModel.Channels.IOutputChannel> při použití pouze <xref:System.ServiceModel.Activities.Send> aktivity (žádné <xref:System.ServiceModel.Activities.ReceiveReply>).  
  
## <a name="the-cache-sharing-levels"></a>Sdílení úrovně mezipaměti  
 Ve výchozím nastavení v pracovním postupu hostované <xref:System.ServiceModel.WorkflowServiceHost> je mezipaměť používaná aplikací <xref:System.ServiceModel.Activities.Send> zasílání zpráv aktivity je sdílen na všechny instance pracovního postupu v <xref:System.ServiceModel.WorkflowServiceHost> (hostitele úroveň ukládání do mezipaměti). Pro klienta pracovní postup, který není hostované <xref:System.ServiceModel.WorkflowServiceHost>, mezipaměť je k dispozici pouze pro instanci pracovního postupu (ukládání do mezipaměti na úrovni instance). Mezipaměť je dostupná jenom pro <xref:System.ServiceModel.Activities.Send> aktivity, které nepoužívají koncové body definované v konfiguraci, pokud nebezpečné ukládání do mezipaměti není povolena.  
  
 Tady jsou různé mezipaměti sdílení úrovně, které jsou k dispozici pro <xref:System.ServiceModel.Activities.Send> aktivity v pracovním postupu a jejich doporučené použití:  
  
-   **Hostování úroveň**: V hostiteli, úrovně sdílení mezipaměť je dostupná jenom pro instance pracovních postupů, které jsou hostované v hostiteli služby pracovního postupu. Mezipaměť se dají sdílet taky mezi hostiteli služby pracovního postupu v mezipaměti celého procesu.  
  
-   **Instance úroveň**: V instanci, úrovně sdílení, mezipaměť je k dispozici instance určitý pracovní postup v průběhu svého životního cyklu, ale mezipaměť není k dispozici pro ostatní instance pracovního postupu.  
  
-   **Žádná mezipaměť**: Mezipaměť je vypnuto ve výchozím nastavení máte pracovní postup, který používá koncové body definované v konfiguraci. Doporučujeme také ponechat mezipaměti vypnuté v tomto případě protože zapnutí může nezabezpečená. Například, pokud jiné identity (jiné přihlašovací údaje nebo použití zosobnění) se vyžaduje pro každý odeslat.  
  
## <a name="changing-the-cache-sharing-level-for-a-client-workflow"></a>Změna mezipaměti sdílení úrovně pro klienta pracovní postup  
 Nastavení mezipaměti sdílení v pracovním postupu klienta, přidat instanci <xref:System.ServiceModel.Activities.SendMessageChannelCache> třídy jako rozšíření k požadované sadě instancí pracovních postupů. Výsledkem je do mezipaměti pro sdílení obsahu napříč všemi instancemi pracovního postupu. Následující příklady kódu ukazují, jak provést tyto kroky.  
  
 Nejprve deklarujte instanci typu <xref:System.ServiceModel.Activities.SendMessageChannelCache>.  
  
```csharp  
// Create an instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension =  
    new SendMessageChannelCache();  
```  
  
 V dalším kroku přidejte rozšíření mezipaměti ke každé instanci pracovního postupu klienta.  
  
```csharp 
WorkflowApplication clientInstance1 = new WorkflowApplication(new clientWorkflow1());  
WorkflowApplication clientInstance2 = new WorkflowApplication(new clientWorkflow2());  
  
// Share the cache extension object   
  
clientInstance1.Extensions.Add(sharedChannelCacheExtension);  
clientInstance2.Extensions.Add(sharedChannelCacheExtension);  
```  
  
## <a name="changing-the-cache-sharing-level-for-a-hosted-workflow-service"></a>Změna mezipaměti sdílení úrovně služby hostované pracovního postupu  
 Nastavení mezipaměti sdílení v služby hostované pracovního postupu, přidat instanci <xref:System.ServiceModel.Activities.SendMessageChannelCache> třídy jako rozšíření pro všechny hostitele služby pracovního postupu. Výsledkem je do mezipaměti pro sdílení obsahu mezi všechny hostitele služby pracovního postupu. Následující příklady kódu ukazují provedení těchto kroků.  
  
 Nejprve deklarujte instanci typu <xref:System.ServiceModel.Activities.SendMessageChannelCache> na úrovni třídy.  
  
```csharp  
// Create static instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension = new  
    SendMessageChannelCache();  
```  
  
 V dalším kroku přidáte statická mezipaměť rozšíření na každém hostiteli služby pracovního postupu.  
  
```csharp  
WorkflowServiceHost host1 = new WorkflowServiceHost(new serviceWorkflow1(), new Uri(baseAddress1));  
WorkflowServiceHost host2 = new WorkflowServiceHost(new serviceWorkflow2(), new Uri(baseAddress2));  
  
// Share the static cache to get an AppDomain level cache.  
host1.WorkflowExtensions.Add(sharedChannelCacheExtension);  
host2.WorkflowExtensions.Add(sharedChannelCacheExtension);  
```  
  
 Nastavení mezipaměti sdílení v služby hostované pracovního postupu na úrovni instance, přidejte `Func<SendMessageChannelCache>` jako rozšíření hostitele služby pracovního postupu a přiřaďte tento delegát kódu, který vytvoří novou instanci třídy <xref:System.ServiceModel.Activities.SendMessageChannelCache> třídy. Výsledkem různé mezipaměti pro každou instanci jednotlivé pracovní postupy, namísto do jedné mezipaměti sdílena všemi instancemi pracovního postupu na hostiteli služby pracovního postupu. Následující příklad kódu ukazuje, jak toho dosáhnout pomocí výrazu lambda přímo definovat <xref:System.ServiceModel.Activities.SendMessageChannelCache> rozšíření odkazující na delegáta.  
  
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
 Můžete přizpůsobit nastavení mezipaměti kanálu objekt pro vytváření a mezipaměti kanálu mezipaměti. Nastavení mezipaměti jsou definovány v <xref:System.ServiceModel.Activities.ChannelCacheSettings> třídy. <xref:System.ServiceModel.Activities.SendMessageChannelCache> Třída definuje výchozí nastavení mezipaměti pro mezipaměti kanálu objekt pro vytváření a kanál mezipaměti v její výchozí konstruktor. V následující tabulce jsou uvedeny výchozí hodnoty nastavení mezipaměti pro každý typ mezipaměti.  
  
|Nastavení|LeaseTimeout (min)|IdleTimeout (min)|MaxItemsInCache|  
|-|-|-|-|  
|Výchozí objekt pro vytváření mezipaměti|Hodnotu TimeSpan.MaxValue|2|16|  
|Výchozí kanál mezipaměti|5|2|16|  
  
 Chcete-li přizpůsobit nastavení objekt pro vytváření mezipaměti a kanál mezipaměti vytvořit instanci <xref:System.ServiceModel.Activities.SendMessageChannelCache> třídy pomocí konstruktoru s parametry <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> a předejte mu novou instanci třídy <xref:System.ServiceModel.Activities.ChannelCacheSettings> pomocí vlastní hodnoty a každý z `factorySettings` a `channelSettings` Parametry. Dále přidejte novou instanci této třídy jako rozšíření hostitele služby pracovního postupu nebo instance pracovního postupu. Následující příklad kódu ukazuje, jak tyto kroky provést pro instanci pracovního postupu.  
  
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
  
 Pokud chcete povolit ukládání do mezipaměti, když služba pracovního postupu má koncové body definované v konfiguraci, vytvořit instanci <xref:System.ServiceModel.Activities.SendMessageChannelCache> třídy pomocí konstruktoru s parametry <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> s `allowUnsafeCaching` parametr nastaven na `true`. Dále přidejte novou instanci této třídy jako rozšíření hostitele služby pracovního postupu nebo instance pracovního postupu. Následující příklad kódu ukazuje, jak povolit ukládání do mezipaměti pro instanci pracovního postupu.  
  
```csharp  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache{ AllowUnsafeCaching = true };  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 Chcete-li zakázat mezipaměť zcela pro vytváření kanálů a kanály, zakažte mezipaměti kanálu objekt pro vytváření. Tím také vypne mezipaměti kanálu jako kanály jsou vlastněny jejich odpovídajících objektů pro vytváření kanálů. Chcete-li zakázat mezipaměti kanálu objekt pro vytváření, předejte `factorySettings` parametr <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> konstruktor inicializovány na <xref:System.ServiceModel.Activities.ChannelCacheSettings> instanci s <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> hodnotu 0. Následující příklad kódu ukazuje to.  
  
```csharp  
// Disable the factory cache. This results in the channel cache to be turned off as well.  
ChannelCacheSettings factorySettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0 };  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings();  
  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache(factorySettings, channelSettings);   
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 Je možné použít pouze mezipaměti kanálu objekt pro vytváření a zakažte mezipaměti kanálu předáním `channelSettings` parametr <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> konstruktor inicializovány na <xref:System.ServiceModel.Activities.ChannelCacheSettings> instanci s <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> hodnotu 0. Následující příklad kódu ukazuje to.  
  
```csharp  
ChannelCacheSettings factorySettings = new ChannelCacheSettings();  
// Disable only the channel cache.  
ChannelCacheSettings channelSettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0};  
  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache(factorySettings, channelSettings);   
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 V služby hostované pracovního postupu můžete určit nastavení objekt pro vytváření mezipaměti a kanál mezipaměti v konfiguračním souboru aplikace. Chcete-li to provést, přidejte chování služby, který obsahuje nastavení mezipaměti pro objekt pro vytváření a kanál mezipaměti a ke službě Toto chování služby. Následující příklad ukazuje obsah, který obsahuje konfigurační soubor `MyChannelCacheBehavior` služeb chování s nastavením vlastní objekt pro vytváření mezipaměti a kanál mezipaměti. Toto chování služby se přidá do této služby prostřednictvím `behaviorConfiguarion` atribut.  
  
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
