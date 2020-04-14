---
title: Vývoj napříč platformami pomocí přenosné knihovny tříd
ms.date: 09/17/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Portable Class Library [.NET Framework]
- targeting multiple platforms
- multiple platforms, targeting
ms.assetid: c31e1663-c164-4e65-b66d-d3aa8750a154
ms.openlocfilehash: 7caddd7361b8f364762fb4357e35cb918ae99263
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242800"
---
# <a name="cross-platform-development-with-the-portable-class-library"></a><span data-ttu-id="ee93e-102">Vývoj napříč platformami s knihovnou přenosných tříd</span><span class="sxs-lookup"><span data-stu-id="ee93e-102">Cross-platform development with the Portable Class Library</span></span>

<span data-ttu-id="ee93e-103">Typ projektu Knihovna přenosných tříd v sadě Visual Studio vám pomůže rychle a snadno vytvářet aplikace a knihovny pro různé platformy pro platformy Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="ee93e-103">The Portable Class Library project type in Visual Studio helps you build cross-platform apps and libraries for Microsoft platforms quickly and easily.</span></span>

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

<span data-ttu-id="ee93e-104">Přenosné knihovny tříd vám mohou pomoci zkrátit čas a náklady na vývoj a testování kódu.</span><span class="sxs-lookup"><span data-stu-id="ee93e-104">Portable class libraries can help you reduce the time and costs of developing and testing code.</span></span> <span data-ttu-id="ee93e-105">Tento typ projektu slouží k zápisu a vytváření přenosných sestavení rozhraní .NET Framework a potom odkazovat na tato sestavení z aplikací, které cílí na více platforem, jako je rozhraní .NET Framework, iOS nebo Mac.</span><span class="sxs-lookup"><span data-stu-id="ee93e-105">Use this project type to write and build portable .NET Framework assemblies, and then reference those assemblies from apps that target multiple platforms such as the .NET Framework, iOS, or Mac.</span></span>

<span data-ttu-id="ee93e-106">I po vytvoření projektu knihovny přenosných tříd v sadě Visual Studio a jeho zahájení jeho vývoje můžete změnit cílové platformy.</span><span class="sxs-lookup"><span data-stu-id="ee93e-106">Even after you create a Portable Class Library project in Visual Studio and start developing it, you can change the target platforms.</span></span> <span data-ttu-id="ee93e-107">Visual Studio zkompiluje vaši knihovnu s novými sestaveními, které vám pomohou identifikovat změny, které je třeba provést v kódu.</span><span class="sxs-lookup"><span data-stu-id="ee93e-107">Visual Studio compiles your library with the new assemblies, which helps you identify the changes you need to make in your code.</span></span>

## <a name="create-a-portable-class-library-project"></a><span data-ttu-id="ee93e-108">Vytvoření projektu knihovny přenosných tříd</span><span class="sxs-lookup"><span data-stu-id="ee93e-108">Create a Portable Class Library project</span></span>

<span data-ttu-id="ee93e-109">Chcete-li vytvořit knihovnu přenosných tříd, použijte šablonu poskytnutou v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ee93e-109">To create a Portable Class Library, use the template provided in Visual Studio.</span></span> <span data-ttu-id="ee93e-110">Vytvořte nový projekt **(Soubor** > **nový projekt**) a v dialogovém okně Nový **projekt** vyberte programovací jazyk (Visual C# nebo Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="ee93e-110">Create a new project (**File** > **New Project**), and in the **New Project** dialog box, select your programming language (Visual C# or Visual Basic).</span></span> <span data-ttu-id="ee93e-111">Potom vyberte šablonu **Knihovna tříd (Starší přenosné).**</span><span class="sxs-lookup"><span data-stu-id="ee93e-111">Then, select the **Class Library (Legacy Portable)** template.</span></span> <span data-ttu-id="ee93e-112">Zadejte název projektu a zvolte **OK**.</span><span class="sxs-lookup"><span data-stu-id="ee93e-112">Enter a name for your project and choose **OK**.</span></span>

<span data-ttu-id="ee93e-113">Zobrazí se dialogové okno **Přidat knihovnu přenosných tříd.**</span><span class="sxs-lookup"><span data-stu-id="ee93e-113">The **Add Portable Class Library** dialog box appears.</span></span> <span data-ttu-id="ee93e-114">Zvolte dva nebo více cílů a pak zvolte **OK**.</span><span class="sxs-lookup"><span data-stu-id="ee93e-114">Choose two or more targets, and then choose **OK**.</span></span>

![Přidání cílů knihovny přenosných tříd v sadě Visual Studio](media/add-portable-class-library.png)

## <a name="change-targets"></a><span data-ttu-id="ee93e-116">Změnit cíle</span><span class="sxs-lookup"><span data-stu-id="ee93e-116">Change targets</span></span>

<span data-ttu-id="ee93e-117">Cílové platformy projektu knihovny přenosných tříd můžete změnit, když jej vytvoříte nebo po spuštění vývoje.</span><span class="sxs-lookup"><span data-stu-id="ee93e-117">You can change the target platforms of a portable class library project when you create it or after you've started development.</span></span> <span data-ttu-id="ee93e-118">Pokud chcete změnit cíle po vytvoření projektu, otevřete v **Průzkumníku řešení**místní nabídku pro projekt knihovny přenosných tříd (nikoli řešení) a pak zvolte **Vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="ee93e-118">If you want to change the targets after you've created your project, in **Solution Explorer**, open the shortcut menu for your Portable Class Library project (not the solution), and then choose **Properties**.</span></span> <span data-ttu-id="ee93e-119">Na stránce vlastností projektu karta **Knihovna** zobrazuje platformy, na které projekt aktuálně cílí.</span><span class="sxs-lookup"><span data-stu-id="ee93e-119">On the project properties page, the **Library** tab shows the platforms that your project currently targets.</span></span>

![Vlastnosti projektu pro přenosnou knihovnu tříd v sadě Visual Studio](media/pcl-project-properties.png)

<span data-ttu-id="ee93e-121">Chcete-li přidat nebo odebrat cíle, zvolte tlačítko **Změnit** a zaškrtněte a zrušte zaškrtnutí příslušných políček.</span><span class="sxs-lookup"><span data-stu-id="ee93e-121">To add or remove targets, choose the **Change** button, and then select and clear the appropriate check boxes.</span></span>

<span data-ttu-id="ee93e-122">Změníte-li cíle, rozhraní API, která jsou k dispozici pro vývoj projektu, se změní tak, aby odpovídala vašemu výběru.</span><span class="sxs-lookup"><span data-stu-id="ee93e-122">When you change the targets, the APIs that are available to you for developing your project will change to match your selection.</span></span> <span data-ttu-id="ee93e-123">Visual Studio hlásí chyby a upozornění, které mohou nastat v důsledku změny cílů.</span><span class="sxs-lookup"><span data-stu-id="ee93e-123">Visual Studio reports the errors and warnings that may occur as a result of the targets changing.</span></span>

<span data-ttu-id="ee93e-124">Pokud chcete vyhodnotit přenositelnost sestavení před prováděním změn v sadě Visual Studio, můžete použít [nástroj .NET Portability Analyzer](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer).</span><span class="sxs-lookup"><span data-stu-id="ee93e-124">If you want to evaluate the portability of your assemblies before you make changes in Visual Studio, you can use the [.NET Portability Analyzer](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer).</span></span>

## <a name="supported-types-and-members"></a><span data-ttu-id="ee93e-125">Podporované typy a členy</span><span class="sxs-lookup"><span data-stu-id="ee93e-125">Supported types and members</span></span>

<span data-ttu-id="ee93e-126">Typy a členy, které jsou k dispozici v projektech knihovny přenosných tříd, jsou omezeny několika faktory kompatibility:</span><span class="sxs-lookup"><span data-stu-id="ee93e-126">The types and members that are available in Portable Class Library projects are constrained by several compatibility factors:</span></span>

- <span data-ttu-id="ee93e-127">Musí být sdíleny mezi vybranými cíli.</span><span class="sxs-lookup"><span data-stu-id="ee93e-127">They must be shared across the targets you selected.</span></span>

- <span data-ttu-id="ee93e-128">Musí se chovat podobně mezi těmito cíli.</span><span class="sxs-lookup"><span data-stu-id="ee93e-128">The must behave similarly across those targets.</span></span>

- <span data-ttu-id="ee93e-129">Nesmí se jednat o kandidáty na vyřazení.</span><span class="sxs-lookup"><span data-stu-id="ee93e-129">They must not be candidates for deprecation.</span></span>

- <span data-ttu-id="ee93e-130">Musí dávat smysl v přenosném prostředí, zejména v případě nepřenosných podpůrných členů.</span><span class="sxs-lookup"><span data-stu-id="ee93e-130">They must make sense in a portable environment, especially when supporting members are not portable.</span></span>

<span data-ttu-id="ee93e-131">Pokud je člen podporován v knihovně přenosných tříd a pro vybrané cíle, zobrazí se v projektu v aplikaci IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="ee93e-131">If a member is supported in the Portable Class Library and for your selected targets, it will appear in your project in IntelliSense.</span></span> <span data-ttu-id="ee93e-132">Nezapomeňte však, že rozhraní API může být podporováno v knihovně přenosných tříd, ale to, zda můžete rozhraní API použít, závisí na vybraných cílech.</span><span class="sxs-lookup"><span data-stu-id="ee93e-132">However, remember that an API may be supported in the Portable Class Library, but whether you can use the API depends on the targets you select.</span></span>

## <a name="api-differences-in-the-portable-class-library"></a><span data-ttu-id="ee93e-133">Rozdíly rozhraní API v knihovně přenosných tříd</span><span class="sxs-lookup"><span data-stu-id="ee93e-133">API differences in the Portable Class Library</span></span>

<span data-ttu-id="ee93e-134">Aby byla sestavení knihovny přenosných tříd kompatibilní na všech podporovaných platformách, některé členy byly v knihovně přenosných tříd mírně změněny.</span><span class="sxs-lookup"><span data-stu-id="ee93e-134">To make Portable Class Library assemblies compatible across all supported platforms, some members have been slightly changed in the Portable Class Library.</span></span>

## <a name="use-the-portable-class-library"></a><span data-ttu-id="ee93e-135">Použití knihovny přenosných tříd</span><span class="sxs-lookup"><span data-stu-id="ee93e-135">Use the Portable Class Library</span></span>

<span data-ttu-id="ee93e-136">Po sestavení projektu knihovny přenosných tříd, stačí odkazovat z jiných projektů.</span><span class="sxs-lookup"><span data-stu-id="ee93e-136">After you build your Portable Class Library project, you just reference it from other projects.</span></span> <span data-ttu-id="ee93e-137">Můžete vytvořit odkaz na projekt nebo konkrétní sestavení, která obsahují třídy, ke kterým chcete získat přístup.</span><span class="sxs-lookup"><span data-stu-id="ee93e-137">You can reference either the project or specific assemblies that contain the classes you want to access.</span></span>

<span data-ttu-id="ee93e-138">Chcete-li spustit aplikaci, která odkazuje na sestavení knihovny přenosných tříd, musí být v počítači nainstalována požadovaná verze (nebo novější) cílových platforem.</span><span class="sxs-lookup"><span data-stu-id="ee93e-138">To run an app that references a Portable Class Library assembly, the required version (or later) of the targeted platforms must be installed on your computer.</span></span> <span data-ttu-id="ee93e-139">Visual Studio obsahuje všechny požadované architektury, takže můžete spustit aplikaci bez dalších úprav v počítači, který jste použili k vývoji aplikace.</span><span class="sxs-lookup"><span data-stu-id="ee93e-139">Visual Studio contains all the required frameworks, so you can run the app without further modification on the computer that you used to develop the app.</span></span>

### <a name="deploy-a-universal-windows-app"></a><span data-ttu-id="ee93e-140">Nasazení univerzální aplikace pro Windows</span><span class="sxs-lookup"><span data-stu-id="ee93e-140">Deploy a Universal Windows app</span></span>

<span data-ttu-id="ee93e-141">Když vytvoříte univerzální aplikaci pro Windows, která odkazuje na sestavení knihovny přenosných tříd, vše, co potřebujete k nasazení aplikace, je zahrnuto v balíčku aplikace a nejsou vyžadovány žádné další kroky.</span><span class="sxs-lookup"><span data-stu-id="ee93e-141">When you create a Universal Windows app that references a Portable Class Library assembly, everything you need to deploy the app is included in the app package, and no further steps are required.</span></span>

### <a name="deploy-a-net-framework-app"></a><span data-ttu-id="ee93e-142">Nasazení aplikace rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ee93e-142">Deploy a .NET Framework app</span></span>

<span data-ttu-id="ee93e-143">Při nasazení aplikace rozhraní .NET Framework, která odkazuje na sestavení knihovny přenosných tříd, je nutné zadat závislost na správné verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ee93e-143">When you deploy a .NET Framework app that references a Portable Class Library assembly, you must specify a dependency on the correct version of the .NET Framework.</span></span> <span data-ttu-id="ee93e-144">Určením této závislosti zajistíte instalaci požadované verze společně s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="ee93e-144">By specifying this dependency, you ensure that the required version is installed with your app.</span></span>

- <span data-ttu-id="ee93e-145">Chcete-li vytvořit závislost pomocí funkce ClickOnce: V **Průzkumníku řešení**, zvolte uzel projektu pro projekt, který chcete publikovat.</span><span class="sxs-lookup"><span data-stu-id="ee93e-145">To create a dependency with ClickOnce deployment: In **Solution Explorer**, choose the project node for the project you want to publish.</span></span> <span data-ttu-id="ee93e-146">(Jedná se o projekt, který odkazuje na projekt knihovny přenosných tříd.) Na řádku nabídek zvolte**Vlastnosti** **projektu** > a pak zvolte kartu **Publikovat.** Na stránce **Publikovat** zvolte **Požadavky**.</span><span class="sxs-lookup"><span data-stu-id="ee93e-146">(This is the project that references the Portable Class Library project.) On the menu bar, choose **Project** > **Properties**, and then choose the **Publish** tab. On the **Publish** page, choose **Prerequisites**.</span></span> <span data-ttu-id="ee93e-147">Jako předpoklad vyberte požadovanou verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ee93e-147">Select the required .NET Framework version as a prerequisite.</span></span>

- <span data-ttu-id="ee93e-148">Chcete-li vytvořit závislost s projektem instalace: V **Průzkumníku řešení**zvolte projekt instalace.</span><span class="sxs-lookup"><span data-stu-id="ee93e-148">To create a dependency with a setup project: In **Solution Explorer**, choose the setup project.</span></span> <span data-ttu-id="ee93e-149">Na řádku nabídek zvolte**Požadavky\*\*\*\*na vlastnosti** >  **projektu** > .</span><span class="sxs-lookup"><span data-stu-id="ee93e-149">On the menu bar, choose **Project** > **Properties** > **Prerequisites**.</span></span> <span data-ttu-id="ee93e-150">Jako předpoklad vyberte požadovanou verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ee93e-150">Select the required .NET Framework version as a prerequisite.</span></span>

<span data-ttu-id="ee93e-151">Další informace o nasazení aplikací rozhraní .NET Framework naleznete v [Příručce k nasazení pro vývojáře](../../../docs/framework/deployment/deployment-guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="ee93e-151">For more information about deploying .NET Framework apps, see [Deployment Guide for Developers](../../../docs/framework/deployment/deployment-guide-for-developers.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ee93e-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="ee93e-152">See also</span></span>

- [<span data-ttu-id="ee93e-153">Používání knihovny přenosných tříd spolu s modelem MVVM</span><span class="sxs-lookup"><span data-stu-id="ee93e-153">Using Portable Class Library with MVVM</span></span>](using-portable-class-library-with-model-view-view-model.md)
- [<span data-ttu-id="ee93e-154">Prostředky aplikací pro knihovny, které cílí na více platforem</span><span class="sxs-lookup"><span data-stu-id="ee93e-154">App Resources for Libraries That Target Multiple Platforms</span></span>](app-resources-for-libraries-that-target-multiple-platforms.md)
- [<span data-ttu-id="ee93e-155">Analyzátor přenosové schopnosti rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="ee93e-155">.NET Portability Analyzer</span></span>](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)
- [<span data-ttu-id="ee93e-156">Podpora pro aplikace pro web Windows Store a prostředí Windows Runtime v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ee93e-156">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
- [<span data-ttu-id="ee93e-157">Nasazení</span><span class="sxs-lookup"><span data-stu-id="ee93e-157">Deployment</span></span>](../../../docs/framework/deployment/net-framework-applications.md)
