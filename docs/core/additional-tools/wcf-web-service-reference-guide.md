---
title: Přidat odkaz na webovou službu WCF
description: Přehled nástroje Microsoft WCF Web Service Reference Provider Tool, který přidává funkce pro projekty .NET Core a ASP.NET Core, podobně jako přidat odkaz na službu pro projekty rozhraní .NET Framework.
author: dasetser
ms.date: 10/29/2019
ms.custom: mvc
ms.openlocfilehash: cdd6b457d289dd7b752c97c5645f0797f24b72aa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715674"
---
# <a name="use-the-wcf-web-service-reference-provider-tool"></a><span data-ttu-id="c0705-103">Použití nástroje WCF Web Service Reference Provider Tool</span><span class="sxs-lookup"><span data-stu-id="c0705-103">Use the WCF Web Service Reference Provider Tool</span></span>

<span data-ttu-id="c0705-104">V průběhu let mnoho vývojářů sady Visual Studio si užilo produktivitu, kterou nástroj [**Add Service Reference**](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) poskytl, když jejich projekty rozhraní .NET Framework potřebovaly přístup k webovým službám.</span><span class="sxs-lookup"><span data-stu-id="c0705-104">Over the years, many Visual Studio developers have enjoyed the productivity that the [**Add Service Reference**](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) tool provided when their .NET Framework projects needed to access web services.</span></span>  <span data-ttu-id="c0705-105">Nástroj **WCF Web Service Reference** je rozšíření připojené služby visual studia, které poskytuje prostředí, jako je funkce Přidat odkaz na službu pro projekty .NET Core a ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="c0705-105">The **WCF Web Service Reference** tool is a Visual Studio connected service extension that provides an experience like the Add Service Reference functionality for .NET Core and ASP.NET Core projects.</span></span> <span data-ttu-id="c0705-106">Tento nástroj načte metadata z webové služby v aktuálním řešení, v síťovém umístění nebo ze souboru WSDL a vygeneruje zdrojový soubor kompatibilní s rozhraním .NET Core obsahující kód proxy klienta WCF (Windows Communication Foundation), který můžete použít pro přístup k webu. Služby.</span><span class="sxs-lookup"><span data-stu-id="c0705-106">This tool retrieves metadata from a web service in the current solution, on a network location, or from a WSDL file, and generates a .NET Core compatible source file containing Windows Communication Foundation (WCF) client proxy code that you can use to access the web service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c0705-107">Měli byste odkazovat pouze na služby z důvěryhodného zdroje.</span><span class="sxs-lookup"><span data-stu-id="c0705-107">You should only reference services from a trusted source.</span></span> <span data-ttu-id="c0705-108">Přidání odkazů z nedůvěryhodného zdroje může ohrozit zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c0705-108">Adding references from an untrusted source may compromise security.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c0705-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c0705-109">Prerequisites</span></span>

- <span data-ttu-id="c0705-110">[Visual Studio 2017 verze 15.5](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) nebo novější verze</span><span class="sxs-lookup"><span data-stu-id="c0705-110">[Visual Studio 2017 version 15.5](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) or later versions</span></span>

## <a name="how-to-use-the-extension"></a><span data-ttu-id="c0705-111">Jak používat rozšíření</span><span class="sxs-lookup"><span data-stu-id="c0705-111">How to use the extension</span></span>

> [!NOTE]
> <span data-ttu-id="c0705-112">Možnost **WCF Web Service Reference** je použitelná pro projekty vytvořené pomocí následujících šablon projektu:</span><span class="sxs-lookup"><span data-stu-id="c0705-112">The **WCF Web Service Reference** option is applicable to projects created using the following project templates:</span></span>
>
> - <span data-ttu-id="c0705-113">**Visual C#** > **.NET Core**</span><span class="sxs-lookup"><span data-stu-id="c0705-113">**Visual C#** > **.NET Core**</span></span>
> - <span data-ttu-id="c0705-114">**Visual C#** > **.NET Standard**</span><span class="sxs-lookup"><span data-stu-id="c0705-114">**Visual C#** > **.NET Standard**</span></span>
> - <span data-ttu-id="c0705-115">**Visual C#** > **Webová** > ASP.NET základní**webová aplikace** Visual C#</span><span class="sxs-lookup"><span data-stu-id="c0705-115">**Visual C#** > **Web** > **ASP.NET Core Web Application**</span></span>

<span data-ttu-id="c0705-116">Pomocí šablony projektu **ASP.NET základní webové aplikace** jako příklad vás tento článek provede přidáním odkazu na službu WCF do projektu:</span><span class="sxs-lookup"><span data-stu-id="c0705-116">Using the **ASP.NET Core Web Application** project template as an example, this article walks you through adding a WCF service reference to the project:</span></span>

1. <span data-ttu-id="c0705-117">V Průzkumníku řešení poklepejte na uzel **Připojené služby** projektu (pro projekt .NET Core nebo .NET Standard je tato možnost k dispozici po klepnutí pravým tlačítkem myši na uzel **Závislosti** projektu v Průzkumníku řešení).</span><span class="sxs-lookup"><span data-stu-id="c0705-117">In Solution Explorer, double-click the **Connected Services** node of the project (for a .NET Core or .NET Standard project this option is available when you right-click on the **Dependencies** node of the project in Solution Explorer).</span></span>

    <span data-ttu-id="c0705-118">Stránka **Připojené služby** se zobrazí na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="c0705-118">The **Connected Services** page appears as shown in the following image:</span></span>

    ![Karta Propojená služba Visual Studio pro jádro rozhraní .NET](./media/wcf-web-service-reference-guide/wcfcs-ConnectedServicesPage.png)

2. <span data-ttu-id="c0705-120">Na stránce **Připojené služby** klepněte na **položku Microsoft WCF Web Service Reference Provider**.</span><span class="sxs-lookup"><span data-stu-id="c0705-120">On the **Connected Services** page, click **Microsoft WCF Web Service Reference Provider**.</span></span> <span data-ttu-id="c0705-121">Tím se zobrazí Průvodce **odkazem na konfiguraci webové služby WCF:**</span><span class="sxs-lookup"><span data-stu-id="c0705-121">This brings up the **Configure WCF Web Service Reference** wizard:</span></span>

    ![Karta Koncový bod služby Visual Studio pro jádro rozhraní .NET](./media/wcf-web-service-reference-guide/wcfcs-ServiceEndpointPage.png)

3. <span data-ttu-id="c0705-123">Vyberte službu.</span><span class="sxs-lookup"><span data-stu-id="c0705-123">Select a service.</span></span>

    <span data-ttu-id="c0705-124">3a.</span><span class="sxs-lookup"><span data-stu-id="c0705-124">3a.</span></span> <span data-ttu-id="c0705-125">V průvodci konfigurovat referenční webové **služby WCF** je k dispozici několik možností vyhledávání služeb:</span><span class="sxs-lookup"><span data-stu-id="c0705-125">There are several services search options available within the **Configure WCF Web Service Reference** wizard:</span></span>

     * <span data-ttu-id="c0705-126">Chcete-li vyhledat služby definované v aktuálním řešení, klepněte na tlačítko **Zjistit.**</span><span class="sxs-lookup"><span data-stu-id="c0705-126">To search for services defined in the current solution, click the **Discover** button.</span></span>
     * <span data-ttu-id="c0705-127">Chcete-li vyhledat služby hostované na zadané adrese, zadejte adresu URL služby do pole **Adresa** a klepněte na tlačítko **Přejít.**</span><span class="sxs-lookup"><span data-stu-id="c0705-127">To search for services hosted at a specified address, enter a service URL in the **Address** box and click the **Go** button.</span></span>
     * <span data-ttu-id="c0705-128">Chcete-li vybrat soubor WSDL, který obsahuje informace o metadatech webové služby, klepněte na tlačítko **Procházet.**</span><span class="sxs-lookup"><span data-stu-id="c0705-128">To select a WSDL file that contains the web service metadata information, click the **Browse** button.</span></span>

    <span data-ttu-id="c0705-129">3b.</span><span class="sxs-lookup"><span data-stu-id="c0705-129">3b.</span></span> <span data-ttu-id="c0705-130">Vyberte službu ze seznamu výsledků hledání v poli **Služby.**</span><span class="sxs-lookup"><span data-stu-id="c0705-130">Select the service from the search results list in the **Services** box.</span></span> <span data-ttu-id="c0705-131">V případě potřeby zadejte obor názvů pro generovaný kód do odpovídajícího textového pole **Jmenný prostor.**</span><span class="sxs-lookup"><span data-stu-id="c0705-131">If needed, enter the namespace for the generated code in the corresponding **Namespace** text box.</span></span>

    <span data-ttu-id="c0705-132">3c.</span><span class="sxs-lookup"><span data-stu-id="c0705-132">3c.</span></span> <span data-ttu-id="c0705-133">Klepnutím na tlačítko **Další** otevřete **možnosti datového typu** a stránky **Možnosti klienta.**</span><span class="sxs-lookup"><span data-stu-id="c0705-133">Click the **Next** button to open the **Data Type Options** and the **Client Options** pages.</span></span> <span data-ttu-id="c0705-134">Případně můžete klepnutím na tlačítko **Dokončit** použít výchozí možnosti.</span><span class="sxs-lookup"><span data-stu-id="c0705-134">Alternatively, click the **Finish** button to use the default options.</span></span>

4. <span data-ttu-id="c0705-135">Formulář **Možnosti datového typu** umožňuje upřesnit nastavení konfigurace odkazu na vygenerovanou službu:</span><span class="sxs-lookup"><span data-stu-id="c0705-135">The **Data Type Options** form enables you to refine the generated service reference configuration settings:</span></span>

    ![Karta Možnosti datového typu sady Visual Studio pro jádro rozhraní .NET](./media/wcf-web-service-reference-guide/wcfcs-DataTypesPage.png)

    > [!NOTE]
    > <span data-ttu-id="c0705-137">Možnost **Znovu použít typy v odkazovaných sestaveních** je užitečná, když jsou datové typy potřebné pro generování referenčního kódu služby definovány v jednom z odkazovaných sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="c0705-137">The **Reuse types in referenced assemblies** check box option is useful when data types needed for service reference code generation are defined in one of your project's referenced assemblies.</span></span>  <span data-ttu-id="c0705-138">Je důležité znovu použít tyto existující datové typy, aby se zabránilo sopakování typu kompilace nebo problémům za běhu.</span><span class="sxs-lookup"><span data-stu-id="c0705-138">It's important to reuse those existing data types to avoid compile-time type clash or runtime issues.</span></span>

    <span data-ttu-id="c0705-139">Může dojít ke zpoždění při načítání informací o typu, v závislosti na počtu závislostí projektu a dalších faktorech výkonu systému.</span><span class="sxs-lookup"><span data-stu-id="c0705-139">There may be a delay while type information is loaded, depending on the number of project dependencies and other system performance factors.</span></span> <span data-ttu-id="c0705-140">Tlačítko **Dokončit** je během načítání zakázáno, pokud není zaškrtnuto políčko **Znovu použít v odkazovaných sestavách.**</span><span class="sxs-lookup"><span data-stu-id="c0705-140">The **Finish** button is disabled during loading unless the **Reuse types in referenced assemblies** check box is unchecked.</span></span>

5. <span data-ttu-id="c0705-141">Po dokončení klepněte na **tlačítko Dokončit.**</span><span class="sxs-lookup"><span data-stu-id="c0705-141">Click **Finish** when you are done.</span></span>

<span data-ttu-id="c0705-142">Při zobrazování průběhu nástroj:</span><span class="sxs-lookup"><span data-stu-id="c0705-142">While displaying progress, the tool:</span></span>

- <span data-ttu-id="c0705-143">Stáhne metadata ze služby WCF.</span><span class="sxs-lookup"><span data-stu-id="c0705-143">Downloads metadata from the WCF service.</span></span>
- <span data-ttu-id="c0705-144">Generuje referenční kód služby v souboru s názvem *reference.cs*a přidá jej do projektu v uzlu **Připojené služby.**</span><span class="sxs-lookup"><span data-stu-id="c0705-144">Generates the service reference code in a file named *reference.cs*, and adds it to your project under the **Connected Services** node.</span></span>
- <span data-ttu-id="c0705-145">Aktualizuje soubor projektu (.csproj) s Odkazy na balíček NuGet potřebné ke kompilaci a spuštění na cílové platformě.</span><span class="sxs-lookup"><span data-stu-id="c0705-145">Updates the project file (.csproj) with NuGet package references required to compile and run on the target platform.</span></span>

![Okno Průběh sady Visual Studio](./media/wcf-web-service-reference-guide/wcfcs-ProgressWindow.png)

<span data-ttu-id="c0705-147">Po dokončení těchto procesů můžete vytvořit instanci generovaného typu klienta WCF a vyvolat operace služby.</span><span class="sxs-lookup"><span data-stu-id="c0705-147">When these processes complete, you can create an instance of the generated WCF client type and invoke the service operations.</span></span>

## <a name="see-also"></a><span data-ttu-id="c0705-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="c0705-148">See also</span></span>

- [<span data-ttu-id="c0705-149">Začínáme s aplikacemi Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="c0705-149">Get started with Windows Communication Foundation applications</span></span>](../../framework/wcf/getting-started-tutorial.md)
- [<span data-ttu-id="c0705-150">Služby Windows Communication Foundation a datové služby WCF v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c0705-150">Windows Communication Foundation services and WCF data services in Visual Studio</span></span>](/visualstudio/data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio)
- [<span data-ttu-id="c0705-151">Funkce podporované wcf na .NET Core</span><span class="sxs-lookup"><span data-stu-id="c0705-151">WCF supported features on .NET Core</span></span>](https://github.com/dotnet/wcf/blob/master/release-notes/SupportedFeatures-v2.1.0.md)

## <a name="feedback--questions"></a><span data-ttu-id="c0705-152">Zpětná vazba & otázky</span><span class="sxs-lookup"><span data-stu-id="c0705-152">Feedback & questions</span></span>

<span data-ttu-id="c0705-153">Máte-li jakékoli dotazy nebo zpětnou vazbu, nahlaste to v [komunitě vývojářů](https://developercommunity.visualstudio.com/) pomocí nástroje [Nahlásit problém.](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)</span><span class="sxs-lookup"><span data-stu-id="c0705-153">If you have any questions or feedback, report it at [Developer Community](https://developercommunity.visualstudio.com/) using the [Report a problem](/visualstudio/ide/how-to-report-a-problem-with-visual-studio) tool.</span></span>

## <a name="release-notes"></a><span data-ttu-id="c0705-154">Poznámky k verzi</span><span class="sxs-lookup"><span data-stu-id="c0705-154">Release notes</span></span>

- <span data-ttu-id="c0705-155">Aktualizované informace o verzi, včetně známých problémů, naleznete v [poznámkách k verzi.](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md)</span><span class="sxs-lookup"><span data-stu-id="c0705-155">Refer to the [Release notes](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md) for updated release information, including known issues.</span></span>
