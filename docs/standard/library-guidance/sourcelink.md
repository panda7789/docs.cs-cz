---
title: Knihovny SourceLink a .NET
description: Doporučené osvědčené postupy pro používání SourceLink k vylepšení ladění pro knihovny .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: fa4af47eaa5dd1510640c2bf0ebb2187b56efae0
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49123873"
---
# <a name="sourcelink"></a><span data-ttu-id="cf27d-103">SourceLink</span><span class="sxs-lookup"><span data-stu-id="cf27d-103">SourceLink</span></span>

<span data-ttu-id="cf27d-104">SourceLink je technologie, která umožňuje ladění zdrojového kódu sestavení .NET z Nugetu vývojáři.</span><span class="sxs-lookup"><span data-stu-id="cf27d-104">SourceLink is a technology that enables source code debugging of .NET assemblies from NuGet by developers.</span></span> <span data-ttu-id="cf27d-105">SourceLink provede při vytváření balíčku NuGet a vloží zdrojová metadata ovládací prvek uvnitř sestavení a balíček.</span><span class="sxs-lookup"><span data-stu-id="cf27d-105">SourceLink executes when creating the NuGet package and embeds source control metadata inside assemblies and the package.</span></span> <span data-ttu-id="cf27d-106">Vývojáři, kteří Stáhnout balíček a SourceLink povolené v sadě Visual Studio můžete krokovat s vnořením jeho zdrojový kód.</span><span class="sxs-lookup"><span data-stu-id="cf27d-106">Developers who download the package and have SourceLink enabled in Visual Studio can step into its source code.</span></span> <span data-ttu-id="cf27d-107">SourceLink poskytuje metadata ovládací prvek zdroje k vytvoření skvělé možnosti ladění.</span><span class="sxs-lookup"><span data-stu-id="cf27d-107">SourceLink provides source control metadata to create a great debugging experience.</span></span>

## <a name="sourcelink-demo"></a><span data-ttu-id="cf27d-108">Ukázka SourceLink</span><span class="sxs-lookup"><span data-stu-id="cf27d-108">SourceLink demo</span></span>

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-sourcelink"></a><span data-ttu-id="cf27d-109">Pomocí SourceLink</span><span class="sxs-lookup"><span data-stu-id="cf27d-109">Using SourceLink</span></span>

<span data-ttu-id="cf27d-110">Pokyny k používání SourceLink můžete najít na [dotnet/sourceLink](https://github.com/dotnet/sourcelink/blob/master/README.md) úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="cf27d-110">Instructions for using SourceLink can be found on the [dotnet/sourceLink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub repository.</span></span>

<span data-ttu-id="cf27d-111">Můžete použít [NuGet – Průzkumník balíčků](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) potvrďte, že SourceLink metadata úspěšně vloženy do balíčku.</span><span class="sxs-lookup"><span data-stu-id="cf27d-111">You can use [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) to confirm that the SourceLink metadata has been successfully embedded in the package.</span></span> <span data-ttu-id="cf27d-112">Zkontrolujte `Repository` metadata jsou k dispozici s identifikátorem komentář a soubory PDB se nachází na každém cíli .dll.</span><span class="sxs-lookup"><span data-stu-id="cf27d-112">Check the `Repository` metadata is present with a comment identifier and that .pdb files are located with each target's .dll.</span></span>

<span data-ttu-id="cf27d-113">![V Průzkumníku balíčků NuGet SourceLink](./media/sourcelink/nuget-package-explorer-sourcelink.png "SourceLink v Průzkumníku balíčků NuGet")</span><span class="sxs-lookup"><span data-stu-id="cf27d-113">![SourceLink in NuGet Package Explorer](./media/sourcelink/nuget-package-explorer-sourcelink.png "SourceLink in NuGet Package Explorer")</span></span>

<span data-ttu-id="cf27d-114">**✔️ ZVAŽTE** pomocí SourceLink přidat metadata ovládací prvek zdroje k sestavení a balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="cf27d-114">**✔️ CONSIDER** using SourceLink to add source control metadata to your assemblies and NuGet package.</span></span>

<span data-ttu-id="cf27d-115">**✔️ ZVAŽTE** včetně soubory PDB v balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="cf27d-115">**✔️ CONSIDER** including PDB files in the NuGet package.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="cf27d-116">[Předchozí](./dependencies.md)
[další](./publish-nuget-package.md)</span><span class="sxs-lookup"><span data-stu-id="cf27d-116">[Previous](./dependencies.md)
[Next](./publish-nuget-package.md)</span></span>
