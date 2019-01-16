---
title: Knihovny SourceLink a .NET
description: Doporučené osvědčené postupy pro používání SourceLink k vylepšení ladění pro knihovny .NET.
author: jamesnk
ms.author: mairaw
ms.date: 01/15/2019
ms.openlocfilehash: be97f868e2fcfc6c45e4bbac45b033f8914f4d99
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333535"
---
# <a name="sourcelink"></a><span data-ttu-id="56289-103">SourceLink</span><span class="sxs-lookup"><span data-stu-id="56289-103">SourceLink</span></span>

<span data-ttu-id="56289-104">SourceLink je technologie, která umožňuje ladění zdrojového kódu sestavení .NET z Nugetu vývojáři.</span><span class="sxs-lookup"><span data-stu-id="56289-104">SourceLink is a technology that enables source code debugging of .NET assemblies from NuGet by developers.</span></span> <span data-ttu-id="56289-105">SourceLink provede při vytváření balíčku NuGet a vloží zdrojová metadata ovládací prvek uvnitř sestavení a balíček.</span><span class="sxs-lookup"><span data-stu-id="56289-105">SourceLink executes when creating the NuGet package and embeds source control metadata inside assemblies and the package.</span></span> <span data-ttu-id="56289-106">Vývojáři, kteří Stáhnout balíček a SourceLink povolené v sadě Visual Studio můžete krokovat s vnořením jeho zdrojový kód.</span><span class="sxs-lookup"><span data-stu-id="56289-106">Developers who download the package and have SourceLink enabled in Visual Studio can step into its source code.</span></span> <span data-ttu-id="56289-107">SourceLink poskytuje metadata ovládací prvek zdroje k vytvoření skvělé možnosti ladění.</span><span class="sxs-lookup"><span data-stu-id="56289-107">SourceLink provides source control metadata to create a great debugging experience.</span></span>

## <a name="sourcelink-demo"></a><span data-ttu-id="56289-108">Ukázka SourceLink</span><span class="sxs-lookup"><span data-stu-id="56289-108">SourceLink demo</span></span>

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-sourcelink"></a><span data-ttu-id="56289-109">Pomocí SourceLink</span><span class="sxs-lookup"><span data-stu-id="56289-109">Using SourceLink</span></span>

<span data-ttu-id="56289-110">Pokyny k používání SourceLink můžete najít na [dotnet/sourceLink](https://github.com/dotnet/sourcelink/blob/master/README.md) úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="56289-110">Instructions for using SourceLink can be found on the [dotnet/sourceLink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub repository.</span></span>

<span data-ttu-id="56289-111">Můžete použít [NuGet – Průzkumník balíčků](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) potvrďte, že SourceLink metadata úspěšně vloženy do balíčku.</span><span class="sxs-lookup"><span data-stu-id="56289-111">You can use [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) to confirm that the SourceLink metadata has been successfully embedded in the package.</span></span> <span data-ttu-id="56289-112">Zkontrolujte `Repository` metadata jsou k dispozici s identifikátorem komentář a soubory PDB se nachází na každém cíli .dll.</span><span class="sxs-lookup"><span data-stu-id="56289-112">Check the `Repository` metadata is present with a comment identifier and that .pdb files are located with each target's .dll.</span></span>

<span data-ttu-id="56289-113">![V Průzkumníku balíčků NuGet SourceLink](./media/sourcelink/nuget-package-explorer-sourcelink.png "SourceLink v Průzkumníku balíčků NuGet")</span><span class="sxs-lookup"><span data-stu-id="56289-113">![SourceLink in NuGet Package Explorer](./media/sourcelink/nuget-package-explorer-sourcelink.png "SourceLink in NuGet Package Explorer")</span></span>

<span data-ttu-id="56289-114">**✔️ ZVAŽTE** pomocí SourceLink přidat metadata ovládací prvek zdroje k sestavení a balíčky NuGet.</span><span class="sxs-lookup"><span data-stu-id="56289-114">**✔️ CONSIDER** using SourceLink to add source control metadata to your assemblies and NuGet packages.</span></span>

> [!TIP]
> <span data-ttu-id="56289-115">Přidáním atributů ladicího programu na daný typ můžete dále vylepšit možnosti ladění pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="56289-115">You can further enhance a developer's debugging experience by adding debugger attributes to your types.</span></span>
> * <span data-ttu-id="56289-116"><xref:System.Diagnostics.DebuggerDisplayAttribute> můžete přizpůsobit, jak třídy nebo pole se zobrazí v oknech proměnných ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="56289-116"><xref:System.Diagnostics.DebuggerDisplayAttribute> can customize how a class or field is displayed in the debugger variable windows.</span></span>
> * <span data-ttu-id="56289-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute> Dává pokyn ladicímu programu vstup do kódu místo krokování s vnořením do kódu.</span><span class="sxs-lookup"><span data-stu-id="56289-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute> instructs the debugger to step through the code instead of stepping into the code.</span></span>
> * <span data-ttu-id="56289-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute> Určuje, zda člen je zobrazeno v oknech proměnných ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="56289-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute> controls whether a member is displayed in the debugger variable windows.</span></span>

<span data-ttu-id="56289-119">**✔️ ZVAŽTE** publikování souborů symbolů (`*.pdb`).</span><span class="sxs-lookup"><span data-stu-id="56289-119">**✔️ CONSIDER** publishing symbol files (`*.pdb`).</span></span>

> <span data-ttu-id="56289-120">Další informace o soubory symbolů a balíčky symbolů, naleznete v tématu [Symbol balíčky](./nuget.md#symbol-packages).</span><span class="sxs-lookup"><span data-stu-id="56289-120">For more information about symbol files and symbol packages, see [Symbol packages](./nuget.md#symbol-packages).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="56289-121">[Předchozí](dependencies.md)
>[další](publish-nuget-package.md)</span><span class="sxs-lookup"><span data-stu-id="56289-121">[Previous](dependencies.md)
[Next](publish-nuget-package.md)</span></span>
