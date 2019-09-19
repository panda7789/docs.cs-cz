---
title: Serializace JSON v .NET
author: tdykstra
ms.author: tdykstra
ms.date: 09/16/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
ms.openlocfilehash: 6cb45fded220b6123dbf4461f5f1cf1c3556ff69
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083097"
---
# <a name="json-serialization-in-net"></a><span data-ttu-id="e9bdb-102">Serializace JSON v .NET</span><span class="sxs-lookup"><span data-stu-id="e9bdb-102">JSON serialization in .NET</span></span>

<span data-ttu-id="e9bdb-103">`System.Text.Json` Obor názvů poskytuje funkce pro serializaci do a z JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="e9bdb-103">The `System.Text.Json` namespace provides functionality for serializing to and from JavaScript Object Notation (JSON).</span></span>

<span data-ttu-id="e9bdb-104">Návrh knihovny zvýrazňuje vysoký výkon a nedostatečné přidělení paměti nad rozsáhlou sadu funkcí.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-104">The library design emphasizes high performance and low memory allocation over an extensive feature set.</span></span> <span data-ttu-id="e9bdb-105">Integrovaná podpora UTF-8 optimalizuje proces čtení a zápisu textu JSON kódovaného jako UTF-8, což je nejbezpečnější kódování dat na webu a soubory na disku.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-105">Built-in UTF-8 support optimizes the process of reading and writing JSON text encoded as UTF-8, which is the most prevalent encoding for data on the web and files on disk.</span></span>

<span data-ttu-id="e9bdb-106">Knihovna také poskytuje třídy pro práci s modelem objektů dokumentů v paměti (DOM).</span><span class="sxs-lookup"><span data-stu-id="e9bdb-106">The library also provides classes for working with an in-memory document object model (DOM).</span></span> <span data-ttu-id="e9bdb-107">Tato funkce umožňuje náhodný přístup jen pro čtení prvků v souboru JSON nebo v řetězci.</span><span class="sxs-lookup"><span data-stu-id="e9bdb-107">This feature enables random read-only access of the elements in a JSON file or string.</span></span> 

## <a name="how-to-get-the-library"></a><span data-ttu-id="e9bdb-108">Jak získat knihovnu</span><span class="sxs-lookup"><span data-stu-id="e9bdb-108">How to get the library</span></span>

* <span data-ttu-id="e9bdb-109">Knihovna je integrovaná jako součást sdíleného rozhraní [.NET Core 3,0](https://aka.ms/netcore3download) .</span><span class="sxs-lookup"><span data-stu-id="e9bdb-109">The library is built-in as part of the [.NET Core 3.0](https://aka.ms/netcore3download) shared framework.</span></span>
* <span data-ttu-id="e9bdb-110">Pro jiná cílová rozhraní nainstalujte balíček NuGet [System. text. JSON](https://www.nuget.org/packages/System.Text.Json) .</span><span class="sxs-lookup"><span data-stu-id="e9bdb-110">For other target frameworks, install the [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet package.</span></span> <span data-ttu-id="e9bdb-111">Balíček podporuje:</span><span class="sxs-lookup"><span data-stu-id="e9bdb-111">The package supports:</span></span>
  * <span data-ttu-id="e9bdb-112">.NET Standard 2,0 a novější verze</span><span class="sxs-lookup"><span data-stu-id="e9bdb-112">.NET Standard 2.0 and later versions</span></span>
  * <span data-ttu-id="e9bdb-113">.NET Framework 4,61 a novější verze</span><span class="sxs-lookup"><span data-stu-id="e9bdb-113">.NET Framework 4.61 and later versions</span></span>
  * <span data-ttu-id="e9bdb-114">.NET Core 2,0 a novější verze</span><span class="sxs-lookup"><span data-stu-id="e9bdb-114">.NET Core 2.0 and later versions</span></span>

## <a name="additional-resources"></a><span data-ttu-id="e9bdb-115">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="e9bdb-115">Additional resources</span></span>

* [<span data-ttu-id="e9bdb-116">Jak používat knihovnu</span><span class="sxs-lookup"><span data-stu-id="e9bdb-116">How to use the library</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="e9bdb-117">Zdrojový kód</span><span class="sxs-lookup"><span data-stu-id="e9bdb-117">Source code</span></span>](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json)
* [<span data-ttu-id="e9bdb-118">Referenční dokumentace rozhraní API</span><span class="sxs-lookup"><span data-stu-id="e9bdb-118">API reference</span></span>](xref:System.Text.Json)
* [<span data-ttu-id="e9bdb-119">Plán</span><span class="sxs-lookup"><span data-stu-id="e9bdb-119">Roadmap</span></span>](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/roadmap/README.md)
* <span data-ttu-id="e9bdb-120">Problémy GitHubu v úložišti dotnet/corefx</span><span class="sxs-lookup"><span data-stu-id="e9bdb-120">GitHub issues in the dotnet/corefx repository</span></span>
  * [<span data-ttu-id="e9bdb-121">Diskuze o vývoji System. text. JSON</span><span class="sxs-lookup"><span data-stu-id="e9bdb-121">Discussion about the development of System.Text.Json</span></span>](https://github.com/dotnet/corefx/issues/33115)
  * [<span data-ttu-id="e9bdb-122">Všechny problémy System. text. JSON</span><span class="sxs-lookup"><span data-stu-id="e9bdb-122">All System.Text.Json issues</span></span>](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json)
  * [<span data-ttu-id="e9bdb-123">Problémy System. text. JSON s označením JSON – funkce-doc</span><span class="sxs-lookup"><span data-stu-id="e9bdb-123">System.Text.Json issues labeled json-functionality-doc</span></span>](https://github.com/dotnet/corefx/labels/json-functionality-doc)
