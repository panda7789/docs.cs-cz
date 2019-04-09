---
title: Formátování informačního kanálu (JSON)
ms.date: 03/30/2017
ms.assetid: f9c0b295-55e7-48ea-b308-ba51c7d31143
ms.openlocfilehash: 322e6e120dd37c572e0ea98cb27cde50329ae365
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59131466"
---
# <a name="feed-formatter-json"></a><span data-ttu-id="52508-102">Formátování informačního kanálu (JSON)</span><span class="sxs-lookup"><span data-stu-id="52508-102">Feed Formatter (JSON)</span></span>
<span data-ttu-id="52508-103">Tento příklad ukazuje, jak k serializaci instancí <xref:System.ServiceModel.Syndication.SyndicationFeed> ve formátu JavaScript Object Notation (JSON) pomocí vlastní třídy <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="52508-103">This sample shows how to serialize an instance of a <xref:System.ServiceModel.Syndication.SyndicationFeed> class in JavaScript Object Notation (JSON) format by using a custom <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> and the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>  
  
## <a name="architecture-of-the-sample"></a><span data-ttu-id="52508-104">Architektura ukázky</span><span class="sxs-lookup"><span data-stu-id="52508-104">Architecture of the Sample</span></span>  
 <span data-ttu-id="52508-105">Ukázka implementuje třídu s názvem `JsonFeedFormatter` , která dědí z <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span><span class="sxs-lookup"><span data-stu-id="52508-105">The sample implements a class named `JsonFeedFormatter` that inherits from <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span></span> <span data-ttu-id="52508-106">`JsonFeedFormatter` Třídy se může spolehnout <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> číst a zapisovat data ve formátu JSON.</span><span class="sxs-lookup"><span data-stu-id="52508-106">The `JsonFeedFormatter` class relies on the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> to read and write the data in JSON format.</span></span> <span data-ttu-id="52508-107">Interně, formátovací modul používá vlastní sada datových typů kontraktu s názvem `JsonSyndicationFeed` a `JsonSyndicationItem` řídit formát JSON data vytvořená modulem pro serializaci.</span><span class="sxs-lookup"><span data-stu-id="52508-107">Internally, the formatter uses a custom set of data contract types named `JsonSyndicationFeed` and `JsonSyndicationItem` to control the format of the JSON data produced by the serializer.</span></span> <span data-ttu-id="52508-108">Tyto podrobnosti implementace jsou skryté koncového uživatele, což volání provedená oproti standardní <xref:System.ServiceModel.Syndication.SyndicationFeed> a <xref:System.ServiceModel.Syndication.SyndicationItem> třídy.</span><span class="sxs-lookup"><span data-stu-id="52508-108">These implementation details are hidden from the end user, allowing calls to be made against the standard <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem> classes.</span></span>  
  
## <a name="writing-json-feeds"></a><span data-ttu-id="52508-109">Zápis JSON kanály</span><span class="sxs-lookup"><span data-stu-id="52508-109">Writing JSON feeds</span></span>  
 <span data-ttu-id="52508-110">Zápis JSON kanálu se dá udělat pomocí `JsonFeedFormatter` (implementováno v této ukázce) se <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="52508-110">Writing a JSON feed can be accomplished by using the `JsonFeedFormatter` (implemented in this sample) with the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> as shown in the following sample code.</span></span>  
  
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
  
## <a name="reading-a-json-feed"></a><span data-ttu-id="52508-111">Čtení informačního kanálu ve formátu JSON</span><span class="sxs-lookup"><span data-stu-id="52508-111">Reading a JSON feed</span></span>  
 <span data-ttu-id="52508-112">Získání <xref:System.ServiceModel.Syndication.SyndicationFeed> z dat ve streamu formátu JSON, můžete provést pomocí `JsonFeedFormatter` tak, jak zobrazit v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="52508-112">Obtaining a <xref:System.ServiceModel.Syndication.SyndicationFeed> from a stream of JSON-formatted data can be accomplished with the `JsonFeedFormatter` as show in the following code.</span></span>  
  
 `//Read in the feed using the DataContractJsonSerializer`  
  
 `DataContractJsonSerializer readSerializer = new DataContractJsonSerializer(typeof(JsonFeedFormatter));`  
  
 `JsonFeedFormatter formatter = readSerializer.ReadObject(stream) as JsonFeedFormatter;`  
  
 `SyndicationFeed feedRead = formatter.Feed;`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="52508-113">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="52508-113">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="52508-114">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="52508-114">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="52508-115">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="52508-115">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="52508-116">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="52508-116">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="52508-117">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="52508-117">The samples may already be installed on your computer.</span></span> <span data-ttu-id="52508-118">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="52508-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="52508-119">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="52508-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="52508-120">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="52508-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\JsonFeeds`  
