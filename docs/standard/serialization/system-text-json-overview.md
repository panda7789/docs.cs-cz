---
title: Serializace a deserializace C# JSON pomocí-.NET
ms.date: 09/16/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 6561d5e1580e1170369622ebc7bb330ff4e0964f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705779"
---
# <a name="json-serialization-in-net---overview"></a><span data-ttu-id="eb190-102">Serializace JSON v .NET – přehled</span><span class="sxs-lookup"><span data-stu-id="eb190-102">JSON serialization in .NET - overview</span></span>

<span data-ttu-id="eb190-103">Obor názvů `System.Text.Json` poskytuje funkce pro serializaci a deserializaci z JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="eb190-103">The `System.Text.Json` namespace provides functionality for serializing to and deserializing from JavaScript Object Notation (JSON).</span></span>

<span data-ttu-id="eb190-104">Návrh knihovny zvýrazňuje vysoký výkon a nedostatečné přidělení paměti nad rozsáhlou sadu funkcí.</span><span class="sxs-lookup"><span data-stu-id="eb190-104">The library design emphasizes high performance and low memory allocation over an extensive feature set.</span></span> <span data-ttu-id="eb190-105">Integrovaná podpora UTF-8 optimalizuje proces čtení a zápisu textu JSON kódovaného jako UTF-8, což je nejbezpečnější kódování dat na webu a soubory na disku.</span><span class="sxs-lookup"><span data-stu-id="eb190-105">Built-in UTF-8 support optimizes the process of reading and writing JSON text encoded as UTF-8, which is the most prevalent encoding for data on the web and files on disk.</span></span>

<span data-ttu-id="eb190-106">Knihovna také poskytuje třídy pro práci s modelem objektů dokumentů v paměti (DOM).</span><span class="sxs-lookup"><span data-stu-id="eb190-106">The library also provides classes for working with an in-memory document object model (DOM).</span></span> <span data-ttu-id="eb190-107">Tato funkce umožňuje náhodný přístup jen pro čtení prvků v souboru JSON nebo v řetězci.</span><span class="sxs-lookup"><span data-stu-id="eb190-107">This feature enables random read-only access of the elements in a JSON file or string.</span></span> 

## <a name="how-to-get-the-library"></a><span data-ttu-id="eb190-108">Jak získat knihovnu</span><span class="sxs-lookup"><span data-stu-id="eb190-108">How to get the library</span></span>

* <span data-ttu-id="eb190-109">Knihovna je integrovaná jako součást sdíleného rozhraní [.NET Core 3,0](https://aka.ms/netcore3download) .</span><span class="sxs-lookup"><span data-stu-id="eb190-109">The library is built-in as part of the [.NET Core 3.0](https://aka.ms/netcore3download) shared framework.</span></span>
* <span data-ttu-id="eb190-110">Pro jiná cílová rozhraní nainstalujte balíček NuGet [System. text. JSON](https://www.nuget.org/packages/System.Text.Json) .</span><span class="sxs-lookup"><span data-stu-id="eb190-110">For other target frameworks, install the [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet package.</span></span> <span data-ttu-id="eb190-111">Balíček podporuje:</span><span class="sxs-lookup"><span data-stu-id="eb190-111">The package supports:</span></span>
  * <span data-ttu-id="eb190-112">.NET Standard 2,0 a novější verze</span><span class="sxs-lookup"><span data-stu-id="eb190-112">.NET Standard 2.0 and later versions</span></span>
  * <span data-ttu-id="eb190-113">.NET Framework 4.6.1 a novější verze</span><span class="sxs-lookup"><span data-stu-id="eb190-113">.NET Framework 4.6.1 and later versions</span></span>
  * <span data-ttu-id="eb190-114">.NET Core 2,0, 2,1 a 2,2</span><span class="sxs-lookup"><span data-stu-id="eb190-114">.NET Core 2.0, 2.1, and 2.2</span></span>

## <a name="additional-resources"></a><span data-ttu-id="eb190-115">Další materiály a zdroje informací</span><span class="sxs-lookup"><span data-stu-id="eb190-115">Additional resources</span></span>

* [<span data-ttu-id="eb190-116">Jak používat knihovnu</span><span class="sxs-lookup"><span data-stu-id="eb190-116">How to use the library</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="eb190-117">Zdrojový kód</span><span class="sxs-lookup"><span data-stu-id="eb190-117">Source code</span></span>](https://github.com/dotnet/runtime/tree/master/src/libraries/System.Text.Json)
* [<span data-ttu-id="eb190-118">Referenční dokumentace rozhraní API</span><span class="sxs-lookup"><span data-stu-id="eb190-118">API reference</span></span>](xref:System.Text.Json)
* [<span data-ttu-id="eb190-119">Plán</span><span class="sxs-lookup"><span data-stu-id="eb190-119">Roadmap</span></span>](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Text.Json/roadmap/README.md)
* <span data-ttu-id="eb190-120">Problémy GitHubu v úložišti dotnet/corefx</span><span class="sxs-lookup"><span data-stu-id="eb190-120">GitHub issues in the dotnet/corefx repository</span></span>
  * [<span data-ttu-id="eb190-121">Diskuze o vývoji System. text. JSON</span><span class="sxs-lookup"><span data-stu-id="eb190-121">Discussion about the development of System.Text.Json</span></span>](https://github.com/dotnet/corefx/issues/33115) <!-- TODO: Issues are still not moved to the new repo-->
  * [<span data-ttu-id="eb190-122">Všechny problémy System. text. JSON</span><span class="sxs-lookup"><span data-stu-id="eb190-122">All System.Text.Json issues</span></span>](https://github.com/dotnet/runtime/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json)
  * [<span data-ttu-id="eb190-123">Problémy System. text. JSON s označením JSON – funkce-doc</span><span class="sxs-lookup"><span data-stu-id="eb190-123">System.Text.Json issues labeled json-functionality-doc</span></span>](https://github.com/dotnet/runtime/labels/json-functionality-doc)
