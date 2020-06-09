---
title: Formátování informačního kanálu (JSON)
ms.date: 03/30/2017
ms.assetid: f9c0b295-55e7-48ea-b308-ba51c7d31143
ms.openlocfilehash: 7b535a5090d3c7df59b7faada35fc324a77b5651
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594670"
---
# <a name="feed-formatter-json"></a><span data-ttu-id="84f14-102">Formátování informačního kanálu (JSON)</span><span class="sxs-lookup"><span data-stu-id="84f14-102">Feed Formatter (JSON)</span></span>
<span data-ttu-id="84f14-103">Tento příklad ukazuje, jak serializovat instanci <xref:System.ServiceModel.Syndication.SyndicationFeed> třídy ve formátu JavaScript Object Notation (JSON) pomocí vlastní <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> .</span><span class="sxs-lookup"><span data-stu-id="84f14-103">This sample shows how to serialize an instance of a <xref:System.ServiceModel.Syndication.SyndicationFeed> class in JavaScript Object Notation (JSON) format by using a custom <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> and the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
## <a name="architecture-of-the-sample"></a><span data-ttu-id="84f14-104">Architektura ukázky</span><span class="sxs-lookup"><span data-stu-id="84f14-104">Architecture of the Sample</span></span>  
 <span data-ttu-id="84f14-105">Ukázka implementuje třídu s názvem `JsonFeedFormatter` , která dědí z <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> .</span><span class="sxs-lookup"><span data-stu-id="84f14-105">The sample implements a class named `JsonFeedFormatter` that inherits from <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span></span> <span data-ttu-id="84f14-106">`JsonFeedFormatter`Třída spoléhá na <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ke čtení a zápisu dat ve formátu JSON.</span><span class="sxs-lookup"><span data-stu-id="84f14-106">The `JsonFeedFormatter` class relies on the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> to read and write the data in JSON format.</span></span> <span data-ttu-id="84f14-107">Interně, formátovací modul používá vlastní sadu typů kontraktů dat s názvem `JsonSyndicationFeed` a `JsonSyndicationItem` k řízení formátu dat JSON vytvořených serializátorem.</span><span class="sxs-lookup"><span data-stu-id="84f14-107">Internally, the formatter uses a custom set of data contract types named `JsonSyndicationFeed` and `JsonSyndicationItem` to control the format of the JSON data produced by the serializer.</span></span> <span data-ttu-id="84f14-108">Tyto podrobnosti implementace jsou skryté od koncového uživatele, což umožňuje provádět volání proti standardním <xref:System.ServiceModel.Syndication.SyndicationFeed> <xref:System.ServiceModel.Syndication.SyndicationItem> třídám a.</span><span class="sxs-lookup"><span data-stu-id="84f14-108">These implementation details are hidden from the end user, allowing calls to be made against the standard <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem> classes.</span></span>  
  
## <a name="writing-json-feeds"></a><span data-ttu-id="84f14-109">Zápis kanálů JSON</span><span class="sxs-lookup"><span data-stu-id="84f14-109">Writing JSON feeds</span></span>  
 <span data-ttu-id="84f14-110">Zápis datového kanálu JSON se dá provést pomocí `JsonFeedFormatter` (implementované v této ukázce) s, jak je <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="84f14-110">Writing a JSON feed can be accomplished by using the `JsonFeedFormatter` (implemented in this sample) with the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> as shown in the following sample code.</span></span>  
  
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
  
## <a name="reading-a-json-feed"></a><span data-ttu-id="84f14-111">Čtení informačního kanálu JSON</span><span class="sxs-lookup"><span data-stu-id="84f14-111">Reading a JSON feed</span></span>  
 <span data-ttu-id="84f14-112">Získání a <xref:System.ServiceModel.Syndication.SyndicationFeed> z datového proudu dat ve formátu JSON lze dosáhnout pomocí, jak je `JsonFeedFormatter` znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="84f14-112">Obtaining a <xref:System.ServiceModel.Syndication.SyndicationFeed> from a stream of JSON-formatted data can be accomplished with the `JsonFeedFormatter` as show in the following code.</span></span>  
  
 `//Read in the feed using the DataContractJsonSerializer`  
  
 `DataContractJsonSerializer readSerializer = new DataContractJsonSerializer(typeof(JsonFeedFormatter));`  
  
 `JsonFeedFormatter formatter = readSerializer.ReadObject(stream) as JsonFeedFormatter;`  
  
 `SyndicationFeed feedRead = formatter.Feed;`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="84f14-113">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="84f14-113">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="84f14-114">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="84f14-114">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="84f14-115">Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="84f14-115">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="84f14-116">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="84f14-116">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="84f14-117">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="84f14-117">The samples may already be installed on your computer.</span></span> <span data-ttu-id="84f14-118">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="84f14-118">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="84f14-119">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="84f14-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="84f14-120">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="84f14-120">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\JsonFeeds`  
