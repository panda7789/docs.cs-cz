---
title: Formátování informačního kanálu (JSON)
ms.date: 03/30/2017
ms.assetid: f9c0b295-55e7-48ea-b308-ba51c7d31143
ms.openlocfilehash: bc73ae11f66d2c325fab274f8deec11355ce8b99
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44084202"
---
# <a name="feed-formatter-json"></a>Formátování informačního kanálu (JSON)
Tento příklad ukazuje, jak k serializaci instancí <xref:System.ServiceModel.Syndication.SyndicationFeed> ve formátu JavaScript Object Notation (JSON) pomocí vlastní třídy <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.  
  
## <a name="architecture-of-the-sample"></a>Architektura ukázky  
 Ukázka implementuje třídu s názvem `JsonFeedFormatter` , která dědí z <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>. `JsonFeedFormatter` Třídy se může spolehnout <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> číst a zapisovat data ve formátu JSON. Interně, formátovací modul používá vlastní sada datových typů kontraktu s názvem `JsonSyndicationFeed` a `JsonSyndicationItem` řídit formát JSON data vytvořená modulem pro serializaci. Tyto podrobnosti implementace jsou skryté koncového uživatele, což volání provedená oproti standardní <xref:System.ServiceModel.Syndication.SyndicationFeed> a <xref:System.ServiceModel.Syndication.SyndicationItem> třídy.  
  
## <a name="writing-json-feeds"></a>Zápis JSON kanály  
 Zápis JSON kanálu se dá udělat pomocí `JsonFeedFormatter` (implementováno v této ukázce) se <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> jak je znázorněno v následujícím ukázkovém kódu.  
  
```  
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
  
## <a name="reading-a-json-feed"></a>Čtení informačního kanálu ve formátu JSON  
 Získání <xref:System.ServiceModel.Syndication.SyndicationFeed> z dat ve streamu formátu JSON, můžete provést pomocí `JsonFeedFormatter` tak, jak zobrazit v následujícím kódu.  
  
 `//Read in the feed using the DataContractJsonSerializer`  
  
 `DataContractJsonSerializer readSerializer = new DataContractJsonSerializer(typeof(JsonFeedFormatter));`  
  
 `JsonFeedFormatter formatter = readSerializer.ReadObject(stream) as JsonFeedFormatter;`  
  
 `SyndicationFeed feedRead = formatter.Feed;`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\JsonFeeds`  
  
## <a name="see-also"></a>Viz také
