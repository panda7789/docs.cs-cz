---
title: Ukázka informačních kanálů streamování
ms.date: 03/30/2017
ms.assetid: 1f1228c0-daaa-45f0-b93e-c4a158113744
ms.openlocfilehash: 1eb9f2194b2c7e4879cf9e443fea337c73986361
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425362"
---
# <a name="streaming-feeds-sample"></a><span data-ttu-id="25e73-102">Ukázka informačních kanálů streamování</span><span class="sxs-lookup"><span data-stu-id="25e73-102">Streaming Feeds Sample</span></span>
<span data-ttu-id="25e73-103">Tato ukázka předvádí, jak spravovat informační kanály syndikace, které obsahují velký počet položek.</span><span class="sxs-lookup"><span data-stu-id="25e73-103">This sample demonstrates how to manage syndication feeds that contain large numbers of items.</span></span> <span data-ttu-id="25e73-104">Ukázka na serveru ukazuje, jak zpozdit vytvoření jednotlivých objektů <xref:System.ServiceModel.Syndication.SyndicationItem> v rámci informačního kanálu až do chvíle, kdy je položka zapsána do síťového datového proudu.</span><span class="sxs-lookup"><span data-stu-id="25e73-104">On the server, the sample demonstrates how to delay the creation of individual <xref:System.ServiceModel.Syndication.SyndicationItem> objects within the feed until immediately before the item is written to the network stream.</span></span>  
  
 <span data-ttu-id="25e73-105">V tomto klientovi Ukázka ukazuje, jak lze použít vlastní formátovací modul informačního kanálu syndikace ke čtení jednotlivých položek ze síťového datového proudu, aby čtení informačního kanálu nikdy nebylo plně uloženo do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="25e73-105">On the client, the sample shows how a custom syndication feed formatter can be used to read individual items from the network stream so that the feed being read is never fully buffered into memory.</span></span>  
  
 <span data-ttu-id="25e73-106">Aby bylo možné nejlépe předvést možnosti streamování rozhraní API syndikace, používá tato ukázka poněkud nepravděpodobný scénář, ve kterém server zveřejňuje informační kanál, který obsahuje nekonečný počet položek.</span><span class="sxs-lookup"><span data-stu-id="25e73-106">To best demonstrate the streaming capability of the syndication API, this sample uses a somewhat unlikely scenario in which the server exposes a feed that contains an infinite number of items.</span></span> <span data-ttu-id="25e73-107">V takovém případě server pokračuje v generování nových položek do informačního kanálu, dokud nezjistí, že klient přečetl zadaný počet položek z informačního kanálu (ve výchozím nastavení je to 10).</span><span class="sxs-lookup"><span data-stu-id="25e73-107">In this case, the server continues generating new items into the feed until it determines that the client has read a specified number of items from the feed (by default, 10).</span></span> <span data-ttu-id="25e73-108">Pro jednoduchost je implementace klienta i serveru implementována ve stejném procesu a pomocí sdíleného `ItemCounter`ho objektu uchovává přehled o počtu položek, které klient vytvořil.</span><span class="sxs-lookup"><span data-stu-id="25e73-108">For simplicity, both the client and the server are implemented in the same process and use a shared `ItemCounter` object to keep track of how many items the client has produced.</span></span> <span data-ttu-id="25e73-109">Typ `ItemCounter` existuje pouze pro účel, který umožňuje, aby se ukázkový scénář ukončil čistě a nejedná se o základní prvek vzoru, který je prokázán.</span><span class="sxs-lookup"><span data-stu-id="25e73-109">The `ItemCounter` type exists only for the purpose of allowing the sample scenario to terminate cleanly, and is not a core element of the pattern being demonstrated.</span></span>  
  
 <span data-ttu-id="25e73-110">Tato ukázka využívá vizuální C# iterátory (pomocí `yield return` konstrukce klíčového slova).</span><span class="sxs-lookup"><span data-stu-id="25e73-110">The demonstration makes use of Visual C# iterators (using the `yield return` keyword construct).</span></span> <span data-ttu-id="25e73-111">Další informace o iterátorech najdete v tématu používání iterátorů na webu MSDN.</span><span class="sxs-lookup"><span data-stu-id="25e73-111">For more information about iterators, see the "Using Iterators" topic on MSDN.</span></span>  
  
## <a name="service"></a><span data-ttu-id="25e73-112">Služba</span><span class="sxs-lookup"><span data-stu-id="25e73-112">Service</span></span>  
 <span data-ttu-id="25e73-113">Služba implementuje základní kontrakt <xref:System.ServiceModel.Web.WebGetAttribute>, který se skládá z jedné operace, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="25e73-113">The service implements a basic <xref:System.ServiceModel.Web.WebGetAttribute> contract that consists of one operation, as shown in the following code.</span></span>  
  
```csharp  
[ServiceContract]  
interface IStreamingFeedService  
{  
    [WebGet]  
    [OperationContract]  
    Atom10FeedFormatter StreamedFeed();  
}  
```  
  
 <span data-ttu-id="25e73-114">Služba implementuje tuto smlouvu pomocí `ItemGenerator` třídy pro vytvoření potenciálně nekonečného proudu <xref:System.ServiceModel.Syndication.SyndicationItem> instancí pomocí iterátoru, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="25e73-114">The service implements this contract by using an `ItemGenerator` class to create a potentially infinite stream of <xref:System.ServiceModel.Syndication.SyndicationItem> instances using an iterator, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="25e73-115">Když implementace služby vytvoří informační kanál, místo kolekce položek vyrovnávací paměti se použije výstup `ItemGenerator.GenerateItems()`.</span><span class="sxs-lookup"><span data-stu-id="25e73-115">When the service implementation creates the feed, the output of `ItemGenerator.GenerateItems()` is used instead of a buffered collection of items.</span></span>  
  
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
  
 <span data-ttu-id="25e73-116">V důsledku toho není datový proud položky nikdy plně ukládán do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="25e73-116">As a result, the item stream is never fully buffered into memory.</span></span> <span data-ttu-id="25e73-117">Toto chování lze sledovat nastavením zarážky v příkazu `yield return` v rámci metody `ItemGenerator.GenerateItems()` a zaznamenání, že tato zarážka je zjištěna poprvé poté, co služba vrátí výsledek metody `StreamedFeed()`.</span><span class="sxs-lookup"><span data-stu-id="25e73-117">You can observe this behavior by setting a breakpoint on the `yield return` statement inside of the `ItemGenerator.GenerateItems()` method and noting that this breakpoint is encountered for the first time after the service has returned the result of the `StreamedFeed()` method.</span></span>  
  
## <a name="client"></a><span data-ttu-id="25e73-118">Klient</span><span class="sxs-lookup"><span data-stu-id="25e73-118">Client</span></span>  
 <span data-ttu-id="25e73-119">Klient v této ukázce používá vlastní implementaci <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>, která zpozdí materializace jednotlivých položek v informačním kanálu namísto jejich ukládání do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="25e73-119">The client in this sample uses a custom <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> implementation that delays the materialization of individual items in the feed instead of buffering them into memory.</span></span> <span data-ttu-id="25e73-120">Vlastní `StreamedAtom10FeedFormatter` instance se používá následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="25e73-120">The custom `StreamedAtom10FeedFormatter` instance is used as follows.</span></span>  
  
```csharp  
XmlReader reader = XmlReader.Create("http://localhost:8000/Service/Feeds/StreamedFeed");  
StreamedAtom10FeedFormatter formatter = new StreamedAtom10FeedFormatter(counter);  
  
SyndicationFeed feed = formatter.ReadFrom(reader);  
```  
  
 <span data-ttu-id="25e73-121">V normálním případě volání <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> nevrátí, dokud nebude celý obsah informačního kanálu načten ze sítě a ukládán do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="25e73-121">Normally, a call to <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> does not return until the entire contents of the feed have been read from the network and buffered into memory.</span></span> <span data-ttu-id="25e73-122">Objekt `StreamedAtom10FeedFormatter` však přepisuje <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29>, aby vracel iterátor místo kolekce s vyrovnávací pamětí, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="25e73-122">However, the `StreamedAtom10FeedFormatter` object overrides <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> to return an iterator instead of a buffered collection, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="25e73-123">V důsledku toho se žádná položka nenačte ze sítě, dokud klientská aplikace, která projde výsledky `ReadItems()`, není připravená ji použít.</span><span class="sxs-lookup"><span data-stu-id="25e73-123">As a result, each item is not read from the network until the client application traversing the results of `ReadItems()` is ready to use it.</span></span> <span data-ttu-id="25e73-124">Toto chování lze sledovat nastavením zarážky v příkazu `yield return` v rámci `StreamedAtom10FeedFormatter.DelayReadItems()` a všímáte, že tato zarážka se při prvním výskytu volání `ReadFrom()` dokončí.</span><span class="sxs-lookup"><span data-stu-id="25e73-124">You can observe this behavior by setting a breakpoint on the `yield return` statement inside of `StreamedAtom10FeedFormatter.DelayReadItems()` and noticing that this breakpoint is encountered for the first time after the call to `ReadFrom()` completes.</span></span>  
  
 <span data-ttu-id="25e73-125">Následující pokyny ukazují, jak sestavit a spustit ukázku.</span><span class="sxs-lookup"><span data-stu-id="25e73-125">The following instructions show how to build and run the sample.</span></span> <span data-ttu-id="25e73-126">Všimněte si, že i když server přestane generovat položky poté, co klient přečte 10 položek, výstup ukazuje, že klient čte podstatně více než 10 položek.</span><span class="sxs-lookup"><span data-stu-id="25e73-126">Note that although the server stops generating items after the client has read 10 items, the output shows that the client reads significantly more than 10 items.</span></span> <span data-ttu-id="25e73-127">Důvodem je to, že síťová vazba, kterou ukázka používá, přenáší data v segmentech o čtyřech kilobajtech (KB).</span><span class="sxs-lookup"><span data-stu-id="25e73-127">This is because the networking binding used by the sample transmits data in four-kilobyte (KB) segments.</span></span> <span data-ttu-id="25e73-128">Klient tak obdrží 4KB dat položek předtím, než má příležitost číst i jednu položku.</span><span class="sxs-lookup"><span data-stu-id="25e73-128">As such, the client receives 4KB of item data before it has the opportunity to read even one item.</span></span> <span data-ttu-id="25e73-129">Jedná se o normální chování (při posílání streamovaná data HTTP v dostatečně velkých segmentech zvyšuje výkon).</span><span class="sxs-lookup"><span data-stu-id="25e73-129">This is normal behavior (sending streamed HTTP data in reasonably-sized segments increases performance).</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="25e73-130">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="25e73-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="25e73-131">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="25e73-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="25e73-132">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="25e73-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="25e73-133">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="25e73-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="25e73-134">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="25e73-134">The samples may already be installed on your computer.</span></span> <span data-ttu-id="25e73-135">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="25e73-135">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="25e73-136">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="25e73-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="25e73-137">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="25e73-137">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StreamingFeeds`  
  
## <a name="see-also"></a><span data-ttu-id="25e73-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="25e73-138">See also</span></span>

- [<span data-ttu-id="25e73-139">Samostatný diagnostický informační kanál</span><span class="sxs-lookup"><span data-stu-id="25e73-139">Stand-Alone Diagnostics Feed</span></span>](../../../../docs/framework/wcf/samples/stand-alone-diagnostics-feed-sample.md)
