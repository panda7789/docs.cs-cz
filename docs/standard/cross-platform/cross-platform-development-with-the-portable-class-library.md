---
title: Vývoj napříč platformami pomocí přenosné knihovny tříd
ms.date: 09/17/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Portable Class Library [.NET Framework]
- targeting multiple platforms
- multiple platforms, targeting
ms.assetid: c31e1663-c164-4e65-b66d-d3aa8750a154
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e5b6a32aa465700fb316bf2269c4d057ff823443
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64590337"
---
# <a name="cross-platform-development-with-the-portable-class-library"></a><span data-ttu-id="eead7-102">Vývoj pro různé platformy pomocí přenosné knihovny tříd</span><span class="sxs-lookup"><span data-stu-id="eead7-102">Cross-platform development with the Portable Class Library</span></span>

<span data-ttu-id="eead7-103">Typ knihovny přenosných tříd projektu v sadě Visual Studio pomáhá rychle a snadno vytvářet aplikace pro různé platformy a knihovny pro platformy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="eead7-103">The Portable Class Library project type in Visual Studio helps you build cross-platform apps and libraries for Microsoft platforms quickly and easily.</span></span>

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

<span data-ttu-id="eead7-104">Přenosné knihovny tříd můžete zkrátit čas a náklady na vývoj a testování kódu.</span><span class="sxs-lookup"><span data-stu-id="eead7-104">Portable class libraries can help you reduce the time and costs of developing and testing code.</span></span> <span data-ttu-id="eead7-105">Použít tento typ projektu můžete zapisovat a sestavovat přenosná sestavení rozhraní .NET Framework a odkázat na tato sestavení z aplikace, které se vyvíjet pro víc platforem, jako je například rozhraní .NET Framework, iOS nebo Mac</span><span class="sxs-lookup"><span data-stu-id="eead7-105">Use this project type to write and build portable .NET Framework assemblies, and then reference those assemblies from apps that target multiple platforms such as the .NET Framework, iOS, or Mac.</span></span>

<span data-ttu-id="eead7-106">I po vytvoření projektu přenosné knihovny tříd v sadě Visual Studio a začít s vývojem ho můžete změnit cílové platformy.</span><span class="sxs-lookup"><span data-stu-id="eead7-106">Even after you create a Portable Class Library project in Visual Studio and start developing it, you can change the target platforms.</span></span> <span data-ttu-id="eead7-107">Visual Studio zkompiluje knihovny pomocí nové sestavení, který vám pomůže identifikovat změny, které je třeba provést v kódu.</span><span class="sxs-lookup"><span data-stu-id="eead7-107">Visual Studio compiles your library with the new assemblies, which helps you identify the changes you need to make in your code.</span></span>

## <a name="create-a-portable-class-library-project"></a><span data-ttu-id="eead7-108">Vytvoření projektu knihovny přenosných tříd</span><span class="sxs-lookup"><span data-stu-id="eead7-108">Create a Portable Class Library project</span></span>

<span data-ttu-id="eead7-109">K vytvoření přenosné knihovny tříd pomocí šablony v sadě Visual Studio k dispozici.</span><span class="sxs-lookup"><span data-stu-id="eead7-109">To create a Portable Class Library, use the template provided in Visual Studio.</span></span> <span data-ttu-id="eead7-110">Vytvoření nového projektu (**souboru** > **nový projekt**) a **nový projekt** dialogového okna, vyberte svůj oblíbený programovací jazyk (Visual C# nebo Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="eead7-110">Create a new project (**File** > **New Project**), and in the **New Project** dialog box, select your programming language (Visual C# or Visual Basic).</span></span> <span data-ttu-id="eead7-111">Vyberte **knihovna tříd (starší přenosná)** šablony.</span><span class="sxs-lookup"><span data-stu-id="eead7-111">Then, select the **Class Library (Legacy Portable)** template.</span></span> <span data-ttu-id="eead7-112">Zadejte název pro váš projekt a zvolte **OK**.</span><span class="sxs-lookup"><span data-stu-id="eead7-112">Enter a name for your project and choose **OK**.</span></span>

<span data-ttu-id="eead7-113">**Přidat přenosnou knihovnu tříd** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="eead7-113">The **Add Portable Class Library** dialog box appears.</span></span> <span data-ttu-id="eead7-114">Vyberte dvě nebo více cílů a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="eead7-114">Choose two or more targets, and then choose **OK**.</span></span>

![Přidání cíle představující knihovny přenosných tříd v sadě Visual Studio](media/add-portable-class-library.png)

## <a name="change-targets"></a><span data-ttu-id="eead7-116">Změnit cíle</span><span class="sxs-lookup"><span data-stu-id="eead7-116">Change targets</span></span>

<span data-ttu-id="eead7-117">Při vytváření nebo poté, co jste začali vývoje můžete změnit cílové platformy projektu knihovny přenosných tříd.</span><span class="sxs-lookup"><span data-stu-id="eead7-117">You can change the target platforms of a portable class library project when you create it or after you’ve started development.</span></span> <span data-ttu-id="eead7-118">Pokud chcete změnit cíle po vytvoření projektu v **Průzkumníka řešení**, otevřete místní nabídku projektu přenosné knihovny tříd (nikoli řešení) a klikněte na tlačítko **vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="eead7-118">If you want to change the targets after you’ve created your project, in **Solution Explorer**, open the shortcut menu for your Portable Class Library project (not the solution), and then choose **Properties**.</span></span> <span data-ttu-id="eead7-119">Na stránce Vlastnosti projektu **knihovny** karta zobrazuje platformy, že aktuálně váš projekt cílí.</span><span class="sxs-lookup"><span data-stu-id="eead7-119">On the project properties page, the **Library** tab shows the platforms that your project currently targets.</span></span>

![Vlastnosti projektu pro přenosné knihovny tříd v sadě Visual Studio](media/pcl-project-properties.png)

<span data-ttu-id="eead7-121">Chcete-li přidat nebo odebrat cíle, zvolte **změnu** tlačítko a potom vyberte a zrušte zaškrtnutí příslušných políček.</span><span class="sxs-lookup"><span data-stu-id="eead7-121">To add or remove targets, choose the **Change** button, and then select and clear the appropriate check boxes.</span></span>

<span data-ttu-id="eead7-122">Při změně cíle, které rozhraní API, která jsou k dispozici pro vývoj projektu se změní podle vašeho výběru.</span><span class="sxs-lookup"><span data-stu-id="eead7-122">When you change the targets, the APIs that are available to you for developing your project will change to match your selection.</span></span> <span data-ttu-id="eead7-123">Visual Studio hlásí chyby a upozornění, které mohou nastat v důsledku změny cíle.</span><span class="sxs-lookup"><span data-stu-id="eead7-123">Visual Studio reports the errors and warnings that may occur as a result of the targets changing.</span></span>

<span data-ttu-id="eead7-124">Pokud chcete vyhodnotit přenositelnost vašeho sestavení před provádět změny v sadě Visual Studio, můžete použít [.NET Portability Analyzeru](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b).</span><span class="sxs-lookup"><span data-stu-id="eead7-124">If you want to evaluate the portability of your assemblies before you make changes in Visual Studio, you can use the [.NET Portability Analyzer](https://visualstudiogallery.msdn.microsoft.com/1177943e-cfb7-4822-a8a6-e56c7905292b).</span></span>

## <a name="supported-types-and-members"></a><span data-ttu-id="eead7-125">Podporované typy a členy</span><span class="sxs-lookup"><span data-stu-id="eead7-125">Supported types and members</span></span>

<span data-ttu-id="eead7-126">Typy a členy, které jsou k dispozici v projektech knihovny přenosných tříd jsou omezeny několika faktory kompatibility:</span><span class="sxs-lookup"><span data-stu-id="eead7-126">The types and members that are available in Portable Class Library projects are constrained by several compatibility factors:</span></span>

- <span data-ttu-id="eead7-127">Musí být sdíleny napříč cíli, který jste vybrali.</span><span class="sxs-lookup"><span data-stu-id="eead7-127">They must be shared across the targets you selected.</span></span>

- <span data-ttu-id="eead7-128">Musí chovat podobně napříč těmito cíli.</span><span class="sxs-lookup"><span data-stu-id="eead7-128">The must behave similarly across those targets.</span></span>

- <span data-ttu-id="eead7-129">Nesmí se jednat o kandidáty na vyřazení.</span><span class="sxs-lookup"><span data-stu-id="eead7-129">They must not be candidates for deprecation.</span></span>

- <span data-ttu-id="eead7-130">Musí dávat smysl v přenosném prostředí, zejména v případě nepřenosných podpůrných členů.</span><span class="sxs-lookup"><span data-stu-id="eead7-130">They must make sense in a portable environment, especially when supporting members are not portable.</span></span>

<span data-ttu-id="eead7-131">Pokud člen je podporován v přenosné knihovny tříd a pro vybrané cíle, zobrazí se v projektu v technologii IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="eead7-131">If a member is supported in the Portable Class Library and for your selected targets, it will appear in your project in IntelliSense.</span></span> <span data-ttu-id="eead7-132">Nezapomeňte však, že rozhraní API může nepodporuje v přenosné knihovně tříd, ale, zda můžete použít rozhraní API závisí na cíle, které můžete vybrat.</span><span class="sxs-lookup"><span data-stu-id="eead7-132">However, remember that an API may be supported in the Portable Class Library, but whether you can use the API depends on the targets you select.</span></span>

## <a name="api-differences-in-the-portable-class-library"></a><span data-ttu-id="eead7-133">API – rozdíly v přenosné knihovně tříd</span><span class="sxs-lookup"><span data-stu-id="eead7-133">API differences in the Portable Class Library</span></span>

<span data-ttu-id="eead7-134">Chcete-li sestavení knihovny přenosných tříd kompatibilní na všech podporovaných platformách, změna některých členů se poněkud in Portable Class Library.</span><span class="sxs-lookup"><span data-stu-id="eead7-134">To make Portable Class Library assemblies compatible across all supported platforms, some members have been slightly changed in the Portable Class Library.</span></span>

## <a name="use-the-portable-class-library"></a><span data-ttu-id="eead7-135">Použití přenosné knihovny tříd</span><span class="sxs-lookup"><span data-stu-id="eead7-135">Use the Portable Class Library</span></span>

<span data-ttu-id="eead7-136">Po vytvoření projektu knihovny přenosných tříd něj můžete odkazovat z jiných projektů.</span><span class="sxs-lookup"><span data-stu-id="eead7-136">After you build your Portable Class Library project, you just reference it from other projects.</span></span> <span data-ttu-id="eead7-137">Můžete vytvořit odkaz na projekt nebo konkrétní sestavení, která obsahují třídy, ke kterým chcete získat přístup.</span><span class="sxs-lookup"><span data-stu-id="eead7-137">You can reference either the project or specific assemblies that contain the classes you want to access.</span></span>

<span data-ttu-id="eead7-138">Chcete-li spustit aplikaci, která odkazuje na sestavení knihovny přenosných tříd, požadovaná verze (nebo novější) verze cílových platforem musí být nainstalován v počítači.</span><span class="sxs-lookup"><span data-stu-id="eead7-138">To run an app that references a Portable Class Library assembly, the required version (or later) of the targeted platforms must be installed on your computer.</span></span> <span data-ttu-id="eead7-139">Visual Studio obsahuje všechna požadovaná rozhraní, takže můžete aplikaci bez další úpravy spustit na počítači, který jste použili při vývoji aplikace.</span><span class="sxs-lookup"><span data-stu-id="eead7-139">Visual Studio contains all the required frameworks, so you can run the app without further modification on the computer that you used to develop the app.</span></span>

### <a name="deploy-a-universal-windows-app"></a><span data-ttu-id="eead7-140">Nasazení aplikace pro Universal Windows</span><span class="sxs-lookup"><span data-stu-id="eead7-140">Deploy a Universal Windows app</span></span>

<span data-ttu-id="eead7-141">Při vytváření aplikace Universal Windows, která odkazuje na sestavení knihovny přenosných tříd, všechno, co potřebujete k nasazení aplikace je součástí balíčku aplikace a nejsou vyžadovány žádné další kroky.</span><span class="sxs-lookup"><span data-stu-id="eead7-141">When you create a Universal Windows app that references a Portable Class Library assembly, everything you need to deploy the app is included in the app package, and no further steps are required.</span></span>

### <a name="deploy-a-net-framework-app"></a><span data-ttu-id="eead7-142">Nasazení .NET Framework aplikace</span><span class="sxs-lookup"><span data-stu-id="eead7-142">Deploy a .NET Framework app</span></span>

<span data-ttu-id="eead7-143">Když nasadíte aplikaci .NET Framework, která odkazuje na sestavení knihovny přenosných tříd, je nutné určit závislost na správnou verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="eead7-143">When you deploy a .NET Framework app that references a Portable Class Library assembly, you must specify a dependency on the correct version of the .NET Framework.</span></span> <span data-ttu-id="eead7-144">Určením této závislosti zajistíte instalaci požadované verze společně s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="eead7-144">By specifying this dependency, you ensure that the required version is installed with your app.</span></span>

- <span data-ttu-id="eead7-145">Vytvoření závislosti s nasazením ClickOnce: V **Průzkumníka řešení**, zvolte uzel projektu pro projekt, kterou chcete publikovat.</span><span class="sxs-lookup"><span data-stu-id="eead7-145">To create a dependency with ClickOnce deployment: In **Solution Explorer**, choose the project node for the project you want to publish.</span></span> <span data-ttu-id="eead7-146">(Jedná se o projekt, který odkazuje na projekt knihovny přenosných tříd.) V panelu nabídky zvolte **projektu** > **vlastnosti**a klikněte na tlačítko **publikovat** kartu. Na **publikovat** zvolte **požadavky**.</span><span class="sxs-lookup"><span data-stu-id="eead7-146">(This is the project that references the Portable Class Library project.) On the menu bar, choose **Project** > **Properties**, and then choose the **Publish** tab. On the **Publish** page, choose **Prerequisites**.</span></span> <span data-ttu-id="eead7-147">Jako předpoklad vyberte požadovanou verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="eead7-147">Select the required .NET Framework version as a prerequisite.</span></span>

- <span data-ttu-id="eead7-148">Vytvoření závislosti pomocí projektu instalace: V **Průzkumníka řešení**, vyberte projekt instalace.</span><span class="sxs-lookup"><span data-stu-id="eead7-148">To create a dependency with a setup project: In **Solution Explorer**, choose the setup project.</span></span> <span data-ttu-id="eead7-149">V panelu nabídky zvolte **projektu** > **vlastnosti** > **požadavky**.</span><span class="sxs-lookup"><span data-stu-id="eead7-149">On the menu bar, choose **Project** > **Properties** > **Prerequisites**.</span></span> <span data-ttu-id="eead7-150">Jako předpoklad vyberte požadovanou verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="eead7-150">Select the required .NET Framework version as a prerequisite.</span></span>

<span data-ttu-id="eead7-151">Další informace o nasazení aplikací rozhraní .NET Framework najdete v tématu [Průvodce nasazením pro vývojáře](../../../docs/framework/deployment/deployment-guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="eead7-151">For more information about deploying .NET Framework apps, see [Deployment Guide for Developers](../../../docs/framework/deployment/deployment-guide-for-developers.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="eead7-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eead7-152">See also</span></span>

- [<span data-ttu-id="eead7-153">Používání knihovny přenosných tříd spolu s modelem MVVM</span><span class="sxs-lookup"><span data-stu-id="eead7-153">Using Portable Class Library with MVVM</span></span>](../../../docs/standard/cross-platform/using-portable-class-library-with-model-view-view-model.md)
- [<span data-ttu-id="eead7-154">Prostředky aplikací pro knihovny cílené na více platforem</span><span class="sxs-lookup"><span data-stu-id="eead7-154">App Resources for Libraries That Target Multiple Platforms</span></span>](../../../docs/standard/cross-platform/app-resources-for-libraries-that-target-multiple-platforms.md)
- [<span data-ttu-id="eead7-155">.NET portability Analyzeru</span><span class="sxs-lookup"><span data-stu-id="eead7-155">.NET Portability Analyzer</span></span>](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)
- [<span data-ttu-id="eead7-156">Podpora pro aplikace pro web Windows Store a prostředí Windows Runtime v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="eead7-156">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
- [<span data-ttu-id="eead7-157">Nasazení</span><span class="sxs-lookup"><span data-stu-id="eead7-157">Deployment</span></span>](../../../docs/framework/deployment/net-framework-applications.md)
