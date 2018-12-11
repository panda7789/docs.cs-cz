---
title: Přidat odkaz webové služby WCF
description: Přehled Microsoft WCF Web Service Reference Provider nástroj, který přidá funkce pro projekty .NET Core a ASP.NET Core, podobně jako přidat odkaz na službu pro projekty .NET Framework.
author: mlacouture
ms.date: 04/19/2018
ms.custom: mvc, seodec18
ms.openlocfilehash: 3566a92e05c03cc77e59a14e3b2521a1d6d0758a
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245571"
---
# <a name="use-the-wcf-web-service-reference-provider-tool"></a><span data-ttu-id="58ef7-103">Použijte nástroj WCF Web Service odkaz na poskytovatele</span><span class="sxs-lookup"><span data-stu-id="58ef7-103">Use the WCF Web Service Reference Provider Tool</span></span>

<span data-ttu-id="58ef7-104">V průběhu let, celá řada vývojářů sady Visual Studio pracovalo produktivity, která [ **přidat odkaz na službu** ](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) nástroje, které jsou k dispozici v případě potřeby svých projektů rozhraní .NET Framework pro přístup k webovým službám.</span><span class="sxs-lookup"><span data-stu-id="58ef7-104">Over the years, many Visual Studio developers have enjoyed the productivity that the [**Add Service Reference**](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) tool provided when their .NET Framework projects needed to access web services.</span></span>  <span data-ttu-id="58ef7-105">**WCF Web Service Reference** nástroj je rozšíření sady Visual Studio připojené služby, která poskytuje stejně jako funkce Přidat odkaz na službu pro .NET Core a ASP.NET Core projekty.</span><span class="sxs-lookup"><span data-stu-id="58ef7-105">The **WCF Web Service Reference** tool is a Visual Studio connected service extension that provides an experience like the Add Service Reference functionality for .NET Core and ASP.NET Core projects.</span></span> <span data-ttu-id="58ef7-106">Tento nástroj načte metadata z webové služby v aktuálním řešení, na umístění v síti, nebo ze souboru WSDL a vytvoří soubor kompatibilní zdroj .NET Core obsahující kód na proxy serveru klienta Windows Communication Foundation (WCF), který používáte pro přístup k webu Služba.</span><span class="sxs-lookup"><span data-stu-id="58ef7-106">This tool retrieves metadata from a web service in the current solution, on a network location, or from a WSDL file, and generates a .NET Core compatible source file containing Windows Communication Foundation (WCF) client proxy code that you can use to access the web service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="58ef7-107">Služby by měly odkazovat pouze z důvěryhodného zdroje.</span><span class="sxs-lookup"><span data-stu-id="58ef7-107">You should only reference services from a trusted source.</span></span> <span data-ttu-id="58ef7-108">Přidávání odkazů z nedůvěryhodných zdrojů může ohrozit zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="58ef7-108">Adding references from an untrusted source may compromise security.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="58ef7-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="58ef7-109">Prerequisites</span></span>

* <span data-ttu-id="58ef7-110">[Visual Studio 2017 15.5](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) nebo novější verze</span><span class="sxs-lookup"><span data-stu-id="58ef7-110">[Visual Studio 2017 15.5](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) or later versions</span></span>

## <a name="how-to-use-the-extension"></a><span data-ttu-id="58ef7-111">Jak používat rozšíření</span><span class="sxs-lookup"><span data-stu-id="58ef7-111">How to use the extension</span></span>

> [!NOTE]
> <span data-ttu-id="58ef7-112">**WCF Web Service Reference** možnost se vztahuje na projekty vytvořené pomocí následující šablony projektů:</span><span class="sxs-lookup"><span data-stu-id="58ef7-112">The **WCF Web Service Reference** option is applicable to projects created using the following project templates:</span></span>
> * <span data-ttu-id="58ef7-113">**Vizuální C#**   >  **.NET Core**</span><span class="sxs-lookup"><span data-stu-id="58ef7-113">**Visual C#** > **.NET Core**</span></span>
> * <span data-ttu-id="58ef7-114">**Vizuální C#**   >  **.NET Standard**</span><span class="sxs-lookup"><span data-stu-id="58ef7-114">**Visual C#** > **.NET Standard**</span></span>
> * <span data-ttu-id="58ef7-115">**Vizuální C#**   >  **webové** > **webová aplikace ASP.NET Core**</span><span class="sxs-lookup"><span data-stu-id="58ef7-115">**Visual C#** > **Web** > **ASP.NET Core Web Application**</span></span>

<span data-ttu-id="58ef7-116">Použití **webové aplikace ASP.NET Core** šablony projektu jako příklad, tento článek vás provede přidáním odkazu na službu WCF do projektu:</span><span class="sxs-lookup"><span data-stu-id="58ef7-116">Using the **ASP.NET Core Web Application** project template as an example, this article walks you through adding a WCF service reference to the project:</span></span>

1. <span data-ttu-id="58ef7-117">V Průzkumníku řešení poklikejte **připojené služby** uzlu projektu (pro projekt .NET Core nebo .NET Standard tato možnost je k dispozici, když kliknete pravým tlačítkem na **závislosti** uzlu projekt v Průzkumníku řešení).</span><span class="sxs-lookup"><span data-stu-id="58ef7-117">In Solution Explorer, double-click the **Connected Services** node of the project (for a .NET Core or .NET Standard project this option is available when you right-click on the **Dependencies** node of the project in Solution Explorer).</span></span>

<span data-ttu-id="58ef7-118">**Připojené služby** stránka se zobrazí, jak je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="58ef7-118">The **Connected Services** page appears as shown in the following image:</span></span>

![Visual Studio Connected Services kartu pro .NET Core](./media/wcf-web-service-reference-guide/wcfcs-ConnectedServicesPage.png)

2. <span data-ttu-id="58ef7-120">Na **připojené služby** klikněte na **Microsoft WCF Web Service Reference Provider**.</span><span class="sxs-lookup"><span data-stu-id="58ef7-120">On the **Connected Services** page, click **Microsoft WCF Web Service Reference Provider**.</span></span> <span data-ttu-id="58ef7-121">Tím se zobrazí **konfigurace WCF Web Service Reference** průvodce:</span><span class="sxs-lookup"><span data-stu-id="58ef7-121">This brings up the **Configure WCF Web Service Reference** wizard:</span></span>

![Visual Studio koncový bod služby kartu pro .NET Core](./media/wcf-web-service-reference-guide/wcfcs-ServiceEndpointPage.png)

3. <span data-ttu-id="58ef7-123">Vyberte službu.</span><span class="sxs-lookup"><span data-stu-id="58ef7-123">Select a service.</span></span>

    <span data-ttu-id="58ef7-124">3a.</span><span class="sxs-lookup"><span data-stu-id="58ef7-124">3a.</span></span> <span data-ttu-id="58ef7-125">Nejsou k dispozici v rámci několika možností hledání služeb **konfigurace WCF Web Service Reference** průvodce:</span><span class="sxs-lookup"><span data-stu-id="58ef7-125">There are several services search options available within the **Configure WCF Web Service Reference** wizard:</span></span>
    
     * <span data-ttu-id="58ef7-126">K vyhledání služby definované v aktuálním řešení, klikněte na tlačítko **Discover** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="58ef7-126">To search for services defined in the current solution, click the **Discover** button.</span></span> 
     * <span data-ttu-id="58ef7-127">K vyhledání služeb hostovaných na zadané adrese, zadejte adresu URL služby v **adresu** pole a klikněte na tlačítko **Přejít** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="58ef7-127">To search for services hosted at a specified address, enter a service URL in the **Address** box and click the **Go** button.</span></span>
     * <span data-ttu-id="58ef7-128">Pokud chcete vybrat soubor WSDL, který obsahuje informace o webových službách metadat, klikněte na tlačítko **Procházet** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="58ef7-128">To select a WSDL file that contains the web service metadata information, click the **Browse** button.</span></span> 
     
    <span data-ttu-id="58ef7-129">3b.</span><span class="sxs-lookup"><span data-stu-id="58ef7-129">3b.</span></span> <span data-ttu-id="58ef7-130">Tuto službu vybrat ze seznamu výsledků hledání v **služby** pole.</span><span class="sxs-lookup"><span data-stu-id="58ef7-130">Select the service from the search results list in the **Services** box.</span></span> <span data-ttu-id="58ef7-131">V případě potřeby zadejte obor názvů pro generovaný kód z odpovídajících **Namespace** textového pole.</span><span class="sxs-lookup"><span data-stu-id="58ef7-131">If needed, enter the namespace for the generated code in the corresponding **Namespace** text box.</span></span>
    
    <span data-ttu-id="58ef7-132">3c.</span><span class="sxs-lookup"><span data-stu-id="58ef7-132">3c.</span></span> <span data-ttu-id="58ef7-133">Klikněte na tlačítko **Další** tlačítko Otevřít **možnosti datového typu** a **možnosti klienta** stránky.</span><span class="sxs-lookup"><span data-stu-id="58ef7-133">Click the **Next** button to open the **Data Type Options** and the **Client Options** pages.</span></span> <span data-ttu-id="58ef7-134">Alternativně klepněte na tlačítko **Dokončit** tlačítko a použijte výchozí možnosti.</span><span class="sxs-lookup"><span data-stu-id="58ef7-134">Alternatively, click the **Finish** button to use the default options.</span></span>


4. <span data-ttu-id="58ef7-135">**Možnosti datového typu** formuláře můžete upřesnit nastavení konfigurace odkazu generované služby:</span><span class="sxs-lookup"><span data-stu-id="58ef7-135">The **Data Type Options** form enables you to refine the generated service reference configuration settings:</span></span>

![Visual Studio datový typ možnosti pro .NET Core](./media/wcf-web-service-reference-guide/wcfcs-DataTypesPage.png)

> [!NOTE]
> <span data-ttu-id="58ef7-137">**Znovu použít typy v odkazovaných sestaveních** zaškrtávací políčko možnost je užitečná, když datové typy, které jsou potřeba pro generování kódu pro odkaz na službu jsou definovány v jednom z odkazovaných sestavení vašeho projektu.</span><span class="sxs-lookup"><span data-stu-id="58ef7-137">The **Reuse types in referenced assemblies** check box option is useful when data types needed for service reference code generation are defined in one of your project's referenced assemblies.</span></span>  <span data-ttu-id="58ef7-138">Je důležité pro opětovné použití těchto existující datové typy, abyste předešli problémům s konflikt nebo modul runtime typu v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="58ef7-138">It's important to reuse those existing data types to avoid compile-time type clash or runtime issues.</span></span>

<span data-ttu-id="58ef7-139">Může docházet k prodlevám při načítání informací o typu, v závislosti na počtu závislostí projektu a dalších faktorů výkon systému.</span><span class="sxs-lookup"><span data-stu-id="58ef7-139">There may be a delay while type information is loaded, depending on the number of project dependencies and other system performance factors.</span></span> <span data-ttu-id="58ef7-140">**Dokončit** během načítání, pokud je tlačítko neaktivní **znovu použít typy v odkazovaných sestaveních** zaškrtávací políčko je zaškrtnuté políčko.</span><span class="sxs-lookup"><span data-stu-id="58ef7-140">The **Finish** button is disabled during loading unless the **Reuse types in referenced assemblies** check box is unchecked.</span></span>

5. <span data-ttu-id="58ef7-141">Klikněte na tlačítko **Dokončit** až budete hotovi.</span><span class="sxs-lookup"><span data-stu-id="58ef7-141">Click **Finish** when you are done.</span></span>


<span data-ttu-id="58ef7-142">Při zobrazování průběhu, nástroj:</span><span class="sxs-lookup"><span data-stu-id="58ef7-142">While displaying progress, the tool:</span></span>

* <span data-ttu-id="58ef7-143">Soubory ke stažení metadat ze služby WCF.</span><span class="sxs-lookup"><span data-stu-id="58ef7-143">Downloads metadata from the WCF service.</span></span> 
* <span data-ttu-id="58ef7-144">Generuje kód odkazu na službu do souboru s názvem *reference.cs*a přidá jej do projektu v rámci **připojené služby** uzlu.</span><span class="sxs-lookup"><span data-stu-id="58ef7-144">Generates the service reference code in a file named *reference.cs*, and adds it to your project under the **Connected Services** node.</span></span> 
* <span data-ttu-id="58ef7-145">Aktualizuje soubor projektu (.csproj) s odkazy na balíčky NuGet, které vyžaduje kompilace a spuštění na cílové platformě.</span><span class="sxs-lookup"><span data-stu-id="58ef7-145">Updates the project file (.csproj) with NuGet package references required to compile and run on the target platform.</span></span>

![Visual Studio průběh](./media/wcf-web-service-reference-guide/wcfcs-ProgressWindow.png)

<span data-ttu-id="58ef7-147">Po dokončení těchto procesů, můžete vytvořit instanci typu generovaného klienta WCF a volání operací služby.</span><span class="sxs-lookup"><span data-stu-id="58ef7-147">When these processes complete, you can create an instance of the generated WCF client type and invoke the service operations.</span></span>

## <a name="next-steps"></a><span data-ttu-id="58ef7-148">Další kroky</span><span class="sxs-lookup"><span data-stu-id="58ef7-148">Next steps</span></span>

### <a name="feedback--questions"></a><span data-ttu-id="58ef7-149">Zpětná vazba a otázky</span><span class="sxs-lookup"><span data-stu-id="58ef7-149">Feedback & questions</span></span>
<span data-ttu-id="58ef7-150">Pokud máte jakékoli dotazy nebo připomínky, [otevřete problém na Githubu](https://github.com/dotnet/wcf/issues/new).</span><span class="sxs-lookup"><span data-stu-id="58ef7-150">If you have any questions or feedback, [open an issue on GitHub](https://github.com/dotnet/wcf/issues/new).</span></span> <span data-ttu-id="58ef7-151">Můžete také zkontrolovat všechny stávající dotazy nebo potíže [v WCF úložišti na Githubu](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span><span class="sxs-lookup"><span data-stu-id="58ef7-151">You can also review any existing questions or issues [at the WCF repo on GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span></span>

### <a name="release-notes"></a><span data-ttu-id="58ef7-152">Zpráva k vydání verze</span><span class="sxs-lookup"><span data-stu-id="58ef7-152">Release notes</span></span>
* <span data-ttu-id="58ef7-153">Odkazovat [poznámky k verzi](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md) aktualizovanou verzi informace, včetně známých problémů.</span><span class="sxs-lookup"><span data-stu-id="58ef7-153">Refer to the [Release notes](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md) for updated release information, including known issues.</span></span> 
