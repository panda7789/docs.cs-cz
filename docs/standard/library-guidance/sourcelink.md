---
title: Zdrojové propojení a knihovny .NET
description: Doporučení osvědčených postupů pro použití zdrojového odkazu ke zlepšení ladění knihoven .NET.
ms.date: 01/15/2019
ms.openlocfilehash: 3d768ae6e79efa23a8402ea37bc34cd58cd52c8c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "76744550"
---
# <a name="source-link"></a><span data-ttu-id="17b24-103">Odkaz na zdroj</span><span class="sxs-lookup"><span data-stu-id="17b24-103">Source Link</span></span>

<span data-ttu-id="17b24-104">Zdrojový odkaz je technologie, která umožňuje ladění zdrojového kódu sestavení .NET z NuGet vývojáři.</span><span class="sxs-lookup"><span data-stu-id="17b24-104">Source Link is a technology that enables source code debugging of .NET assemblies from NuGet by developers.</span></span> <span data-ttu-id="17b24-105">Zdrojový odkaz se spustí při vytváření balíčku NuGet a vloží metadata správy zdrojového kódu uvnitř sestavení a balíček.</span><span class="sxs-lookup"><span data-stu-id="17b24-105">Source Link executes when creating the NuGet package and embeds source control metadata inside assemblies and the package.</span></span> <span data-ttu-id="17b24-106">Vývojáři, kteří si stáhnou balíček a mají povolenou zdrojovou vazbu v sadě Visual Studio, mohou vstoupit do jeho zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="17b24-106">Developers who download the package and have Source Link enabled in Visual Studio can step into its source code.</span></span> <span data-ttu-id="17b24-107">Zdrojový odkaz poskytuje metadata správy zdrojového kódu k vytvoření skvělého prostředí ladění.</span><span class="sxs-lookup"><span data-stu-id="17b24-107">Source Link provides source control metadata to create a great debugging experience.</span></span>

## <a name="source-link-demo"></a><span data-ttu-id="17b24-108">Ukázka zdrojového odkazu</span><span class="sxs-lookup"><span data-stu-id="17b24-108">Source Link demo</span></span>

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-source-link"></a><span data-ttu-id="17b24-109">Použití zdrojového odkazu</span><span class="sxs-lookup"><span data-stu-id="17b24-109">Using Source Link</span></span>

<span data-ttu-id="17b24-110">Pokyny pro použití zdrojového odkazu naleznete v úložišti [GitHub dotnet/sourcelink.](https://github.com/dotnet/sourcelink/blob/master/README.md)</span><span class="sxs-lookup"><span data-stu-id="17b24-110">Instructions for using Source Link can be found on the [dotnet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub repository.</span></span>

<span data-ttu-id="17b24-111">Pomocí [aplikace NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) můžete potvrdit, že metadata zdrojového odkazu byla úspěšně vložena do balíčku.</span><span class="sxs-lookup"><span data-stu-id="17b24-111">You can use [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) to confirm that the Source Link metadata has been successfully embedded in the package.</span></span> <span data-ttu-id="17b24-112">Zkontrolujte, `Repository` zda jsou metadata vybavena identifikátorem potvrzení a že soubory PDB jsou umístěny s dll každého cíle.</span><span class="sxs-lookup"><span data-stu-id="17b24-112">Check the `Repository` metadata is present with a commit identifier and that .pdb files are located with each target's .dll.</span></span>

<span data-ttu-id="17b24-113">![Zdrojový odkaz v Průzkumníku balíčků NuGet](./media/sourcelink/nuget-package-explorer-sourcelink.png "Zdrojový odkaz v Průzkumníku balíčků NuGet")</span><span class="sxs-lookup"><span data-stu-id="17b24-113">![Source Link in NuGet Package Explorer](./media/sourcelink/nuget-package-explorer-sourcelink.png "Source Link in NuGet Package Explorer")</span></span>

<span data-ttu-id="17b24-114">✔️ zvažte použití zdrojového odkazu k přidání metadat správy zdrojového kódu do sestavení a balíčků NuGet.</span><span class="sxs-lookup"><span data-stu-id="17b24-114">✔️ CONSIDER using Source Link to add source control metadata to your assemblies and NuGet packages.</span></span>

> [!TIP]
> <span data-ttu-id="17b24-115">Můžete dále vylepšit vývojáře ladění prostředí přidáním ladicí atributy do typů.</span><span class="sxs-lookup"><span data-stu-id="17b24-115">You can further enhance a developer's debugging experience by adding debugger attributes to your types.</span></span>
>
> * <span data-ttu-id="17b24-116"><xref:System.Diagnostics.DebuggerDisplayAttribute>můžete přizpůsobit způsob zobrazení třídy nebo pole v oknech proměnných ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="17b24-116"><xref:System.Diagnostics.DebuggerDisplayAttribute> can customize how a class or field is displayed in the debugger variable windows.</span></span>
> * <span data-ttu-id="17b24-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute>instruuje ladicí program krokovat kód namísto krokování do kódu.</span><span class="sxs-lookup"><span data-stu-id="17b24-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute> instructs the debugger to step through the code instead of stepping into the code.</span></span>
> * <span data-ttu-id="17b24-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute>určuje, zda je člen zobrazen v oknech proměnných ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="17b24-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute> controls whether a member is displayed in the debugger variable windows.</span></span>

<span data-ttu-id="17b24-119">✔️ ZVAŽTe publikování`*.pdb`souborů symbolů ( ).</span><span class="sxs-lookup"><span data-stu-id="17b24-119">✔️ CONSIDER publishing symbol files (`*.pdb`).</span></span>

> <span data-ttu-id="17b24-120">Pro nejlepší ladění prostředí knihovna by měla publikovat soubory symbolů, stejně jako použít zdrojový odkaz.</span><span class="sxs-lookup"><span data-stu-id="17b24-120">For the best debugging experience your library should publish symbol files as well as use Source Link.</span></span> <span data-ttu-id="17b24-121">Další informace o souborech symbolů a balíčcích symbolů naleznete v [tématu Balíčky symbolů](./nuget.md#symbol-packages).</span><span class="sxs-lookup"><span data-stu-id="17b24-121">For more information about symbol files and symbol packages, see [Symbol packages](./nuget.md#symbol-packages).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="17b24-122">[Předchozí](dependencies.md)
>[další](publish-nuget-package.md)</span><span class="sxs-lookup"><span data-stu-id="17b24-122">[Previous](dependencies.md)
[Next](publish-nuget-package.md)</span></span>
