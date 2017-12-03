---
title: "Integrace mezipaměti ASP.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f581923a-8a72-42fc-bd6a-46de2aaeecc1
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 23cdd79d72f7cb40758fafb63ee4d0f725cbfc1c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="aspnet-caching-integration"></a><span data-ttu-id="f03f5-102">Integrace mezipaměti ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f03f5-102">ASP.NET Caching Integration</span></span>
<span data-ttu-id="f03f5-103">Tento příklad ukazuje, jak využívat výstupní mezipaměti technologie ASP.NET pomocí programovacího modelu WCF WEB HTTP.</span><span class="sxs-lookup"><span data-stu-id="f03f5-103">This sample demonstrates how to utilize the ASP.NET output cache with the WCF WEB HTTP programming model.</span></span> <span data-ttu-id="f03f5-104">Najdete v tématu [základní služba prostředků](../../../../docs/framework/wcf/samples/basic-resource-service.md) ukázku vlastním hostováním verzi tento scénář, který popisuje implementace služby podrobněji.</span><span class="sxs-lookup"><span data-stu-id="f03f5-104">Please see the [Basic Resource Service](../../../../docs/framework/wcf/samples/basic-resource-service.md) sample for a self-hosted version of this scenario that discusses the service implementation in depth.</span></span> <span data-ttu-id="f03f5-105">Toto téma se zaměřuje na funkce integrace výstupní mezipaměti technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f03f5-105">This topic focuses on the ASP.NET output cache integration feature.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="f03f5-106">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="f03f5-106">Demonstrates</span></span>  
 <span data-ttu-id="f03f5-107">Integrace s ASP.NET výstupní mezipaměti</span><span class="sxs-lookup"><span data-stu-id="f03f5-107">Integration with the ASP.NET Output Cache</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f03f5-108">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="f03f5-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f03f5-109">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="f03f5-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f03f5-110">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="f03f5-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f03f5-111">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="f03f5-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetCachingIntegration`  
  
## <a name="discussion"></a><span data-ttu-id="f03f5-112">Diskusní</span><span class="sxs-lookup"><span data-stu-id="f03f5-112">Discussion</span></span>  
 <span data-ttu-id="f03f5-113">Ukázce se používá <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> využívat ASP.NET ukládání výstupu do mezipaměti s [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby.</span><span class="sxs-lookup"><span data-stu-id="f03f5-113">The sample uses the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> to utilize ASP.NET output caching with the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service.</span></span> <span data-ttu-id="f03f5-114"><xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> Se použije k operacím služby a poskytuje název profilu mezipaměti v konfiguračním souboru, která má být použita k odpovědím z danou operaci.</span><span class="sxs-lookup"><span data-stu-id="f03f5-114">The <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> is applied to service operations, and provides the name of a cache profile in a configuration file that should be applied to responses from the given operation.</span></span>  
  
 <span data-ttu-id="f03f5-115">V souboru Service.cs ukázkový projekt služby jak `GetCustomer` a `GetCustomers` operace jsou označené jako <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, který poskytuje název profilu mezipaměti "CacheFor60Seconds".</span><span class="sxs-lookup"><span data-stu-id="f03f5-115">In the Service.cs file of the sample Service project, both the `GetCustomer` and `GetCustomers` operations are marked with the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, which provides the cache profile name "CacheFor60Seconds".</span></span> <span data-ttu-id="f03f5-116">V souboru Web.config projektu služby, je profil mezipaměti "CacheFor60Seconds" uvedených v části <`caching`> elementu <`system.web`>.</span><span class="sxs-lookup"><span data-stu-id="f03f5-116">In the Web.config file of the Service project, the cache profile "CacheFor60Seconds" is provided under the <`caching`> element of <`system.web`>.</span></span> <span data-ttu-id="f03f5-117">Pro tento profil mezipaměti, hodnota `duration` atribut je "60", takže odpovědi související s tímto profilem se ukládat do mezipaměti ve výstupní mezipaměti technologie ASP.NET po dobu 60 sekund.</span><span class="sxs-lookup"><span data-stu-id="f03f5-117">For this cache profile, the value of the `duration` attribute is "60", so responses associated with this profile are cached in the ASP.NET output cache for 60 seconds.</span></span> <span data-ttu-id="f03f5-118">Navíc pro tento profil mezipaměti `varmByParam` je nastavena na hodnotu "format" Ano požadavky s různými hodnotami `format` dotaz parametr řetězce jejich odpovědi v mezipaměti samostatně.</span><span class="sxs-lookup"><span data-stu-id="f03f5-118">Also, for this cache profile, the `varmByParam` attribute is set to "format" so requests with different values for the `format` query string parameter have their responses cached separately.</span></span> <span data-ttu-id="f03f5-119">Nakonec mezipaměti profilu `varyByHeader` atribut je nastaven na "Přijmout", aby jejich odpovědi v mezipaměti samostatně požadavků s různé hodnoty hlavičky Accept.</span><span class="sxs-lookup"><span data-stu-id="f03f5-119">Lastly, the cache profile’s `varyByHeader` attribute is set to "Accept", so requests with different Accept header values have their responses cached separately.</span></span>  
  
 <span data-ttu-id="f03f5-120">Program.cs v projektu klienta ukazuje, jak mohou být klienta vytvořené pomocí <xref:System.Net.HttpWebRequest>.</span><span class="sxs-lookup"><span data-stu-id="f03f5-120">Program.cs in the Client project demonstrates how such a client can be authored using <xref:System.Net.HttpWebRequest>.</span></span> <span data-ttu-id="f03f5-121">Všimněte si, že se jedná pouze jeden způsob pro přístup ke službě WCF.</span><span class="sxs-lookup"><span data-stu-id="f03f5-121">Note that this is just one way to access a WCF service.</span></span> <span data-ttu-id="f03f5-122">Je také možné přístup ke službě pomocí jiné třídy rozhraní .NET Framework jako [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kanálu a <xref:System.Net.WebClient>.</span><span class="sxs-lookup"><span data-stu-id="f03f5-122">It is also possible to access the service using other .NET Framework classes like the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] channel factory and <xref:System.Net.WebClient>.</span></span> <span data-ttu-id="f03f5-123">Další ukázky v sadě SDK (například [základní služba HTTP](../../../../docs/framework/wcf/samples/basic-http-service.md) ukázka a [automatický výběr formátu](../../../../docs/framework/wcf/samples/automatic-format-selection.md) ukázkové) ukazují, jak používat tyto třídy ke komunikaci s [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby.</span><span class="sxs-lookup"><span data-stu-id="f03f5-123">Other samples in the SDK (such as the [Basic HTTP Service](../../../../docs/framework/wcf/samples/basic-http-service.md) sample and the [Automatic Format Selection](../../../../docs/framework/wcf/samples/automatic-format-selection.md) sample) illustrate how to use these classes to communicate with a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
## <a name="to-run-the-sample"></a><span data-ttu-id="f03f5-124">Chcete-li spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="f03f5-124">To run the sample</span></span>  
 <span data-ttu-id="f03f5-125">Ukázka se skládá ze tří projektů:</span><span class="sxs-lookup"><span data-stu-id="f03f5-125">The sample consists of three projects:</span></span>  
  
-   <span data-ttu-id="f03f5-126">**Služba**: projektu A webové aplikace, který zahrnuje služby WCF HTTP hostované v technologii ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f03f5-126">**Service**: A Web Application project that includes a WCF HTTP service hosted in ASP.NET.</span></span>  
  
-   <span data-ttu-id="f03f5-127">**Klient**: projekt konzolové aplikace, která provádí volání do služby.</span><span class="sxs-lookup"><span data-stu-id="f03f5-127">**Client**: A console application project that makes calls to the service.</span></span>  
  
-   <span data-ttu-id="f03f5-128">**Běžné**: sdílené knihovny, které obsahuje typ zákazníka používané klientem a službou.</span><span class="sxs-lookup"><span data-stu-id="f03f5-128">**Common**: A shared library that contains the Customer type used by the client and service.</span></span>  
  
 <span data-ttu-id="f03f5-129">Klienta konzolové aplikace běží, klient odešle žádosti o službu a zapisuje příslušné informace z odpovědi do okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="f03f5-129">As the Client console application runs, the client makes requests to the service and writes the pertinent information from the responses to the console window.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="f03f5-130">Chcete-li spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="f03f5-130">To run the sample</span></span>  
  
1.  <span data-ttu-id="f03f5-131">Otevřete řešení pro ukázku integrace ukládání do mezipaměti technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f03f5-131">Open the solution for the ASP.NET Caching Integration Sample.</span></span>  
  
2.  <span data-ttu-id="f03f5-132">Stisknutím kombinace kláves CTRL + SHIFT + B řešení sestavíte.</span><span class="sxs-lookup"><span data-stu-id="f03f5-132">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="f03f5-133">Pokud **Průzkumníku řešení** okno ještě není otevřené, stiskněte CTRL + W + S.</span><span class="sxs-lookup"><span data-stu-id="f03f5-133">If the **Solution Explorer** window is not already open, press CTRL+W+S.</span></span>  
  
4.  <span data-ttu-id="f03f5-134">Z **Průzkumníku řešení** okna, klikněte pravým tlačítkem **služby** projektu a vyberte **spustit novou instanci**.</span><span class="sxs-lookup"><span data-stu-id="f03f5-134">From the **Solution Explorer** window, right click the **Service** project and select **Start New Instance**.</span></span> <span data-ttu-id="f03f5-135">Spustí vývojový server ASP.NET, který hostuje službu.</span><span class="sxs-lookup"><span data-stu-id="f03f5-135">This launches the ASP.NET development server, which hosts the service.</span></span>  
  
5.  <span data-ttu-id="f03f5-136">Z **Průzkumníku řešení** okna, klikněte pravým tlačítkem **klienta** projektu a vyberte **spustit novou instanci**.</span><span class="sxs-lookup"><span data-stu-id="f03f5-136">From the **Solution Explorer** window, right click the **Client** project and select **Start New Instance**.</span></span>  
  
6.  <span data-ttu-id="f03f5-137">V okně konzoly klienta se zobrazí a poskytuje identifikátor URI spuštěné služby a identifikátor URI HTML stránka pro spuštěnou službu nápovědy.</span><span class="sxs-lookup"><span data-stu-id="f03f5-137">The client console window appears and provides the URI of the running service and the URI of the HTML help page for the running service.</span></span> <span data-ttu-id="f03f5-138">V libovolném bodě v čase můžete zobrazit na stránce nápovědy HTML zadáním identifikátor URI stránky nápovědy v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="f03f5-138">At any point in time you can view the HTML help page by typing the URI of the help page in a browser.</span></span>  
  
7.  <span data-ttu-id="f03f5-139">Ukázka běží, zapíše klienta stavu aktuální aktivity.</span><span class="sxs-lookup"><span data-stu-id="f03f5-139">As the sample runs, the client writes the status of the current activity.</span></span>  
  
8.  <span data-ttu-id="f03f5-140">Stisknutím libovolné klávesy ukončit klientská aplikace konzoly.</span><span class="sxs-lookup"><span data-stu-id="f03f5-140">Press any key to terminate the client console application.</span></span>  
  
9. <span data-ttu-id="f03f5-141">Stisknutím klávesy SHIFT + F5 ukončete ladění služby.</span><span class="sxs-lookup"><span data-stu-id="f03f5-141">Press SHIFT+F5 to stop debugging the service.</span></span>  
  
10. <span data-ttu-id="f03f5-142">V oznamovací oblasti systému Windows klikněte pravým tlačítkem na ikonu ASP.NET development server a vyberte **Zastavit**.</span><span class="sxs-lookup"><span data-stu-id="f03f5-142">In the Windows Notification Area, right click the ASP.NET development server icon and select **Stop**.</span></span>
