---
title: Zdrojový odkaz a knihovny .NET
description: Doporučení osvědčených postupů pro použití odkazu na zdroj ke zlepšení ladění pro knihovny .NET.
ms.date: 01/15/2019
ms.openlocfilehash: 0261019087bce8e9d088a90c5e36bdd0b22f556b
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212422"
---
# <a name="source-link"></a><span data-ttu-id="0901b-103">Odkaz na zdroj</span><span class="sxs-lookup"><span data-stu-id="0901b-103">Source Link</span></span>

<span data-ttu-id="0901b-104">Zdrojový odkaz je technologie, která umožňuje ladění zdrojového kódu ze sestavení .NET z NuGet vývojářů.</span><span class="sxs-lookup"><span data-stu-id="0901b-104">Source Link is a technology that enables source code debugging of .NET assemblies from NuGet by developers.</span></span> <span data-ttu-id="0901b-105">Zdrojový odkaz se spustí při vytváření balíčku NuGet a vloží metadata správy zdrojového kódu do sestavení a balíčku.</span><span class="sxs-lookup"><span data-stu-id="0901b-105">Source Link executes when creating the NuGet package and embeds source control metadata inside assemblies and the package.</span></span> <span data-ttu-id="0901b-106">Vývojáři, kteří si balíček stáhli a mají povolený odkaz na zdroj v rámci sady Visual Studio, mohou krokovat se svým zdrojovým kódem.</span><span class="sxs-lookup"><span data-stu-id="0901b-106">Developers who download the package and have Source Link enabled in Visual Studio can step into its source code.</span></span> <span data-ttu-id="0901b-107">Odkaz na zdroj poskytuje metadata správy zdrojového kódu pro vytvoření skvělého prostředí ladění.</span><span class="sxs-lookup"><span data-stu-id="0901b-107">Source Link provides source control metadata to create a great debugging experience.</span></span>

## <a name="source-link-demo"></a><span data-ttu-id="0901b-108">Ukázka zdrojového odkazu</span><span class="sxs-lookup"><span data-stu-id="0901b-108">Source Link demo</span></span>

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-source-link"></a><span data-ttu-id="0901b-109">Použití odkazu na zdroj</span><span class="sxs-lookup"><span data-stu-id="0901b-109">Using Source Link</span></span>

<span data-ttu-id="0901b-110">Pokyny pro použití zdrojového odkazu najdete v úložišti GitHub [/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHubu.</span><span class="sxs-lookup"><span data-stu-id="0901b-110">Instructions for using Source Link can be found on the [dotnet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub repository.</span></span>

<span data-ttu-id="0901b-111">Pomocí [Průzkumníka balíčků NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) můžete zkontrolovat, jestli se metadata zdrojového odkazu úspěšně vložila do balíčku.</span><span class="sxs-lookup"><span data-stu-id="0901b-111">You can use [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) to confirm that the Source Link metadata has been successfully embedded in the package.</span></span> <span data-ttu-id="0901b-112">Ověřte, že `Repository` metadata jsou k dispozici s identifikátorem potvrzení a že jsou umístěny soubory. pdb s každou cílovou knihovnou DLL.</span><span class="sxs-lookup"><span data-stu-id="0901b-112">Check the `Repository` metadata is present with a commit identifier and that .pdb files are located with each target's .dll.</span></span>

<span data-ttu-id="0901b-113">![Odkaz na zdroj v Průzkumníkovi balíčků NuGet](./media/sourcelink/nuget-package-explorer-sourcelink.png "Odkaz na zdroj v Průzkumníkovi balíčků NuGet")</span><span class="sxs-lookup"><span data-stu-id="0901b-113">![Source Link in NuGet Package Explorer](./media/sourcelink/nuget-package-explorer-sourcelink.png "Source Link in NuGet Package Explorer")</span></span>

<span data-ttu-id="0901b-114">✔️ Zvažte použití odkazu na zdroj k přidání metadat správy zdrojového kódu do sestavení a balíčků NuGet.</span><span class="sxs-lookup"><span data-stu-id="0901b-114">✔️ CONSIDER using Source Link to add source control metadata to your assemblies and NuGet packages.</span></span>

> [!TIP]
> <span data-ttu-id="0901b-115">Můžete dál vylepšit možnosti ladění vývojářů přidáním atributů ladicího programu do vašich typů.</span><span class="sxs-lookup"><span data-stu-id="0901b-115">You can further enhance a developer's debugging experience by adding debugger attributes to your types.</span></span>
>
> * <span data-ttu-id="0901b-116"><xref:System.Diagnostics.DebuggerDisplayAttribute>může přizpůsobit způsob zobrazení třídy nebo pole v oknech proměnných ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="0901b-116"><xref:System.Diagnostics.DebuggerDisplayAttribute> can customize how a class or field is displayed in the debugger variable windows.</span></span>
> * <span data-ttu-id="0901b-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute>instruuje ladicí program, aby procházel kód místo krokování s kódem.</span><span class="sxs-lookup"><span data-stu-id="0901b-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute> instructs the debugger to step through the code instead of stepping into the code.</span></span>
> * <span data-ttu-id="0901b-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute>Určuje, zda je člen zobrazen v oknech proměnných ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="0901b-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute> controls whether a member is displayed in the debugger variable windows.</span></span>

<span data-ttu-id="0901b-119">✔️ Zvažte publikování souborů symbolů ( `*.pdb` ).</span><span class="sxs-lookup"><span data-stu-id="0901b-119">✔️ CONSIDER publishing symbol files (`*.pdb`).</span></span>

> <span data-ttu-id="0901b-120">Pro nejlepší prostředí ladění by knihovna měla publikovat soubory symbolů a také odkaz použít zdroj.</span><span class="sxs-lookup"><span data-stu-id="0901b-120">For the best debugging experience your library should publish symbol files as well as use Source Link.</span></span> <span data-ttu-id="0901b-121">Další informace o souborech symbolů a balíčcích symbolů najdete v tématu [balíčky symbolů](./nuget.md#symbol-packages).</span><span class="sxs-lookup"><span data-stu-id="0901b-121">For more information about symbol files and symbol packages, see [Symbol packages](./nuget.md#symbol-packages).</span></span>

<span data-ttu-id="0901b-122">✔️ Zvažte povolení deterministického sestavení.</span><span class="sxs-lookup"><span data-stu-id="0901b-122">✔️ CONSIDER enabling deterministic builds.</span></span>

> <span data-ttu-id="0901b-123">Deterministické sestavení umožňují ověření, že výsledný binární soubor byl sestaven ze zadaného zdroje a poskytuje sledovatelnost.</span><span class="sxs-lookup"><span data-stu-id="0901b-123">Deterministic builds enable verification that the resulting binary was built from the specified source and provide traceability.</span></span> <span data-ttu-id="0901b-124">Další informace o deterministické sestavení a pokyny pro jejich povolení naleznete v tématu [deterministické sestavení](https://github.com/clairernovotny/DeterministicBuilds).</span><span class="sxs-lookup"><span data-stu-id="0901b-124">For more information about deterministic builds and instructions for enabling them, see [Deterministic Builds](https://github.com/clairernovotny/DeterministicBuilds).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="0901b-125">[Předchozí](dependencies.md) 
> [Další](publish-nuget-package.md)</span><span class="sxs-lookup"><span data-stu-id="0901b-125">[Previous](dependencies.md)
[Next](publish-nuget-package.md)</span></span>
