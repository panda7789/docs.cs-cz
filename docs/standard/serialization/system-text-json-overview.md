---
title: Serializace a deserializace C# JSON pomocí-.NET
ms.date: 01/10/2020
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: c05783963ba521109fb542f247ec9e62fdb5c2d9
ms.sourcegitcommit: dfad244ba549702b649bfef3bb057e33f24a8fb2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/12/2020
ms.locfileid: "75904646"
---
# <a name="json-serialization-and-deserialization-marshalling-and-unmarshalling-in-net---overview"></a><span data-ttu-id="9efe7-102">Serializace a deserializace JSON (zařazení a zrušení zařazení) v .NET – přehled</span><span class="sxs-lookup"><span data-stu-id="9efe7-102">JSON serialization and deserialization (marshalling and unmarshalling) in .NET - overview</span></span>

<span data-ttu-id="9efe7-103">Obor názvů `System.Text.Json` poskytuje funkce pro serializaci a deserializaci z JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="9efe7-103">The `System.Text.Json` namespace provides functionality for serializing to and deserializing from JavaScript Object Notation (JSON).</span></span>

<span data-ttu-id="9efe7-104">Návrh knihovny zvýrazňuje vysoký výkon a nedostatečné přidělení paměti nad rozsáhlou sadu funkcí.</span><span class="sxs-lookup"><span data-stu-id="9efe7-104">The library design emphasizes high performance and low memory allocation over an extensive feature set.</span></span> <span data-ttu-id="9efe7-105">Integrovaná podpora UTF-8 optimalizuje proces čtení a zápisu textu JSON kódovaného jako UTF-8, což je nejbezpečnější kódování dat na webu a soubory na disku.</span><span class="sxs-lookup"><span data-stu-id="9efe7-105">Built-in UTF-8 support optimizes the process of reading and writing JSON text encoded as UTF-8, which is the most prevalent encoding for data on the web and files on disk.</span></span>

<span data-ttu-id="9efe7-106">Knihovna také poskytuje třídy pro práci s modelem objektů dokumentů v paměti (DOM).</span><span class="sxs-lookup"><span data-stu-id="9efe7-106">The library also provides classes for working with an in-memory document object model (DOM).</span></span> <span data-ttu-id="9efe7-107">Tato funkce umožňuje náhodný přístup jen pro čtení prvků v souboru JSON nebo v řetězci.</span><span class="sxs-lookup"><span data-stu-id="9efe7-107">This feature enables random read-only access of the elements in a JSON file or string.</span></span> 

## <a name="how-to-get-the-library"></a><span data-ttu-id="9efe7-108">Jak získat knihovnu</span><span class="sxs-lookup"><span data-stu-id="9efe7-108">How to get the library</span></span>

* <span data-ttu-id="9efe7-109">Knihovna je integrovaná jako součást sdíleného rozhraní [.NET Core 3,0](https://aka.ms/netcore3download) .</span><span class="sxs-lookup"><span data-stu-id="9efe7-109">The library is built-in as part of the [.NET Core 3.0](https://aka.ms/netcore3download) shared framework.</span></span>
* <span data-ttu-id="9efe7-110">Pro jiná cílová rozhraní nainstalujte balíček NuGet [System. text. JSON](https://www.nuget.org/packages/System.Text.Json) .</span><span class="sxs-lookup"><span data-stu-id="9efe7-110">For other target frameworks, install the [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet package.</span></span> <span data-ttu-id="9efe7-111">Balíček podporuje:</span><span class="sxs-lookup"><span data-stu-id="9efe7-111">The package supports:</span></span>
  * <span data-ttu-id="9efe7-112">.NET Standard 2,0 a novější verze</span><span class="sxs-lookup"><span data-stu-id="9efe7-112">.NET Standard 2.0 and later versions</span></span>
  * <span data-ttu-id="9efe7-113">.NET Framework 4.7.2 a novější verze</span><span class="sxs-lookup"><span data-stu-id="9efe7-113">.NET Framework 4.7.2 and later versions</span></span>
  * <span data-ttu-id="9efe7-114">.NET Core 2,0, 2,1 a 2,2</span><span class="sxs-lookup"><span data-stu-id="9efe7-114">.NET Core 2.0, 2.1, and 2.2</span></span>

## <a name="additional-resources"></a><span data-ttu-id="9efe7-115">Další materiály a zdroje informací</span><span class="sxs-lookup"><span data-stu-id="9efe7-115">Additional resources</span></span>

* [<span data-ttu-id="9efe7-116">Jak používat knihovnu</span><span class="sxs-lookup"><span data-stu-id="9efe7-116">How to use the library</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="9efe7-117">Postup migrace z Newtonsoft. JSON</span><span class="sxs-lookup"><span data-stu-id="9efe7-117">How to migrate from Newtonsoft.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="9efe7-118">Zápis převaděčů</span><span class="sxs-lookup"><span data-stu-id="9efe7-118">How to write converters</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="9efe7-119">Zdrojový kód System. text. JSON</span><span class="sxs-lookup"><span data-stu-id="9efe7-119">System.Text.Json source code</span></span>](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json)
* [<span data-ttu-id="9efe7-120">Reference k rozhraní API System. text. JSON</span><span class="sxs-lookup"><span data-stu-id="9efe7-120">System.Text.Json API reference</span></span>](xref:System.Text.Json)
* [<span data-ttu-id="9efe7-121">Reference k rozhraní API System. text. JSON. Serialization</span><span class="sxs-lookup"><span data-stu-id="9efe7-121">System.Text.Json.Serialization API reference</span></span>](xref:System.Text.Json.Serialization)
<!-- * [Roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
