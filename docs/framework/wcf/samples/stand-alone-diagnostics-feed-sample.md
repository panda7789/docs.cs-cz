---
title: Ukázka samostatného diagnostického informačního kanálu
ms.date: 03/30/2017
ms.assetid: d31c6c1f-292c-4d95-8e23-ed8565970ea5
ms.openlocfilehash: 4520883b5db19c28544a5576ca600b83e37eede3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76787934"
---
# <a name="stand-alone-diagnostics-feed-sample"></a><span data-ttu-id="84aac-102">Ukázka samostatného diagnostického informačního kanálu</span><span class="sxs-lookup"><span data-stu-id="84aac-102">Stand-Alone Diagnostics Feed Sample</span></span>
<span data-ttu-id="84aac-103">Tato ukázka předvádí, jak vytvořit informační kanál RSS/Atom pro syndikaci pomocí Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="84aac-103">This sample demonstrates how to create an RSS/Atom feed for syndication with Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="84aac-104">Jedná se o základní program "Hello World", který ukazuje základy objektového modelu a jak ho nastavit ve službě Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="84aac-104">It is a basic "Hello World" program that shows the basics of the object model and how to set it up on a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="84aac-105">Modely WCF: informační kanály syndikace jako operace služby, které vracejí speciální datový typ, <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span><span class="sxs-lookup"><span data-stu-id="84aac-105">WCF models syndication feeds as service operations that return a special data type, <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span></span> <span data-ttu-id="84aac-106">Instance <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> mohou serializovat informační kanál do formátů RSS 2,0 a Atom 1,0.</span><span class="sxs-lookup"><span data-stu-id="84aac-106">Instances of <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> can serialize a feed into both the RSS 2.0 and Atom 1.0 formats.</span></span> <span data-ttu-id="84aac-107">Následující vzorový kód ukazuje použití smlouvy.</span><span class="sxs-lookup"><span data-stu-id="84aac-107">The following sample code shows the contract used.</span></span>  
  
```csharp  
[ServiceContract(Namespace = "")]  
    interface IDiagnosticsService  
    {  
        [OperationContract]  
        //The [WebGet] attribute controls how WCF dispatches  
        //HTTP requests to service operations based on a URI suffix  
        //(the part of the request URI after the endpoint address)  
        //using the HTTP GET method. The UriTemplate specifies a relative  
        //path of 'feed', and specifies that the format is  
        //supplied using a query string.   
        [WebGet(UriTemplate="feed?format={format}")]  
        [ServiceKnownType(typeof(Atom10FeedFormatter))]  
        [ServiceKnownType(typeof(Rss20FeedFormatter))]  
        SyndicationFeedFormatter GetProcesses(string format);  
    }  
```  
  
 <span data-ttu-id="84aac-108">Operace `GetProcesses` je označena atributem <xref:System.ServiceModel.Web.WebGetAttribute>, který umožňuje řídit, jak služba WCF odesílá požadavky HTTP GET na operace služby a určuje formát odeslaných zpráv.</span><span class="sxs-lookup"><span data-stu-id="84aac-108">The `GetProcesses` operation is annotated with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute that enables you to control how WCF dispatches HTTP GET requests to service operations and specify the format of the messages sent.</span></span>  
  
 <span data-ttu-id="84aac-109">Podobně jako u libovolné služby WCF se můžou informační kanály syndikace hostovat sami v jakékoli spravované aplikaci.</span><span class="sxs-lookup"><span data-stu-id="84aac-109">Like any WCF service, syndication feeds can be self hosted in any managed application.</span></span> <span data-ttu-id="84aac-110">Služba syndikace vyžaduje konkrétní vazbu (<xref:System.ServiceModel.WebHttpBinding>) a specifické chování koncového bodu (<xref:System.ServiceModel.Description.WebHttpBehavior>), aby fungovalo správně.</span><span class="sxs-lookup"><span data-stu-id="84aac-110">Syndication services require a specific binding (the <xref:System.ServiceModel.WebHttpBinding>) and a specific endpoint behavior (the <xref:System.ServiceModel.Description.WebHttpBehavior>) to function correctly.</span></span> <span data-ttu-id="84aac-111">Nová třída <xref:System.ServiceModel.Web.WebServiceHost> poskytuje pohodlný rozhraní API pro vytváření takových koncových bodů bez konkrétní konfigurace.</span><span class="sxs-lookup"><span data-stu-id="84aac-111">The new <xref:System.ServiceModel.Web.WebServiceHost> class provides a convenient API for creating such endpoints without specific configuration.</span></span>  
  
```csharp  
WebServiceHost host = new WebServiceHost(typeof(ProcessService), new Uri("http://localhost:8000/diagnostics"));  
  
            //The WebServiceHost will automatically provide a default endpoint at the base address  
            //using the proper binding (the WebHttpBinding) and endpoint behavior (the WebHttpBehavior)  
```  
  
 <span data-ttu-id="84aac-112">Alternativně můžete použít <xref:System.ServiceModel.Activation.WebServiceHostFactory> ze souboru hostovaného v rámci služby IIS k poskytnutí ekvivalentních funkcí (Tato technika není znázorněna v tomto ukázkovém kódu).</span><span class="sxs-lookup"><span data-stu-id="84aac-112">Alternatively, you can use <xref:System.ServiceModel.Activation.WebServiceHostFactory> from within an IIS-hosted .svc file to provide equivalent functionality (this technique is not demonstrated in this sample code).</span></span>  
  
```xml
<%@ ServiceHost Language="C#|VB" Debug="true" Service="ProcessService" %>
```
  
 <span data-ttu-id="84aac-113">Vzhledem k tomu, že tato služba přijímá žádosti pomocí standardního HTTP GET, můžete k přístupu ke službě použít libovolného klienta využívajícího technologii RSS nebo ATOM.</span><span class="sxs-lookup"><span data-stu-id="84aac-113">Because this service receives requests using the standard HTTP GET, you can use any RSS or ATOM-aware client to access the service.</span></span> <span data-ttu-id="84aac-114">Výstup této služby můžete například zobrazit tak, že přejdete na `http://localhost:8000/diagnostics/feed/?format=atom` nebo `http://localhost:8000/diagnostics/feed/?format=rss` v prohlížeči podporujícím technologii RSS.</span><span class="sxs-lookup"><span data-stu-id="84aac-114">For example, you can view the output of this service by navigating to `http://localhost:8000/diagnostics/feed/?format=atom` or `http://localhost:8000/diagnostics/feed/?format=rss` in an RSS-aware browser.</span></span>
  
 <span data-ttu-id="84aac-115">Můžete také použít způsob, [jakým objektový model Syndikace WCF mapuje na Atom a RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) pro čtení publikovaných dat a jejich zpracování pomocí imperativního kódu.</span><span class="sxs-lookup"><span data-stu-id="84aac-115">You can also use the [How the WCF Syndication Object Model Maps to Atom and RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) to read syndicated data and process it using imperative code.</span></span>  
  
```csharp
XmlReader reader = XmlReader.Create( "http://localhost:8000/diagnostics/feed/?format=rss",
    new XmlReaderSettings()
    {
        //MaxCharactersInDocument can be used to control the maximum amount of data
        //read from the reader and helps prevent OutOfMemoryException
        MaxCharactersInDocument = 1024 * 64
    } );

SyndicationFeed feed = SyndicationFeed.Load(reader);

foreach (SyndicationItem i in feed.Items)
{
    XmlSyndicationContent content = i.Content as XmlSyndicationContent;
    ProcessData pd = content.ReadContent<ProcessData>();

    Console.WriteLine(i.Title.Text);
    Console.WriteLine(pd.ToString());
}
```
  
## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="84aac-116">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="84aac-116">Set up, build, and run the sample</span></span>
  
1. <span data-ttu-id="84aac-117">Ujistěte se, že máte v počítači správné oprávnění k registraci adres pro HTTP a HTTPS, jak je vysvětleno v postupu nastavení v části Postup nastavení v [Windows Communication Foundationch ukázkách](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="84aac-117">Ensure that you have the right address registration permission for HTTP and HTTPS on the computer as explained in the set up instructions in [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="84aac-118">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="84aac-118">Build the solution.</span></span>

3. <span data-ttu-id="84aac-119">Spusťte konzolovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="84aac-119">Run the console application.</span></span>

4. <span data-ttu-id="84aac-120">Když je spuštěná Konzolová aplikace, přejděte do `http://localhost:8000/diagnostics/feed/?format=atom` nebo `http://localhost:8000/diagnostics/feed/?format=rss` pomocí prohlížeče podporujícího technologii RSS.</span><span class="sxs-lookup"><span data-stu-id="84aac-120">While the console application is running, navigate to `http://localhost:8000/diagnostics/feed/?format=atom` or `http://localhost:8000/diagnostics/feed/?format=rss` using an RSS-aware browser.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="84aac-121">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="84aac-121">The samples may already be installed on your computer.</span></span> <span data-ttu-id="84aac-122">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="84aac-122">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="84aac-123">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="84aac-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="84aac-124">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="84aac-124">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\DiagnosticsFeed`

## <a name="see-also"></a><span data-ttu-id="84aac-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="84aac-125">See also</span></span>

- [<span data-ttu-id="84aac-126">Programovací model webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="84aac-126">WCF Web HTTP Programming Model</span></span>](../feature-details/wcf-web-http-programming-model.md)
- [<span data-ttu-id="84aac-127">Syndikace WCF</span><span class="sxs-lookup"><span data-stu-id="84aac-127">WCF Syndication</span></span>](../feature-details/wcf-syndication.md)
