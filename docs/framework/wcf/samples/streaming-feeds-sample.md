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
# <a name="streaming-feeds-sample"></a><span data-ttu-id="e2bb4-102">Ukázka informačních kanálů streamování</span><span class="sxs-lookup"><span data-stu-id="e2bb4-102">Streaming Feeds Sample</span></span>
<span data-ttu-id="e2bb4-103">Tato ukázka ukazuje, jak spravovat syndikační kanály, které obsahují velký počet položek.</span><span class="sxs-lookup"><span data-stu-id="e2bb4-103">This sample demonstrates how to manage syndication feeds that contain large numbers of items.</span></span> <span data-ttu-id="e2bb4-104">Na serveru ukázka ukazuje, jak odložit vytvoření <xref:System.ServiceModel.Syndication.SyndicationItem> jednotlivých objektů v rámci informačního kanálu, dokud bezprostředně před položkou zapsána do síťového proudu.</span><span class="sxs-lookup"><span data-stu-id="e2bb4-104">On the server, the sample demonstrates how to delay the creation of individual <xref:System.ServiceModel.Syndication.SyndicationItem> objects within the feed until immediately before the item is written to the network stream.</span></span>  
  
 <span data-ttu-id="e2bb4-105">Na straně klienta ukázka ukazuje, jak vlastní syndikace krmivo formodul lze použít ke čtení jednotlivých položek ze síťového proudu tak, aby zdroj čtení není nikdy plně do vyrovnávací paměti do paměti.</span><span class="sxs-lookup"><span data-stu-id="e2bb4-105">On the client, the sample shows how a custom syndication feed formatter can be used to read individual items from the network stream so that the feed being read is never fully buffered into memory.</span></span>  
  
 <span data-ttu-id="e2bb4-106">Chcete-li nejlépe demonstrovat schopnost streamování syndikace rozhraní API, tato ukázka používá poněkud nepravděpodobný scénář, ve kterém server zveřejňuje informační kanál, který obsahuje nekonečný počet položek.</span><span class="sxs-lookup"><span data-stu-id="e2bb4-106">To best demonstrate the streaming capability of the syndication API, this sample uses a somewhat unlikely scenario in which the server exposes a feed that contains an infinite number of items.</span></span> <span data-ttu-id="e2bb4-107">V tomto případě server pokračuje ve generování nových položek do informačního kanálu, dokud nezjistí, že klient přečetl zadaný počet položek z informačního kanálu (ve výchozím nastavení 10).</span><span class="sxs-lookup"><span data-stu-id="e2bb4-107">In this case, the server continues generating new items into the feed until it determines that the client has read a specified number of items from the feed (by default, 10).</span></span> <span data-ttu-id="e2bb4-108">Pro jednoduchost klient a server jsou implementovány ve stejném procesu `ItemCounter` a použít sdílený objekt sledovat, kolik položek klient vytvořil.</span><span class="sxs-lookup"><span data-stu-id="e2bb4-108">For simplicity, both the client and the server are implemented in the same process and use a shared `ItemCounter` object to keep track of how many items the client has produced.</span></span> <span data-ttu-id="e2bb4-109">Typ `ItemCounter` existuje pouze za účelem povolení ukázkový scénář ukončit čistě a není základní prvek vzoru je prokázáno.</span><span class="sxs-lookup"><span data-stu-id="e2bb4-109">The `ItemCounter` type exists only for the purpose of allowing the sample scenario to terminate cleanly, and is not a core element of the pattern being demonstrated.</span></span>  
  
 <span data-ttu-id="e2bb4-110">Demonstrace využívá visual c# iterátory (pomocí `yield return` klíčové ho konstruktu).</span><span class="sxs-lookup"><span data-stu-id="e2bb4-110">The demonstration makes use of Visual C# iterators (using the `yield return` keyword construct).</span></span> <span data-ttu-id="e2bb4-111">Další informace o iterátorech naleznete v tématu "Using Iterators" na msdn.</span><span class="sxs-lookup"><span data-stu-id="e2bb4-111">For more information about iterators, see the "Using Iterators" topic on MSDN.</span></span>  
  
## <a name="service"></a><span data-ttu-id="e2bb4-112">Služba</span><span class="sxs-lookup"><span data-stu-id="e2bb4-112">Service</span></span>  
 <span data-ttu-id="e2bb4-113">Služba implementuje <xref:System.ServiceModel.Web.WebGetAttribute> základní smlouvu, která se skládá z jedné operace, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="e2bb4-113">The service implements a basic <xref:System.ServiceModel.Web.WebGetAttribute> contract that consists of one operation, as shown in the following code.</span></span>  
  
```csharp  
[ServiceContract]  
interface IStreamingFeedService  
{  
    [WebGet]  
    [OperationContract]  
    Atom10FeedFormatter StreamedFeed();  
}  
```  
  
 <span data-ttu-id="e2bb4-114">Služba implementuje tuto smlouvu `ItemGenerator` pomocí třídy k <xref:System.ServiceModel.Syndication.SyndicationItem> vytvoření potenciálně nekonečného proudu instancí pomocí iterátoru, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="e2bb4-114">The service implements this contract by using an `ItemGenerator` class to create a potentially infinite stream of <xref:System.ServiceModel.Syndication.SyndicationItem> instances using an iterator, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="e2bb4-115">Když implementace služby vytvoří informační `ItemGenerator.GenerateItems()` kanál, výstup se používá namísto vyrovnávací kolekce položek.</span><span class="sxs-lookup"><span data-stu-id="e2bb4-115">When the service implementation creates the feed, the output of `ItemGenerator.GenerateItems()` is used instead of a buffered collection of items.</span></span>  
  
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
  
 <span data-ttu-id="e2bb4-116">V důsledku toho datový proud položky není nikdy plně do vyrovnávací paměti do paměti.</span><span class="sxs-lookup"><span data-stu-id="e2bb4-116">As a result, the item stream is never fully buffered into memory.</span></span> <span data-ttu-id="e2bb4-117">Toto chování můžete sledovat nastavením `yield return` zarážky na `ItemGenerator.GenerateItems()` příkaz uvnitř metody a s tím, že tato zarážka `StreamedFeed()` je zjištěna poprvé poté, co služba vrátila výsledek metody.</span><span class="sxs-lookup"><span data-stu-id="e2bb4-117">You can observe this behavior by setting a breakpoint on the `yield return` statement inside of the `ItemGenerator.GenerateItems()` method and noting that this breakpoint is encountered for the first time after the service has returned the result of the `StreamedFeed()` method.</span></span>  
  
## <a name="client"></a><span data-ttu-id="e2bb4-118">Klient</span><span class="sxs-lookup"><span data-stu-id="e2bb4-118">Client</span></span>  
 <span data-ttu-id="e2bb4-119">Klient v této ukázce používá vlastní <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> implementaci, která zpožďuje materializaci jednotlivých položek v informačním kanálu namísto ukládání do vyrovnávací paměti do paměti.</span><span class="sxs-lookup"><span data-stu-id="e2bb4-119">The client in this sample uses a custom <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> implementation that delays the materialization of individual items in the feed instead of buffering them into memory.</span></span> <span data-ttu-id="e2bb4-120">Vlastní `StreamedAtom10FeedFormatter` instance se používá následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="e2bb4-120">The custom `StreamedAtom10FeedFormatter` instance is used as follows.</span></span>  
  
```csharp  
XmlReader reader = XmlReader.Create("http://localhost:8000/Service/Feeds/StreamedFeed");  
StreamedAtom10FeedFormatter formatter = new StreamedAtom10FeedFormatter(counter);  
  
SyndicationFeed feed = formatter.ReadFrom(reader);  
```  
  
 <span data-ttu-id="e2bb4-121">Volání se <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> obvykle nevrátí, dokud celý obsah informačního kanálu byly přečteny ze sítě a do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="e2bb4-121">Normally, a call to <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter.ReadFrom%28System.Xml.XmlReader%29> does not return until the entire contents of the feed have been read from the network and buffered into memory.</span></span> <span data-ttu-id="e2bb4-122">Objekt však `StreamedAtom10FeedFormatter` přepíše <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> vrátit iterátor namísto vyrovnávací paměti kolekce, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="e2bb4-122">However, the `StreamedAtom10FeedFormatter` object overrides <xref:System.ServiceModel.Syndication.Atom10FeedFormatter.ReadItems%28System.Xml.XmlReader%2CSystem.ServiceModel.Syndication.SyndicationFeed%2CSystem.Boolean%40%29> to return an iterator instead of a buffered collection, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="e2bb4-123">V důsledku toho každá položka není číst ze sítě, dokud `ReadItems()` klientská aplikace procházet výsledky je připraven k použití.</span><span class="sxs-lookup"><span data-stu-id="e2bb4-123">As a result, each item is not read from the network until the client application traversing the results of `ReadItems()` is ready to use it.</span></span> <span data-ttu-id="e2bb4-124">Toto chování můžete sledovat nastavením `yield return` zarážky `StreamedAtom10FeedFormatter.DelayReadItems()` na příkaz uvnitř a všimněte si, že tato zarážka je zjištěna poprvé po `ReadFrom()` dokončení volání.</span><span class="sxs-lookup"><span data-stu-id="e2bb4-124">You can observe this behavior by setting a breakpoint on the `yield return` statement inside of `StreamedAtom10FeedFormatter.DelayReadItems()` and noticing that this breakpoint is encountered for the first time after the call to `ReadFrom()` completes.</span></span>  
  
 <span data-ttu-id="e2bb4-125">Následující pokyny ukazují, jak vytvořit a spustit ukázku.</span><span class="sxs-lookup"><span data-stu-id="e2bb4-125">The following instructions show how to build and run the sample.</span></span> <span data-ttu-id="e2bb4-126">Všimněte si, že i když server přestane generovat položky poté, co klient přečetl 10 položek, výstup ukazuje, že klient čte výrazně více než 10 položek.</span><span class="sxs-lookup"><span data-stu-id="e2bb4-126">Note that although the server stops generating items after the client has read 10 items, the output shows that the client reads significantly more than 10 items.</span></span> <span data-ttu-id="e2bb4-127">Důvodem je, že síťová vazba používaná ukázkou přenáší data v segmentech kb čtyř kilobajtů.</span><span class="sxs-lookup"><span data-stu-id="e2bb4-127">This is because the networking binding used by the sample transmits data in four-kilobyte (KB) segments.</span></span> <span data-ttu-id="e2bb4-128">Jako takový klient obdrží 4 KB dat položky před tím, než má možnost číst i jednu položku.</span><span class="sxs-lookup"><span data-stu-id="e2bb4-128">As such, the client receives 4KB of item data before it has the opportunity to read even one item.</span></span> <span data-ttu-id="e2bb4-129">Toto je normální chování (odesílání dat protokolu HTTP datových proudů v přiměřeně velkých segmentech zvyšuje výkon).</span><span class="sxs-lookup"><span data-stu-id="e2bb4-129">This is normal behavior (sending streamed HTTP data in reasonably-sized segments increases performance).</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e2bb4-130">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="e2bb4-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e2bb4-131">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e2bb4-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="e2bb4-132">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e2bb4-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="e2bb4-133">Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e2bb4-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e2bb4-134">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="e2bb4-134">The samples may already be installed on your computer.</span></span> <span data-ttu-id="e2bb4-135">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="e2bb4-135">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="e2bb4-136">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="e2bb4-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e2bb4-137">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="e2bb4-137">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StreamingFeeds`  
  
## <a name="see-also"></a><span data-ttu-id="e2bb4-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="e2bb4-138">See also</span></span>

- [<span data-ttu-id="e2bb4-139">Samostatný diagnostický informační kanál</span><span class="sxs-lookup"><span data-stu-id="e2bb4-139">Stand-Alone Diagnostics Feed</span></span>](../../../../docs/framework/wcf/samples/stand-alone-diagnostics-feed-sample.md)
