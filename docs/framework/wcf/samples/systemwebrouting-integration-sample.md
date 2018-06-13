---
title: Ukázka integrace názvového prostoru SystemWebRouting
ms.date: 03/30/2017
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
ms.openlocfilehash: 52b908d354771cb2b351e339881647462340b716
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806523"
---
# <a name="systemwebrouting-integration-sample"></a><span data-ttu-id="4ba48-102">Ukázka integrace názvového prostoru SystemWebRouting</span><span class="sxs-lookup"><span data-stu-id="4ba48-102">SystemWebRouting Integration Sample</span></span>
<span data-ttu-id="4ba48-103">Tento příklad znázorňuje hostování vrstvě integrace s třídy v <xref:System.Web.Routing> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="4ba48-103">This sample demonstrates the hosting layer’s integration with the classes in the <xref:System.Web.Routing> namespace.</span></span> <span data-ttu-id="4ba48-104">Třídy v <xref:System.Web.Routing> obor názvů povolit aplikaci použití adres URL, které neodpovídají přímo na fyzický prostředek.</span><span class="sxs-lookup"><span data-stu-id="4ba48-104">The classes in the <xref:System.Web.Routing> namespace allow an application to use URLs that do not directly correspond to a physical resource.</span></span> <span data-ttu-id="4ba48-105">Použití směrování webové umožňuje vývojáři k vytvoření virtuální adresy pro protokol HTTP, která jsou pak mapována na skutečné služby WCF.</span><span class="sxs-lookup"><span data-stu-id="4ba48-105">Using Web routing allows the developer to create virtual addresses for HTTP that are then mapped back to actual WCF services.</span></span> <span data-ttu-id="4ba48-106">To je užitečné, když musí být hostované služby WCF, bez nutnosti fyzického souboru či prostředku nebo když služby je nutné přistupovat pomocí adresy URL, které neobsahují soubory, jako je například HTML nebo .aspx.</span><span class="sxs-lookup"><span data-stu-id="4ba48-106">This is useful when a WCF service must be hosted without requiring a physical file or resource, or when services must be accessed with URLs that do not contain files such as .html or .aspx.</span></span> <span data-ttu-id="4ba48-107">Tento příklad ukazuje, jak využívat <xref:System.Web.Routing.RouteTable> třídy za účelem vytvoření virtuální identifikátory URI, které jsou namapovány na spuštění služby definované v souboru global.asax.</span><span class="sxs-lookup"><span data-stu-id="4ba48-107">This sample demonstrates how to utilize the <xref:System.Web.Routing.RouteTable> class to create virtual URIs that map to running services defined in global.asax.</span></span> 

> [!NOTE]
>  <span data-ttu-id="4ba48-108">Třídy v <xref:System.Web.Routing> obor názvů fungovat pouze pro služby hostované přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="4ba48-108">The classes in the <xref:System.Web.Routing> namespace only work for services hosted over HTTP.</span></span>  
  
<span data-ttu-id="4ba48-109">Tento příklad používá k vytvoření dvou informačních kanálů RSS WCF: `movies` kanálu a `channels` informačního kanálu.</span><span class="sxs-lookup"><span data-stu-id="4ba48-109">This example uses WCF to create two RSS feeds: a `movies` feed and a `channels` feed.</span></span> <span data-ttu-id="4ba48-110">Adresy URL k aktivaci služby neobsahují rozšíření a jsou zaregistrovány v `Application_Start` metodu `Global` třída odvozená z <xref:System.Web.HttpApplication> třídy.</span><span class="sxs-lookup"><span data-stu-id="4ba48-110">The URLs to activate the services do not contain an extension and are registered in the `Application_Start` method of the `Global` class derived from the <xref:System.Web.HttpApplication> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4ba48-111">Tato ukázka funguje pouze v Internetové informační služby (IIS) 7.0 a novější, jako služby IIS 6.0 používá jinou metodu pro podporu adresy URL bez přípony.</span><span class="sxs-lookup"><span data-stu-id="4ba48-111">This sample only works in Internet Information Services (IIS) 7.0 and later, as IIS 6.0 uses a different method for supporting extension-less URLs.</span></span>  

#### <a name="to-download-this-sample"></a><span data-ttu-id="4ba48-112">Chcete-li stáhnout tuto ukázku</span><span class="sxs-lookup"><span data-stu-id="4ba48-112">To download this sample</span></span>
  
<span data-ttu-id="4ba48-113">Tato ukázka může již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="4ba48-113">This sample may already be installed on your computer.</span></span> <span data-ttu-id="4ba48-114">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="4ba48-114">Check for the following (default) directory before continuing.</span></span>  
   
`<InstallDrive>:\WF_WCF_Samples`  
   
 <span data-ttu-id="4ba48-115">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="4ba48-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4ba48-116">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="4ba48-116">This sample is located in the following directory.</span></span>  
   
`<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="4ba48-117">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="4ba48-117">To use this sample</span></span>  
  
1.  <span data-ttu-id="4ba48-118">Pomocí sady Visual Studio, otevřete soubor WebRoutingIntegration.sln.</span><span class="sxs-lookup"><span data-stu-id="4ba48-118">Using Visual Studio, open the WebRoutingIntegration.sln file.</span></span>  
  
2.  <span data-ttu-id="4ba48-119">Pokud chcete spustit řešení a spustí webový server vývoj, stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="4ba48-119">To run the solution and start the Web development server, press F5.</span></span>  
  
     <span data-ttu-id="4ba48-120">Zobrazí se pro vzorovou výpis adresáře.</span><span class="sxs-lookup"><span data-stu-id="4ba48-120">A directory listing for the sample appears.</span></span> <span data-ttu-id="4ba48-121">Všimněte si, že neexistují žádné soubory s příponou souboru .svc.</span><span class="sxs-lookup"><span data-stu-id="4ba48-121">Note that there are no files with an .svc file extension.</span></span>  
  
3.  <span data-ttu-id="4ba48-122">Na panelu Adresa přidat `movies` na adresu URL, takže to čte http://localhost:[port] / filmy a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="4ba48-122">In the address bar, add `movies` to the URL, so that it reads http://localhost:[port]/movies and press ENTER.</span></span>  
  
     <span data-ttu-id="4ba48-123">Informační kanál filmy se zobrazí v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="4ba48-123">The movies feed appears in the browser.</span></span>  
  
4.  <span data-ttu-id="4ba48-124">Na panelu Adresa přidat `channels` na adresu URL, takže se čtení http://localhost:[port] / kanálů a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="4ba48-124">In the address bar, add `channels` to the URL, so that is reads http://localhost:[port]/channels and press ENTER.</span></span>  
  
     <span data-ttu-id="4ba48-125">Informační kanál kanály se zobrazí v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="4ba48-125">The channels feed appears in the browser.</span></span>  
  
5.  <span data-ttu-id="4ba48-126">Zavřete webový prohlížeč, stisknutím klávesy ALT + F4.</span><span class="sxs-lookup"><span data-stu-id="4ba48-126">Close the Web browser, by pressing ALT+F4.</span></span>  
  
     <span data-ttu-id="4ba48-127">Pokud není ukončený vývojový server, klikněte pravým tlačítkem myši na ikonu v oznamovací oblasti a vyberte **Zastavit**.</span><span class="sxs-lookup"><span data-stu-id="4ba48-127">If the development server has not exited, right-click the notification area icon and select **Stop**.</span></span>  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a><span data-ttu-id="4ba48-128">Při použití tohoto příkladu při hostovaný ve službě IIS</span><span class="sxs-lookup"><span data-stu-id="4ba48-128">To use this sample when hosted in IIS</span></span>  
  
1.  <span data-ttu-id="4ba48-129">Pomocí sady Visual Studio, otevřete soubor WebRoutingIntegration.sln.</span><span class="sxs-lookup"><span data-stu-id="4ba48-129">Using Visual Studio, open the WebRoutingIntegration.sln file.</span></span>  
  
2.  <span data-ttu-id="4ba48-130">Sestavení projektu, stisknutím kombinace kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="4ba48-130">Build the project, by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="4ba48-131">Vytvoření webové aplikace ve Správci Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="4ba48-131">Create a Web application in Internet Information Services (IIS) Manager.</span></span>  
  
    1.  <span data-ttu-id="4ba48-132">Ve Správci služby IIS klikněte pravým tlačítkem **Default Web Site** a vyberte **přidat aplikaci**.</span><span class="sxs-lookup"><span data-stu-id="4ba48-132">In IIS Manager, right click the **Default Web Site** and select **Add an Application**.</span></span>  
  
    2.  <span data-ttu-id="4ba48-133">Pro **alias**, zadejte v `WebRoutingIntegration`.</span><span class="sxs-lookup"><span data-stu-id="4ba48-133">For the **alias**, type in `WebRoutingIntegration`.</span></span>  
  
    3.  <span data-ttu-id="4ba48-134">Pro **fyzická cesta**, vyberte složku služby v projektu.</span><span class="sxs-lookup"><span data-stu-id="4ba48-134">For the **Physical Path**, select the Service folder inside the project.</span></span>  
  
    4.  <span data-ttu-id="4ba48-135">Press **OK**.</span><span class="sxs-lookup"><span data-stu-id="4ba48-135">Press **OK**.</span></span>  
  
4.  <span data-ttu-id="4ba48-136">Spustit aplikaci, tak, že kliknete pravým tlačítkem na webové aplikace a výběr **spravovat aplikace** a potom **Procházet**.</span><span class="sxs-lookup"><span data-stu-id="4ba48-136">Start the application, by right-clicking the Web application and selecting **Manage Application** and then **Browse**.</span></span>  
  
5.  <span data-ttu-id="4ba48-137">Na panelu Adresa přidat `movies` na adresu URL, takže se čtení http://localhost:[port] / filmy a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="4ba48-137">In the address bar, add `movies` to the URL, so that is reads http://localhost:[port]/movies and press ENTER.</span></span>  
  
     <span data-ttu-id="4ba48-138">Informační kanál filmy se zobrazí v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="4ba48-138">The movies feed appears in the browser.</span></span>  
  
6.  <span data-ttu-id="4ba48-139">Na panelu Adresa přidat `channels` na adresu URL, takže se čtení http://localhost:[port] / kanálů a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="4ba48-139">In the address bar, add `channels` to the URL, so that is reads http://localhost:[port]/channels and press ENTER.</span></span>  
  
     <span data-ttu-id="4ba48-140">Informační kanál kanály se zobrazí v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="4ba48-140">The channels feed appears in the browser.</span></span>  
  
7.  <span data-ttu-id="4ba48-141">Zavřete webový prohlížeč, stisknutím klávesy ALT + F4.</span><span class="sxs-lookup"><span data-stu-id="4ba48-141">Close the Web browser, by pressing ALT+F4.</span></span>  
  
 <span data-ttu-id="4ba48-142">Tento příklad ukazuje, že hostování vrstva je schopný skládání s třídy v <xref:System.Web.Routing> obor názvů pro směrování požadavků služby hostované přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="4ba48-142">This sample demonstrates that the hosting layer is capable of composing with the classes in the <xref:System.Web.Routing> namespace for routing the requests of services hosted over HTTP.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4ba48-143">Je nutné aktualizovat výchozí verze fondu aplikací na [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] Pokud je nastaven na hodnotu verze 2.</span><span class="sxs-lookup"><span data-stu-id="4ba48-143">You must update the default application pool version to [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] if it’s set to version 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ba48-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="4ba48-144">See Also</span></span>  
 [<span data-ttu-id="4ba48-145">Ukázky trvalosti a hostování AppFabric</span><span class="sxs-lookup"><span data-stu-id="4ba48-145">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
