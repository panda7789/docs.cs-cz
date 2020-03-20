---
title: Ukázka informačních kanálů streamování
ms.date: 03/30/2017
ms.assetid: 1f1228c0-daaa-45f0-b93e-c4a158113744
ms.openlocfilehash: 7a887fa1eceac4d8ee323f03fd5bc536bb1dc579
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143964"
---
# <a name="streaming-feeds-sample"></a>Ukázka informačních kanálů streamování
Tato ukázka ukazuje, jak spravovat syndikační kanály, které obsahují velký počet položek. Na serveru ukázka ukazuje, jak odložit vytvoření <xref:System.ServiceModel.Syndication.SyndicationItem> jednotlivých objektů v rámci informačního kanálu, dokud bezprostředně před položkou zapsána do síťového proudu.  
  
 Na straně klienta ukázka ukazuje, jak vlastní syndikace krmivo formodul lze použít ke čtení jednotlivých položek ze síťového proudu tak, aby zdroj čtení není nikdy plně do vyrovnávací paměti do paměti.  
  
 Chcete-li nejlépe demonstrovat schopnost streamování syndikace rozhraní API, tato ukázka používá poněkud nepravděpodobný scénář, ve kterém server zveřejňuje informační kanál, který obsahuje nekonečný počet položek. V tomto případě server pokračuje ve generování nových položek do informačního kanálu, dokud nezjistí, že klient přečetl zadaný počet položek z informačního kanálu (ve výchozím nastavení 10). Pro jednoduchost klient a server jsou implementovány ve stejném procesu `ItemCounter` a použít sdílený objekt sledovat, kolik položek klient vytvořil. Typ `ItemCounter` existuje pouze za účelem povolení ukázkový scénář ukončit čistě a není základní prvek vzoru je prokázáno.  
  
 Demonstrace využívá visual c# iterátory (pomocí `yield return` klíčové ho konstruktu). Další informace o iterátorech naleznete v tématu "Using Iterators" na msdn.  
  
## <a name="service"></a>Služba  
 Služba implementuje <xref:System.ServiceModel.Web.WebGetAttribute> základní smlouvu, která se skládá z jedné operace, jak je znázorněno v následujícím kódu.  
  
```csharp  
[ServiceContract]  
interface IStreamingFeedService  
{  
    [WebGet]  
    [OperationContract]  
    Atom10FeedFormatter StreamedFeed();  
}  
```  
  
 Služba implementuje tuto smlouvu `ItemGenerator` pomocí třídy k <xref:System.ServiceModel.Syndication.SyndicationItem> vytvoření potenciálně nekonečného proudu instancí pomocí iterátoru, jak je znázorněno v následujícím kódu.  
  
```csharp
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
  
 Když implementace služby vytvoří informační `ItemGenerator.GenerateItems()` kanál, výstup se používá namísto vyrovnávací kolekce položek.  
  
```csharp
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
  
 V důsledku toho datový proud položky není nikdy plně do vyrovnávací paměti do paměti. Toto chování můžete sledovat nastavením `yield return` zarážky na `ItemGenerator.GenerateItems()` příkaz uvnitř metody a s tím, že tato zarážka `StreamedFeed()` je zjištěna poprvé poté, co služba vrátila výsledek metody.  
  
## <a name="client"></a>Klient  
 Klient v této ukázce používá vlastní <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> implementaci, která zpožďuje materializaci jednotlivých položek v informačním kanálu namísto ukládání do vyrovnávací paměti do paměti. Vlastní `StreamedAtom10FeedFormatter` instance se používá následujícím způsobem.  
  
```csharp  
XmlReader reader = XmlReader.Create("http://localhost:8000/Service/Feeds/StreamedFeed");  
StreamedAtom10FeedFormatter formatter = new StreamedAtom10FeedFormatter(counter);  
  
SyndicationFeed feed = formatter.ReadFrom(reader);  
```  
  
 Volání se <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> obvykle nevrátí, dokud celý obsah informačního kanálu byly přečteny ze sítě a do vyrovnávací paměti. Objekt však `StreamedAtom10FeedFormatter` přepíše <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> vrátit iterátor namísto vyrovnávací paměti kolekce, jak je znázorněno v následujícím kódu.  
  
```csharp  
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
  
 V důsledku toho každá položka není číst ze sítě, dokud `ReadItems()` klientská aplikace procházet výsledky je připraven k použití. Toto chování můžete sledovat nastavením `yield return` zarážky `StreamedAtom10FeedFormatter.DelayReadItems()` na příkaz uvnitř a všimněte si, že tato zarážka je zjištěna poprvé po `ReadFrom()` dokončení volání.  
  
 Následující pokyny ukazují, jak vytvořit a spustit ukázku. Všimněte si, že i když server přestane generovat položky poté, co klient přečetl 10 položek, výstup ukazuje, že klient čte výrazně více než 10 položek. Důvodem je, že síťová vazba používaná ukázkou přenáší data v segmentech kb čtyř kilobajtů. Jako takový klient obdrží 4 KB dat položky před tím, než má možnost číst i jednu položku. Toto je normální chování (odesílání dat protokolu HTTP datových proudů v přiměřeně velkých segmentech zvyšuje výkon).  
  
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
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StreamingFeeds`  
  
## <a name="see-also"></a>Viz také

- [Samostatný diagnostický informační kanál](../../../../docs/framework/wcf/samples/stand-alone-diagnostics-feed-sample.md)
