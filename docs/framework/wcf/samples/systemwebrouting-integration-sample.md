---
title: "Ukázka integrace názvového prostoru SystemWebRouting"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1718ea9c6ea1e029b66955e88fd54e20db1a3527
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="systemwebrouting-integration-sample"></a><span data-ttu-id="962b7-102">Ukázka integrace názvového prostoru SystemWebRouting</span><span class="sxs-lookup"><span data-stu-id="962b7-102">SystemWebRouting Integration Sample</span></span>
<span data-ttu-id="962b7-103">Tento příklad znázorňuje hostování vrstvě integrace s třídy v <xref:System.Web.Routing> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="962b7-103">This sample demonstrates the hosting layer’s integration with the classes in the <xref:System.Web.Routing> namespace.</span></span> <span data-ttu-id="962b7-104">Třídy v <xref:System.Web.Routing> obor názvů povolit aplikaci použití adres URL, které neodpovídají přímo na fyzický prostředek.</span><span class="sxs-lookup"><span data-stu-id="962b7-104">The classes in the <xref:System.Web.Routing> namespace allow an application to use URLs that do not directly correspond to a physical resource.</span></span> <span data-ttu-id="962b7-105">Použití směrování webové umožňuje vývojáři k vytvoření virtuální adresy pro protokol HTTP, která jsou pak mapována na skutečné [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby.</span><span class="sxs-lookup"><span data-stu-id="962b7-105">Using Web routing allows the developer to create virtual addresses for HTTP that are then mapped back to actual [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services.</span></span> <span data-ttu-id="962b7-106">To je užitečné, když musí být hostované služby WCF, bez nutnosti fyzického souboru či prostředku nebo když služby je nutné přistupovat pomocí adresy URL, které neobsahují soubory, jako je například HTML nebo .aspx.</span><span class="sxs-lookup"><span data-stu-id="962b7-106">This is useful when a WCF service must be hosted without requiring a physical file or resource, or when services must be accessed with URLs that do not contain files such as .html or .aspx.</span></span> <span data-ttu-id="962b7-107">Tento příklad ukazuje, jak využívat <xref:System.Web.Routing.RouteTable> třídy za účelem vytvoření virtuální identifikátory URI, které jsou namapovány na spuštění služby definované v souboru global.asax.</span><span class="sxs-lookup"><span data-stu-id="962b7-107">This sample demonstrates how to utilize the <xref:System.Web.Routing.RouteTable> class to create virtual URIs that map to running services defined in global.asax.</span></span> <span data-ttu-id="962b7-108">V tomto příkladu jsou dva informačních kanálů RSS vytvořený WCF: `movies` kanálu a `channels` informačního kanálu.</span><span class="sxs-lookup"><span data-stu-id="962b7-108">For this example, there are two RSS feeds created using WCF: a `movies` feed and a `channels` feed.</span></span> <span data-ttu-id="962b7-109">Adresy URL k aktivaci služby neobsahují rozšíření a jsou zaregistrovány v `Application_Start` metodu `Global` třída odvozená z <xref:System.Web.HttpApplication.Application_Start> třídy.</span><span class="sxs-lookup"><span data-stu-id="962b7-109">The URLs to activate the services do not contain an extension and are registered in the `Application_Start` method of the `Global` class derived from the <xref:System.Web.HttpApplication.Application_Start> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="962b7-110">Třídy v <xref:System.Web.Routing> obor názvů fungovat pouze pro služby hostované přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="962b7-110">The classes in the <xref:System.Web.Routing> namespace only work for services hosted over HTTP.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="962b7-111">Tato ukázka funguje pouze [!INCLUDE[iisver](../../../../includes/iisver-md.md)], jako [!INCLUDE[iis60](../../../../includes/iis60-md.md)] používá jinou metodu pro podporu adresy URL bez přípony.</span><span class="sxs-lookup"><span data-stu-id="962b7-111">This sample only works in [!INCLUDE[iisver](../../../../includes/iisver-md.md)], as [!INCLUDE[iis60](../../../../includes/iis60-md.md)] uses a different method for supporting extension-less URLs.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="962b7-112">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="962b7-112">The samples may already be installed on your computer.</span></span> <span data-ttu-id="962b7-113">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="962b7-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="962b7-114">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="962b7-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="962b7-115">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="962b7-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="962b7-116">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="962b7-116">To use this sample</span></span>  
  
1.  <span data-ttu-id="962b7-117">Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete soubor WebRoutingIntegration.sln.</span><span class="sxs-lookup"><span data-stu-id="962b7-117">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the WebRoutingIntegration.sln file.</span></span>  
  
2.  <span data-ttu-id="962b7-118">Pokud chcete spustit řešení a spustí webový server vývoj, stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="962b7-118">To run the solution and start the Web development server, press F5.</span></span>  
  
     <span data-ttu-id="962b7-119">Zobrazí se pro vzorovou výpis adresáře.</span><span class="sxs-lookup"><span data-stu-id="962b7-119">A directory listing for the sample appears.</span></span> <span data-ttu-id="962b7-120">Všimněte si, že neexistují žádné soubory s příponou souboru .svc.</span><span class="sxs-lookup"><span data-stu-id="962b7-120">Note that there are no files with an .svc file extension.</span></span>  
  
3.  <span data-ttu-id="962b7-121">Na panelu Adresa přidat `movies` na adresu URL, takže se čtení http://localhost: [port] / filmy a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="962b7-121">In the address bar, add `movies` to the URL, so that is reads http://localhost:[port]/movies and press ENTER.</span></span>  
  
     <span data-ttu-id="962b7-122">Informační kanál filmy se zobrazí v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="962b7-122">The movies feed appears in the browser.</span></span>  
  
4.  <span data-ttu-id="962b7-123">Na panelu Adresa přidat `channels` na adresu URL, takže se čtení http://localhost: [port] / kanálů a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="962b7-123">In the address bar, add `channels` to the URL, so that is reads http://localhost:[port]/channels and press ENTER.</span></span>  
  
     <span data-ttu-id="962b7-124">Informační kanál kanály se zobrazí v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="962b7-124">The channels feed appears in the browser.</span></span>  
  
5.  <span data-ttu-id="962b7-125">Zavřete webový prohlížeč, stisknutím klávesy ALT + F4.</span><span class="sxs-lookup"><span data-stu-id="962b7-125">Close the Web browser, by pressing ALT+F4.</span></span>  
  
     <span data-ttu-id="962b7-126">Pokud není ukončený vývojový server, klikněte pravým tlačítkem myši na ikonu v oznamovací oblasti a vyberte **Zastavit**.</span><span class="sxs-lookup"><span data-stu-id="962b7-126">If the development server has not exited, right-click the notification area icon and select **Stop**.</span></span>  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a><span data-ttu-id="962b7-127">Při použití tohoto příkladu při hostovaný ve službě IIS</span><span class="sxs-lookup"><span data-stu-id="962b7-127">To use this sample when hosted in IIS</span></span>  
  
1.  <span data-ttu-id="962b7-128">Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete soubor WebRoutingIntegration.sln.</span><span class="sxs-lookup"><span data-stu-id="962b7-128">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the WebRoutingIntegration.sln file.</span></span>  
  
2.  <span data-ttu-id="962b7-129">Sestavení projektu, stisknutím kombinace kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="962b7-129">Build the project, by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="962b7-130">Vytvoření webové aplikace ve Správci Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="962b7-130">Create a Web application in Internet Information Services (IIS) Manager.</span></span>  
  
    1.  <span data-ttu-id="962b7-131">Ve Správci služby IIS klikněte pravým tlačítkem **Default Web Site** a vyberte **přidat aplikaci**.</span><span class="sxs-lookup"><span data-stu-id="962b7-131">In IIS Manager, right click the **Default Web Site** and select **Add an Application**.</span></span>  
  
    2.  <span data-ttu-id="962b7-132">Pro **alias**, zadejte v `WebRoutingIntegration`.</span><span class="sxs-lookup"><span data-stu-id="962b7-132">For the **alias**, type in `WebRoutingIntegration`.</span></span>  
  
    3.  <span data-ttu-id="962b7-133">Pro **fyzická cesta**, vyberte složku služby v projektu.</span><span class="sxs-lookup"><span data-stu-id="962b7-133">For the **Physical Path**, select the Service folder inside the project.</span></span>  
  
    4.  <span data-ttu-id="962b7-134">Press **OK**.</span><span class="sxs-lookup"><span data-stu-id="962b7-134">Press **OK**.</span></span>  
  
4.  <span data-ttu-id="962b7-135">Spustit aplikaci, tak, že kliknete pravým tlačítkem na webové aplikace a výběr **spravovat aplikace** a potom **Procházet**.</span><span class="sxs-lookup"><span data-stu-id="962b7-135">Start the application, by right-clicking the Web application and selecting **Manage Application** and then **Browse**.</span></span>  
  
5.  <span data-ttu-id="962b7-136">Na panelu Adresa přidat `movies` na adresu URL, takže se čtení http://localhost: [port] / filmy a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="962b7-136">In the address bar, add `movies` to the URL, so that is reads http://localhost:[port]/movies and press ENTER.</span></span>  
  
     <span data-ttu-id="962b7-137">Informační kanál filmy se zobrazí v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="962b7-137">The movies feed appears in the browser.</span></span>  
  
6.  <span data-ttu-id="962b7-138">Na panelu Adresa přidat `channels` na adresu URL, takže se čtení http://localhost: [port] / kanálů a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="962b7-138">In the address bar, add `channels` to the URL, so that is reads http://localhost:[port]/channels and press ENTER.</span></span>  
  
     <span data-ttu-id="962b7-139">Informační kanál kanály se zobrazí v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="962b7-139">The channels feed appears in the browser.</span></span>  
  
7.  <span data-ttu-id="962b7-140">Zavřete webový prohlížeč, stisknutím klávesy ALT + F4.</span><span class="sxs-lookup"><span data-stu-id="962b7-140">Close the Web browser, by pressing ALT+F4.</span></span>  
  
 <span data-ttu-id="962b7-141">Tento příklad ukazuje, že hostování vrstva je schopný skládání s třídy v <xref:System.Web.Routing> obor názvů pro směrování požadavků služby hostované přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="962b7-141">This sample demonstrates that the hosting layer is capable of composing with the classes in the <xref:System.Web.Routing> namespace for routing the requests of services hosted over HTTP.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="962b7-142">Aktualizujte prosím výchozí verze fondu aplikací na [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] Pokud je nastaven na hodnotu verze 2.</span><span class="sxs-lookup"><span data-stu-id="962b7-142">Please update the default application pool version to [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] if it’s set to version 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="962b7-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="962b7-143">See Also</span></span>  
 [<span data-ttu-id="962b7-144">Ukázky trvalosti a hostování AppFabric</span><span class="sxs-lookup"><span data-stu-id="962b7-144">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
