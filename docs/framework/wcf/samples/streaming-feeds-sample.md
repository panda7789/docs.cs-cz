---
title: Ukázka informačních kanálů streamování
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1f1228c0-daaa-45f0-b93e-c4a158113744
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 24dfd6c7eb2c1df6605d03bfb99cc82c0a489377
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="streaming-feeds-sample"></a>Ukázka informačních kanálů streamování
Tento příklad znázorňuje postup správy informační kanály syndikace, které obsahují velkým počtem položek. Na serveru, ukázky ukazuje, jak zpoždění vytvoření jednotlivé <xref:System.ServiceModel.Syndication.SyndicationItem> objekty v rámci kanálu dokud okamžitě, než položka se zapíše do datového proudu sítě.  
  
 Na straně klienta příklad ukazuje, jak můžete použít vlastní syndikace formátování informačního kanálu ke čtení jednotlivé položky z datového proudu sítě tak, aby čteného informačního kanálu do vyrovnávací paměti nikdy plně do paměti.  
  
 K předvedení nejlépe streamování schopností syndikace rozhraní API, používá tato ukázka poněkud pravděpodobně scénář, ve kterém server zpřístupní informačního kanálu, který obsahuje nekonečné počet položek. V tomto případě server pokračuje v generování nových položek do informačního kanálu, dokud se určuje, že klient má ke čtení zadaný počet položek z informačního kanálu (ve výchozím nastavení, 10). Pro jednoduchost, klienta a serveru jsou implementované v rámci jednoho procesu a použít sdílenou `ItemCounter` má vytvořeného objektu k udržování přehledu o tom, kolik položek klienta. `ItemCounter` Typ existuje pouze pro účely povolení vzorový scénář ukončit ještě jednou a není element základní vzoru předmětem ukázky.  
  
 Ukázky využívá z Visual C# iterátory (pomocí `yield``return` – klíčové slovo konstrukce). [!INCLUDE[crabout](../../../../includes/crabout-md.md)] iterátory, naleznete v části "Použití iterátory" na webu MSDN.  
  
## <a name="service"></a>Služba  
 Služba implementuje základní <xref:System.ServiceModel.Web.WebGetAttribute> kontrakt, který se skládá z jedné operace, jak je znázorněno v následujícím kódu.  
  
```  
[ServiceContract]  
interface IStreamingFeedService  
{  
    [WebGet]  
    [OperationContract]  
    Atom10FeedFormatter StreamedFeed();  
}  
```  
  
 Služba implementuje pomocí tento kontrakt `ItemGenerator` třídy za účelem vytvoření potenciálně nekonečné proud <xref:System.ServiceModel.Syndication.SyndicationItem> instance pomocí iterator, jak je znázorněno v následujícím kódu.  
  
```  
class ItemGenerator  
{  
    public IEnumerable<SyndicationItem> GenerateItems()  
    {  
        while (counter.GetCount() < maxItemsRead)  
        {  
            itemsReturned++;  
            yield return CreateNextItem();  
        }  
  
    }  
    ...  
}  
```  
  
 Při implementaci služby vytvoří informačního kanálu, výstup `ItemGenerator.GenerateItems()` se používá místo ve vyrovnávací paměti kolekce položek.  
  
```  
public Atom10FeedFormatter StreamedFeed()  
{  
    SyndicationFeed feed = new SyndicationFeed("Streamed feed", "Feed to test streaming", null);  
    //Generate an infinite stream of items. Both the client and the service share  
    //a reference to the ItemCounter, which allows the sample to terminate  
    //execution after the client has read 10 items from the stream  
    ItemGenerator itemGenerator = new ItemGenerator(this.counter, 10);  
  
    feed.Items = itemGenerator.GenerateItems();  
    return feed.GetAtom10Formatter();  
}  
```  
  
 V důsledku toho položky datového proudu do vyrovnávací paměti nikdy plně do paměti. Toto chování můžete sledovat pomocí nastavení boru přerušení na `yield``return` příkaz uvnitř `ItemGenerator.GenerateItems()` metoda a poznamenat, že je tento zarážek došlo poprvé po služba vrátila výsledek `StreamedFeed()` metoda.  
  
## <a name="client"></a>Klient  
 Klient v této ukázce používá vlastní <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> implementace, která zpozdí materialization jednotlivých položek v informačním kanálu místo ukládání do vyrovnávací paměti je do paměti. Vlastní `StreamedAtom10FeedFormatter` instance se používá následujícím způsobem.  
  
```  
XmlReader reader = XmlReader.Create("http://localhost:8000/Service/Feeds/StreamedFeed");  
StreamedAtom10FeedFormatter formatter = new StreamedAtom10FeedFormatter(counter);  
  
SyndicationFeed feed = formatter.ReadFrom(reader);  
```  
  
 Za normálních okolností volání <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> nevrátí, dokud nebude načtena ze sítě a uložená do vyrovnávací paměti do paměti celý obsah informačního kanálu. Ale `StreamedAtom10FeedFormatter` objektu přepsání <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> vrátit iterator místo kolekci ve vyrovnávací paměti, jak je znázorněno v následujícím kódu.  
  
```  
protected override IEnumerable<SyndicationItem> ReadItems(XmlReader reader, SyndicationFeed feed, out bool areAllItemsRead)  
{  
    areAllItemsRead = false;  
    return DelayReadItems(reader, feed);  
}  
  
private IEnumerable<SyndicationItem> DelayReadItems(XmlReader reader, SyndicationFeed feed)  
{  
    while (reader.IsStartElement("entry", "http://www.w3.org/2005/Atom"))  
    {  
        yield return this.ReadItem(reader, feed);  
    }  
  
    reader.ReadEndElement();  
}  
```  
  
 V důsledku toho není každou položku číst ze sítě. dokud klientská aplikace procházení výsledky `ReadItems()` je připravený k použití ho. Toto chování můžete sledovat pomocí nastavení boru přerušení na `yield``return` příkaz uvnitř `StreamedAtom10FeedFormatter.DelayReadItems()` a vašeho povšimnutí, že je tento zarážek došlo poprvé po zavolání `ReadFrom()` dokončení.  
  
 Následující pokyny ukazují, jak sestavit a spustit ukázku. Všimněte si, že i když server zastaví generování položky po klienta má čtení 10 položek, výstup ukazuje, že klient čte výrazně víc než 10 položek. Je to proto, že síťové vazby používané ukázku odesílá data v segmentech čtyř kilobajtů (KB). Jako takový obdrží klient 4KB položky dat před má možnost číst i jednu položku. Toto chování je očekávané (odeslání přenášené datovými proudy dat protokolu HTTP v přiměřené velikosti segmenty zvýšení výkonu).  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StreamingFeeds`  
  
## <a name="see-also"></a>Viz také  
 [Samostatný diagnostický informační kanál](../../../../docs/framework/wcf/samples/stand-alone-diagnostics-feed-sample.md)
