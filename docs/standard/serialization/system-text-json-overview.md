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
# <a name="json-serialization-in-net"></a>Serializace JSON v .NET

`System.Text.Json` Obor názvů poskytuje funkce pro serializaci do a z JavaScript Object Notation (JSON).

Návrh knihovny zvýrazňuje vysoký výkon a nedostatečné přidělení paměti nad rozsáhlou sadu funkcí. Integrovaná podpora UTF-8 optimalizuje proces čtení a zápisu textu JSON kódovaného jako UTF-8, což je nejbezpečnější kódování dat na webu a soubory na disku.

Knihovna také poskytuje třídy pro práci s modelem objektů dokumentů v paměti (DOM). Tato funkce umožňuje náhodný přístup jen pro čtení prvků v souboru JSON nebo v řetězci. 

## <a name="how-to-get-the-library"></a>Jak získat knihovnu

* Knihovna je integrovaná jako součást sdíleného rozhraní [.NET Core 3,0](https://aka.ms/netcore3download) .
* Pro jiná cílová rozhraní nainstalujte balíček NuGet [System. text. JSON](https://www.nuget.org/packages/System.Text.Json) . Balíček podporuje:
  * .NET Standard 2,0 a novější verze
  * .NET Framework 4,61 a novější verze
  * .NET Core 2,0 a novější verze

## <a name="additional-resources"></a>Další zdroje

* [Jak používat knihovnu](system-text-json-how-to.md)
* [Zdrojový kód](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json)
* [Referenční dokumentace rozhraní API](xref:System.Text.Json)
* [Plán](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/roadmap/README.md)
* Problémy GitHubu v úložišti dotnet/corefx
  * [Diskuze o vývoji System. text. JSON](https://github.com/dotnet/corefx/issues/33115)
  * [Všechny problémy System. text. JSON](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json)
  * [Problémy System. text. JSON s označením JSON – funkce-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc)
