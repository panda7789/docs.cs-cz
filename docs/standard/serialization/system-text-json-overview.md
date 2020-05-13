---
title: Serializace a deserializace JSON pomocí C#-.NET
description: Tento přehled popisuje System.Text.Json funkce oboru názvů pro serializaci a deserializaci z formátu JSON v rozhraní .NET.
ms.date: 01/10/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 909d979d46b30939e304af071de65d230febd92d
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83380129"
---
# <a name="json-serialization-and-deserialization-marshalling-and-unmarshalling-in-net---overview"></a><span data-ttu-id="03b67-103">Serializace a deserializace JSON (zařazení a zrušení zařazení) v .NET – přehled</span><span class="sxs-lookup"><span data-stu-id="03b67-103">JSON serialization and deserialization (marshalling and unmarshalling) in .NET - overview</span></span>

<span data-ttu-id="03b67-104">`System.Text.Json`Obor názvů poskytuje funkce pro serializaci a deserializaci z JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="03b67-104">The `System.Text.Json` namespace provides functionality for serializing to and deserializing from JavaScript Object Notation (JSON).</span></span>

<span data-ttu-id="03b67-105">Návrh knihovny zvýrazňuje vysoký výkon a nedostatečné přidělení paměti nad rozsáhlou sadu funkcí.</span><span class="sxs-lookup"><span data-stu-id="03b67-105">The library design emphasizes high performance and low memory allocation over an extensive feature set.</span></span> <span data-ttu-id="03b67-106">Integrovaná podpora UTF-8 optimalizuje proces čtení a zápisu textu JSON kódovaného jako UTF-8, což je nejbezpečnější kódování dat na webu a soubory na disku.</span><span class="sxs-lookup"><span data-stu-id="03b67-106">Built-in UTF-8 support optimizes the process of reading and writing JSON text encoded as UTF-8, which is the most prevalent encoding for data on the web and files on disk.</span></span>

<span data-ttu-id="03b67-107">Knihovna také poskytuje třídy pro práci s modelem objektů dokumentů v paměti (DOM).</span><span class="sxs-lookup"><span data-stu-id="03b67-107">The library also provides classes for working with an in-memory document object model (DOM).</span></span> <span data-ttu-id="03b67-108">Tato funkce umožňuje náhodný přístup jen pro čtení prvků v souboru JSON nebo v řetězci.</span><span class="sxs-lookup"><span data-stu-id="03b67-108">This feature enables random read-only access of the elements in a JSON file or string.</span></span>

## <a name="how-to-get-the-library"></a><span data-ttu-id="03b67-109">Jak získat knihovnu</span><span class="sxs-lookup"><span data-stu-id="03b67-109">How to get the library</span></span>

* <span data-ttu-id="03b67-110">Knihovna je integrovaná jako součást sdíleného rozhraní [.NET Core 3,0](https://aka.ms/netcore3download) .</span><span class="sxs-lookup"><span data-stu-id="03b67-110">The library is built-in as part of the [.NET Core 3.0](https://aka.ms/netcore3download) shared framework.</span></span>
* <span data-ttu-id="03b67-111">Pro jiná cílová rozhraní nainstalujte [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="03b67-111">For other target frameworks, install the [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet package.</span></span> <span data-ttu-id="03b67-112">Balíček podporuje:</span><span class="sxs-lookup"><span data-stu-id="03b67-112">The package supports:</span></span>
  * <span data-ttu-id="03b67-113">.NET Standard 2,0 a novější verze</span><span class="sxs-lookup"><span data-stu-id="03b67-113">.NET Standard 2.0 and later versions</span></span>
  * <span data-ttu-id="03b67-114">.NET Framework 4.7.2 a novější verze</span><span class="sxs-lookup"><span data-stu-id="03b67-114">.NET Framework 4.7.2 and later versions</span></span>
  * <span data-ttu-id="03b67-115">.NET Core 2,0, 2,1 a 2,2</span><span class="sxs-lookup"><span data-stu-id="03b67-115">.NET Core 2.0, 2.1, and 2.2</span></span>

## <a name="additional-resources"></a><span data-ttu-id="03b67-116">Další materiály a zdroje informací</span><span class="sxs-lookup"><span data-stu-id="03b67-116">Additional resources</span></span>

* [<span data-ttu-id="03b67-117">Jak používat knihovnu</span><span class="sxs-lookup"><span data-stu-id="03b67-117">How to use the library</span></span>](system-text-json-how-to.md)
* <span data-ttu-id="03b67-118">[Postup migrace zNewtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span><span class="sxs-lookup"><span data-stu-id="03b67-118">[How to migrate from Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span></span>
* [<span data-ttu-id="03b67-119">Zápis převaděčů</span><span class="sxs-lookup"><span data-stu-id="03b67-119">How to write converters</span></span>](system-text-json-converters-how-to.md)
* <span data-ttu-id="03b67-120">[System.Text.Jsonzdrojový kód](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="03b67-120">[System.Text.Json source code](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json)</span></span>
* <span data-ttu-id="03b67-121">[System.Text.JsonReference k rozhraní API](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="03b67-121">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="03b67-122">[System.Text.Json. Reference k rozhraní API serializace](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="03b67-122">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
<!-- * [Roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
