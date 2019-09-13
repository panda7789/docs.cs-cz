---
title: Zdrojový odkaz a knihovny .NET
description: Doporučení osvědčených postupů pro použití odkazu na zdroj ke zlepšení ladění pro knihovny .NET.
author: jamesnk
ms.author: mairaw
ms.date: 01/15/2019
ms.openlocfilehash: 7530c984ce4bbe9e40362bd550bec57ac585a550
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928989"
---
# <a name="source-link"></a><span data-ttu-id="02c82-103">Odkaz na zdroj</span><span class="sxs-lookup"><span data-stu-id="02c82-103">Source Link</span></span>

<span data-ttu-id="02c82-104">Zdrojový odkaz je technologie, která umožňuje ladění zdrojového kódu ze sestavení .NET z NuGet vývojářů.</span><span class="sxs-lookup"><span data-stu-id="02c82-104">Source Link is a technology that enables source code debugging of .NET assemblies from NuGet by developers.</span></span> <span data-ttu-id="02c82-105">Zdrojový odkaz se spustí při vytváření balíčku NuGet a vloží metadata správy zdrojového kódu do sestavení a balíčku.</span><span class="sxs-lookup"><span data-stu-id="02c82-105">Source Link executes when creating the NuGet package and embeds source control metadata inside assemblies and the package.</span></span> <span data-ttu-id="02c82-106">Vývojáři, kteří si balíček stáhli a mají povolený odkaz na zdroj v rámci sady Visual Studio, mohou krokovat se svým zdrojovým kódem.</span><span class="sxs-lookup"><span data-stu-id="02c82-106">Developers who download the package and have Source Link enabled in Visual Studio can step into its source code.</span></span> <span data-ttu-id="02c82-107">Odkaz na zdroj poskytuje metadata správy zdrojového kódu pro vytvoření skvělého prostředí ladění.</span><span class="sxs-lookup"><span data-stu-id="02c82-107">Source Link provides source control metadata to create a great debugging experience.</span></span>

## <a name="source-link-demo"></a><span data-ttu-id="02c82-108">Ukázka zdrojového odkazu</span><span class="sxs-lookup"><span data-stu-id="02c82-108">Source Link demo</span></span>

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-source-link"></a><span data-ttu-id="02c82-109">Použití odkazu na zdroj</span><span class="sxs-lookup"><span data-stu-id="02c82-109">Using Source Link</span></span>

<span data-ttu-id="02c82-110">Pokyny pro použití zdrojového odkazu najdete v úložišti GitHub [/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHubu.</span><span class="sxs-lookup"><span data-stu-id="02c82-110">Instructions for using Source Link can be found on the [dotnet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub repository.</span></span>

<span data-ttu-id="02c82-111">Pomocí [Průzkumníka balíčků NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) můžete zkontrolovat, jestli se metadata zdrojového odkazu úspěšně vložila do balíčku.</span><span class="sxs-lookup"><span data-stu-id="02c82-111">You can use [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) to confirm that the Source Link metadata has been successfully embedded in the package.</span></span> <span data-ttu-id="02c82-112">Ověřte, že metadata jsou k dispozici s identifikátorem komentáře a že jsou umístěny soubory. pdb s každou cílovou knihovnou DLL. `Repository`</span><span class="sxs-lookup"><span data-stu-id="02c82-112">Check the `Repository` metadata is present with a comment identifier and that .pdb files are located with each target's .dll.</span></span>

<span data-ttu-id="02c82-113">![Odkaz na zdroj v Průzkumníkovi balíčků NuGet](./media/sourcelink/nuget-package-explorer-sourcelink.png "Odkaz na zdroj v Průzkumníkovi balíčků NuGet")</span><span class="sxs-lookup"><span data-stu-id="02c82-113">![Source Link in NuGet Package Explorer](./media/sourcelink/nuget-package-explorer-sourcelink.png "Source Link in NuGet Package Explorer")</span></span>

<span data-ttu-id="02c82-114">**✔️ zvažte** použití odkazu na zdroj k přidání metadat správy zdrojového kódu do sestavení a balíčků NuGet.</span><span class="sxs-lookup"><span data-stu-id="02c82-114">**✔️ CONSIDER** using Source Link to add source control metadata to your assemblies and NuGet packages.</span></span>

> [!TIP]
> <span data-ttu-id="02c82-115">Můžete dál vylepšit možnosti ladění vývojářů přidáním atributů ladicího programu do vašich typů.</span><span class="sxs-lookup"><span data-stu-id="02c82-115">You can further enhance a developer's debugging experience by adding debugger attributes to your types.</span></span>
>
> * <span data-ttu-id="02c82-116"><xref:System.Diagnostics.DebuggerDisplayAttribute>může přizpůsobit způsob zobrazení třídy nebo pole v oknech proměnných ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="02c82-116"><xref:System.Diagnostics.DebuggerDisplayAttribute> can customize how a class or field is displayed in the debugger variable windows.</span></span>
> * <span data-ttu-id="02c82-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute>instruuje ladicí program, aby procházel kód místo krokování s kódem.</span><span class="sxs-lookup"><span data-stu-id="02c82-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute> instructs the debugger to step through the code instead of stepping into the code.</span></span>
> * <span data-ttu-id="02c82-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute>Určuje, zda je člen zobrazen v oknech proměnných ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="02c82-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute> controls whether a member is displayed in the debugger variable windows.</span></span>

<span data-ttu-id="02c82-119">**✔️ zvažte** publikování souborů symbolů (`*.pdb`).</span><span class="sxs-lookup"><span data-stu-id="02c82-119">**✔️ CONSIDER** publishing symbol files (`*.pdb`).</span></span>

> <span data-ttu-id="02c82-120">Pro nejlepší prostředí ladění by knihovna měla publikovat soubory symbolů a také odkaz použít zdroj.</span><span class="sxs-lookup"><span data-stu-id="02c82-120">For the best debugging experience your library should publish symbol files as well as use Source Link.</span></span> <span data-ttu-id="02c82-121">Další informace o souborech symbolů a balíčcích symbolů najdete v tématu [balíčky symbolů](./nuget.md#symbol-packages).</span><span class="sxs-lookup"><span data-stu-id="02c82-121">For more information about symbol files and symbol packages, see [Symbol packages](./nuget.md#symbol-packages).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="02c82-122">[Předchozí](dependencies.md)Další
>[](publish-nuget-package.md)</span><span class="sxs-lookup"><span data-stu-id="02c82-122">[Previous](dependencies.md)
[Next](publish-nuget-package.md)</span></span>
