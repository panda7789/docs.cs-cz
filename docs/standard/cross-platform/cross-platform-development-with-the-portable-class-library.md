---
title: Vývoj napříč platformami pomocí přenosné knihovny tříd
ms.date: 09/17/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Portable Class Library [.NET Framework]
- targeting multiple platforms
- multiple platforms, targeting
ms.assetid: c31e1663-c164-4e65-b66d-d3aa8750a154
ms.openlocfilehash: 033c9bc6e506d0ae2b9f20fedb72d1b7f29e434b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288911"
---
# <a name="cross-platform-development-with-the-portable-class-library"></a><span data-ttu-id="0517d-102">Vývoj pro různé platformy pomocí přenosné knihovny tříd</span><span class="sxs-lookup"><span data-stu-id="0517d-102">Cross-platform development with the Portable Class Library</span></span>

<span data-ttu-id="0517d-103">Typ projektu přenositelné knihovny tříd v aplikaci Visual Studio vám pomůže rychle a snadno vytvářet aplikace a knihovny pro více platforem pro platformy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="0517d-103">The Portable Class Library project type in Visual Studio helps you build cross-platform apps and libraries for Microsoft platforms quickly and easily.</span></span>

[!INCLUDE[standard](../../../includes/pcl-to-standard.md)]

<span data-ttu-id="0517d-104">Přenositelné knihovny tříd vám můžou snížit čas a náklady na vývoj a testování kódu.</span><span class="sxs-lookup"><span data-stu-id="0517d-104">Portable class libraries can help you reduce the time and costs of developing and testing code.</span></span> <span data-ttu-id="0517d-105">Tento typ projektu použijte k zápisu a sestavení přenosných .NET Framework sestavení a pak na tato sestavení odkazovat z aplikací, které cílí na více platforem, jako je .NET Framework, iOS nebo Mac.</span><span class="sxs-lookup"><span data-stu-id="0517d-105">Use this project type to write and build portable .NET Framework assemblies, and then reference those assemblies from apps that target multiple platforms such as the .NET Framework, iOS, or Mac.</span></span>

<span data-ttu-id="0517d-106">I po vytvoření přenositelného projektu knihovny tříd v aplikaci Visual Studio a zahájení jeho vývoje můžete změnit cílové platformy.</span><span class="sxs-lookup"><span data-stu-id="0517d-106">Even after you create a Portable Class Library project in Visual Studio and start developing it, you can change the target platforms.</span></span> <span data-ttu-id="0517d-107">Visual Studio zkompiluje vaši knihovnu s novými sestaveními, což vám pomůže identifikovat změny, které je třeba provést ve svém kódu.</span><span class="sxs-lookup"><span data-stu-id="0517d-107">Visual Studio compiles your library with the new assemblies, which helps you identify the changes you need to make in your code.</span></span>

## <a name="create-a-portable-class-library-project"></a><span data-ttu-id="0517d-108">Vytvořit projekt přenositelné knihovny tříd</span><span class="sxs-lookup"><span data-stu-id="0517d-108">Create a Portable Class Library project</span></span>

<span data-ttu-id="0517d-109">Chcete-li vytvořit přenosnou knihovnu tříd, použijte šablonu poskytnutou v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0517d-109">To create a Portable Class Library, use the template provided in Visual Studio.</span></span> <span data-ttu-id="0517d-110">Vytvořte nový projekt (**soubor**  >  **Nový projekt**) a v dialogovém okně **Nový projekt** vyberte programovací jazyk (Visual C# nebo Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="0517d-110">Create a new project (**File** > **New Project**), and in the **New Project** dialog box, select your programming language (Visual C# or Visual Basic).</span></span> <span data-ttu-id="0517d-111">Pak vyberte šablonu **Knihovna tříd (starší přenosná verze)** .</span><span class="sxs-lookup"><span data-stu-id="0517d-111">Then, select the **Class Library (Legacy Portable)** template.</span></span> <span data-ttu-id="0517d-112">Zadejte název projektu a klikněte na **tlačítko OK**.</span><span class="sxs-lookup"><span data-stu-id="0517d-112">Enter a name for your project and choose **OK**.</span></span>

<span data-ttu-id="0517d-113">Zobrazí se dialogové okno **Přidat přenosnou knihovnu tříd** .</span><span class="sxs-lookup"><span data-stu-id="0517d-113">The **Add Portable Class Library** dialog box appears.</span></span> <span data-ttu-id="0517d-114">Zvolte dva nebo více cílů a pak zvolte **OK**.</span><span class="sxs-lookup"><span data-stu-id="0517d-114">Choose two or more targets, and then choose **OK**.</span></span>

![Přidání cílů přenosných knihoven tříd v aplikaci Visual Studio](media/add-portable-class-library.png)

## <a name="change-targets"></a><span data-ttu-id="0517d-116">Změnit cíle</span><span class="sxs-lookup"><span data-stu-id="0517d-116">Change targets</span></span>

<span data-ttu-id="0517d-117">Cílové platformy projektu přenositelné knihovny tříd můžete změnit při jeho vytváření nebo po zahájení vývoje.</span><span class="sxs-lookup"><span data-stu-id="0517d-117">You can change the target platforms of a portable class library project when you create it or after you've started development.</span></span> <span data-ttu-id="0517d-118">Chcete-li změnit cíle po vytvoření projektu, v **Průzkumník řešení**otevřete místní nabídku pro váš projekt přenositelné knihovny tříd (nikoli řešení) a pak zvolte možnost **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="0517d-118">If you want to change the targets after you've created your project, in **Solution Explorer**, open the shortcut menu for your Portable Class Library project (not the solution), and then choose **Properties**.</span></span> <span data-ttu-id="0517d-119">Na stránce Vlastnosti projektu se na kartě **Knihovna** zobrazují platformy, na které váš projekt aktuálně cílí.</span><span class="sxs-lookup"><span data-stu-id="0517d-119">On the project properties page, the **Library** tab shows the platforms that your project currently targets.</span></span>

![Vlastnosti projektu pro přenosnou knihovnu tříd v aplikaci Visual Studio](media/pcl-project-properties.png)

<span data-ttu-id="0517d-121">Chcete-li přidat nebo odebrat cíle, klikněte na tlačítko **změnit** a zaškrtněte políčka a zrušte zaškrtnutí příslušných políček.</span><span class="sxs-lookup"><span data-stu-id="0517d-121">To add or remove targets, choose the **Change** button, and then select and clear the appropriate check boxes.</span></span>

<span data-ttu-id="0517d-122">Když změníte cíle, rozhraní API, která jsou k dispozici pro vývoj projektu, se změní tak, aby odpovídala vašemu výběru.</span><span class="sxs-lookup"><span data-stu-id="0517d-122">When you change the targets, the APIs that are available to you for developing your project will change to match your selection.</span></span> <span data-ttu-id="0517d-123">Visual Studio hlásí chyby a upozornění, která se mohou vyskytnout v důsledku změny cílů.</span><span class="sxs-lookup"><span data-stu-id="0517d-123">Visual Studio reports the errors and warnings that may occur as a result of the targets changing.</span></span>

<span data-ttu-id="0517d-124">Pokud chcete vyhodnotit přenositelnost vašich sestavení před provedením změn v aplikaci Visual Studio, můžete použít [analyzátor přenositelnosti .NET](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer).</span><span class="sxs-lookup"><span data-stu-id="0517d-124">If you want to evaluate the portability of your assemblies before you make changes in Visual Studio, you can use the [.NET Portability Analyzer](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer).</span></span>

## <a name="supported-types-and-members"></a><span data-ttu-id="0517d-125">Podporované typy a členy</span><span class="sxs-lookup"><span data-stu-id="0517d-125">Supported types and members</span></span>

<span data-ttu-id="0517d-126">Typy a členy, které jsou k dispozici v projektech přenositelné knihovny tříd, jsou omezeny několika faktory kompatibility:</span><span class="sxs-lookup"><span data-stu-id="0517d-126">The types and members that are available in Portable Class Library projects are constrained by several compatibility factors:</span></span>

- <span data-ttu-id="0517d-127">Musí být sdíleny napříč vybranými cíli.</span><span class="sxs-lookup"><span data-stu-id="0517d-127">They must be shared across the targets you selected.</span></span>

- <span data-ttu-id="0517d-128">Se musí chovat podobně jako u těchto cílů.</span><span class="sxs-lookup"><span data-stu-id="0517d-128">The must behave similarly across those targets.</span></span>

- <span data-ttu-id="0517d-129">Nesmí se jednat o kandidáty na vyřazení.</span><span class="sxs-lookup"><span data-stu-id="0517d-129">They must not be candidates for deprecation.</span></span>

- <span data-ttu-id="0517d-130">Musí dávat smysl v přenosném prostředí, zejména v případě nepřenosných podpůrných členů.</span><span class="sxs-lookup"><span data-stu-id="0517d-130">They must make sense in a portable environment, especially when supporting members are not portable.</span></span>

<span data-ttu-id="0517d-131">Pokud je člen podporovaný v knihovně přenosných tříd a pro vybrané cíle, zobrazí se ve vašem projektu v IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="0517d-131">If a member is supported in the Portable Class Library and for your selected targets, it will appear in your project in IntelliSense.</span></span> <span data-ttu-id="0517d-132">Nezapomeňte však, že rozhraní API může být podporováno v přenositelné knihovně tříd, ale zda lze použít rozhraní API závisí na cílích, které vyberete.</span><span class="sxs-lookup"><span data-stu-id="0517d-132">However, remember that an API may be supported in the Portable Class Library, but whether you can use the API depends on the targets you select.</span></span>

## <a name="api-differences-in-the-portable-class-library"></a><span data-ttu-id="0517d-133">Rozdíly v rozhraní API v přenosných knihovnách tříd</span><span class="sxs-lookup"><span data-stu-id="0517d-133">API differences in the Portable Class Library</span></span>

<span data-ttu-id="0517d-134">Chcete-li vytvořit přenosná sestavení knihovny tříd kompatibilní napříč všemi podporovanými platformami, některé členy byly v přenositelné knihovně tříd mírně změněny.</span><span class="sxs-lookup"><span data-stu-id="0517d-134">To make Portable Class Library assemblies compatible across all supported platforms, some members have been slightly changed in the Portable Class Library.</span></span>

## <a name="use-the-portable-class-library"></a><span data-ttu-id="0517d-135">Použití přenositelné knihovny tříd</span><span class="sxs-lookup"><span data-stu-id="0517d-135">Use the Portable Class Library</span></span>

<span data-ttu-id="0517d-136">Po sestavení přenositelného projektu knihovny tříd se na něj pouze odkazuje z jiných projektů.</span><span class="sxs-lookup"><span data-stu-id="0517d-136">After you build your Portable Class Library project, you just reference it from other projects.</span></span> <span data-ttu-id="0517d-137">Můžete vytvořit odkaz na projekt nebo konkrétní sestavení, která obsahují třídy, ke kterým chcete získat přístup.</span><span class="sxs-lookup"><span data-stu-id="0517d-137">You can reference either the project or specific assemblies that contain the classes you want to access.</span></span>

<span data-ttu-id="0517d-138">Chcete-li spustit aplikaci, která odkazuje na přenositelné sestavení knihovny tříd, musí být v počítači nainstalována požadovaná verze (nebo novější) cílových platforem.</span><span class="sxs-lookup"><span data-stu-id="0517d-138">To run an app that references a Portable Class Library assembly, the required version (or later) of the targeted platforms must be installed on your computer.</span></span> <span data-ttu-id="0517d-139">Visual Studio obsahuje všechna požadovaná rozhraní, takže můžete aplikaci spustit bez dalších úprav na počítači, který jste použili k vývoji aplikace.</span><span class="sxs-lookup"><span data-stu-id="0517d-139">Visual Studio contains all the required frameworks, so you can run the app without further modification on the computer that you used to develop the app.</span></span>

### <a name="deploy-a-universal-windows-app"></a><span data-ttu-id="0517d-140">Nasazení univerzální aplikace pro Windows</span><span class="sxs-lookup"><span data-stu-id="0517d-140">Deploy a Universal Windows app</span></span>

<span data-ttu-id="0517d-141">Při vytváření univerzální aplikace pro Windows, která odkazuje na přenositelné sestavení knihovny tříd, je vše, co potřebujete k nasazení aplikace, součástí balíčku aplikace a nejsou potřeba žádné další kroky.</span><span class="sxs-lookup"><span data-stu-id="0517d-141">When you create a Universal Windows app that references a Portable Class Library assembly, everything you need to deploy the app is included in the app package, and no further steps are required.</span></span>

### <a name="deploy-a-net-framework-app"></a><span data-ttu-id="0517d-142">Nasazení aplikace .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0517d-142">Deploy a .NET Framework app</span></span>

<span data-ttu-id="0517d-143">Když nasadíte aplikaci .NET Framework, která odkazuje na přenositelné sestavení knihovny tříd, je nutné zadat závislost na správné verzi .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0517d-143">When you deploy a .NET Framework app that references a Portable Class Library assembly, you must specify a dependency on the correct version of the .NET Framework.</span></span> <span data-ttu-id="0517d-144">Určením této závislosti zajistíte instalaci požadované verze společně s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="0517d-144">By specifying this dependency, you ensure that the required version is installed with your app.</span></span>

- <span data-ttu-id="0517d-145">Vytvoření závislosti s nasazením ClickOnce: v **Průzkumník řešení**vyberte uzel projektu pro projekt, který chcete publikovat.</span><span class="sxs-lookup"><span data-stu-id="0517d-145">To create a dependency with ClickOnce deployment: In **Solution Explorer**, choose the project node for the project you want to publish.</span></span> <span data-ttu-id="0517d-146">(Jedná se o projekt, který odkazuje na přenosný projekt knihovny tříd.) V panelu nabídek zvolte **Project**  >  **vlastnosti**projektu a pak klikněte na kartu **publikovat** . Na stránce **publikovat** vyberte **požadované součásti**.</span><span class="sxs-lookup"><span data-stu-id="0517d-146">(This is the project that references the Portable Class Library project.) On the menu bar, choose **Project** > **Properties**, and then choose the **Publish** tab. On the **Publish** page, choose **Prerequisites**.</span></span> <span data-ttu-id="0517d-147">Jako předpoklad vyberte požadovanou verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0517d-147">Select the required .NET Framework version as a prerequisite.</span></span>

- <span data-ttu-id="0517d-148">Vytvoření závislosti pomocí projektu instalace: v **Průzkumník řešení**vyberte projekt instalace.</span><span class="sxs-lookup"><span data-stu-id="0517d-148">To create a dependency with a setup project: In **Solution Explorer**, choose the setup project.</span></span> <span data-ttu-id="0517d-149">Na panelu nabídek vyberte možnost vlastnosti **projektu**  >  **Properties**  >  **požadavky**.</span><span class="sxs-lookup"><span data-stu-id="0517d-149">On the menu bar, choose **Project** > **Properties** > **Prerequisites**.</span></span> <span data-ttu-id="0517d-150">Jako předpoklad vyberte požadovanou verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0517d-150">Select the required .NET Framework version as a prerequisite.</span></span>

<span data-ttu-id="0517d-151">Další informace o nasazení aplikací .NET Framework najdete v tématu [Průvodce nasazením pro vývojáře](../../framework/deployment/deployment-guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="0517d-151">For more information about deploying .NET Framework apps, see [Deployment Guide for Developers](../../framework/deployment/deployment-guide-for-developers.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0517d-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="0517d-152">See also</span></span>

- [<span data-ttu-id="0517d-153">Používání knihovny přenosných tříd spolu s modelem MVVM</span><span class="sxs-lookup"><span data-stu-id="0517d-153">Using Portable Class Library with MVVM</span></span>](using-portable-class-library-with-model-view-view-model.md)
- [<span data-ttu-id="0517d-154">Prostředky aplikací pro knihovny, které cílí na více platforem</span><span class="sxs-lookup"><span data-stu-id="0517d-154">App Resources for Libraries That Target Multiple Platforms</span></span>](app-resources-for-libraries-that-target-multiple-platforms.md)
- [<span data-ttu-id="0517d-155">Analyzátor přenositelnosti .NET</span><span class="sxs-lookup"><span data-stu-id="0517d-155">.NET Portability Analyzer</span></span>](https://marketplace.visualstudio.com/items?itemName=ConnieYau.NETPortabilityAnalyzer)
- [<span data-ttu-id="0517d-156">Podpora pro aplikace pro web Windows Store a prostředí Windows Runtime v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0517d-156">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](support-for-windows-store-apps-and-windows-runtime.md)
- [<span data-ttu-id="0517d-157">Nasazení</span><span class="sxs-lookup"><span data-stu-id="0517d-157">Deployment</span></span>](../../framework/deployment/net-framework-applications.md)
