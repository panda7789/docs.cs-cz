---
title: Vývoj napříč platformami pomocí přenosné knihovny tříd
description: Vytvářejte aplikace a knihovny pro více platforem pro platformy Microsoftu rychle a snadno pomocí přenositelného typu projektu knihovny tříd v .NET.
ms.date: 09/17/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Portable Class Library [.NET Framework]
- targeting multiple platforms
- multiple platforms, targeting
ms.assetid: c31e1663-c164-4e65-b66d-d3aa8750a154
ms.openlocfilehash: be1a49f7da7ce98f9e5e3ff8d927ce5230bfa8d8
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769142"
---
# <a name="cross-platform-development-with-the-portable-class-library"></a><span data-ttu-id="7db0e-103">Vývoj pro různé platformy pomocí přenosné knihovny tříd</span><span class="sxs-lookup"><span data-stu-id="7db0e-103">Cross-platform development with the Portable Class Library</span></span>

<span data-ttu-id="7db0e-104">Typ projektu přenositelné knihovny tříd v aplikaci Visual Studio vám pomůže rychle a snadno vytvářet aplikace a knihovny pro více platforem pro platformy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="7db0e-104">The Portable Class Library project type in Visual Studio helps you build cross-platform apps and libraries for Microsoft platforms quickly and easily.</span></span>

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

<span data-ttu-id="7db0e-105">Přenositelné knihovny tříd vám můžou snížit čas a náklady na vývoj a testování kódu.</span><span class="sxs-lookup"><span data-stu-id="7db0e-105">Portable class libraries can help you reduce the time and costs of developing and testing code.</span></span> <span data-ttu-id="7db0e-106">Tento typ projektu použijte k zápisu a sestavení přenosných .NET Framework sestavení a pak na tato sestavení odkazovat z aplikací, které cílí na více platforem, jako je .NET Framework, iOS nebo Mac.</span><span class="sxs-lookup"><span data-stu-id="7db0e-106">Use this project type to write and build portable .NET Framework assemblies, and then reference those assemblies from apps that target multiple platforms such as the .NET Framework, iOS, or Mac.</span></span>

<span data-ttu-id="7db0e-107">I po vytvoření přenositelného projektu knihovny tříd v aplikaci Visual Studio a zahájení jeho vývoje můžete změnit cílové platformy.</span><span class="sxs-lookup"><span data-stu-id="7db0e-107">Even after you create a Portable Class Library project in Visual Studio and start developing it, you can change the target platforms.</span></span> <span data-ttu-id="7db0e-108">Visual Studio zkompiluje vaši knihovnu s novými sestaveními, což vám pomůže identifikovat změny, které je třeba provést ve svém kódu.</span><span class="sxs-lookup"><span data-stu-id="7db0e-108">Visual Studio compiles your library with the new assemblies, which helps you identify the changes you need to make in your code.</span></span>

## <a name="create-a-portable-class-library-project"></a><span data-ttu-id="7db0e-109">Vytvořit projekt přenositelné knihovny tříd</span><span class="sxs-lookup"><span data-stu-id="7db0e-109">Create a Portable Class Library project</span></span>

<span data-ttu-id="7db0e-110">Chcete-li vytvořit přenosnou knihovnu tříd, použijte šablonu poskytnutou v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7db0e-110">To create a Portable Class Library, use the template provided in Visual Studio.</span></span> <span data-ttu-id="7db0e-111">Vytvořte nový projekt (**soubor**  >  **Nový projekt**) a v dialogovém okně **Nový projekt** vyberte programovací jazyk (Visual C# nebo Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="7db0e-111">Create a new project (**File** > **New Project**), and in the **New Project** dialog box, select your programming language (Visual C# or Visual Basic).</span></span> <span data-ttu-id="7db0e-112">Pak vyberte šablonu **Knihovna tříd (starší přenosná verze)** .</span><span class="sxs-lookup"><span data-stu-id="7db0e-112">Then, select the **Class Library (Legacy Portable)** template.</span></span> <span data-ttu-id="7db0e-113">Zadejte název projektu a klikněte na **tlačítko OK**.</span><span class="sxs-lookup"><span data-stu-id="7db0e-113">Enter a name for your project and choose **OK**.</span></span>

<span data-ttu-id="7db0e-114">Zobrazí se dialogové okno **Přidat přenosnou knihovnu tříd** .</span><span class="sxs-lookup"><span data-stu-id="7db0e-114">The **Add Portable Class Library** dialog box appears.</span></span> <span data-ttu-id="7db0e-115">Zvolte dva nebo více cílů a pak zvolte **OK**.</span><span class="sxs-lookup"><span data-stu-id="7db0e-115">Choose two or more targets, and then choose **OK**.</span></span>

![Přidání cílů přenosných knihoven tříd v aplikaci Visual Studio](media/add-portable-class-library.png)

## <a name="change-targets"></a><span data-ttu-id="7db0e-117">Změnit cíle</span><span class="sxs-lookup"><span data-stu-id="7db0e-117">Change targets</span></span>

<span data-ttu-id="7db0e-118">Cílové platformy projektu přenositelné knihovny tříd můžete změnit při jeho vytváření nebo po zahájení vývoje.</span><span class="sxs-lookup"><span data-stu-id="7db0e-118">You can change the target platforms of a portable class library project when you create it or after you've started development.</span></span> <span data-ttu-id="7db0e-119">Chcete-li změnit cíle po vytvoření projektu, v **Průzkumník řešení**otevřete místní nabídku pro váš projekt přenositelné knihovny tříd (nikoli řešení) a pak zvolte možnost **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="7db0e-119">If you want to change the targets after you've created your project, in **Solution Explorer**, open the shortcut menu for your Portable Class Library project (not the solution), and then choose **Properties**.</span></span> <span data-ttu-id="7db0e-120">Na stránce Vlastnosti projektu se na kartě **Knihovna** zobrazují platformy, na které váš projekt aktuálně cílí.</span><span class="sxs-lookup"><span data-stu-id="7db0e-120">On the project properties page, the **Library** tab shows the platforms that your project currently targets.</span></span>

![Vlastnosti projektu pro přenosnou knihovnu tříd v aplikaci Visual Studio](media/pcl-project-properties.png)

<span data-ttu-id="7db0e-122">Chcete-li přidat nebo odebrat cíle, klikněte na tlačítko **změnit** a zaškrtněte políčka a zrušte zaškrtnutí příslušných políček.</span><span class="sxs-lookup"><span data-stu-id="7db0e-122">To add or remove targets, choose the **Change** button, and then select and clear the appropriate check boxes.</span></span>

<span data-ttu-id="7db0e-123">Když změníte cíle, rozhraní API, která jsou k dispozici pro vývoj projektu, se změní tak, aby odpovídala vašemu výběru.</span><span class="sxs-lookup"><span data-stu-id="7db0e-123">When you change the targets, the APIs that are available to you for developing your project will change to match your selection.</span></span> <span data-ttu-id="7db0e-124">Visual Studio hlásí chyby a upozornění, která se mohou vyskytnout v důsledku změny cílů.</span><span class="sxs-lookup"><span data-stu-id="7db0e-124">Visual Studio reports the errors and warnings that may occur as a result of the targets changing.</span></span>

<span data-ttu-id="7db0e-125">Pokud chcete vyhodnotit přenositelnost vašich sestavení před provedením změn v aplikaci Visual Studio, můžete použít [analyzátor přenositelnosti .NET](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer).</span><span class="sxs-lookup"><span data-stu-id="7db0e-125">If you want to evaluate the portability of your assemblies before you make changes in Visual Studio, you can use the [.NET Portability Analyzer](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer).</span></span>

## <a name="supported-types-and-members"></a><span data-ttu-id="7db0e-126">Podporované typy a členy</span><span class="sxs-lookup"><span data-stu-id="7db0e-126">Supported types and members</span></span>

<span data-ttu-id="7db0e-127">Typy a členy, které jsou k dispozici v projektech přenositelné knihovny tříd, jsou omezeny několika faktory kompatibility:</span><span class="sxs-lookup"><span data-stu-id="7db0e-127">The types and members that are available in Portable Class Library projects are constrained by several compatibility factors:</span></span>

- <span data-ttu-id="7db0e-128">Musí být sdíleny napříč vybranými cíli.</span><span class="sxs-lookup"><span data-stu-id="7db0e-128">They must be shared across the targets you selected.</span></span>

- <span data-ttu-id="7db0e-129">Se musí chovat podobně jako u těchto cílů.</span><span class="sxs-lookup"><span data-stu-id="7db0e-129">The must behave similarly across those targets.</span></span>

- <span data-ttu-id="7db0e-130">Nesmí se jednat o kandidáty na vyřazení.</span><span class="sxs-lookup"><span data-stu-id="7db0e-130">They must not be candidates for deprecation.</span></span>

- <span data-ttu-id="7db0e-131">Musí dávat smysl v přenosném prostředí, zejména v případě nepřenosných podpůrných členů.</span><span class="sxs-lookup"><span data-stu-id="7db0e-131">They must make sense in a portable environment, especially when supporting members are not portable.</span></span>

<span data-ttu-id="7db0e-132">Pokud je člen podporovaný v knihovně přenosných tříd a pro vybrané cíle, zobrazí se ve vašem projektu v IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="7db0e-132">If a member is supported in the Portable Class Library and for your selected targets, it will appear in your project in IntelliSense.</span></span> <span data-ttu-id="7db0e-133">Nezapomeňte však, že rozhraní API může být podporováno v přenositelné knihovně tříd, ale zda lze použít rozhraní API závisí na cílích, které vyberete.</span><span class="sxs-lookup"><span data-stu-id="7db0e-133">However, remember that an API may be supported in the Portable Class Library, but whether you can use the API depends on the targets you select.</span></span>

## <a name="api-differences-in-the-portable-class-library"></a><span data-ttu-id="7db0e-134">Rozdíly v rozhraní API v přenosných knihovnách tříd</span><span class="sxs-lookup"><span data-stu-id="7db0e-134">API differences in the Portable Class Library</span></span>

<span data-ttu-id="7db0e-135">Chcete-li vytvořit přenosná sestavení knihovny tříd kompatibilní napříč všemi podporovanými platformami, některé členy byly v přenositelné knihovně tříd mírně změněny.</span><span class="sxs-lookup"><span data-stu-id="7db0e-135">To make Portable Class Library assemblies compatible across all supported platforms, some members have been slightly changed in the Portable Class Library.</span></span>

## <a name="use-the-portable-class-library"></a><span data-ttu-id="7db0e-136">Použití přenositelné knihovny tříd</span><span class="sxs-lookup"><span data-stu-id="7db0e-136">Use the Portable Class Library</span></span>

<span data-ttu-id="7db0e-137">Po sestavení přenositelného projektu knihovny tříd se na něj pouze odkazuje z jiných projektů.</span><span class="sxs-lookup"><span data-stu-id="7db0e-137">After you build your Portable Class Library project, you just reference it from other projects.</span></span> <span data-ttu-id="7db0e-138">Můžete vytvořit odkaz na projekt nebo konkrétní sestavení, která obsahují třídy, ke kterým chcete získat přístup.</span><span class="sxs-lookup"><span data-stu-id="7db0e-138">You can reference either the project or specific assemblies that contain the classes you want to access.</span></span>

<span data-ttu-id="7db0e-139">Chcete-li spustit aplikaci, která odkazuje na přenositelné sestavení knihovny tříd, musí být v počítači nainstalována požadovaná verze (nebo novější) cílových platforem.</span><span class="sxs-lookup"><span data-stu-id="7db0e-139">To run an app that references a Portable Class Library assembly, the required version (or later) of the targeted platforms must be installed on your computer.</span></span> <span data-ttu-id="7db0e-140">Visual Studio obsahuje všechna požadovaná rozhraní, takže můžete aplikaci spustit bez dalších úprav na počítači, který jste použili k vývoji aplikace.</span><span class="sxs-lookup"><span data-stu-id="7db0e-140">Visual Studio contains all the required frameworks, so you can run the app without further modification on the computer that you used to develop the app.</span></span>

### <a name="deploy-a-universal-windows-app"></a><span data-ttu-id="7db0e-141">Nasazení univerzální aplikace pro Windows</span><span class="sxs-lookup"><span data-stu-id="7db0e-141">Deploy a Universal Windows app</span></span>

<span data-ttu-id="7db0e-142">Při vytváření univerzální aplikace pro Windows, která odkazuje na přenositelné sestavení knihovny tříd, je vše, co potřebujete k nasazení aplikace, součástí balíčku aplikace a nejsou potřeba žádné další kroky.</span><span class="sxs-lookup"><span data-stu-id="7db0e-142">When you create a Universal Windows app that references a Portable Class Library assembly, everything you need to deploy the app is included in the app package, and no further steps are required.</span></span>

### <a name="deploy-a-net-framework-app"></a><span data-ttu-id="7db0e-143">Nasazení aplikace .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7db0e-143">Deploy a .NET Framework app</span></span>

<span data-ttu-id="7db0e-144">Když nasadíte aplikaci .NET Framework, která odkazuje na přenositelné sestavení knihovny tříd, je nutné zadat závislost na správné verzi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7db0e-144">When you deploy a .NET Framework app that references a Portable Class Library assembly, you must specify a dependency on the correct version of the .NET Framework.</span></span> <span data-ttu-id="7db0e-145">Určením této závislosti zajistíte instalaci požadované verze společně s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="7db0e-145">By specifying this dependency, you ensure that the required version is installed with your app.</span></span>

- <span data-ttu-id="7db0e-146">Vytvoření závislosti s nasazením ClickOnce: v **Průzkumník řešení**vyberte uzel projektu pro projekt, který chcete publikovat.</span><span class="sxs-lookup"><span data-stu-id="7db0e-146">To create a dependency with ClickOnce deployment: In **Solution Explorer**, choose the project node for the project you want to publish.</span></span> <span data-ttu-id="7db0e-147">(Jedná se o projekt, který odkazuje na přenosný projekt knihovny tříd.) V panelu nabídek zvolte **Project**  >  **vlastnosti**projektu a pak klikněte na kartu **publikovat** . Na stránce **publikovat** vyberte **požadované součásti**.</span><span class="sxs-lookup"><span data-stu-id="7db0e-147">(This is the project that references the Portable Class Library project.) On the menu bar, choose **Project** > **Properties**, and then choose the **Publish** tab. On the **Publish** page, choose **Prerequisites**.</span></span> <span data-ttu-id="7db0e-148">Jako předpoklad vyberte požadovanou verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7db0e-148">Select the required .NET Framework version as a prerequisite.</span></span>

- <span data-ttu-id="7db0e-149">Vytvoření závislosti pomocí projektu instalace: v **Průzkumník řešení**vyberte projekt instalace.</span><span class="sxs-lookup"><span data-stu-id="7db0e-149">To create a dependency with a setup project: In **Solution Explorer**, choose the setup project.</span></span> <span data-ttu-id="7db0e-150">Na panelu nabídek vyberte možnost vlastnosti **projektu**  >  **Properties**  >  **požadavky**.</span><span class="sxs-lookup"><span data-stu-id="7db0e-150">On the menu bar, choose **Project** > **Properties** > **Prerequisites**.</span></span> <span data-ttu-id="7db0e-151">Jako předpoklad vyberte požadovanou verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7db0e-151">Select the required .NET Framework version as a prerequisite.</span></span>

<span data-ttu-id="7db0e-152">Další informace o nasazení aplikací .NET Framework najdete v tématu [Průvodce nasazením pro vývojáře](../../framework/deployment/deployment-guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="7db0e-152">For more information about deploying .NET Framework apps, see [Deployment Guide for Developers](../../framework/deployment/deployment-guide-for-developers.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7db0e-153">Viz také</span><span class="sxs-lookup"><span data-stu-id="7db0e-153">See also</span></span>

- [<span data-ttu-id="7db0e-154">Používání knihovny přenosných tříd spolu s modelem MVVM</span><span class="sxs-lookup"><span data-stu-id="7db0e-154">Using Portable Class Library with MVVM</span></span>](using-portable-class-library-with-model-view-view-model.md)
- [<span data-ttu-id="7db0e-155">Prostředky aplikací pro knihovny, které cílí na více platforem</span><span class="sxs-lookup"><span data-stu-id="7db0e-155">App Resources for Libraries That Target Multiple Platforms</span></span>](app-resources-for-libraries-that-target-multiple-platforms.md)
- [<span data-ttu-id="7db0e-156">Analyzátor přenositelnosti .NET</span><span class="sxs-lookup"><span data-stu-id="7db0e-156">.NET Portability Analyzer</span></span>](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)
- [<span data-ttu-id="7db0e-157">Podpora pro aplikace pro web Windows Store a prostředí Windows Runtime v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7db0e-157">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](support-for-windows-store-apps-and-windows-runtime.md)
- [<span data-ttu-id="7db0e-158">Nasazení</span><span class="sxs-lookup"><span data-stu-id="7db0e-158">Deployment</span></span>](../../framework/deployment/net-framework-applications.md)
