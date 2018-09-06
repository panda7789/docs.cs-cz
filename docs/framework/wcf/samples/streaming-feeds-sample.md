---
title: Ukázka informačních kanálů streamování
ms.date: 03/30/2017
ms.assetid: 1f1228c0-daaa-45f0-b93e-c4a158113744
ms.openlocfilehash: 17639273ece804dc531cbbc3ab9135c814ea632d
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43800025"
---
# <a name="streaming-feeds-sample"></a><span data-ttu-id="984fb-102">Ukázka informačních kanálů streamování</span><span class="sxs-lookup"><span data-stu-id="984fb-102">Streaming Feeds Sample</span></span>
<span data-ttu-id="984fb-103">Tento příklad ukazuje, jak spravovat informační kanály syndikace, které obsahují velký počet položek.</span><span class="sxs-lookup"><span data-stu-id="984fb-103">This sample demonstrates how to manage syndication feeds that contain large numbers of items.</span></span> <span data-ttu-id="984fb-104">Na serveru, ukázka ukazuje, jak pozdržet jednotlivých <xref:System.ServiceModel.Syndication.SyndicationItem> objekty v rámci kanálu až do bezprostředně před položky jsou zapsána do datového proudu sítě.</span><span class="sxs-lookup"><span data-stu-id="984fb-104">On the server, the sample demonstrates how to delay the creation of individual <xref:System.ServiceModel.Syndication.SyndicationItem> objects within the feed until immediately before the item is written to the network stream.</span></span>  
  
 <span data-ttu-id="984fb-105">V klientském počítači příklad ukazuje použití vlastního formátování informačního kanálu syndikace číst jednotlivých položek z datového proudu sítě tak, aby čteného informačního kanálu do vyrovnávací paměti nikdy plně do paměti.</span><span class="sxs-lookup"><span data-stu-id="984fb-105">On the client, the sample shows how a custom syndication feed formatter can be used to read individual items from the network stream so that the feed being read is never fully buffered into memory.</span></span>  
  
 <span data-ttu-id="984fb-106">K předvedení nejlépe streamování funkce syndikace rozhraní API, tato ukázka používá poněkud nepravděpodobném scénáři, ve kterém server poskytuje informační kanál, který obsahuje neomezený počet položek.</span><span class="sxs-lookup"><span data-stu-id="984fb-106">To best demonstrate the streaming capability of the syndication API, this sample uses a somewhat unlikely scenario in which the server exposes a feed that contains an infinite number of items.</span></span> <span data-ttu-id="984fb-107">V tomto případě server pokračuje ve generování nových položek do informačního kanálu, dokud se určí, že klient má číst zadaný počet položek z informačního kanálu (výchozí hodnota je 10).</span><span class="sxs-lookup"><span data-stu-id="984fb-107">In this case, the server continues generating new items into the feed until it determines that the client has read a specified number of items from the feed (by default, 10).</span></span> <span data-ttu-id="984fb-108">Pro jednoduchost, klienta a serveru jsou implementovány v rámci stejného procesu a používat sdílené `ItemCounter` objektu, který chcete sledovat, kolik položek klient vytvořil.</span><span class="sxs-lookup"><span data-stu-id="984fb-108">For simplicity, both the client and the server are implemented in the same process and use a shared `ItemCounter` object to keep track of how many items the client has produced.</span></span> <span data-ttu-id="984fb-109">`ItemCounter` Typ existuje pouze pro účely povolení ukázkový scénář, který má ukončit čistě a není elementem základní vzor, který jsme vám právě ukázali.</span><span class="sxs-lookup"><span data-stu-id="984fb-109">The `ItemCounter` type exists only for the purpose of allowing the sample scenario to terminate cleanly, and is not a core element of the pattern being demonstrated.</span></span>  
  
 <span data-ttu-id="984fb-110">Ukázky využívá Visual C# iterátory (pomocí `yield return` konstrukce – klíčové slovo).</span><span class="sxs-lookup"><span data-stu-id="984fb-110">The demonstration makes use of Visual C# iterators (using the `yield return` keyword construct).</span></span> <span data-ttu-id="984fb-111">Další informace o iterátorech naleznete v tématu "Používání iterátorů" na webu MSDN.</span><span class="sxs-lookup"><span data-stu-id="984fb-111">For more information about iterators, see the "Using Iterators" topic on MSDN.</span></span>  
  
## <a name="service"></a><span data-ttu-id="984fb-112">Služba</span><span class="sxs-lookup"><span data-stu-id="984fb-112">Service</span></span>  
 <span data-ttu-id="984fb-113">Služba implementuje základní <xref:System.ServiceModel.Web.WebGetAttribute> kontrakt, který se skládá z jedné operace, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="984fb-113">The service implements a basic <xref:System.ServiceModel.Web.WebGetAttribute> contract that consists of one operation, as shown in the following code.</span></span>  
  
```  
[ServiceContract]  
interface IStreamingFeedService  
{  
    [WebGet]  
    [OperationContract]  
    Atom10FeedFormatter StreamedFeed();  
}  
```  
  
 <span data-ttu-id="984fb-114">Služba implementuje tento kontrakt s použitím `ItemGenerator` třídy za účelem vytvoření potenciálně nekonečné datový proud <xref:System.ServiceModel.Syndication.SyndicationItem> instance pomocí iterátoru, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="984fb-114">The service implements this contract by using an `ItemGenerator` class to create a potentially infinite stream of <xref:System.ServiceModel.Syndication.SyndicationItem> instances using an iterator, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="984fb-115">Při implementaci služby vytvoří kanál, výstup `ItemGenerator.GenerateItems()` se používá místo ve vyrovnávací paměti kolekce položek.</span><span class="sxs-lookup"><span data-stu-id="984fb-115">When the service implementation creates the feed, the output of `ItemGenerator.GenerateItems()` is used instead of a buffered collection of items.</span></span>  
  
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
  
 <span data-ttu-id="984fb-116">V důsledku toho položky datového proudu do vyrovnávací paměti nikdy plně do paměti.</span><span class="sxs-lookup"><span data-stu-id="984fb-116">As a result, the item stream is never fully buffered into memory.</span></span> <span data-ttu-id="984fb-117">Toto chování můžete sledovat pomocí nastavení zarážky na `yield return` příkaz uvnitř `ItemGenerator.GenerateItems()` metoda a poznamenat, že tato zarážka dochází poprvé po služba vrátila výsledek `StreamedFeed()` metody.</span><span class="sxs-lookup"><span data-stu-id="984fb-117">You can observe this behavior by setting a breakpoint on the `yield return` statement inside of the `ItemGenerator.GenerateItems()` method and noting that this breakpoint is encountered for the first time after the service has returned the result of the `StreamedFeed()` method.</span></span>  
  
## <a name="client"></a><span data-ttu-id="984fb-118">Klient</span><span class="sxs-lookup"><span data-stu-id="984fb-118">Client</span></span>  
 <span data-ttu-id="984fb-119">Klient v této ukázce používá vlastní <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> implementace, která způsobuje zpoždění materializace jednotlivých položek v informačním kanálu namísto jejich ukládání do vyrovnávací paměti do paměti.</span><span class="sxs-lookup"><span data-stu-id="984fb-119">The client in this sample uses a custom <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> implementation that delays the materialization of individual items in the feed instead of buffering them into memory.</span></span> <span data-ttu-id="984fb-120">Vlastní `StreamedAtom10FeedFormatter` instance se používá takto.</span><span class="sxs-lookup"><span data-stu-id="984fb-120">The custom `StreamedAtom10FeedFormatter` instance is used as follows.</span></span>  
  
```  
XmlReader reader = XmlReader.Create("http://localhost:8000/Service/Feeds/StreamedFeed");  
StreamedAtom10FeedFormatter formatter = new StreamedAtom10FeedFormatter(counter);  
  
SyndicationFeed feed = formatter.ReadFrom(reader);  
```  
  
 <span data-ttu-id="984fb-121">Za normálních okolností volání <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> nevrací dokud celý obsah informačního kanálu mají číst ze sítě a uložená do vyrovnávací paměti do paměti.</span><span class="sxs-lookup"><span data-stu-id="984fb-121">Normally, a call to <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> does not return until the entire contents of the feed have been read from the network and buffered into memory.</span></span> <span data-ttu-id="984fb-122">Ale `StreamedAtom10FeedFormatter` objektu přepsání <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> vrátit iterátor místo ve vyrovnávací paměti kolekce, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="984fb-122">However, the `StreamedAtom10FeedFormatter` object overrides <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> to return an iterator instead of a buffered collection, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="984fb-123">V důsledku toho není každé položky číst ze sítě do klientské aplikace, procházení výsledky `ReadItems()` je připravený k použití.</span><span class="sxs-lookup"><span data-stu-id="984fb-123">As a result, each item is not read from the network until the client application traversing the results of `ReadItems()` is ready to use it.</span></span> <span data-ttu-id="984fb-124">Toto chování můžete sledovat pomocí nastavení zarážky na `yield return` příkaz uvnitř `StreamedAtom10FeedFormatter.DelayReadItems()` a pozorujte, že tato zarážka dochází poprvé po volání `ReadFrom()` dokončí.</span><span class="sxs-lookup"><span data-stu-id="984fb-124">You can observe this behavior by setting a breakpoint on the `yield return` statement inside of `StreamedAtom10FeedFormatter.DelayReadItems()` and noticing that this breakpoint is encountered for the first time after the call to `ReadFrom()` completes.</span></span>  
  
 <span data-ttu-id="984fb-125">Následující pokyny ukazují, jak sestavit a spustit vzorku.</span><span class="sxs-lookup"><span data-stu-id="984fb-125">The following instructions show how to build and run the sample.</span></span> <span data-ttu-id="984fb-126">Všimněte si, že i když server přestane generování položky po klienta má ke čtení 10 položek, výstup ukazuje, že klient čte výrazně více než 10 položek.</span><span class="sxs-lookup"><span data-stu-id="984fb-126">Note that although the server stops generating items after the client has read 10 items, the output shows that the client reads significantly more than 10 items.</span></span> <span data-ttu-id="984fb-127">Je to proto, že síťové vazby používané v rámci ukázky přenáší data v příslušných segmentech čtyři kilobajtů (KB).</span><span class="sxs-lookup"><span data-stu-id="984fb-127">This is because the networking binding used by the sample transmits data in four-kilobyte (KB) segments.</span></span> <span data-ttu-id="984fb-128">V důsledku toho klient obdrží 4KB dat položky předtím, než má možnost číst i jenom jednu položku.</span><span class="sxs-lookup"><span data-stu-id="984fb-128">As such, the client receives 4KB of item data before it has the opportunity to read even one item.</span></span> <span data-ttu-id="984fb-129">Toto chování je běžné (odesílání datové proudy HTTP v rozumné míře velikosti segmentů zvýšení výkonu).</span><span class="sxs-lookup"><span data-stu-id="984fb-129">This is normal behavior (sending streamed HTTP data in reasonably-sized segments increases performance).</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="984fb-130">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="984fb-130">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="984fb-131">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="984fb-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="984fb-132">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="984fb-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="984fb-133">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="984fb-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="984fb-134">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="984fb-134">The samples may already be installed on your computer.</span></span> <span data-ttu-id="984fb-135">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="984fb-135">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="984fb-136">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="984fb-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="984fb-137">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="984fb-137">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StreamingFeeds`  
  
## <a name="see-also"></a><span data-ttu-id="984fb-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="984fb-138">See Also</span></span>  
 [<span data-ttu-id="984fb-139">Samostatný diagnostický informační kanál</span><span class="sxs-lookup"><span data-stu-id="984fb-139">Stand-Alone Diagnostics Feed</span></span>](../../../../docs/framework/wcf/samples/stand-alone-diagnostics-feed-sample.md)
