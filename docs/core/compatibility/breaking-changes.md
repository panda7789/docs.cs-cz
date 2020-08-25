---
title: Změny způsobující chyby
description: Přečtěte si o nejnovějších změnách v každé verzi .NET Core.
ms.date: 11/27/2019
ms.openlocfilehash: 73c1576aa92f0e236ead0ca1a12ac26efcbf3cbe
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88810895"
---
# <a name="breaking-change-selectors"></a><span data-ttu-id="c6a9b-103">Odrušující selektory změn</span><span class="sxs-lookup"><span data-stu-id="c6a9b-103">Breaking change selectors</span></span>

<span data-ttu-id="c6a9b-104">Následující selektory verzí a oblastí poskytují filtrovaný seznam použitelných nezměněných změn mezi různými verzemi .NET Core, ASP.NET Core a EF Core.</span><span class="sxs-lookup"><span data-stu-id="c6a9b-104">The following version and area selectors provide a filtered list of applicable breaking changes between different versions of .NET Core, ASP.NET Core, and EF Core.</span></span> <span data-ttu-id="c6a9b-105">Můžete také procházet články verze na verzi nebo oblasti technologie v obsahu.</span><span class="sxs-lookup"><span data-stu-id="c6a9b-105">You can also browse version-to-version or technology area articles in the table of contents.</span></span>

## <a name="by-version"></a><span data-ttu-id="c6a9b-106">Podle verze</span><span class="sxs-lookup"><span data-stu-id="c6a9b-106">By version</span></span>

<span data-ttu-id="c6a9b-107">Vyberte verzi rozhraní .NET, na kterou aktuálně cílíte, a potom verzi .NET Core, na kterou chcete migrovat:</span><span class="sxs-lookup"><span data-stu-id="c6a9b-107">Select the .NET version that you're currently targeting and then the .NET Core version you wish to migrate to:</span></span>

> [!div class="op_multi_selector" title1="Z cílové verze" title2="Do migrované verze"]
>
> - [(3,1 | 5,0)](3.1-5.0.md)
> - [(3,0 | 3,1)](3.0-3.1.md)
> - [(2,2 | 3,1)](2.2-3.1.md)
> - [(2,2 | 3,0)](2.2-3.0.md)
> - [(2,0 | 2,1)](2.0-2.1.md)
> - [(.NET Framework | jádro .NET Core)](fx-core.md)

## <a name="by-technology-area"></a><span data-ttu-id="c6a9b-116">Podle technologické oblasti</span><span class="sxs-lookup"><span data-stu-id="c6a9b-116">By technology area</span></span>

<span data-ttu-id="c6a9b-117">Vyberte oblast technologie .NET Core, které vás zajímá.</span><span class="sxs-lookup"><span data-stu-id="c6a9b-117">Select the .NET Core technology area that you're interested in.</span></span> <span data-ttu-id="c6a9b-118">Jednotlivé změny jsou seřazené podle verze .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c6a9b-118">Individual changes are ordered by .NET Core version.</span></span>

> [!div class="op_single_selector"]
>
> - [ASP.NET Core](aspnetcore.md)
> - [Analýza kódu](code-analysis.md)
> - [Knihovny Core .NET](corefx.md)
> - [Kryptografie](cryptography.md)
> - [EF Core](/ef/core/what-is-new/ef-core-3.0/breaking-changes)
> - [Globalizace](globalization.md)
> - [Zprostředkovatel komunikace](interop.md)
> - [Sítě](networking.md)
> - [Serializace](serialization.md)
> - [Visual Basic](visualbasic.md)
> - [Windows Forms](winforms.md)

## <a name="github-issues-and-announcements"></a><span data-ttu-id="c6a9b-130">Problémy a oznámení GitHubu</span><span class="sxs-lookup"><span data-stu-id="c6a9b-130">GitHub issues and announcements</span></span>

<span data-ttu-id="c6a9b-131">Můžete si také prohlédnout jednotlivé problémy, které podrobně popisují zásadní změny v .NET Core v následujících úložištích GitHub:</span><span class="sxs-lookup"><span data-stu-id="c6a9b-131">You can also view individual issues that detail the breaking changes introduced in .NET Core in the following GitHub repositories:</span></span>

- <span data-ttu-id="c6a9b-132">Pro .NET Core, úložiště [dotnet/docs](https://github.com/dotnet/docs/issues?q=is%3Aissue+label%3Abreaking-change) .</span><span class="sxs-lookup"><span data-stu-id="c6a9b-132">For .NET Core, the [dotnet/docs](https://github.com/dotnet/docs/issues?q=is%3Aissue+label%3Abreaking-change) repository.</span></span>
- <span data-ttu-id="c6a9b-133">Pro ASP.NET Core úložiště [ASPNET/oznámení](https://github.com/aspnet/Announcements/issues?q=is%3Aissue+is%3Aopen+label%3A%22Breaking+change%22+label%3A3.0.0) .</span><span class="sxs-lookup"><span data-stu-id="c6a9b-133">For ASP.NET Core, the [aspnet/Announcements](https://github.com/aspnet/Announcements/issues?q=is%3Aissue+is%3Aopen+label%3A%22Breaking+change%22+label%3A3.0.0) repository.</span></span>
- <span data-ttu-id="c6a9b-134">Pro Entity Framework Core úložiště [dotnet/efcore](https://github.com/dotnet/efcore/issues?q=is%3Aopen+is%3Aissue+label%3Abreaking-change) .</span><span class="sxs-lookup"><span data-stu-id="c6a9b-134">For Entity Framework Core, the [dotnet/efcore](https://github.com/dotnet/efcore/issues?q=is%3Aopen+is%3Aissue+label%3Abreaking-change) repository.</span></span>

## <a name="see-also"></a><span data-ttu-id="c6a9b-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="c6a9b-135">See also</span></span>

- [<span data-ttu-id="c6a9b-136">Migrace z .NET Framework do .NET Core</span><span class="sxs-lookup"><span data-stu-id="c6a9b-136">Migrate from .NET Framework to .NET Core</span></span>](../porting/index.md)
