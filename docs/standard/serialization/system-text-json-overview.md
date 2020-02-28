---
title: Serializace a deserializace C# JSON pomocí-.NET
ms.date: 01/10/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 660a2831aa6a807486fc47eae880bcd11347c547
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159543"
---
# <a name="json-serialization-and-deserialization-marshalling-and-unmarshalling-in-net---overview"></a><span data-ttu-id="bb62d-102">Serializace a deserializace JSON (zařazení a zrušení zařazení) v .NET – přehled</span><span class="sxs-lookup"><span data-stu-id="bb62d-102">JSON serialization and deserialization (marshalling and unmarshalling) in .NET - overview</span></span>

<span data-ttu-id="bb62d-103">Obor názvů `System.Text.Json` poskytuje funkce pro serializaci a deserializaci z JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="bb62d-103">The `System.Text.Json` namespace provides functionality for serializing to and deserializing from JavaScript Object Notation (JSON).</span></span>

<span data-ttu-id="bb62d-104">Návrh knihovny zvýrazňuje vysoký výkon a nedostatečné přidělení paměti nad rozsáhlou sadu funkcí.</span><span class="sxs-lookup"><span data-stu-id="bb62d-104">The library design emphasizes high performance and low memory allocation over an extensive feature set.</span></span> <span data-ttu-id="bb62d-105">Integrovaná podpora UTF-8 optimalizuje proces čtení a zápisu textu JSON kódovaného jako UTF-8, což je nejbezpečnější kódování dat na webu a soubory na disku.</span><span class="sxs-lookup"><span data-stu-id="bb62d-105">Built-in UTF-8 support optimizes the process of reading and writing JSON text encoded as UTF-8, which is the most prevalent encoding for data on the web and files on disk.</span></span>

<span data-ttu-id="bb62d-106">Knihovna také poskytuje třídy pro práci s modelem objektů dokumentů v paměti (DOM).</span><span class="sxs-lookup"><span data-stu-id="bb62d-106">The library also provides classes for working with an in-memory document object model (DOM).</span></span> <span data-ttu-id="bb62d-107">Tato funkce umožňuje náhodný přístup jen pro čtení prvků v souboru JSON nebo v řetězci.</span><span class="sxs-lookup"><span data-stu-id="bb62d-107">This feature enables random read-only access of the elements in a JSON file or string.</span></span>

## <a name="how-to-get-the-library"></a><span data-ttu-id="bb62d-108">Jak získat knihovnu</span><span class="sxs-lookup"><span data-stu-id="bb62d-108">How to get the library</span></span>

* <span data-ttu-id="bb62d-109">Knihovna je integrovaná jako součást sdíleného rozhraní [.NET Core 3,0](https://aka.ms/netcore3download) .</span><span class="sxs-lookup"><span data-stu-id="bb62d-109">The library is built-in as part of the [.NET Core 3.0](https://aka.ms/netcore3download) shared framework.</span></span>
* <span data-ttu-id="bb62d-110">Pro jiná cílová rozhraní nainstalujte balíček NuGet [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) .</span><span class="sxs-lookup"><span data-stu-id="bb62d-110">For other target frameworks, install the [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet package.</span></span> <span data-ttu-id="bb62d-111">Balíček podporuje:</span><span class="sxs-lookup"><span data-stu-id="bb62d-111">The package supports:</span></span>
  * <span data-ttu-id="bb62d-112">.NET Standard 2,0 a novější verze</span><span class="sxs-lookup"><span data-stu-id="bb62d-112">.NET Standard 2.0 and later versions</span></span>
  * <span data-ttu-id="bb62d-113">.NET Framework 4.7.2 a novější verze</span><span class="sxs-lookup"><span data-stu-id="bb62d-113">.NET Framework 4.7.2 and later versions</span></span>
  * <span data-ttu-id="bb62d-114">.NET Core 2,0, 2,1 a 2,2</span><span class="sxs-lookup"><span data-stu-id="bb62d-114">.NET Core 2.0, 2.1, and 2.2</span></span>

## <a name="additional-resources"></a><span data-ttu-id="bb62d-115">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="bb62d-115">Additional resources</span></span>

* [<span data-ttu-id="bb62d-116">Jak používat knihovnu</span><span class="sxs-lookup"><span data-stu-id="bb62d-116">How to use the library</span></span>](system-text-json-how-to.md)
* <span data-ttu-id="bb62d-117">[Postup migrace z Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span><span class="sxs-lookup"><span data-stu-id="bb62d-117">[How to migrate from Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span></span>
* [<span data-ttu-id="bb62d-118">Zápis převaděčů</span><span class="sxs-lookup"><span data-stu-id="bb62d-118">How to write converters</span></span>](system-text-json-converters-how-to.md)
* <span data-ttu-id="bb62d-119">[zdrojový kód System.Text.Json](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="bb62d-119">[System.Text.Json source code](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json)</span></span>
* <span data-ttu-id="bb62d-120">[Reference k rozhraní API System.Text.Json](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="bb62d-120">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="bb62d-121">[System.Text.Json. Reference k rozhraní API serializace](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="bb62d-121">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
<!-- * [Roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
