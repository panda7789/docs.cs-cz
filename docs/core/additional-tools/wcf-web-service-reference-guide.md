---
title: "Nástroj zprostředkovatele Microsoft WCF webové služby odkaz"
description: "Přehled Microsoft WCF webové služby odkaz zprostředkovatele nástroj, který přidá funkce pro .NET Core a ASP.NET Core projekty, podobně jako přidat odkaz na službu pro projekty rozhraní .NET Framework."
author: mlacouture
manager: wpickett
ms.author: johalex
ms.date: 01/19/2018
ms.topic: article
ms.prod: .net-core
ms.custom: mvc
ms.openlocfilehash: e445361f9f4a858f4b34ca1008670fadc62b8b3c
ms.sourcegitcommit: dd6ea7f0e581ac84e0a90d9b23c463fcf1ec3ce7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2018
---
# <a name="microsoft-wcf-web-service-reference-provider-tool"></a><span data-ttu-id="f0f78-103">Nástroj zprostředkovatele Microsoft WCF webové služby odkaz</span><span class="sxs-lookup"><span data-stu-id="f0f78-103">Microsoft WCF Web Service Reference Provider Tool</span></span>

<span data-ttu-id="f0f78-104">V průběhu let, celá řada vývojářů Visual Studio líbilo na produktivitu, [ **přidat odkaz na službu** ](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) nástroj, který poskytuje při jejich projektů rozhraní .NET Framework potřebné pro přístup k webovým službám.</span><span class="sxs-lookup"><span data-stu-id="f0f78-104">Over the years, many Visual Studio developers have enjoyed the productivity that the [**Add Service Reference**](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) tool provided when their .NET Framework projects needed to access web services.</span></span>  <span data-ttu-id="f0f78-105">**Odkaz na službu WCF Web** nástroj je rozšíření služby Visual Studio připojené, která poskytuje prostředí jako je třeba funkcionalita přidat odkaz na službu pro .NET Core a ASP.NET Core projekty.</span><span class="sxs-lookup"><span data-stu-id="f0f78-105">The **WCF Web Service Reference** tool is a Visual Studio connected service extension that provides an experience like the Add Service Reference functionality for .NET Core and ASP.NET Core projects.</span></span> <span data-ttu-id="f0f78-106">Tento nástroj získává metadata z webové služby v aktuálním řešení v umístění v síti, nebo ze souboru WSDL a vytvoří soubor kompatibilní zdroj .NET Core obsahující kód proxy serveru klienta Windows Communication Foundation (WCF), který můžete použít pro přístup k webu Služba.</span><span class="sxs-lookup"><span data-stu-id="f0f78-106">This tool retrieves metadata from a web service in the current solution, on a network location, or from a WSDL file, and generates a .NET Core compatible source file containing Windows Communication Foundation (WCF) client proxy code that you can use to access the web service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f0f78-107">Služby by měl odkazovat jenom z důvěryhodného zdroje.</span><span class="sxs-lookup"><span data-stu-id="f0f78-107">You should only reference services from a trusted source.</span></span> <span data-ttu-id="f0f78-108">Přidání odkazů z nedůvěryhodných zdrojů může ohrozit zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="f0f78-108">Adding references from an untrusted source may compromise security.</span></span> 

## <a name="how-to-use-the-extension"></a><span data-ttu-id="f0f78-109">Jak používat rozšíření</span><span class="sxs-lookup"><span data-stu-id="f0f78-109">How to use the extension</span></span>

> [!NOTE]
> <span data-ttu-id="f0f78-110">**Odkaz na službu WCF Web** možnost se vztahuje na projekty vytvořené pomocí následujících šablon projektu:</span><span class="sxs-lookup"><span data-stu-id="f0f78-110">The **WCF Web Service Reference** option is applicable to projects created using the following project templates:</span></span>
> * <span data-ttu-id="f0f78-111">**Visual C#** > **.NET Core**</span><span class="sxs-lookup"><span data-stu-id="f0f78-111">**Visual C#** > **.NET Core**</span></span>
> * <span data-ttu-id="f0f78-112">**Visual C#** > **Standard rozhraní .NET**</span><span class="sxs-lookup"><span data-stu-id="f0f78-112">**Visual C#** > **.NET Standard**</span></span>
> * <span data-ttu-id="f0f78-113">**Visual C#** > **webové** > **webové aplikace ASP.NET Core**</span><span class="sxs-lookup"><span data-stu-id="f0f78-113">**Visual C#** > **Web** > **ASP.NET Core Web Application**</span></span>

<span data-ttu-id="f0f78-114">Pomocí **webové aplikace ASP.NET Core** šablony projektu jako příklad, tento článek vás provede procesem přidání odkazu na službu WCF do projektu:</span><span class="sxs-lookup"><span data-stu-id="f0f78-114">Using the **ASP.NET Core Web Application** project template as an example, this article walks you through adding a WCF service reference to the project:</span></span>

1. <span data-ttu-id="f0f78-115">V Průzkumníku řešení klikněte dvakrát na **připojení služby** uzel projektu (pro .NET Core nebo .NET Standard projekt tato možnost je dostupná, když klikněte pravým tlačítkem na **závislosti** uzlu projekt v Průzkumníku řešení).</span><span class="sxs-lookup"><span data-stu-id="f0f78-115">In Solution Explorer, double-click the **Connected Services** node of the project (for a .NET Core or .NET Standard project this option is available when you right-click on the **Dependencies** node of the project in Solution Explorer).</span></span>

<span data-ttu-id="f0f78-116">**Připojené služby** stránka se zobrazí, jak je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="f0f78-116">The **Connected Services** page appears as shown in the following image:</span></span>

![Karta připojené služby](./media/wcf-web-service-reference-guide/wcfcs-ConnectedServicesPage.png)

2. <span data-ttu-id="f0f78-118">Na **připojené služby** klikněte na tlačítko **odkaz zprostředkovatele služby Microsoft WCF webové služby**.</span><span class="sxs-lookup"><span data-stu-id="f0f78-118">On the **Connected Services** page, click **Microsoft WCF Web Service Reference Provider**.</span></span> <span data-ttu-id="f0f78-119">Po výběru této možnosti **nastavit odkaz na službu Web WCF** průvodce:</span><span class="sxs-lookup"><span data-stu-id="f0f78-119">This brings up the **Configure WCF Web Service Reference** wizard:</span></span>

![Karta koncový bod služby](./media/wcf-web-service-reference-guide/wcfcs-ServiceEndpointPage.png)

3. <span data-ttu-id="f0f78-121">Vyberte službu.</span><span class="sxs-lookup"><span data-stu-id="f0f78-121">Select a service.</span></span>

    <span data-ttu-id="f0f78-122">3a.</span><span class="sxs-lookup"><span data-stu-id="f0f78-122">3a.</span></span> <span data-ttu-id="f0f78-123">Nejsou k dispozici v rámci několik možností vyhledávání služby **nastavit odkaz na službu Web WCF** průvodce:</span><span class="sxs-lookup"><span data-stu-id="f0f78-123">There are several services search options available within the **Configure WCF Web Service Reference** wizard:</span></span>
    
     * <span data-ttu-id="f0f78-124">Chcete-li vyhledat služby definované v aktuálním řešení, klikněte na tlačítko **Discover** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="f0f78-124">To search for services defined in the current solution, click the **Discover** button.</span></span> 
     * <span data-ttu-id="f0f78-125">K vyhledání služeb hostovaných na zadané adrese, zadejte adresu URL služby v **adresu** pole a klikněte na tlačítko **přejděte** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="f0f78-125">To search for services hosted at a specified address, enter a service URL in the **Address** box and click the **Go** button.</span></span>
     * <span data-ttu-id="f0f78-126">Chcete-li vybrat WSDL soubor, který obsahuje informace metadat webové služby, klikněte na tlačítko **Procházet** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="f0f78-126">To select a WSDL file that contains the web service metadata information, click the **Browse** button.</span></span> 
     
    <span data-ttu-id="f0f78-127">3b.</span><span class="sxs-lookup"><span data-stu-id="f0f78-127">3b.</span></span> <span data-ttu-id="f0f78-128">Zvolte ze seznamu výsledků hledání v službu **služby** pole.</span><span class="sxs-lookup"><span data-stu-id="f0f78-128">Select the service from the search results list in the **Services** box.</span></span> <span data-ttu-id="f0f78-129">V případě potřeby zadejte obor názvů pro generovaný kód do odpovídajícího **Namespace** textové pole.</span><span class="sxs-lookup"><span data-stu-id="f0f78-129">If needed, enter the namespace for the generated code in the corresponding **Namespace** text box.</span></span>
    
    <span data-ttu-id="f0f78-130">3c.</span><span class="sxs-lookup"><span data-stu-id="f0f78-130">3c.</span></span> <span data-ttu-id="f0f78-131">Klikněte **Další** tlačítko Otevřít **možnosti datového typu** a **možnosti klienta** stránky.</span><span class="sxs-lookup"><span data-stu-id="f0f78-131">Click the **Next** button to open the **Data Type Options** and the **Client Options** pages.</span></span> <span data-ttu-id="f0f78-132">Případně, kliknutím na tlačítko **Dokončit** tlačítko použít výchozí možnosti.</span><span class="sxs-lookup"><span data-stu-id="f0f78-132">Alternatively, click the **Finish** button to use the default options.</span></span>


4. <span data-ttu-id="f0f78-133">**Možnosti datového typu** formulář umožňuje Upřesnit nastavení konfigurace referenčního generovaného služby:</span><span class="sxs-lookup"><span data-stu-id="f0f78-133">The **Data Type Options** form enables you to refine the generated service reference configuration settings:</span></span>

![Karta Možnosti typ dat](./media/wcf-web-service-reference-guide/wcfcs-DataTypesPage.png)

> [!NOTE]
> <span data-ttu-id="f0f78-135">**Znovu použít typy v odkazovaných sestaveních** možnost zaškrtávací políčko je užitečné, když potřebné pro generování kódu služby referenční datové typy jsou definovány v jednom z vašeho projektu odkazované sestavení.</span><span class="sxs-lookup"><span data-stu-id="f0f78-135">The **Reuse types in referenced assemblies** check box option is useful when data types needed for service reference code generation are defined in one of your project's referenced assemblies.</span></span>  <span data-ttu-id="f0f78-136">Je důležité znovu použít tyto existující datové typy, abyste předešli problémům s kolidovat nebo modul runtime typu v čase kompilace.</span><span class="sxs-lookup"><span data-stu-id="f0f78-136">It's important to reuse those existing data types to avoid compile-time type clash or runtime issues.</span></span>

<span data-ttu-id="f0f78-137">Může nastat zpoždění při načtení informací o typu, v závislosti na počtu závislosti projektu a dalších faktorů výkon systému.</span><span class="sxs-lookup"><span data-stu-id="f0f78-137">There may be a delay while type information is loaded, depending on the number of project dependencies and other system performance factors.</span></span> <span data-ttu-id="f0f78-138">**Dokončit** tlačítko k dispozici při načítání, pokud **znovu použít typy v odkazovaných sestaveních** zaškrtávací políčko je zaškrtnuté políčko.</span><span class="sxs-lookup"><span data-stu-id="f0f78-138">The **Finish** button is disabled during loading unless the **Reuse types in referenced assemblies** check box is unchecked.</span></span>

5. <span data-ttu-id="f0f78-139">Klikněte na tlačítko **Dokončit** po dokončení.</span><span class="sxs-lookup"><span data-stu-id="f0f78-139">Click **Finish** when you are done.</span></span>


<span data-ttu-id="f0f78-140">Při zobrazování průběhu nástroje:</span><span class="sxs-lookup"><span data-stu-id="f0f78-140">While displaying progress, the tool:</span></span>

* <span data-ttu-id="f0f78-141">Stáhne metadata ze služby WCF.</span><span class="sxs-lookup"><span data-stu-id="f0f78-141">Downloads metadata from the WCF service.</span></span> 
* <span data-ttu-id="f0f78-142">Generuje kód odkazu služby v souboru s názvem *reference.cs*a přidá ji do projektu v části **připojené služby** uzlu.</span><span class="sxs-lookup"><span data-stu-id="f0f78-142">Generates the service reference code in a file named *reference.cs*, and adds it to your project under the **Connected Services** node.</span></span> 
* <span data-ttu-id="f0f78-143">Aktualizace souboru projektu (.csproj) s odkazy na balíček NuGet potřeba zkompilování a spuštění na cílové platformy.</span><span class="sxs-lookup"><span data-stu-id="f0f78-143">Updates the project file (.csproj) with NuGet package references required to compile and run on the target platform.</span></span>

![Průběh – okno](./media/wcf-web-service-reference-guide/wcfcs-ProgressWindow.png)

<span data-ttu-id="f0f78-145">Po dokončení těchto procesů, můžete vytvořit instanci typu generovaného klienta WCF a vyvolání operací služby.</span><span class="sxs-lookup"><span data-stu-id="f0f78-145">When these processes complete, you can create an instance of the generated WCF client type and invoke the service operations.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f0f78-146">Další kroky</span><span class="sxs-lookup"><span data-stu-id="f0f78-146">Next steps</span></span>

### <a name="feedback--questions"></a><span data-ttu-id="f0f78-147">Názory a dotazy</span><span class="sxs-lookup"><span data-stu-id="f0f78-147">Feedback & questions</span></span>
<span data-ttu-id="f0f78-148">Pokud máte jakékoli dotazy nebo připomínky, [otevřete problém na Githubu](https://github.com/dotnet/wcf/issues/new).</span><span class="sxs-lookup"><span data-stu-id="f0f78-148">If you have any questions or feedback, [open an issue on GitHub](https://github.com/dotnet/wcf/issues/new).</span></span> <span data-ttu-id="f0f78-149">Můžete také zkontrolovat existující dotazy nebo problémy [v úložišti WCF na Githubu](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span><span class="sxs-lookup"><span data-stu-id="f0f78-149">You can also review any existing questions or issues [at the WCF repo on GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span></span>

### <a name="release-notes"></a><span data-ttu-id="f0f78-150">Zpráva k vydání verze</span><span class="sxs-lookup"><span data-stu-id="f0f78-150">Release notes</span></span>
* <span data-ttu-id="f0f78-151">Odkazovat [poznámky k verzi](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md) aktualizované verze informace, včetně známých problémů.</span><span class="sxs-lookup"><span data-stu-id="f0f78-151">Refer to the [Release notes](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md) for updated release information, including known issues.</span></span> 
