---
title: Knihovny architektury
description: Zjistěte, jak knihovny poskytují implementace pro mnoho obecných a specifických typů aplikací, algoritmů a funkcí nástrojů.
author: richlander
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 7b77b6c1-8367-4602-bff3-91e4c05ac643
ms.openlocfilehash: d4444b6d080afa92a4e7fd9f30c5f9358f02f0ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159231"
---
# <a name="framework-libraries"></a>Knihovny architektury

.NET má rozsáhlou standardní sadu knihoven tříd, označovanou jako knihovny základních tříd (základní sada) nebo knihovny tříd architektury (kompletní sada). Tyto knihovny poskytují implementace pro mnoho obecných a specifických typů aplikací, algoritmů a funkcí nástroje. Komerční i komunitní knihovny staví na knihovnách tříd frameworku a poskytují snadno použitelné knihovny pro širokou škálu výpočetních úloh.

Podmnožina těchto knihoven jsou k dispozici s každou implementací rozhraní .NET. Rozhraní API knihovny základních tříd (BCL) se očekávají s libovolnou implementací rozhraní .NET, protože je budou vývojáři chtít i protože je budou potřebovat ke spuštění oblíbené knihovny. Knihovny specifické pro aplikace nad BCL, například ASP.NET, nebudou k dispozici ve všech implementacích rozhraní .NET.

## <a name="base-class-libraries"></a>Knihovny základních tříd

Seznam BCL poskytuje nejzákladnější typy a funkce nástroje a je základem všech ostatních knihoven tříd .NET. Jejich cílem je poskytovat velmi obecné implementace bez jakéhokoli vypojovat jakékoli pracovní zatížení. Výkon je vždy důležité, protože aplikace může upřednostňovat konkrétní zásady, jako je například nízká latence na vysokou propustnost nebo nedostatek paměti na nízké využití procesoru. Tyto knihovny jsou určeny k vysoce výkonné obecně, a přijmout střední-země přístup podle těchto různých obav y výkonu. U většiny aplikací byl tento přístup poměrně úspěšný.

## <a name="primitive-types"></a>Primitivní typy

.NET obsahuje sadu primitivních typů, které se používají (v různé míře) ve všech programech. Tyto typy obsahují data, jako jsou čísla, řetězce, bajty a libovolné objekty. Jazyk C# obsahuje klíčová slova pro tyto typy. Ukázková sada těchto typů je uvedena níže, s odpovídající c# klíčová slova.

* <xref:System.Object?displayProperty=nameWithType>([objekt](../csharp/language-reference/builtin-types/reference-types.md#the-object-type)) - Konečná základní třída v systému typu CLR. Je kořenem hierarchie typů.
* <xref:System.Int16?displayProperty=nameWithType>([krátký](../csharp/language-reference/builtin-types/integral-numeric-types.md)) - 16bitový podepsaný celočíselný typ. Nepodepsaný <xref:System.UInt16> také existuje.
* <xref:System.Int32?displayProperty=nameWithType>([int](../csharp/language-reference/builtin-types/integral-numeric-types.md)) - 32bitový podepsaný celočíselný typ. Nepodepsané [UInt32](../csharp/language-reference/builtin-types/integral-numeric-types.md) také existuje.
* <xref:System.Single?displayProperty=nameWithType>([float](../csharp/language-reference/builtin-types/floating-point-numeric-types.md)) - 32bitový typ s plovoucí desetinnou desetinnou desetinnou tázkou.
* <xref:System.Decimal?displayProperty=nameWithType>([desetinné číslo](../csharp/language-reference/builtin-types/floating-point-numeric-types.md)) - 128bitový desetinný typ.
* <xref:System.Byte?displayProperty=nameWithType>([bajt](../csharp/language-reference/builtin-types/integral-numeric-types.md)) - Nepodepsané 8bitové celé číslo, které představuje bajt paměti.
* <xref:System.Boolean?displayProperty=nameWithType>([bool](../csharp/language-reference/builtin-types/bool.md)) - Logický `true` typ, který představuje nebo `false`.
* <xref:System.Char?displayProperty=nameWithType>([char](../csharp/language-reference/builtin-types/char.md)) - 16bitový číselný typ, který představuje znak Unicode.
* <xref:System.String?displayProperty=nameWithType>([řetězec](../csharp/language-reference/builtin-types/reference-types.md#the-string-type)) - Představuje řadu znaků. Liší se `char[]`od , ale umožňuje `char` indexování do každé osoby v . `string`

## <a name="data-structures"></a>Datové struktury

.NET obsahuje sadu datových struktur, které jsou pracovní koně téměř všech aplikací .NET. Jedná se většinou o sbírky, ale také jiné typy.

* <xref:System.Array>- Představuje pole silně typy objektů, které lze přistupovat index. Má pevnou velikost, podle jeho konstrukce.
* <xref:System.Collections.Generic.List%601>- Představuje silně zadaný seznam objektů, které lze přistupovat podle indexu. Podle potřeby se automaticky mění velikost.
* <xref:System.Collections.Generic.Dictionary%602>- Představuje kolekci hodnot, které jsou indexovány klíčem. Hodnoty lze přistupovat pomocí klíče. Podle potřeby se automaticky mění velikost.
* <xref:System.Uri>- Poskytuje objekt reprezentace identifikátor ujednotného prostředku (URI) a snadný přístup k části identifikátoru URI.
* <xref:System.DateTime>- Představuje okamžik v čase, obvykle vyjádřený jako datum a čas dne.

## <a name="utility-apis"></a>Api pro nástroje

Rozhraní .NET obsahuje sadu rozhraní API nástroje, které poskytují funkce pro mnoho důležitých úkolů.

* <xref:System.Net.Http.HttpClient>- Rozhraní API pro odesílání požadavků HTTP a příjem odpovědí HTTP z prostředku identifikovaného identifikátorem URI.
* <xref:System.Xml.Linq.XDocument>- API pro načítání a dotazování xml dokumentů s LINQ.
* <xref:System.IO.StreamReader>- API pro čtení souborů.
* <xref:System.IO.StreamWriter>- API pro psaní souborů.

## <a name="app-model-apis"></a>Api modelu aplikace

Existuje mnoho modelů aplikací, které lze použít s rozhraním .NET, poskytované několika společnostmi.

* [ASP.NET](https://www.asp.net) – poskytuje webový rámec pro vytváření webů a služeb. Podporováno ve Windows, Linuxu a macOS (závisí na ASP.NET verzi).
