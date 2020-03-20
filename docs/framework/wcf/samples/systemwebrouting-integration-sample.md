---
title: Ukázka integrace názvového prostoru SystemWebRouting
ms.date: 03/30/2017
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
ms.openlocfilehash: 2f12d80085e3ac27dac8ce80b6bb09f69337bfd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143951"
---
# <a name="systemwebrouting-integration-sample"></a><span data-ttu-id="d1654-102">Ukázka integrace názvového prostoru SystemWebRouting</span><span class="sxs-lookup"><span data-stu-id="d1654-102">SystemWebRouting Integration Sample</span></span>
<span data-ttu-id="d1654-103">Tato ukázka ukazuje integraci hostitelské vrstvy s <xref:System.Web.Routing> třídami v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="d1654-103">This sample demonstrates the hosting layer’s integration with the classes in the <xref:System.Web.Routing> namespace.</span></span> <span data-ttu-id="d1654-104">Třídy v <xref:System.Web.Routing> oboru názvů umožňují aplikaci používat adresy URL, které přímo neodpovídají fyzickému prostředku.</span><span class="sxs-lookup"><span data-stu-id="d1654-104">The classes in the <xref:System.Web.Routing> namespace allow an application to use URLs that do not directly correspond to a physical resource.</span></span> <span data-ttu-id="d1654-105">Použití webového směrování umožňuje vývojáři vytvářet virtuální adresy pro protokol HTTP, které jsou pak mapovány zpět na skutečné služby WCF.</span><span class="sxs-lookup"><span data-stu-id="d1654-105">Using Web routing allows the developer to create virtual addresses for HTTP that are then mapped back to actual WCF services.</span></span> <span data-ttu-id="d1654-106">To je užitečné v případě, že služba WCF musí být hostována bez nutnosti fyzického souboru nebo prostředku, nebo pokud musí být ke službám přistupováno pomocí adres URL, které neobsahují soubory jako HTML nebo ASPX.</span><span class="sxs-lookup"><span data-stu-id="d1654-106">This is useful when a WCF service must be hosted without requiring a physical file or resource, or when services must be accessed with URLs that do not contain files such as .html or .aspx.</span></span> <span data-ttu-id="d1654-107">Tato ukázka ukazuje, <xref:System.Web.Routing.RouteTable> jak využít třídu k vytvoření virtuálních identifikátorů URI, které mapují na spuštěné služby definované v global.asax.</span><span class="sxs-lookup"><span data-stu-id="d1654-107">This sample demonstrates how to utilize the <xref:System.Web.Routing.RouteTable> class to create virtual URIs that map to running services defined in global.asax.</span></span>

> [!NOTE]
> <span data-ttu-id="d1654-108">Třídy v <xref:System.Web.Routing> oboru názvů fungují pouze pro služby hostované přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="d1654-108">The classes in the <xref:System.Web.Routing> namespace only work for services hosted over HTTP.</span></span>  
  
<span data-ttu-id="d1654-109">Tento příklad používá WCF k vytvoření dvou `movies` informačních `channels` kanálů RSS: informačního kanálu a informačního kanálu.</span><span class="sxs-lookup"><span data-stu-id="d1654-109">This example uses WCF to create two RSS feeds: a `movies` feed and a `channels` feed.</span></span> <span data-ttu-id="d1654-110">Adresy URL pro aktivaci služeb neobsahují rozšíření a `Application_Start` jsou registrovány v metodě `Global` třídy odvozené z <xref:System.Web.HttpApplication> třídy.</span><span class="sxs-lookup"><span data-stu-id="d1654-110">The URLs to activate the services do not contain an extension and are registered in the `Application_Start` method of the `Global` class derived from the <xref:System.Web.HttpApplication> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d1654-111">Tato ukázka funguje pouze v internetové informační službě (IIS) 7.0 a novějších, protože služba IIS 6.0 používá jinou metodu pro podporu adres URL bez rozšíření.</span><span class="sxs-lookup"><span data-stu-id="d1654-111">This sample only works in Internet Information Services (IIS) 7.0 and later, as IIS 6.0 uses a different method for supporting extension-less URLs.</span></span>  

#### <a name="to-download-this-sample"></a><span data-ttu-id="d1654-112">Chcete-li stáhnout tuto ukázku</span><span class="sxs-lookup"><span data-stu-id="d1654-112">To download this sample</span></span>
  
<span data-ttu-id="d1654-113">Tato ukázka je již pravděpodobně nainstalována v počítači.</span><span class="sxs-lookup"><span data-stu-id="d1654-113">This sample may already be installed on your computer.</span></span> <span data-ttu-id="d1654-114">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="d1654-114">Check for the following (default) directory before continuing.</span></span>  

`<InstallDrive>:\WF_WCF_Samples`  

 <span data-ttu-id="d1654-115">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="d1654-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d1654-116">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="d1654-116">This sample is located in the following directory.</span></span>  

`<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="d1654-117">Chcete-li použít tento vzorek</span><span class="sxs-lookup"><span data-stu-id="d1654-117">To use this sample</span></span>  
  
1. <span data-ttu-id="d1654-118">V sadě Visual Studio otevřete soubor WebRoutingIntegration.sln.</span><span class="sxs-lookup"><span data-stu-id="d1654-118">Using Visual Studio, open the WebRoutingIntegration.sln file.</span></span>  
  
2. <span data-ttu-id="d1654-119">Chcete-li spustit řešení a spustit web development server, stiskněte klávesu F5.</span><span class="sxs-lookup"><span data-stu-id="d1654-119">To run the solution and start the Web development server, press F5.</span></span>  
  
     <span data-ttu-id="d1654-120">Zobrazí se seznam adresářů pro ukázku.</span><span class="sxs-lookup"><span data-stu-id="d1654-120">A directory listing for the sample appears.</span></span> <span data-ttu-id="d1654-121">Všimněte si, že neexistují žádné soubory s příponou souboru SVC.</span><span class="sxs-lookup"><span data-stu-id="d1654-121">Note that there are no files with an .svc file extension.</span></span>  
  
3. <span data-ttu-id="d1654-122">V adresním řádku `movies` přidejte adresu URL, `http://localhost:[port]/movies` aby se přečetla, a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="d1654-122">In the address bar, add `movies` to the URL, so that it reads `http://localhost:[port]/movies` and press ENTER.</span></span>  
  
     <span data-ttu-id="d1654-123">V prohlížeči se zobrazí kanál o filmech.</span><span class="sxs-lookup"><span data-stu-id="d1654-123">The movies feed appears in the browser.</span></span>  
  
4. <span data-ttu-id="d1654-124">V adresním řádku `channels` přidejte do adresy `http://localhost:[port]/channels` URL, aby se přečetla, a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="d1654-124">In the address bar, add `channels` to the URL, so that is reads `http://localhost:[port]/channels` and press ENTER.</span></span>  
  
     <span data-ttu-id="d1654-125">Kanál kanálů se zobrazí v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="d1654-125">The channels feed appears in the browser.</span></span>  
  
5. <span data-ttu-id="d1654-126">Zavřete webový prohlížeč stisknutím kláves ALT+F4.</span><span class="sxs-lookup"><span data-stu-id="d1654-126">Close the Web browser, by pressing ALT+F4.</span></span>  
  
     <span data-ttu-id="d1654-127">Pokud se vývojový server neukončoval, klepněte pravým tlačítkem myši na ikonu oznamovací oblasti a vyberte příkaz **Zastavit**.</span><span class="sxs-lookup"><span data-stu-id="d1654-127">If the development server has not exited, right-click the notification area icon and select **Stop**.</span></span>  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a><span data-ttu-id="d1654-128">Použití této ukázky při hostování ve správě ve správě iis</span><span class="sxs-lookup"><span data-stu-id="d1654-128">To use this sample when hosted in IIS</span></span>  
  
1. <span data-ttu-id="d1654-129">V sadě Visual Studio otevřete soubor WebRoutingIntegration.sln.</span><span class="sxs-lookup"><span data-stu-id="d1654-129">Using Visual Studio, open the WebRoutingIntegration.sln file.</span></span>  
  
2. <span data-ttu-id="d1654-130">Sestavte projekt stisknutím kombinace kláves CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="d1654-130">Build the project, by pressing CTRL+SHIFT+B.</span></span>  
  
3. <span data-ttu-id="d1654-131">Vytvořte webovou aplikaci ve Správci Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="d1654-131">Create a Web application in Internet Information Services (IIS) Manager.</span></span>  
  
    1. <span data-ttu-id="d1654-132">Ve Správci služby IIS klepněte pravým tlačítkem myši na **výchozí web** a vyberte příkaz **Přidat aplikaci**.</span><span class="sxs-lookup"><span data-stu-id="d1654-132">In IIS Manager, right click the **Default Web Site** and select **Add an Application**.</span></span>  
  
    2. <span data-ttu-id="d1654-133">Do **aliasu**zadejte . `WebRoutingIntegration`</span><span class="sxs-lookup"><span data-stu-id="d1654-133">For the **alias**, type in `WebRoutingIntegration`.</span></span>  
  
    3. <span data-ttu-id="d1654-134">Pro **fyzickou cestu**vyberte složku Service uvnitř projektu.</span><span class="sxs-lookup"><span data-stu-id="d1654-134">For the **Physical Path**, select the Service folder inside the project.</span></span>  
  
    4. <span data-ttu-id="d1654-135">Stiskněte **OK**.</span><span class="sxs-lookup"><span data-stu-id="d1654-135">Press **OK**.</span></span>  
  
4. <span data-ttu-id="d1654-136">Spusťte aplikaci tak, že klepnete pravým tlačítkem myši na webovou aplikaci a vyberete **možnost Spravovat aplikaci** a potom **procházet**.</span><span class="sxs-lookup"><span data-stu-id="d1654-136">Start the application, by right-clicking the Web application and selecting **Manage Application** and then **Browse**.</span></span>  
  
5. <span data-ttu-id="d1654-137">V adresním řádku `movies` přidejte do adresy `http://localhost:[port]/movies` URL, aby se přečetla, a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="d1654-137">In the address bar, add `movies` to the URL, so that is reads `http://localhost:[port]/movies` and press ENTER.</span></span>  
  
     <span data-ttu-id="d1654-138">V prohlížeči se zobrazí kanál o filmech.</span><span class="sxs-lookup"><span data-stu-id="d1654-138">The movies feed appears in the browser.</span></span>  
  
6. <span data-ttu-id="d1654-139">V adresním řádku `channels` přidejte do adresy `http://localhost:[port]/channels` URL, aby se přečetla, a stiskněte klávesu ENTER.</span><span class="sxs-lookup"><span data-stu-id="d1654-139">In the address bar, add `channels` to the URL, so that is reads `http://localhost:[port]/channels` and press ENTER.</span></span>  
  
     <span data-ttu-id="d1654-140">Kanál kanálů se zobrazí v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="d1654-140">The channels feed appears in the browser.</span></span>  
  
7. <span data-ttu-id="d1654-141">Zavřete webový prohlížeč stisknutím kláves ALT+F4.</span><span class="sxs-lookup"><span data-stu-id="d1654-141">Close the Web browser, by pressing ALT+F4.</span></span>  
  
 <span data-ttu-id="d1654-142">Tato ukázka ukazuje, že hostitelská vrstva je <xref:System.Web.Routing> schopna skládat s třídami v oboru názvů pro směrování požadavků služeb hostovaných přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="d1654-142">This sample demonstrates that the hosting layer is capable of composing with the classes in the <xref:System.Web.Routing> namespace for routing the requests of services hosted over HTTP.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d1654-143">Pokud je výchozí verze fondu aplikací nastavena na verzi 2, je nutné aktualizovat výchozí verzi fondu aplikací na rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d1654-143">You must update the default application pool version to .NET Framework 4 if it’s set to version 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1654-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="d1654-144">See also</span></span>

- <span data-ttu-id="d1654-145">[Ukázky hostování a perzistence appfabric](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="d1654-145">[AppFabric Hosting and Persistence Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
