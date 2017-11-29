---
title: "Změna úrovní sdílení mezipaměti pro aktivity odesílání"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03926a64-753d-460e-ac06-2a4ff8e1bbf5
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 321daca64218bfe2d8644c31df68b80aa8c775d1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="changing-the-cache-sharing-levels-for-send-activities"></a>Změna úrovní sdílení mezipaměti pro aktivity odesílání
<xref:System.ServiceModel.Activities.SendMessageChannelCache> Rozšíření umožňuje přizpůsobit mezipaměti sdílení úrovní, nastavení objektu pro vytváření mezipaměti kanál, a nastavení kanál mezipaměti pro pracovní postupy, které odesílají zprávy do koncových bodů služby pomocí <xref:System.ServiceModel.Activities.Send> aktivity zasílání zpráv. Tyto pracovní postupy jsou obvykle pracovní postupy klienta, ale mohou být také služby pracovního postupu, které jsou hostovány v <xref:System.ServiceModel.WorkflowServiceHost>. Obsahuje objekt pro vytváření mezipaměti kanál v mezipaměti <xref:System.ServiceModel.ChannelFactory%601> objekty. Mezipaměť kanál obsahuje uložené v mezipaměti kanály.  
  
> [!NOTE]
>  Pracovní postupy můžete použít <xref:System.ServiceModel.Activities.Send> aktivity k odeslání zprávy nebo parametry zasílání zpráv. Modulu runtime pracovního postupu přidává objekty factory kanálu do mezipaměti, která vytvořit kanály typu <xref:System.ServiceModel.Channels.IRequestChannel> při použití <xref:System.ServiceModel.Activities.ReceiveReply> aktivitu <xref:System.ServiceModel.Activities.Send> aktivity a <xref:System.ServiceModel.Channels.IOutputChannel> při použití jenom <xref:System.ServiceModel.Activities.Send> aktivity (žádné <xref:System.ServiceModel.Activities.ReceiveReply>).  
  
## <a name="the-cache-sharing-levels"></a>Úrovní sdílení mezipaměti  
 Ve výchozím nastavení, v pracovním postupu hostované <xref:System.ServiceModel.WorkflowServiceHost> mezipaměti používané <xref:System.ServiceModel.Activities.Send> aktivity zasílání zpráv je sdílen na všechny instance pracovního postupu ve <xref:System.ServiceModel.WorkflowServiceHost> (ukládání do mezipaměti hostitele úrovni). Pro klienta pracovní postup, který není hostované <xref:System.ServiceModel.WorkflowServiceHost>, mezipaměť je k dispozici pouze pro instanci pracovního postupu (ukládání do mezipaměti na úrovni instance). Mezipaměť je k dispozici pouze <xref:System.ServiceModel.Activities.Send> aktivity, které nepoužívají koncové body definované v konfiguraci, pokud není unsafe ukládání do mezipaměti povolena.  
  
 Toto jsou různé mezipaměti sdílení úrovně, které jsou k dispozici pro <xref:System.ServiceModel.Activities.Send> aktivity v pracovním postupu a jejich doporučená použití:  
  
-   **Hostování úroveň**: na hostiteli, úrovně sdílení, mezipaměť je k dispozici pouze instance pracovních postupů, které jsou hostované na hostiteli služby pracovního postupu. Mezipaměti můžete také sdílet mezi hostiteli služby pracovního postupu v mezipaměti úrovni procesu.  
  
-   **Instance úroveň**: V instanci, úrovně sdílení, mezipaměť je k dispozici pro instanci pracovního postupu konkrétní v průběhu své životnosti, ale mezipaměti není k dispozici pro další instance pracovního postupu.  
  
-   **Žádné mezipaměti**: mezipaměť je ve výchozím nastavení vypnuté Pokud máte pracovní postup, který používá koncové body definované v konfiguraci. Doporučujeme také pravidelně mezipaměť je vypnuté v takovém případě vzhledem k tomu může být zapnutí nezabezpečená. Například, pokud jiné identity (jiná pověření nebo pomocí zosobnění) je vyžadována pro každý odeslání.  
  
## <a name="changing-the-cache-sharing-level-for-a-client-workflow"></a>Změna úrovně sdílení pro pracovní postup klienta mezipaměti  
 Nastavení mezipaměti sdílení v pracovním postupu klienta, přidá instanci <xref:System.ServiceModel.Activities.SendMessageChannelCache> třída jako rozšíření na požadovanou sadu instancí pracovních postupů. Výsledkem sdílení mezipaměti napříč všechny instance pracovního postupu. Následující příklady kódu ukazují, jak provést tyto kroky.  
  
 Nejprve deklarujte instanci typu <xref:System.ServiceModel.Activities.SendMessageChannelCache>.  
  
```  
// Create an instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension =  
    new SendMessageChannelCache();  
```  
  
 Dále přidáte rozšíření mezipaměti každá instance workflowu klienta.  
  
```  
WorkflowApplication clientInstance1 = new WorkflowApplication(new clientWorkflow1());  
WorkflowApplication clientInstance2 = new WorkflowApplication(new clientWorkflow2());  
  
// Share the cache extension object   
  
clientInstance1.Extensions.Add(sharedChannelCacheExtension);  
clientInstance2.Extensions.Add(sharedChannelCacheExtension);  
```  
  
## <a name="changing-the-cache-sharing-level-for-a-hosted-workflow-service"></a>Změna mezipaměti úrovně sdílení služby hostovaných pracovních postupů  
 Nastavení mezipaměti sdílení v hostovaných pracovních postupů služby, přidat instanci <xref:System.ServiceModel.Activities.SendMessageChannelCache> třída jako rozšíření pro všechny hostitele služby pracovního postupu. Výsledkem sdílení mezipaměti mezi všechny hostitele služby pracovního postupu. Následující příklady kódu ukazují k provedení těchto kroků.  
  
 Nejprve deklarujte instanci typu <xref:System.ServiceModel.Activities.SendMessageChannelCache> na úrovni třídy.  
  
```  
// Create static instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension = new  
    SendMessageChannelCache();  
```  
  
 V dalším kroku přidejte rozšíření statická mezipaměť na každém hostiteli služby pracovního postupu.  
  
```  
WorkflowServiceHost host1 = new WorkflowServiceHost(new serviceWorkflow1(), new Uri(baseAddress1));  
WorkflowServiceHost host2 = new WorkflowServiceHost(new serviceWorkflow2(), new Uri(baseAddress2));  
  
// Share the static cache to get an AppDomain level cache.  
host1.WorkflowExtensions.Add(sharedChannelCacheExtension);  
host2.WorkflowExtensions.Add(sharedChannelCacheExtension);  
```  
  
 Chcete-li nastavit mezipaměti sdílení v hostovaných pracovních postupů služby na úrovni instance, přidejte `Func<SendMessageChannelCache>` delegovat jako rozšíření hostitele služby pracovního postupu a přiřaďte tento delegát kód, který vytvoří novou instanci třídy <xref:System.ServiceModel.Activities.SendMessageChannelCache> – třída. Výsledkem různé mezipaměti pro každou instanci jednotlivých pracovního postupu, místo do jedné mezipaměti sdílí všechny instance pracovního postupu na hostiteli služby pracovního postupu. Následující příklad kódu ukazuje, jak dosáhnout pomocí výrazu lambda přímo zadat <xref:System.ServiceModel.Activities.SendMessageChannelCache> rozšíření, která delegát odkazuje na.  
  
```  
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
 Můžete přizpůsobit nastavení do mezipaměti pro mezipaměť objekt pro vytváření kanálu a mezipaměť kanál. Nastavení ukládání do mezipaměti jsou definovány v <xref:System.ServiceModel.Activities.ChannelCacheSettings> třídy. <xref:System.ServiceModel.Activities.SendMessageChannelCache> Třída definuje výchozí nastavení mezipaměti pro mezipaměť objekt pro vytváření kanálu a mezipaměť kanál v jeho výchozí konstruktor. Následující tabulka uvádí výchozí hodnoty těchto nastavení mezipaměti pro každý typ mezipaměti.  
  
|Nastavení|LeaseTimeout (min.)|IdleTimeout (min.)|MaxItemsInCache|  
|-|-|-|-|  
|Výchozí objekt pro vytváření mezipaměti|TimeSpan.MaxValue, což|2|16|  
|Výchozí mezipaměti kanálu|5|2|16|  
  
 Pokud chcete přizpůsobit tovární nastavení mezipaměti mezipaměti a kanál, vytváření instancí <xref:System.ServiceModel.Activities.SendMessageChannelCache> pomocí parametrizované konstruktor <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> a předejte novou instanci třídy <xref:System.ServiceModel.Activities.ChannelCacheSettings> s vlastní hodnoty a každý z `factorySettings` a `channelSettings` Parametry. Dál přidejte nové instance této třídy jako rozšíření hostitele služby pracovního postupu nebo instanci pracovního postupu. Následující příklad kódu ukazuje, jak provést tyto kroky pro instanci pracovního postupu.  
  
```  
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
  
 Pokud chcete povolit ukládání do mezipaměti, když má koncové body definované v konfiguraci služby pracovního postupu, vytváření instancí <xref:System.ServiceModel.Activities.SendMessageChannelCache> pomocí parametrizované konstruktor <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> s `allowUnsafeCaching` parametr nastaven na `true`. Dál přidejte nové instance této třídy jako rozšíření hostitele služby pracovního postupu nebo instanci pracovního postupu. Následující příklad kódu ukazuje, jak povolit ukládání do mezipaměti pro instanci pracovního postupu.  
  
```  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache{ AllowUnsafeCaching = true };  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 Zakázat mezipaměti úplně objektů Factory kanálů a kanály, zakažte objekt pro vytváření mezipaměti kanálu. Díky tomu taky vypne mezipaměti kanálu jako kanály jsou vlastněny objekty Factory jejich odpovídající kanál. Zakázat objekt pro vytváření mezipaměti kanál, předat `factorySettings` parametru <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> konstruktor inicializována tak, aby <xref:System.ServiceModel.Activities.ChannelCacheSettings> instanci s <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> hodnotu 0. Následující příklad kódu ukazuje to.  
  
```  
// Disable the factory cache. This results in the channel cache to be turned off as well.  
ChannelCacheSettings factorySettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0 };  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings();  
  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache(factorySettings, channelSettings);   
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 Můžete použít pouze objekt pro vytváření mezipaměti kanál a zakázání mezipaměti kanál předáním `channelSettings` parametru <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> konstruktor inicializována tak, aby <xref:System.ServiceModel.Activities.ChannelCacheSettings> instanci s <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> hodnotu 0. Následující příklad kódu ukazuje to.  
  
```  
ChannelCacheSettings factorySettings = new ChannelCacheSettings();  
// Disable only the channel cache.  
ChannelCacheSettings channelSettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0};  
  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache(factorySettings, channelSettings);   
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 V služby hostované pracovního postupu můžete určit nastavení objekt pro vytváření mezipaměti a kanál mezipaměti v konfiguračním souboru aplikace. Chcete-li to provést, přidejte chování služby, který obsahuje nastavení mezipaměti pro objekt pro vytváření a kanál mezipaměti a ke službě Toto chování služby. Následující příklad ukazuje konfigurační soubor, který obsahuje obsah `MyChannelCacheBehavior` chování služby s vlastní objekt pro vytváření mezipaměti a kanál nastavení ukládání do mezipaměti. Toto chování služby se přidá do služby pomocí `behaviorConfiguarion` atribut.  
  
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
