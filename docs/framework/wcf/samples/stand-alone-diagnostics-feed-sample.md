---
title: "Ukázka samostatného diagnostického informačního kanálu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d31c6c1f-292c-4d95-8e23-ed8565970ea5
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 89de6bcbb44ca70592697ccf891099446b230ce6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="stand-alone-diagnostics-feed-sample"></a><span data-ttu-id="b8936-102">Ukázka samostatného diagnostického informačního kanálu</span><span class="sxs-lookup"><span data-stu-id="b8936-102">Stand-Alone Diagnostics Feed Sample</span></span>
<span data-ttu-id="b8936-103">Tento příklad ukazuje postup vytvoření informačního kanálu RSS nebo kanálu Atom pro syndikace s [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b8936-103">This sample demonstrates how to create an RSS/Atom feed for syndication with [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="b8936-104">Je základní program "Hello World", který ukazuje základy objektový model a jak nastavit na [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby.</span><span class="sxs-lookup"><span data-stu-id="b8936-104">It is a basic "Hello World" program that shows the basics of the object model and how to set it up on a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="b8936-105">modely jako operace služby, které vracejí speciální datového typu, informační kanály syndikace <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span><span class="sxs-lookup"><span data-stu-id="b8936-105"> models syndication feeds as service operations that return a special data type, <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span></span> <span data-ttu-id="b8936-106">Instance <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> může serializovat informačního kanálu do formátů, jak technologie RSS 2.0 a Atom 1.0.</span><span class="sxs-lookup"><span data-stu-id="b8936-106">Instances of <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> can serialize a feed into both the RSS 2.0 and Atom 1.0 formats.</span></span> <span data-ttu-id="b8936-107">Následující vzorový kód ukazuje kontrakt použít.</span><span class="sxs-lookup"><span data-stu-id="b8936-107">The following sample code shows the contract used.</span></span>  
  
```  
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
  
 <span data-ttu-id="b8936-108">`GetProcesses` Je opatřen poznámkou operaci <xref:System.ServiceModel.Web.WebGetAttribute> atribut, který umožňuje určit jak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] odešle zprávu žádosti HTTP GET na služby operations a zadejte formát zprávy odeslané.</span><span class="sxs-lookup"><span data-stu-id="b8936-108">The `GetProcesses` operation is annotated with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute that enables you to control how [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dispatches HTTP GET requests to service operations and specify the format of the messages sent.</span></span>  
  
 <span data-ttu-id="b8936-109">Jako žádné [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby, informační kanály syndikace může být sám sebou hostované ve všech spravovaných aplikací.</span><span class="sxs-lookup"><span data-stu-id="b8936-109">Like any [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service, syndication feeds can be self hosted in any managed application.</span></span> <span data-ttu-id="b8936-110">Syndikace služby vyžadují konkrétní vazbu ( <xref:System.ServiceModel.WebHttpBinding>) a chování konkrétní koncový bod ( <xref:System.ServiceModel.Description.WebHttpBehavior>) fungovat správně.</span><span class="sxs-lookup"><span data-stu-id="b8936-110">Syndication services require a specific binding (the <xref:System.ServiceModel.WebHttpBinding>) and a specific endpoint behavior (the <xref:System.ServiceModel.Description.WebHttpBehavior>) to function correctly.</span></span> <span data-ttu-id="b8936-111">Nové <xref:System.ServiceModel.Web.WebServiceHost> třída poskytuje pohodlné rozhraní API pro vytváření těchto koncových bodů bez konkrétní konfigurace.</span><span class="sxs-lookup"><span data-stu-id="b8936-111">The new <xref:System.ServiceModel.Web.WebServiceHost> class provides a convenient API for creating such endpoints without specific configuration.</span></span>  
  
```  
WebServiceHost host = new WebServiceHost(typeof(ProcessService), new Uri("http://localhost:8000/diagnostics"));  
  
            //The WebServiceHost will automatically provide a default endpoint at the base address  
            //using the proper binding (the WebHttpBinding) and endpoint behavior (the WebHttpBehavior)  
```  
  
 <span data-ttu-id="b8936-112">Alternativně můžete použít <xref:System.ServiceModel.Activation.WebServiceHostFactory> z v rámci soubor hostované službou IIS SVC ekvivalentní nakonfigurovánu (Tento postup není ukázáno v ukázkový kód).</span><span class="sxs-lookup"><span data-stu-id="b8936-112">Alternatively, you can use <xref:System.ServiceModel.Activation.WebServiceHostFactory> from within an IIS-hosted .svc file to provide equivalent functionality (this technique is not demonstrated in this sample code).</span></span>  
  
```  
<%@ ServiceHost Language="C#|VB" Debug="true" Service="ProcessService" %>  
```  
  
 <span data-ttu-id="b8936-113">Protože tato služba přijímá požadavky pomocí standardní HTTP GET, můžete použít libovolného klienta RSS nebo ATOM podporující přístup ke službě.</span><span class="sxs-lookup"><span data-stu-id="b8936-113">Because this service receives requests using the standard HTTP GET, you can use any RSS or ATOM-aware client to access the service.</span></span> <span data-ttu-id="b8936-114">Například můžete zobrazit výstup této služby přechodem na http://localhost: 8000/diagnostiky nebo informační kanál /? formátu =, nebo http://localhost: 8000/diagnostiky nebo informační kanál atom /? formátu = rss v prohlížeči sítě podporující RSS, jako je například Internet Explorer 7.</span><span class="sxs-lookup"><span data-stu-id="b8936-114">For example, you can view the output of this service by navigating to http://localhost:8000/diagnostics/feed/?format=atom or http://localhost:8000/diagnostics/feed/?format=rss in an RSS-aware browser such as Internet Explorer 7.</span></span>  
  
 <span data-ttu-id="b8936-115">Můžete také [jak WCF syndikace objektu modelu mapy na Atom a RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) ke čtení syndikovaný dat a zpracování pomocí imperativní kódu.</span><span class="sxs-lookup"><span data-stu-id="b8936-115">You can also use the [How the WCF Syndication Object Model Maps to Atom and RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) to read syndicated data and process it using imperative code.</span></span>  
  
```  
XmlReader reader = XmlReader.Create( "http://localhost:8000/diagnostics/feed/?format=rss",  
new XmlReaderSettings()  
{  
//MaxCharactersInDocument can be used to control the maximum amount of data   
//read from the reader and helps prevent OutOfMemoryException  
MaxCharactersInDocument = 1024 * 64  
} );  
  
SyndicationFeed feed = SyndicationFeed.Load( reader );  
  
foreach (SyndicationItem i in feed.Items)  
{  
        XmlSyndicationContent content = i.Content as XmlSyndicationContent;  
        ProcessData pd = content.ReadContent<ProcessData>();  
  
        Console.WriteLine(i.Title.Text);  
        Console.WriteLine(pd.ToString());  
}  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b8936-116">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="b8936-116">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="b8936-117">Ujistěte se, zda máte oprávnění registrace správné adresy pro protokol HTTP a HTTPS v počítači, jak je popsáno v nastavení podle pokynů [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b8936-117">Ensure that you have the right address registration permission for HTTP and HTTPS on the computer as explained in the set up instructions in [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="b8936-118">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="b8936-118">Build the solution.</span></span>  
  
3.  <span data-ttu-id="b8936-119">Spusťte konzolovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b8936-119">Run the console application.</span></span>  
  
4.  <span data-ttu-id="b8936-120">Je spuštěn konzolové aplikace, přejděte na http://localhost: 8000/diagnostiky nebo informační kanál /? formátu =, nebo http://localhost: 8000/diagnostiky nebo informační kanál atom /? formátu = rss pomocí podporující RSS prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="b8936-120">While the console application is running, navigate to http://localhost:8000/diagnostics/feed/?format=atom or http://localhost:8000/diagnostics/feed/?format=rss using an RSS-aware browser.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b8936-121">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="b8936-121">The samples may already be installed on your computer.</span></span> <span data-ttu-id="b8936-122">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="b8936-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b8936-123">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="b8936-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b8936-124">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="b8936-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\DiagnosticsFeed`  
  
## <a name="see-also"></a><span data-ttu-id="b8936-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="b8936-125">See Also</span></span>  
 [<span data-ttu-id="b8936-126">Model programování webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="b8936-126">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [<span data-ttu-id="b8936-127">Syndikace WCF</span><span class="sxs-lookup"><span data-stu-id="b8936-127">WCF Syndication</span></span>](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
