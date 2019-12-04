---
title: Ukázka integrace názvového prostoru SystemWebRouting
ms.date: 03/30/2017
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
ms.openlocfilehash: 8be76fa97752680700f1c0eb56c1803fc69155d6
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716628"
---
# <a name="systemwebrouting-integration-sample"></a><span data-ttu-id="890e5-102">Ukázka integrace názvového prostoru SystemWebRouting</span><span class="sxs-lookup"><span data-stu-id="890e5-102">SystemWebRouting Integration Sample</span></span>
<span data-ttu-id="890e5-103">Tato ukázka demonstruje integraci vrstvy hostování se třídami v oboru názvů <xref:System.Web.Routing>.</span><span class="sxs-lookup"><span data-stu-id="890e5-103">This sample demonstrates the hosting layer’s integration with the classes in the <xref:System.Web.Routing> namespace.</span></span> <span data-ttu-id="890e5-104">Třídy v oboru názvů <xref:System.Web.Routing> umožňují aplikaci používat adresy URL, které přímo neodpovídají fyzickému prostředku.</span><span class="sxs-lookup"><span data-stu-id="890e5-104">The classes in the <xref:System.Web.Routing> namespace allow an application to use URLs that do not directly correspond to a physical resource.</span></span> <span data-ttu-id="890e5-105">Použití webového směrování umožňuje vývojářům vytvářet virtuální adresy pro protokol HTTP, které jsou pak namapovány zpět na skutečné služby WCF.</span><span class="sxs-lookup"><span data-stu-id="890e5-105">Using Web routing allows the developer to create virtual addresses for HTTP that are then mapped back to actual WCF services.</span></span> <span data-ttu-id="890e5-106">To je užitečné v případě, že je nutné hostovat služby WCF, aniž by vyžadovaly fyzický soubor nebo prostředek, nebo pokud jsou k dispozici služby s adresami URL, které neobsahují soubory, jako je například. html nebo. aspx.</span><span class="sxs-lookup"><span data-stu-id="890e5-106">This is useful when a WCF service must be hosted without requiring a physical file or resource, or when services must be accessed with URLs that do not contain files such as .html or .aspx.</span></span> <span data-ttu-id="890e5-107">Tato ukázka předvádí, jak použít třídu <xref:System.Web.Routing.RouteTable> k vytvoření virtuálních identifikátorů URI, které jsou mapovány na spuštěné služby definované v souboru Global. asax.</span><span class="sxs-lookup"><span data-stu-id="890e5-107">This sample demonstrates how to utilize the <xref:System.Web.Routing.RouteTable> class to create virtual URIs that map to running services defined in global.asax.</span></span> 

> [!NOTE]
> <span data-ttu-id="890e5-108">Třídy v oboru názvů <xref:System.Web.Routing> fungují pouze pro služby hostované prostřednictvím protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="890e5-108">The classes in the <xref:System.Web.Routing> namespace only work for services hosted over HTTP.</span></span>  
  
<span data-ttu-id="890e5-109">V tomto příkladu se používá WCF k vytvoření dvou kanálů RSS: `movies` informační kanál a `channels`ový kanál.</span><span class="sxs-lookup"><span data-stu-id="890e5-109">This example uses WCF to create two RSS feeds: a `movies` feed and a `channels` feed.</span></span> <span data-ttu-id="890e5-110">Adresy URL pro aktivaci služeb neobsahují rozšíření a jsou registrovány v metodě `Application_Start` `Global` třídy odvozené od třídy <xref:System.Web.HttpApplication>.</span><span class="sxs-lookup"><span data-stu-id="890e5-110">The URLs to activate the services do not contain an extension and are registered in the `Application_Start` method of the `Global` class derived from the <xref:System.Web.HttpApplication> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="890e5-111">Tato ukázka funguje jenom v Internetová informační služba (IIS) 7,0 a novějším, protože služba IIS 6,0 používá jinou metodu pro podporu adres URL bez přípony.</span><span class="sxs-lookup"><span data-stu-id="890e5-111">This sample only works in Internet Information Services (IIS) 7.0 and later, as IIS 6.0 uses a different method for supporting extension-less URLs.</span></span>  

#### <a name="to-download-this-sample"></a><span data-ttu-id="890e5-112">Stažení této ukázky</span><span class="sxs-lookup"><span data-stu-id="890e5-112">To download this sample</span></span>
  
<span data-ttu-id="890e5-113">Tato ukázka již může být v počítači nainstalována.</span><span class="sxs-lookup"><span data-stu-id="890e5-113">This sample may already be installed on your computer.</span></span> <span data-ttu-id="890e5-114">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="890e5-114">Check for the following (default) directory before continuing.</span></span>  
   
`<InstallDrive>:\WF_WCF_Samples`  
   
 <span data-ttu-id="890e5-115">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="890e5-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="890e5-116">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="890e5-116">This sample is located in the following directory.</span></span>  
   
`<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="890e5-117">Použití této ukázky</span><span class="sxs-lookup"><span data-stu-id="890e5-117">To use this sample</span></span>  
  
1. <span data-ttu-id="890e5-118">Pomocí sady Visual Studio otevřete soubor WebRoutingIntegration. sln.</span><span class="sxs-lookup"><span data-stu-id="890e5-118">Using Visual Studio, open the WebRoutingIntegration.sln file.</span></span>  
  
2. <span data-ttu-id="890e5-119">Chcete-li spustit řešení a spustit webový vývojový server, stiskněte klávesu F5.</span><span class="sxs-lookup"><span data-stu-id="890e5-119">To run the solution and start the Web development server, press F5.</span></span>  
  
     <span data-ttu-id="890e5-120">Zobrazí se výpis adresáře pro ukázku.</span><span class="sxs-lookup"><span data-stu-id="890e5-120">A directory listing for the sample appears.</span></span> <span data-ttu-id="890e5-121">Všimněte si, že neexistují žádné soubory s příponou souboru. svc.</span><span class="sxs-lookup"><span data-stu-id="890e5-121">Note that there are no files with an .svc file extension.</span></span>  
  
3. <span data-ttu-id="890e5-122">Do adresního řádku přidejte `movies` k adrese URL, aby četl `http://localhost:[port]/movies` a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="890e5-122">In the address bar, add `movies` to the URL, so that it reads `http://localhost:[port]/movies` and press ENTER.</span></span>  
  
     <span data-ttu-id="890e5-123">Informační kanál filmy se zobrazí v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="890e5-123">The movies feed appears in the browser.</span></span>  
  
4. <span data-ttu-id="890e5-124">Do adresního řádku přidejte `channels` k adrese URL, která je čtena `http://localhost:[port]/channels` a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="890e5-124">In the address bar, add `channels` to the URL, so that is reads `http://localhost:[port]/channels` and press ENTER.</span></span>  
  
     <span data-ttu-id="890e5-125">Informační kanál kanály se zobrazí v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="890e5-125">The channels feed appears in the browser.</span></span>  
  
5. <span data-ttu-id="890e5-126">Stisknutím kombinace kláves ALT + F4 zavřete webový prohlížeč.</span><span class="sxs-lookup"><span data-stu-id="890e5-126">Close the Web browser, by pressing ALT+F4.</span></span>  
  
     <span data-ttu-id="890e5-127">Pokud se vývojový server neukončil, klikněte pravým tlačítkem myši na ikonu oznamovací oblasti a vyberte **zastavit**.</span><span class="sxs-lookup"><span data-stu-id="890e5-127">If the development server has not exited, right-click the notification area icon and select **Stop**.</span></span>  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a><span data-ttu-id="890e5-128">Použití této ukázky při hostování ve službě IIS</span><span class="sxs-lookup"><span data-stu-id="890e5-128">To use this sample when hosted in IIS</span></span>  
  
1. <span data-ttu-id="890e5-129">Pomocí sady Visual Studio otevřete soubor WebRoutingIntegration. sln.</span><span class="sxs-lookup"><span data-stu-id="890e5-129">Using Visual Studio, open the WebRoutingIntegration.sln file.</span></span>  
  
2. <span data-ttu-id="890e5-130">Sestavte projekt stisknutím kombinace kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="890e5-130">Build the project, by pressing CTRL+SHIFT+B.</span></span>  
  
3. <span data-ttu-id="890e5-131">Vytvoření webové aplikace ve Správci služby Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="890e5-131">Create a Web application in Internet Information Services (IIS) Manager.</span></span>  
  
    1. <span data-ttu-id="890e5-132">Ve Správci služby IIS klikněte pravým tlačítkem na **výchozí web** a vyberte **Přidat aplikaci**.</span><span class="sxs-lookup"><span data-stu-id="890e5-132">In IIS Manager, right click the **Default Web Site** and select **Add an Application**.</span></span>  
  
    2. <span data-ttu-id="890e5-133">Jako **alias**zadejte `WebRoutingIntegration`.</span><span class="sxs-lookup"><span data-stu-id="890e5-133">For the **alias**, type in `WebRoutingIntegration`.</span></span>  
  
    3. <span data-ttu-id="890e5-134">Pro **fyzickou cestu**vyberte složku služby v rámci projektu.</span><span class="sxs-lookup"><span data-stu-id="890e5-134">For the **Physical Path**, select the Service folder inside the project.</span></span>  
  
    4. <span data-ttu-id="890e5-135">Stiskněte **OK**.</span><span class="sxs-lookup"><span data-stu-id="890e5-135">Press **OK**.</span></span>  
  
4. <span data-ttu-id="890e5-136">Spusťte aplikaci kliknutím pravým tlačítkem myši na webovou aplikaci a výběrem **možnosti spravovat aplikaci** a následným kliknutím na tlačítko **Procházet**.</span><span class="sxs-lookup"><span data-stu-id="890e5-136">Start the application, by right-clicking the Web application and selecting **Manage Application** and then **Browse**.</span></span>  
  
5. <span data-ttu-id="890e5-137">Do adresního řádku přidejte `movies` k adrese URL, která je čtena `http://localhost:[port]/movies` a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="890e5-137">In the address bar, add `movies` to the URL, so that is reads `http://localhost:[port]/movies` and press ENTER.</span></span>  
  
     <span data-ttu-id="890e5-138">Informační kanál filmy se zobrazí v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="890e5-138">The movies feed appears in the browser.</span></span>  
  
6. <span data-ttu-id="890e5-139">Do adresního řádku přidejte `channels` k adrese URL, která je čtena `http://localhost:[port]/channels` a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="890e5-139">In the address bar, add `channels` to the URL, so that is reads `http://localhost:[port]/channels` and press ENTER.</span></span>  
  
     <span data-ttu-id="890e5-140">Informační kanál kanály se zobrazí v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="890e5-140">The channels feed appears in the browser.</span></span>  
  
7. <span data-ttu-id="890e5-141">Stisknutím kombinace kláves ALT + F4 zavřete webový prohlížeč.</span><span class="sxs-lookup"><span data-stu-id="890e5-141">Close the Web browser, by pressing ALT+F4.</span></span>  
  
 <span data-ttu-id="890e5-142">Tato ukázka předvádí, že hostující vrstva je schopna sestavovat s třídami v oboru názvů <xref:System.Web.Routing> pro směrování žádostí o služby hostované přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="890e5-142">This sample demonstrates that the hosting layer is capable of composing with the classes in the <xref:System.Web.Routing> namespace for routing the requests of services hosted over HTTP.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="890e5-143">Pokud je nastavená na verzi 2, musíte aktualizovat výchozí verzi fondu aplikací na .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="890e5-143">You must update the default application pool version to .NET Framework 4 if it’s set to version 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="890e5-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="890e5-144">See also</span></span>

- [<span data-ttu-id="890e5-145">Hostování technologie AppFabric a ukázky trvalosti</span><span class="sxs-lookup"><span data-stu-id="890e5-145">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
