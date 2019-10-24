---
title: Přidat odkaz na webovou službu WCF
description: Přehled nástroje Microsoft WCF Web Service Reference Provider, který přidává funkce pro projekty .NET Core a ASP.NET Core, podobně jako Přidat odkaz na službu pro .NET Framework projekty.
author: mlacouture
ms.date: 04/19/2018
ms.custom: mvc, seodec18
ms.openlocfilehash: 28eaae4a83d918f8a9e5376eb3c8d42843ffa027
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72773962"
---
# <a name="use-the-wcf-web-service-reference-provider-tool"></a><span data-ttu-id="cd520-103">Použití nástroje poskytovatele referencí webové služby WCF</span><span class="sxs-lookup"><span data-stu-id="cd520-103">Use the WCF Web Service Reference Provider Tool</span></span>

<span data-ttu-id="cd520-104">V průběhu let mnoho vývojářů sady Visual Studio využilo produktivitu, kterou poskytuje nástroj [**Přidat odkaz na službu**](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) , když jejich .NET Framework projekty potřebují pro přístup k webovým službám.</span><span class="sxs-lookup"><span data-stu-id="cd520-104">Over the years, many Visual Studio developers have enjoyed the productivity that the [**Add Service Reference**](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference) tool provided when their .NET Framework projects needed to access web services.</span></span>  <span data-ttu-id="cd520-105">**Referenční nástroj webové služby WCF** je rozšíření propojené služby sady Visual Studio, které poskytuje prostředí, jako je funkce Přidat odkaz na službu pro projekty .NET Core a ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="cd520-105">The **WCF Web Service Reference** tool is a Visual Studio connected service extension that provides an experience like the Add Service Reference functionality for .NET Core and ASP.NET Core projects.</span></span> <span data-ttu-id="cd520-106">Tento nástroj načte metadata z webové služby v aktuálním řešení, v síťovém umístění nebo ze souboru WSDL a vygeneruje Windows Communication Foundation zdrojový proxy kód kompatibilní s .NET Core, který můžete použít pro přístup k webu. službám.</span><span class="sxs-lookup"><span data-stu-id="cd520-106">This tool retrieves metadata from a web service in the current solution, on a network location, or from a WSDL file, and generates a .NET Core compatible source file containing Windows Communication Foundation (WCF) client proxy code that you can use to access the web service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cd520-107">Měli byste odkazovat jenom na služby z důvěryhodného zdroje.</span><span class="sxs-lookup"><span data-stu-id="cd520-107">You should only reference services from a trusted source.</span></span> <span data-ttu-id="cd520-108">Přidání odkazů z nedůvěryhodného zdroje může ohrozit zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="cd520-108">Adding references from an untrusted source may compromise security.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cd520-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cd520-109">Prerequisites</span></span>

- <span data-ttu-id="cd520-110">[Visual Studio 2017 verze 15,5](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) nebo novější verze</span><span class="sxs-lookup"><span data-stu-id="cd520-110">[Visual Studio 2017 version 15.5](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) or later versions</span></span>

## <a name="how-to-use-the-extension"></a><span data-ttu-id="cd520-111">Jak používat rozšíření</span><span class="sxs-lookup"><span data-stu-id="cd520-111">How to use the extension</span></span>

> [!NOTE]
> <span data-ttu-id="cd520-112">Možnost **odkazu webové služby WCF** je platná pro projekty vytvořené pomocí následujících šablon projektu:</span><span class="sxs-lookup"><span data-stu-id="cd520-112">The **WCF Web Service Reference** option is applicable to projects created using the following project templates:</span></span>
>
> - <span data-ttu-id="cd520-113">**Visual C#**   >  **.NET Core**</span><span class="sxs-lookup"><span data-stu-id="cd520-113">**Visual C#** > **.NET Core**</span></span>
> - <span data-ttu-id="cd520-114">**Vizuální C#**   >  **.NET Standard**</span><span class="sxs-lookup"><span data-stu-id="cd520-114">**Visual C#** > **.NET Standard**</span></span>
> - <span data-ttu-id="cd520-115">Webová aplikace  **C# Visual**  > **Web**  > **ASP.NET Core**</span><span class="sxs-lookup"><span data-stu-id="cd520-115">**Visual C#** > **Web** > **ASP.NET Core Web Application**</span></span>

<span data-ttu-id="cd520-116">Pomocí šablony projektu **ASP.NET Core webové aplikace** jako příklad vás tento článek provede přidáním odkazu na službu WCF do projektu:</span><span class="sxs-lookup"><span data-stu-id="cd520-116">Using the **ASP.NET Core Web Application** project template as an example, this article walks you through adding a WCF service reference to the project:</span></span>

1. <span data-ttu-id="cd520-117">V Průzkumník řešení dvakrát klikněte na uzel **připojené služby** projektu (pro projekt .NET Core nebo .NET Standard je tato možnost k dispozici, když kliknete pravým tlačítkem myši na uzel **závislosti** projektu v Průzkumník řešení).</span><span class="sxs-lookup"><span data-stu-id="cd520-117">In Solution Explorer, double-click the **Connected Services** node of the project (for a .NET Core or .NET Standard project this option is available when you right-click on the **Dependencies** node of the project in Solution Explorer).</span></span>

    <span data-ttu-id="cd520-118">Stránka **připojené služby** se zobrazí, jak je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="cd520-118">The **Connected Services** page appears as shown in the following image:</span></span>

    ![Karta připojené služby sady Visual Studio pro .NET Core](./media/wcf-web-service-reference-guide/wcfcs-ConnectedServicesPage.png)

2. <span data-ttu-id="cd520-120">Na stránce **připojené služby** klikněte na **Microsoft WCF Web Service reference Provider**.</span><span class="sxs-lookup"><span data-stu-id="cd520-120">On the **Connected Services** page, click **Microsoft WCF Web Service Reference Provider**.</span></span> <span data-ttu-id="cd520-121">Tím se zobrazí průvodce **konfigurací odkazu na webovou službu WCF** :</span><span class="sxs-lookup"><span data-stu-id="cd520-121">This brings up the **Configure WCF Web Service Reference** wizard:</span></span>

    ![Karta koncového bodu služby sady Visual Studio pro .NET Core](./media/wcf-web-service-reference-guide/wcfcs-ServiceEndpointPage.png)

3. <span data-ttu-id="cd520-123">Vyberte službu.</span><span class="sxs-lookup"><span data-stu-id="cd520-123">Select a service.</span></span>

    <span data-ttu-id="cd520-124">čl.</span><span class="sxs-lookup"><span data-stu-id="cd520-124">3a.</span></span> <span data-ttu-id="cd520-125">V průvodci **konfigurací odkazu webové služby WCF** je dostupných několik možností hledání služeb:</span><span class="sxs-lookup"><span data-stu-id="cd520-125">There are several services search options available within the **Configure WCF Web Service Reference** wizard:</span></span>

     * <span data-ttu-id="cd520-126">Pokud chcete vyhledat služby definované v aktuálním řešení, klikněte na tlačítko **Vyhledat** .</span><span class="sxs-lookup"><span data-stu-id="cd520-126">To search for services defined in the current solution, click the **Discover** button.</span></span>
     * <span data-ttu-id="cd520-127">Pokud chcete vyhledat služby hostované na zadané adrese, zadejte adresu URL služby do pole **adresa** a klikněte na tlačítko **Přejít** .</span><span class="sxs-lookup"><span data-stu-id="cd520-127">To search for services hosted at a specified address, enter a service URL in the **Address** box and click the **Go** button.</span></span>
     * <span data-ttu-id="cd520-128">Chcete-li vybrat soubor WSDL, který obsahuje informace metadat webové služby, klikněte na tlačítko **Procházet** .</span><span class="sxs-lookup"><span data-stu-id="cd520-128">To select a WSDL file that contains the web service metadata information, click the **Browse** button.</span></span>

    <span data-ttu-id="cd520-129">3b.</span><span class="sxs-lookup"><span data-stu-id="cd520-129">3b.</span></span> <span data-ttu-id="cd520-130">Vyberte službu ze seznamu výsledků hledání v poli **služby** .</span><span class="sxs-lookup"><span data-stu-id="cd520-130">Select the service from the search results list in the **Services** box.</span></span> <span data-ttu-id="cd520-131">V případě potřeby zadejte obor názvů pro vygenerovaný kód do textového pole odpovídající **obor názvů** .</span><span class="sxs-lookup"><span data-stu-id="cd520-131">If needed, enter the namespace for the generated code in the corresponding **Namespace** text box.</span></span>

    <span data-ttu-id="cd520-132">3C.</span><span class="sxs-lookup"><span data-stu-id="cd520-132">3c.</span></span> <span data-ttu-id="cd520-133">Kliknutím na tlačítko **Další** otevřete **Možnosti datový typ** a stránky **Možnosti klienta** .</span><span class="sxs-lookup"><span data-stu-id="cd520-133">Click the **Next** button to open the **Data Type Options** and the **Client Options** pages.</span></span> <span data-ttu-id="cd520-134">Případně můžete kliknutím na tlačítko **Dokončit** použít výchozí možnosti.</span><span class="sxs-lookup"><span data-stu-id="cd520-134">Alternatively, click the **Finish** button to use the default options.</span></span>

4. <span data-ttu-id="cd520-135">Formulář **Možnosti datového typu** umožňuje upřesnit vygenerovaná nastavení konfigurace odkazu na službu:</span><span class="sxs-lookup"><span data-stu-id="cd520-135">The **Data Type Options** form enables you to refine the generated service reference configuration settings:</span></span>

    ![Karta možnosti datového typu sady Visual Studio pro .NET Core](./media/wcf-web-service-reference-guide/wcfcs-DataTypesPage.png)

    > [!NOTE]
    > <span data-ttu-id="cd520-137">Možnost **znovu použít typy v odkazovaných sestaveních** zaškrtávací políčko je užitečná, pokud jsou datové typy potřebné pro generování kódu odkazu na službu definovány v jednom z odkazovaných sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="cd520-137">The **Reuse types in referenced assemblies** check box option is useful when data types needed for service reference code generation are defined in one of your project's referenced assemblies.</span></span>  <span data-ttu-id="cd520-138">Je důležité znovu použít tyto existující datové typy, aby nedocházelo ke konfliktům typu v době kompilace nebo běhovým problémům.</span><span class="sxs-lookup"><span data-stu-id="cd520-138">It's important to reuse those existing data types to avoid compile-time type clash or runtime issues.</span></span>

    <span data-ttu-id="cd520-139">Může dojít ke zpoždění, pokud jsou načteny informace o typu, v závislosti na počtu závislostí projektu a dalších systémových faktorech výkonu.</span><span class="sxs-lookup"><span data-stu-id="cd520-139">There may be a delay while type information is loaded, depending on the number of project dependencies and other system performance factors.</span></span> <span data-ttu-id="cd520-140">Tlačítko **Dokončit** je během načítání zakázáno, pokud není zaškrtnuté políčko **znovu použít typy v odkazovaných sestaveních** .</span><span class="sxs-lookup"><span data-stu-id="cd520-140">The **Finish** button is disabled during loading unless the **Reuse types in referenced assemblies** check box is unchecked.</span></span>

5. <span data-ttu-id="cd520-141">Po dokončení klikněte na **Dokončit** .</span><span class="sxs-lookup"><span data-stu-id="cd520-141">Click **Finish** when you are done.</span></span>

<span data-ttu-id="cd520-142">Během zobrazování průběhu nástroje:</span><span class="sxs-lookup"><span data-stu-id="cd520-142">While displaying progress, the tool:</span></span>

- <span data-ttu-id="cd520-143">Stáhne metadata ze služby WCF.</span><span class="sxs-lookup"><span data-stu-id="cd520-143">Downloads metadata from the WCF service.</span></span>
- <span data-ttu-id="cd520-144">Generuje kód odkazu na službu v souboru s názvem *reference.cs*a přidá ho do projektu pod uzlem **připojené služby** .</span><span class="sxs-lookup"><span data-stu-id="cd520-144">Generates the service reference code in a file named *reference.cs*, and adds it to your project under the **Connected Services** node.</span></span>
- <span data-ttu-id="cd520-145">Aktualizuje soubor projektu (. csproj) pomocí odkazů na balíček NuGet potřebných pro zkompilování a spuštění na cílové platformě.</span><span class="sxs-lookup"><span data-stu-id="cd520-145">Updates the project file (.csproj) with NuGet package references required to compile and run on the target platform.</span></span>

![Okno průběhu sady Visual Studio](./media/wcf-web-service-reference-guide/wcfcs-ProgressWindow.png)

<span data-ttu-id="cd520-147">Po dokončení těchto procesů můžete vytvořit instanci vygenerovaného typu klienta WCF a vyvolat operace služby.</span><span class="sxs-lookup"><span data-stu-id="cd520-147">When these processes complete, you can create an instance of the generated WCF client type and invoke the service operations.</span></span>

## <a name="next-steps"></a><span data-ttu-id="cd520-148">Další kroky</span><span class="sxs-lookup"><span data-stu-id="cd520-148">Next steps</span></span>

### <a name="feedback--questions"></a><span data-ttu-id="cd520-149">Názory & dotazů</span><span class="sxs-lookup"><span data-stu-id="cd520-149">Feedback & questions</span></span>

<span data-ttu-id="cd520-150">Pokud máte nějaké dotazy nebo připomínky, [otevřete problém na GitHubu](https://github.com/dotnet/wcf/issues/new).</span><span class="sxs-lookup"><span data-stu-id="cd520-150">If you have any questions or feedback, [open an issue on GitHub](https://github.com/dotnet/wcf/issues/new).</span></span> <span data-ttu-id="cd520-151">V [ÚLOŽIŠTI WCF na GitHubu](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling)můžete také zkontrolovat všechny existující otázky nebo problémy.</span><span class="sxs-lookup"><span data-stu-id="cd520-151">You can also review any existing questions or issues [at the WCF repo on GitHub](https://github.com/dotnet/wcf/issues?utf8=%E2%9C%93&q=is:issue%20label:tooling).</span></span>

### <a name="release-notes"></a><span data-ttu-id="cd520-152">Zpráva k vydání verze</span><span class="sxs-lookup"><span data-stu-id="cd520-152">Release notes</span></span>

- <span data-ttu-id="cd520-153">Aktualizované informace o verzi, včetně známých problémů, najdete v [poznámkách k verzi](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md) .</span><span class="sxs-lookup"><span data-stu-id="cd520-153">Refer to the [Release notes](https://github.com/dotnet/wcf/blob/master/release-notes/WCF-Web-Service-Reference-notes.md) for updated release information, including known issues.</span></span>
