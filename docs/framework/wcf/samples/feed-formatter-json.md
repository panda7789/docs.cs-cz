---
title: Formátování informačního kanálu (JSON)
ms.date: 03/30/2017
ms.assetid: f9c0b295-55e7-48ea-b308-ba51c7d31143
ms.openlocfilehash: 350e07ad37b09f39fc709e20d8f73a41f9d01f30
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183656"
---
# <a name="feed-formatter-json"></a>Formátování informačního kanálu (JSON)
Tato ukázka ukazuje, jak serializovat <xref:System.ServiceModel.Syndication.SyndicationFeed> instanci třídy ve formátu JSON (JavaScript Object Notation) pomocí vlastní <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
## <a name="architecture-of-the-sample"></a>Architektura ukázky  
 Ukázka implementuje `JsonFeedFormatter` třídu s <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>názvem, která dědí z . Třída `JsonFeedFormatter` spoléhá na <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> čtení a zápis dat ve formátu JSON. Interně formátovací modul používá vlastní sadu typů `JsonSyndicationFeed` `JsonSyndicationItem` kontraktů dat s názvem a řídit formát dat JSON vytvořených serializátorem. Tyto podrobnosti implementace jsou skryté od koncového uživatele, <xref:System.ServiceModel.Syndication.SyndicationFeed> což <xref:System.ServiceModel.Syndication.SyndicationItem> umožňuje volání proti standard a třídy.  
  
## <a name="writing-json-feeds"></a>Psaní json kanálů  
 Psaní informačního kanálu JSON lze `JsonFeedFormatter` provést pomocí (implementované <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> v této ukázce) s, jak je znázorněno v následujícím ukázkovém kódu.  
  
```csharp  
//Basic feed with sample data  
SyndicationFeed feed = new SyndicationFeed("Custom JSON feed", "A Syndication extensibility sample", null);  
feed.LastUpdatedTime = DateTime.Now;  
feed.Items = from s in new string[] { "hello", "world" }  
select new SyndicationItem()  
{  
    Summary = SyndicationContent.CreatePlaintextContent(s)  
};  
  
//Write the feed out to a MemoryStream in JSON format  
DataContractJsonSerializer writeSerializer = new DataContractJsonSerializer(typeof(JsonFeedFormatter));  
writeSerializer.WriteObject(stream, new JsonFeedFormatter(feed));  
```  
  
## <a name="reading-a-json-feed"></a>Čtení informačního kanálu JSON  
 Získání <xref:System.ServiceModel.Syndication.SyndicationFeed> z datového proudu dat ve formátu JSON `JsonFeedFormatter` lze provést pomocí jako show v následujícím kódu.  
  
 `//Read in the feed using the DataContractJsonSerializer`  
  
 `DataContractJsonSerializer readSerializer = new DataContractJsonSerializer(typeof(JsonFeedFormatter));`  
  
 `JsonFeedFormatter formatter = readSerializer.ReadObject(stream) as JsonFeedFormatter;`  
  
 `SyndicationFeed feedRead = formatter.Feed;`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\JsonFeeds`  
