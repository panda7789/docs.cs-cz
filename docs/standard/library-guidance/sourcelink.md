---
title: Knihovny odkazu na zdroj a .NET
description: Doporučené osvědčené postupy pro vylepšení ladění pro knihovny .NET pomocí odkazu na zdroj.
author: jamesnk
ms.author: mairaw
ms.date: 01/15/2019
ms.openlocfilehash: 9d3e2b0b3aedbab150072bf6eebff4acb5f8a0b7
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211676"
---
# <a name="source-link"></a><span data-ttu-id="36db4-103">Odkaz na zdroj</span><span class="sxs-lookup"><span data-stu-id="36db4-103">Source Link</span></span>

<span data-ttu-id="36db4-104">Odkaz na zdroj je technologie, která umožňuje ladění zdrojového kódu sestavení .NET z Nugetu vývojáři.</span><span class="sxs-lookup"><span data-stu-id="36db4-104">Source Link is a technology that enables source code debugging of .NET assemblies from NuGet by developers.</span></span> <span data-ttu-id="36db4-105">Odkaz na zdroj provede při vytváření balíčku NuGet a vloží zdrojová metadata ovládací prvek uvnitř sestavení a balíček.</span><span class="sxs-lookup"><span data-stu-id="36db4-105">Source Link executes when creating the NuGet package and embeds source control metadata inside assemblies and the package.</span></span> <span data-ttu-id="36db4-106">Vývojáři, kteří Stáhnout balíček a odkaz na zdroj povolené v sadě Visual Studio můžete krokovat s vnořením jeho zdrojový kód.</span><span class="sxs-lookup"><span data-stu-id="36db4-106">Developers who download the package and have Source Link enabled in Visual Studio can step into its source code.</span></span> <span data-ttu-id="36db4-107">Zdrojový odkaz poskytuje metadata ovládací prvek zdroje k vytvoření skvělé možnosti ladění.</span><span class="sxs-lookup"><span data-stu-id="36db4-107">Source Link provides source control metadata to create a great debugging experience.</span></span>

## <a name="source-link-demo"></a><span data-ttu-id="36db4-108">Ukázka odkaz zdroje</span><span class="sxs-lookup"><span data-stu-id="36db4-108">Source Link demo</span></span>

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-source-link"></a><span data-ttu-id="36db4-109">Pomocí zdrojového odkazu</span><span class="sxs-lookup"><span data-stu-id="36db4-109">Using Source Link</span></span>

<span data-ttu-id="36db4-110">Pokyny, jak pomocí zdrojového odkazu můžete najít na [dotnet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md) úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="36db4-110">Instructions for using Source Link can be found on the [dotnet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub repository.</span></span>

<span data-ttu-id="36db4-111">Můžete použít [NuGet – Průzkumník balíčků](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) potvrďte, že odkaz na zdroj metadat úspěšně vloženy do balíčku.</span><span class="sxs-lookup"><span data-stu-id="36db4-111">You can use [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) to confirm that the Source Link metadata has been successfully embedded in the package.</span></span> <span data-ttu-id="36db4-112">Zkontrolujte `Repository` metadata jsou k dispozici s identifikátorem komentář a soubory PDB se nachází na každém cíli .dll.</span><span class="sxs-lookup"><span data-stu-id="36db4-112">Check the `Repository` metadata is present with a comment identifier and that .pdb files are located with each target's .dll.</span></span>

<span data-ttu-id="36db4-113">![Zdrojový odkaz v Průzkumníku balíčků NuGet](./media/sourcelink/nuget-package-explorer-sourcelink.png "zdrojový odkaz v Průzkumníku balíčků NuGet")</span><span class="sxs-lookup"><span data-stu-id="36db4-113">![Source Link in NuGet Package Explorer](./media/sourcelink/nuget-package-explorer-sourcelink.png "Source Link in NuGet Package Explorer")</span></span>

<span data-ttu-id="36db4-114">**✔️ ZVAŽTE** pomocí zdrojového odkazu pro přidání metadata ovládací prvek zdroje k sestavení a balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="36db4-114">**✔️ CONSIDER** using Source Link to add source control metadata to your assemblies and NuGet packages.</span></span>

> [!TIP]
> <span data-ttu-id="36db4-115">Přidáním atributů ladicího programu na daný typ můžete dále vylepšit možnosti ladění pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="36db4-115">You can further enhance a developer's debugging experience by adding debugger attributes to your types.</span></span>
> * <span data-ttu-id="36db4-116"><xref:System.Diagnostics.DebuggerDisplayAttribute> můžete přizpůsobit, jak třídy nebo pole se zobrazí v oknech proměnných ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="36db4-116"><xref:System.Diagnostics.DebuggerDisplayAttribute> can customize how a class or field is displayed in the debugger variable windows.</span></span>
> * <span data-ttu-id="36db4-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute> Dává pokyn ladicímu programu vstup do kódu místo krokování s vnořením do kódu.</span><span class="sxs-lookup"><span data-stu-id="36db4-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute> instructs the debugger to step through the code instead of stepping into the code.</span></span>
> * <span data-ttu-id="36db4-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute> Určuje, zda člen je zobrazeno v oknech proměnných ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="36db4-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute> controls whether a member is displayed in the debugger variable windows.</span></span>

<span data-ttu-id="36db4-119">**✔️ ZVAŽTE** publikování souborů symbolů (`*.pdb`).</span><span class="sxs-lookup"><span data-stu-id="36db4-119">**✔️ CONSIDER** publishing symbol files (`*.pdb`).</span></span>

> <span data-ttu-id="36db4-120">Pro nejlepší možnosti ladění knihovny by měl publikovat soubory symbolů také pomocí odkazu na zdroj.</span><span class="sxs-lookup"><span data-stu-id="36db4-120">For the best debugging experience your library should publish symbol files as well as use Source Link.</span></span> <span data-ttu-id="36db4-121">Další informace o soubory symbolů a balíčky symbolů, naleznete v tématu [Symbol balíčky](./nuget.md#symbol-packages).</span><span class="sxs-lookup"><span data-stu-id="36db4-121">For more information about symbol files and symbol packages, see [Symbol packages](./nuget.md#symbol-packages).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="36db4-122">[Předchozí](dependencies.md)
>[další](publish-nuget-package.md)</span><span class="sxs-lookup"><span data-stu-id="36db4-122">[Previous](dependencies.md)
[Next](publish-nuget-package.md)</span></span>
