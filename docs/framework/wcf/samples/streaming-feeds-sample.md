---
title: Ukázka informačních kanálů streamování
ms.date: 03/30/2017
ms.assetid: 1f1228c0-daaa-45f0-b93e-c4a158113744
ms.openlocfilehash: 551a97f3cc54915a831fc28eca6ae0ff23101e0b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84589783"
---
# <a name="streaming-feeds-sample"></a>Ukázka informačních kanálů streamování
Tato ukázka předvádí, jak spravovat informační kanály syndikace, které obsahují velký počet položek. Na serveru Ukázka ukazuje, jak zpozdit vytváření jednotlivých <xref:System.ServiceModel.Syndication.SyndicationItem> objektů v rámci kanálu, dokud není bezprostředně předtím, než je položka zapsána do síťového datového proudu.  
  
 V tomto klientovi Ukázka ukazuje, jak lze použít vlastní formátovací modul informačního kanálu syndikace ke čtení jednotlivých položek ze síťového datového proudu, aby čtení informačního kanálu nikdy nebylo plně uloženo do vyrovnávací paměti.  
  
 Aby bylo možné nejlépe předvést možnosti streamování rozhraní API syndikace, používá tato ukázka poněkud nepravděpodobný scénář, ve kterém server zveřejňuje informační kanál, který obsahuje nekonečný počet položek. V takovém případě server pokračuje v generování nových položek do informačního kanálu, dokud nezjistí, že klient přečetl zadaný počet položek z informačního kanálu (ve výchozím nastavení je to 10). Pro jednoduchost je implementace klienta i serveru implementována ve stejném procesu a pomocí sdíleného `ItemCounter` objektu uchovává přehled o počtu položek, které klient vytvořil. `ItemCounter`Typ existuje pouze pro účel, který umožňuje čistě ukončit ukázkový scénář, a není základním prvkem prokazatelně prováděného vzoru.  
  
 Tato ukázka využívá iterátory jazyka Visual C# (pomocí `yield return` konstruktoru klíčového slova). Další informace o iterátorech najdete v tématu používání iterátorů na webu MSDN.  
  
## <a name="service"></a>Služba  
 Služba implementuje základní <xref:System.ServiceModel.Web.WebGetAttribute> kontrakt, který se skládá z jedné operace, jak je znázorněno v následujícím kódu.  
  
```csharp  
[ServiceContract]  
interface IStreamingFeedService  
{  
    [WebGet]  
    [OperationContract]  
    Atom10FeedFormatter StreamedFeed();  
}  
```  
  
 Služba implementuje tuto smlouvu pomocí `ItemGenerator` třídy pro vytvoření potenciálně nekonečného datového proudu <xref:System.ServiceModel.Syndication.SyndicationItem> instancí pomocí iterátoru, jak je znázorněno v následujícím kódu.  
  
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
  
 Když implementace služby vytvoří informační kanál, `ItemGenerator.GenerateItems()` použije se místo kolekce položek s vyrovnávací pamětí výstup.  
  
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
  
 V důsledku toho není datový proud položky nikdy plně ukládán do vyrovnávací paměti. Toto chování lze sledovat nastavením zarážky v `yield return` příkazu uvnitř metody a zaznamenání `ItemGenerator.GenerateItems()` , že tato zarážka je zjištěna poprvé poté, co služba vrátí výsledek `StreamedFeed()` metody.  
  
## <a name="client"></a>Klient  
 Klient v této ukázce používá vlastní <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> implementaci, která zpozdí materializace jednotlivých položek v informačním kanálu namísto jejich ukládání do vyrovnávací paměti. Vlastní `StreamedAtom10FeedFormatter` instance se používá následujícím způsobem.  
  
```csharp  
XmlReader reader = XmlReader.Create("http://localhost:8000/Service/Feeds/StreamedFeed");  
StreamedAtom10FeedFormatter formatter = new StreamedAtom10FeedFormatter(counter);  
  
SyndicationFeed feed = formatter.ReadFrom(reader);  
```  
  
 V normálním případě volání <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> nevrátí, dokud nebude celý obsah informačního kanálu načten ze sítě a ukládán do vyrovnávací paměti. Objekt se však `StreamedAtom10FeedFormatter` přepíše <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> a vrátí iterátor místo kolekce s vyrovnávací pamětí, jak je znázorněno v následujícím kódu.  
  
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
  
 V důsledku toho se žádná položka nenačte ze sítě, dokud klientská aplikace, která projde výsledky, nebude `ReadItems()` připravena k jejímu použití. Toto chování lze sledovat nastavením zarážky v `yield return` příkazu uvnitř `StreamedAtom10FeedFormatter.DelayReadItems()` a všímáte, že tato zarážka je zjištěna poprvé po volání metody `ReadFrom()` dokončí.  
  
 Následující pokyny ukazují, jak sestavit a spustit ukázku. Všimněte si, že i když server přestane generovat položky poté, co klient přečte 10 položek, výstup ukazuje, že klient čte podstatně více než 10 položek. Důvodem je to, že síťová vazba, kterou ukázka používá, přenáší data v segmentech o čtyřech kilobajtech (KB). Klient tak obdrží 4KB dat položek předtím, než má příležitost číst i jednu položku. Jedná se o normální chování (při posílání streamovaná data HTTP v dostatečně velkých segmentech zvyšuje výkon).  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StreamingFeeds`  
  
## <a name="see-also"></a>Viz také

- [Samostatný diagnostický informační kanál](stand-alone-diagnostics-feed-sample.md)
