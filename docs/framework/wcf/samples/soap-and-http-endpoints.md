---
title: "Koncové body SOAP a HTTP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e3c8be75-9dda-4afa-89b6-a82cb3b73cf8
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d122512a16a0959d60bfa658d96aa87a52e40299
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="soap-and-http-endpoints"></a><span data-ttu-id="b721b-102">Koncové body SOAP a HTTP</span><span class="sxs-lookup"><span data-stu-id="b721b-102">SOAP and HTTP Endpoints</span></span>
<span data-ttu-id="b721b-103">Tento příklad znázorňuje způsob implementace služby vzdáleného volání procedur a vystavit ve formátu protokolu SOAP a "prostý formát XML" (POX) naformátovat pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] webové programování modelu.</span><span class="sxs-lookup"><span data-stu-id="b721b-103">This sample demonstrates how to implement an RPC-based service and expose it in the SOAP format and the "Plain Old XML" (POX) format using the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web Programming model.</span></span> <span data-ttu-id="b721b-104">Najdete v článku [základní služba HTTP](../../../../docs/framework/wcf/samples/basic-http-service.md) ukázku další podrobnosti o vazby HTTP pro službu.</span><span class="sxs-lookup"><span data-stu-id="b721b-104">See the [Basic HTTP Service](../../../../docs/framework/wcf/samples/basic-http-service.md) sample for more details about the HTTP binding for the service.</span></span> <span data-ttu-id="b721b-105">Tato ukázka se zaměřuje na podrobnosti, které se vztahují k vystavení stejnou službu prostřednictvím protokolu SOAP a HTTP pomocí různých vazeb.</span><span class="sxs-lookup"><span data-stu-id="b721b-105">This sample focuses on the details that pertain to exposing the same service over SOAP and HTTP using different bindings.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="b721b-106">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="b721b-106">Demonstrates</span></span>  
 <span data-ttu-id="b721b-107">Vystavení služby RPC prostřednictvím protokolu SOAP a HTTP pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b721b-107">Exposing an RPC service over SOAP and HTTP using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="b721b-108">Diskusní</span><span class="sxs-lookup"><span data-stu-id="b721b-108">Discussion</span></span>  
 <span data-ttu-id="b721b-109">Tato ukázka se skládá ze dvou komponent: projektu webové aplikace (služba), který obsahuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby a aplikace konzoly (klient), která volá operací služby pomocí vazby protokolu SOAP a HTTP.</span><span class="sxs-lookup"><span data-stu-id="b721b-109">This sample consists of two components: a Web Application project (Service) that contains a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service and a console application (Client) that invokes service operations using SOAP and HTTP bindings.</span></span>  
  
 <span data-ttu-id="b721b-110">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Služby zpřístupní 2 operations –`GetData` a `PutData` – které odezvu řetězec, který byl předán jako vstup.</span><span class="sxs-lookup"><span data-stu-id="b721b-110">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service exposes 2 operations –`GetData` and `PutData` – that echo the string that was passed as input.</span></span> <span data-ttu-id="b721b-111">Operace služby jsou opatřen poznámkou <xref:System.ServiceModel.Web.WebGetAttribute> a <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b721b-111">The service operations are annotated with <xref:System.ServiceModel.Web.WebGetAttribute> and <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span></span> <span data-ttu-id="b721b-112">Tyto atributy řídit projekce HTTP z těchto operací.</span><span class="sxs-lookup"><span data-stu-id="b721b-112">These attributes control the HTTP projection of these operations.</span></span> <span data-ttu-id="b721b-113">Kromě toho jsou opatřen poznámkou <xref:System.ServiceModel.OperationContractAttribute>, což umožňuje jejich mají být exponovány přes vazby protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="b721b-113">In addition, they are annotated with <xref:System.ServiceModel.OperationContractAttribute>, which enables them to be exposed over SOAP bindings.</span></span> <span data-ttu-id="b721b-114">Služby `PutData` metoda vrátí <xref:System.ServiceModel.Web.WebFaultException>, která se odešlou zpět přes protokol HTTP pomocí stavový kód HTTP a je odeslán zpět přes protokol SOAP jako chyba protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="b721b-114">The service’s `PutData` method throws a <xref:System.ServiceModel.Web.WebFaultException>, which gets sent back over HTTP using the HTTP status code and gets sent back over SOAP as a SOAP fault.</span></span>  
  
 <span data-ttu-id="b721b-115">Konfiguruje soubor Web.config [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby s 3 koncové body:</span><span class="sxs-lookup"><span data-stu-id="b721b-115">The Web.config file configures the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service with 3 endpoints:</span></span>  
  
-   <span data-ttu-id="b721b-116">~/Service.svc/mex koncového bodu, který zveřejňuje metadata služby pro přístup založený na protokolu SOAP klienty.</span><span class="sxs-lookup"><span data-stu-id="b721b-116">The ~/service.svc/mex endpoint that exposes the service metadata for access by SOAP-based clients.</span></span>  
  
-   <span data-ttu-id="b721b-117">~/Service.svc/http koncového bodu, který umožňuje klientům přístup ke službě pomocí vazby HTTP.</span><span class="sxs-lookup"><span data-stu-id="b721b-117">The ~/service.svc/http endpoint that enables clients to access the service using the HTTP binding.</span></span>  
  
-   <span data-ttu-id="b721b-118">~/Service.svc/soap koncového bodu, který umožňuje klientům přístup ke službě pomocí SOAP přes vazby HTTP.</span><span class="sxs-lookup"><span data-stu-id="b721b-118">The ~/service.svc/soap endpoint that allows the clients to access the service using the SOAP over HTTP binding.</span></span>  
  
 <span data-ttu-id="b721b-119">Koncový bod HTTP nastavena <`webHttp`> standardní koncový bod, který má `helpEnabled` nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="b721b-119">The HTTP endpoint is configured with a <`webHttp`> standard endpoint which has `helpEnabled` set to `true`.</span></span> <span data-ttu-id="b721b-120">V důsledku toho služba zpřístupní stránku XHTML na základě nápovědy na ~/service.svc/http/help používaných klienty založené na protokolu HTTP k přístupu ke službě.</span><span class="sxs-lookup"><span data-stu-id="b721b-120">As a result, the service exposes an XHTML based help page at ~/service.svc/http/help that HTTP-based clients can use to access the service.</span></span>  
  
 <span data-ttu-id="b721b-121">Projektu klienta ukazuje přístupu ke službě pomocí serveru proxy protokolu SOAP (vygenerované pomocí **přidat odkaz na službu**) a přístup pomocí služby <xref:System.Net.WebClient>.</span><span class="sxs-lookup"><span data-stu-id="b721b-121">The client project demonstrates accessing the service using a SOAP proxy (generated through **Add Service Reference**) and accessing the service using <xref:System.Net.WebClient>.</span></span>  
  
 <span data-ttu-id="b721b-122">Ukázka se skládá z hostované webové služby a aplikace konzoly.</span><span class="sxs-lookup"><span data-stu-id="b721b-122">The sample consists of a Web-hosted service and a console application.</span></span> <span data-ttu-id="b721b-123">Konzolové aplikace běží, klient odešle žádosti o službu a zapisuje příslušné informace z odpovědi do okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="b721b-123">As the console application runs, the client makes requests to the service and writes the pertinent information from the responses to the console window.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="b721b-124">Chcete-li spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="b721b-124">To run the sample</span></span>  
  
1.  <span data-ttu-id="b721b-125">Otevřete řešení pro protokolu SOAP a ukázkové koncových bodů protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="b721b-125">Open the solution for the SOAP and HTTP Endpoints Sample.</span></span>  
  
2.  <span data-ttu-id="b721b-126">Stisknutím kombinace kláves CTRL + SHIFT + B řešení sestavíte.</span><span class="sxs-lookup"><span data-stu-id="b721b-126">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="b721b-127">Pokud již není otevřený, stiskněte CTRL + W, S otevřete **Průzkumníku řešení** okno.</span><span class="sxs-lookup"><span data-stu-id="b721b-127">If it is not already open, press CTRL+W, S to open the **Solution Explorer** window.</span></span>  
  
4.  <span data-ttu-id="b721b-128">Z **Průzkumníku řešení** okno, klikněte pravým tlačítkem myši **služby** projektu a umístěte kurzor myši **ladění** možnost místní nabídky tak, aby **spustit nový Instance** Kontextová nabídka se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="b721b-128">From the **Solution Explorer** window, right-click the **Service** project and place the cursor over the **Debug** context menu option so that the **Start New Instance** context menu appears.</span></span> <span data-ttu-id="b721b-129">Klikněte na tlačítko **spustit novou instanci**.</span><span class="sxs-lookup"><span data-stu-id="b721b-129">Click **Start New Instance**.</span></span> <span data-ttu-id="b721b-130">Spustí vývojový server ASP.NET, který hostuje službu.</span><span class="sxs-lookup"><span data-stu-id="b721b-130">This launches the ASP.NET development server, which hosts the service.</span></span>  
  
5.  <span data-ttu-id="b721b-131">Z okna Průzkumníku řešení klikněte pravým tlačítkem na projekt klienta a umístěte kurzor přes **ladění** možnost místní nabídky, aby **spustit novou instanci** Kontextová nabídka se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="b721b-131">From the Solution Explorer windows, right-click the Client project and place the cursor over the **Debug** context menu option so that the **Start New Instance** context menu appears.</span></span> <span data-ttu-id="b721b-132">Klikněte na tlačítko **spustit novou instanci**.</span><span class="sxs-lookup"><span data-stu-id="b721b-132">Click **Start New Instance**.</span></span>  
  
6.  <span data-ttu-id="b721b-133">V okně konzoly klienta se zobrazí a poskytuje identifikátor URI spuštěné služby a identifikátor URI HTML stránka pro spuštěnou službu nápovědy.</span><span class="sxs-lookup"><span data-stu-id="b721b-133">The client console window appears and provides the URI of the running service and the URI of the HTML help page for the running service.</span></span> <span data-ttu-id="b721b-134">V libovolném bodě v čase můžete zobrazit na stránce nápovědy HTML zadáním identifikátor URI stránky nápovědy v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="b721b-134">At any point in time you can view the HTML help page by typing the URI of the help page in a browser.</span></span>  
  
7.  <span data-ttu-id="b721b-135">Ukázka běží, zapíše klienta stavu aktuální aktivity.</span><span class="sxs-lookup"><span data-stu-id="b721b-135">As the sample runs, the client writes the status of the current activity.</span></span>  
  
8.  <span data-ttu-id="b721b-136">Stisknutím libovolné klávesy ukončit klientská aplikace konzoly.</span><span class="sxs-lookup"><span data-stu-id="b721b-136">Press any key to terminate the client console application.</span></span>  
  
9. <span data-ttu-id="b721b-137">Stisknutím klávesy SHIFT + F5 ukončete ladění služby.</span><span class="sxs-lookup"><span data-stu-id="b721b-137">Press SHIFT+F5 to stop debugging the service.</span></span>  
  
10. <span data-ttu-id="b721b-138">V oznamovací oblasti systému Windows klikněte pravým tlačítkem na ikonu ASP.NET development server a vyberte **Zastavit** v místní nabídce.</span><span class="sxs-lookup"><span data-stu-id="b721b-138">In the Windows Notification Area, right-click the ASP.NET development server icon and select **Stop** from the context menu.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b721b-139">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="b721b-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b721b-140">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="b721b-140">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b721b-141">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="b721b-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b721b-142">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="b721b-142">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\SoapAndHttpEndpoints`
