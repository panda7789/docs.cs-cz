---
title: Knihovny rozhraní
description: Zjistěte, jak knihoven poskytuje implementaci pro mnoho konkrétní aplikace a obecné typy, algoritmy a funkce nástroj.
author: richlander
ms.author: ronpet
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 7b77b6c1-8367-4602-bff3-91e4c05ac643
ms.openlocfilehash: b3cfc44c430a02ec9ffce75ebff5c8f9cc46505c
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143373"
---
# <a name="framework-libraries"></a>Knihovny rozhraní

.NET má obsáhlém standardní sadu knihoven tříd, označované jako knihovny základních tříd (základní nastavení) nebo knihovny tříd rozhraní framework (úplná sada). Tyto knihovny poskytují implementace pro mnoho konkrétní aplikace a obecné typy, algoritmy a funkce nástroje. Knihovny pro komerční i komunitní postaveny knihovny tříd rozhraní, poskytuje snadno použitelný předem připravená knihovny pro celou sadu výpočetních úloh.

Podmnožinu těchto knihoven jsou součástí každého implementace .NET. Vzhledem k tomu, že se mají vývojáři a protože Oblíbené knihovny budete potřebovat ke spuštění, očekává se základní rozhraní API knihovny tříd (BCL) s žádnou implementaci rozhraní .NET. Knihovny pro konkrétní aplikace nad BCL, jako je ASP.NET, nebudou k dispozici na všech implementace .NET.

## <a name="base-class-libraries"></a>Knihovny základních tříd

BCL poskytuje nejvíce základní typy a funkce nástroje a jsou základní všechny další knihovny tříd .NET. Jejich cílem je poskytovat velmi obecná implementace bez jakékoli posun do jakékoli pracovní zátěže. Výkon je vždy což je důležité, protože aplikace dát přednost konkrétní zásady, třeba s nízkou latencí pro vysoce propustné nebo nedostatku paměti pro využití procesoru s nízkou. Tyto knihovny jsou určeny pro obecně být vysoce výkonné a střední základu přístup podle těchto různých dopadům na výkon. Pro většinu aplikací byl tento přístup úplně úspěšný.

## <a name="primitive-types"></a>Primitivní typy

.NET obsahuje sadu primitivní typy, které se používají (na různých úrovních) ve všech aplikacích. Tyto typy obsahovat data, jako jsou čísla, řetězce, bajtů a libovolné objekty. C# Jazyk obsahuje klíčová slova pro tyto typy. Sadu ukázkových těchto typů je uvedený níže, s odpovídající C# klíčová slova.

* <xref:System.Object?displayProperty=nameWithType> ([objekt](../csharp/language-reference/keywords/object.md)) – systém typů ultimate základní třídy v CLR. Je kořenem hierarchie typu.
* <xref:System.Int16?displayProperty=nameWithType> ([krátký](../csharp/language-reference/keywords/short.md)) – typ celé číslo se znaménkem A 16 bitů. Bez znaménka <xref:System.UInt16> také existuje.
* <xref:System.Int32?displayProperty=nameWithType> ([int](../csharp/language-reference/keywords/int.md)) – typ celé číslo se znaménkem A 32-bit. Bez znaménka [UInt32](../csharp/language-reference/keywords/uint.md) také existuje.
* <xref:System.Single?displayProperty=nameWithType> ([float](../csharp/language-reference/keywords/float.md)) – typ s plovoucí desetinnou čárkou A 32-bit.
* <xref:System.Decimal?displayProperty=nameWithType> ([desítkové](../csharp/language-reference/keywords/decimal.md)) – typ desetinné čárky A 128 bitů.
* <xref:System.Byte?displayProperty=nameWithType> ([bajtů](../csharp/language-reference/keywords/byte.md))-8bitové celé číslo bez znaménka představující bajt paměti.
* <xref:System.Boolean?displayProperty=nameWithType> ([bool](../csharp/language-reference/keywords/bool.md))-logický typ, který představuje `true` nebo `false`.
* <xref:System.Char?displayProperty=nameWithType> ([char](../csharp/language-reference/keywords/char.md))-číselného typu A 16-bit, který představuje znak Unicode.
* <xref:System.String?displayProperty=nameWithType> ([řetězec](../csharp/language-reference/keywords/string.md)) – představuje posloupnost znaků. Jiné než `char[]`, ale umožňuje indexování do jednotlivých `char` v `string`.

## <a name="data-structures"></a>Datové struktury

.NET obsahuje sadu datových struktur, které jsou workhorses téměř všechny aplikace .NET. Tyto jsou většinou kolekce, ale taky obsahovat další typy.

*   <xref:System.Array> -Představuje pole objektů silnými typy, které lze využívat pomocí indexu. Má pevnou velikost, na jeho vytváření.
*   <xref:System.Collections.Generic.List%601> -Představuje výrazným seznamem objektů, které lze využívat pomocí indexu. Velikost automaticky podle potřeby.
*   <xref:System.Collections.Generic.Dictionary%602> -Představuje kolekci hodnot, které jsou indexovány pomocí klíče. Hodnoty lze přistupovat pomocí klíče. Velikost automaticky podle potřeby.
*   <xref:System.Uri> -Poskytuje reprezentaci objektu identifikátor URI (URI) a snadný přístup k různým částem identifikátoru URI.
*   <xref:System.DateTime> -Představuje okamžik v čase, obvykle vyjádřený jako datum a čas.

## <a name="utility-apis"></a>Nástroje rozhraní API

.NET obsahuje sadu nástrojů rozhraní API, která poskytuje funkce pro celou řadu důležitých úloh.

*   <xref:System.Net.Http.HttpClient> – Rozhraní API pro odesílání požadavků HTTP a příjem odpovědí HTTP ze zdroje identifikovaného identifikátorem URI.
*   <xref:System.Xml.Linq.XDocument> – Rozhraní API pro načítání a dotazování na dokumenty XML pomocí jazyka LINQ.
*   <xref:System.IO.StreamReader> – Rozhraní API pro čtení souborů. 
*   <xref:System.IO.StreamWriter> – Rozhraní API pro zápis do souborů.

## <a name="app-model-apis"></a>Model aplikace API

Existuje mnoho – modely aplikace, které lze použít s .NET poskytuje více společností.

*   [ASP.NET](https://www.asp.net) – poskytuje webovou architekturu pro vytváření webů a služeb. Podporováno ve Windows, Linuxu a macOS (závisí na verzi technologie ASP.NET).
