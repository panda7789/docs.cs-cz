---
title: Formátování informačního kanálu (JSON)
ms.date: 03/30/2017
ms.assetid: f9c0b295-55e7-48ea-b308-ba51c7d31143
ms.openlocfilehash: 516a114ee577597611c14ce10ad838d85d6a0fb1
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989894"
---
# <a name="feed-formatter-json"></a>Formátování informačního kanálu (JSON)
Tento příklad ukazuje, jak serializovat instanci <xref:System.ServiceModel.Syndication.SyndicationFeed> třídy ve formátu JavaScript Object Notation (JSON) pomocí vlastní <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
## <a name="architecture-of-the-sample"></a>Architektura ukázky  
 Ukázka implementuje třídu s názvem `JsonFeedFormatter` , která dědí z. <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> `JsonFeedFormatter` Třída spoléhá<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> na ke čtení a zápisu dat ve formátu JSON. Interně, formátovací modul používá vlastní sadu typů kontraktů dat s `JsonSyndicationFeed` názvem `JsonSyndicationItem` a k řízení formátu dat JSON vytvořených serializátorem. Tyto podrobnosti implementace jsou skryté od koncového uživatele, což umožňuje provádět volání proti standardním <xref:System.ServiceModel.Syndication.SyndicationFeed> třídám a. <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
## <a name="writing-json-feeds"></a>Zápis kanálů JSON  
 Zápis datového kanálu JSON se dá provést pomocí `JsonFeedFormatter` (implementované v této ukázce) s, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> jak je znázorněno v následujícím ukázkovém kódu.  
  
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
 Získání a <xref:System.ServiceModel.Syndication.SyndicationFeed> z datového proudu dat ve formátu JSON lze dosáhnout pomocí, `JsonFeedFormatter` jak je znázorněno v následujícím kódu.  
  
 `//Read in the feed using the DataContractJsonSerializer`  
  
 `DataContractJsonSerializer readSerializer = new DataContractJsonSerializer(typeof(JsonFeedFormatter));`  
  
 `JsonFeedFormatter formatter = readSerializer.ReadObject(stream) as JsonFeedFormatter;`  
  
 `SyndicationFeed feedRead = formatter.Feed;`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\JsonFeeds`  
