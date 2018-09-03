---
title: Ukázka informačních kanálů streamování
ms.date: 03/30/2017
ms.assetid: 1f1228c0-daaa-45f0-b93e-c4a158113744
ms.openlocfilehash: 17639273ece804dc531cbbc3ab9135c814ea632d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486578"
---
# <a name="streaming-feeds-sample"></a>Ukázka informačních kanálů streamování
Tento příklad ukazuje, jak spravovat informační kanály syndikace, které obsahují velký počet položek. Na serveru, ukázka ukazuje, jak pozdržet jednotlivých <xref:System.ServiceModel.Syndication.SyndicationItem> objekty v rámci kanálu až do bezprostředně před položky jsou zapsána do datového proudu sítě.  
  
 V klientském počítači příklad ukazuje použití vlastního formátování informačního kanálu syndikace číst jednotlivých položek z datového proudu sítě tak, aby čteného informačního kanálu do vyrovnávací paměti nikdy plně do paměti.  
  
 K předvedení nejlépe streamování funkce syndikace rozhraní API, tato ukázka používá poněkud nepravděpodobném scénáři, ve kterém server poskytuje informační kanál, který obsahuje neomezený počet položek. V tomto případě server pokračuje ve generování nových položek do informačního kanálu, dokud se určí, že klient má číst zadaný počet položek z informačního kanálu (výchozí hodnota je 10). Pro jednoduchost, klienta a serveru jsou implementovány v rámci stejného procesu a používat sdílené `ItemCounter` objektu, který chcete sledovat, kolik položek klient vytvořil. `ItemCounter` Typ existuje pouze pro účely povolení ukázkový scénář, který má ukončit čistě a není elementem základní vzor, který jsme vám právě ukázali.  
  
 Ukázky využívá Visual C# iterátory (pomocí `yield return` konstrukce – klíčové slovo). Další informace o iterátorech naleznete v tématu "Používání iterátorů" na webu MSDN.  
  
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
  
 Služba implementuje tento kontrakt s použitím `ItemGenerator` třídy za účelem vytvoření potenciálně nekonečné datový proud <xref:System.ServiceModel.Syndication.SyndicationItem> instance pomocí iterátoru, jak je znázorněno v následujícím kódu.  
  
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
  
 Při implementaci služby vytvoří kanál, výstup `ItemGenerator.GenerateItems()` se používá místo ve vyrovnávací paměti kolekce položek.  
  
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
  
 V důsledku toho položky datového proudu do vyrovnávací paměti nikdy plně do paměti. Toto chování můžete sledovat pomocí nastavení zarážky na `yield return` příkaz uvnitř `ItemGenerator.GenerateItems()` metoda a poznamenat, že tato zarážka dochází poprvé po služba vrátila výsledek `StreamedFeed()` metody.  
  
## <a name="client"></a>Klient  
 Klient v této ukázce používá vlastní <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> implementace, která způsobuje zpoždění materializace jednotlivých položek v informačním kanálu namísto jejich ukládání do vyrovnávací paměti do paměti. Vlastní `StreamedAtom10FeedFormatter` instance se používá takto.  
  
```  
XmlReader reader = XmlReader.Create("http://localhost:8000/Service/Feeds/StreamedFeed");  
StreamedAtom10FeedFormatter formatter = new StreamedAtom10FeedFormatter(counter);  
  
SyndicationFeed feed = formatter.ReadFrom(reader);  
```  
  
 Za normálních okolností volání <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> nevrací dokud celý obsah informačního kanálu mají číst ze sítě a uložená do vyrovnávací paměti do paměti. Ale `StreamedAtom10FeedFormatter` objektu přepsání <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> vrátit iterátor místo ve vyrovnávací paměti kolekce, jak je znázorněno v následujícím kódu.  
  
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
  
 V důsledku toho není každé položky číst ze sítě do klientské aplikace, procházení výsledky `ReadItems()` je připravený k použití. Toto chování můžete sledovat pomocí nastavení zarážky na `yield return` příkaz uvnitř `StreamedAtom10FeedFormatter.DelayReadItems()` a pozorujte, že tato zarážka dochází poprvé po volání `ReadFrom()` dokončí.  
  
 Následující pokyny ukazují, jak sestavit a spustit vzorku. Všimněte si, že i když server přestane generování položky po klienta má ke čtení 10 položek, výstup ukazuje, že klient čte výrazně více než 10 položek. Je to proto, že síťové vazby používané v rámci ukázky přenáší data v příslušných segmentech čtyři kilobajtů (KB). V důsledku toho klient obdrží 4KB dat položky předtím, než má možnost číst i jenom jednu položku. Toto chování je běžné (odesílání datové proudy HTTP v rozumné míře velikosti segmentů zvýšení výkonu).  
  
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
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StreamingFeeds`  
  
## <a name="see-also"></a>Viz také  
 [Samostatný diagnostický informační kanál](../../../../docs/framework/wcf/samples/stand-alone-diagnostics-feed-sample.md)
