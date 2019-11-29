---
title: Knihovny architektury
description: Přečtěte si, jak knihovny poskytují implementace pro mnoho obecných typů, algoritmů a funkcí, které jsou specifické pro aplikaci.
author: richlander
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 7b77b6c1-8367-4602-bff3-91e4c05ac643
ms.openlocfilehash: bfa9c24ef4cd2c418c91e00318aa47b889078d40
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552661"
---
# <a name="framework-libraries"></a>Knihovny architektury

Rozhraní .NET má obsáhlém standardní sadu knihoven tříd, označované jako základní knihovny tříd (základní sada) nebo knihovny tříd architektury (kompletní sada). Tyto knihovny poskytují implementace pro mnoho obecných a typů specifických pro aplikace, algoritmy a funkce Utility. Komerční i komunitní knihovny sestavují nad knihovnami tříd rozhraní, což usnadňuje použití knihoven mimo polici pro rozsáhlou sadu výpočetních úloh.

Podmnožina těchto knihoven je k dispozici v každé implementaci rozhraní .NET. Rozhraní API knihovny základních tříd (BCL) jsou očekávána implementací rozhraní .NET, protože je budou chtít vývojáři, a protože oblíbené knihovny je budou potřebovat ke spuštění. Knihovny specifické pro aplikaci nad BCL, jako je například ASP.NET, nebudou k dispozici pro všechny implementace rozhraní .NET.

## <a name="base-class-libraries"></a>Základní knihovny tříd

BCL poskytuje nejvíc základních typů a funkcí nástroje a jsou základem všech ostatních knihoven tříd .NET. Jsou zaměřené na poskytování velmi obecných implementací bez jakéhokoli posunutí na jakékoli zatížení. Výkon je vždy důležitým aspektem, protože aplikace mohou upřednostňovat konkrétní zásady, jako je například nízká latence pro vysokou propustnost nebo nízké množství paměti a nízké využití procesoru. Tyto knihovny mají být vysoce výkonné všeobecně a v souladu s těmito různými aspekty týkajícími se výkonu probírají základní přístup. Pro většinu aplikací byl tento přístup poměrně úspěšný.

## <a name="primitive-types"></a>Primitivní typy

Rozhraní .NET zahrnuje sadu primitivních typů, které se používají (do různých stupňů) ve všech programech. Tyto typy obsahují data, jako jsou čísla, řetězce, bajty a libovolné objekty. C# Jazyk obsahuje klíčová slova pro tyto typy. Ukázková sada těchto typů je uvedena níže, se shodnými C# klíčovými slovy.

* <xref:System.Object?displayProperty=nameWithType> ([Object](../csharp/language-reference/builtin-types/reference-types.md#the-object-type)) – nejvyšší základní třída v systému typů CLR. Je kořen hierarchie typů.
* <xref:System.Int16?displayProperty=nameWithType> ([krátký](../csharp/language-reference/builtin-types/integral-numeric-types.md)) – 16bajtový typ signed integer. Nepodepsaný <xref:System.UInt16> také existuje.
* <xref:System.Int32?displayProperty=nameWithType> ([int](../csharp/language-reference/builtin-types/integral-numeric-types.md)) – typ signed integer se znaménkem 32. Neexistuje i typ [UInt32](../csharp/language-reference/builtin-types/integral-numeric-types.md) s nepodepsaným znaménkem.
* <xref:System.Single?displayProperty=nameWithType> ([float](../csharp/language-reference/builtin-types/floating-point-numeric-types.md)) – 32 typ s plovoucí desetinnou čárkou.
* <xref:System.Decimal?displayProperty=nameWithType> ([Decimal](../csharp/language-reference/builtin-types/floating-point-numeric-types.md)) – typ desítkového typu 128.
* <xref:System.Byte?displayProperty=nameWithType> ([Byte](../csharp/language-reference/builtin-types/integral-numeric-types.md)) – 8bitové celé číslo bez znaménka představující bajt paměti.
* <xref:System.Boolean?displayProperty=nameWithType> ([bool](../csharp/language-reference/builtin-types/bool.md)) – typ Boolean reprezentující `true` nebo `false`.
* <xref:System.Char?displayProperty=nameWithType> ([char](../csharp/language-reference/builtin-types/char.md)) – 16bitový číselný typ, který představuje znak Unicode.
* <xref:System.String?displayProperty=nameWithType> ([String](../csharp/language-reference/builtin-types/reference-types.md#the-string-type)) – představuje řadu znaků. Liší se od `char[]`, ale umožňuje indexování do jednotlivých individuálních `char` v `string`.

## <a name="data-structures"></a>Datové struktury

Rozhraní .NET zahrnuje sadu datových struktur, které představují workhorses téměř všech aplikací .NET. Tyto jsou většinou kolekce, ale také obsahují další typy.

* <xref:System.Array> – představuje pole silně typů objektů, ke kterým se dá dostat pomocí indexu. Má pevnou velikost na základě jeho konstrukce.
* <xref:System.Collections.Generic.List%601> – představuje seznam objektů se silným typem, ke kterým se dá dostat pomocí indexu. Automaticky mění velikost podle potřeby.
* <xref:System.Collections.Generic.Dictionary%602> – představuje kolekci hodnot, které jsou indexovány klíčem. K hodnotám je možné přistupovat prostřednictvím klíče. Automaticky mění velikost podle potřeby.
* <xref:System.Uri> – poskytuje reprezentace objektu identifikátoru URI (Uniform Resource) a snadný přístup k částem identifikátoru URI.
* <xref:System.DateTime> – představuje okamžitý čas, obvykle vyjádřený jako datum a denní dobu.

## <a name="utility-apis"></a>Rozhraní API nástrojů

Rozhraní .NET zahrnuje sadu rozhraní API pro nástroj, která poskytují funkce pro mnoho důležitých úloh.

* <xref:System.Net.Http.HttpClient> – rozhraní API pro posílání požadavků HTTP a příjem odpovědí HTTP z prostředku identifikovaného identifikátorem URI.
* <xref:System.Xml.Linq.XDocument> – rozhraní API pro načítání a dotazování dokumentů XML pomocí LINQ.
* <xref:System.IO.StreamReader> – rozhraní API pro čtení souborů. 
* <xref:System.IO.StreamWriter> – rozhraní API pro zápis souborů.

## <a name="app-model-apis"></a>Rozhraní API modelů aplikací

Existuje mnoho modelů aplikací, které je možné používat s .NET, poskytované několika společnostmi.

* [ASP.NET](https://www.asp.net) – poskytuje webové rozhraní pro tvorbu webů a služeb. Podporováno v systémech Windows, Linux a macOS (závisí na verzi ASP.NET).
