---
title: Framework knihovny
description: "Zjistěte, jak knihovny poskytovat implementace pro mnoho konkrétní aplikace a obecné typy, algoritmy a funkce nástroj."
keywords: "Rozhraní .NET, .NET core"
author: richlander
ms.author: ronpet
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 7b77b6c1-8367-4602-bff3-91e4c05ac643
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 9e792eefa551dacda7c01bb03a6035647de04a35
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="framework-libraries"></a>Framework knihovny

Rozhraní .NET má obsáhlou standardní sadu knihovny tříd, označuje jako základní třída knihovny (základní sady) nebo knihovny tříd framework (kompletní sada). Tyto knihovny poskytují implementace pro mnoho konkrétní aplikace a obecné typy, algoritmy a funkce nástroj. Sestavení knihovny komerční i komunity nad knihovny tříd framework, poskytuje snadno použitelný dodávaných knihovny pro celou sadu výpočetních úloh.

Podmnožinu tyto knihovny jsou k dispozici s každou implementace rozhraní .NET. Protože vývojáři budou chcete a protože Oblíbené knihovny budete potřebovat, aby se spouštěly, očekává se základní třídy knihovny (BCL) rozhraní API s žádnou implementaci rozhraní .NET. Konkrétní aplikaci knihovny výše BCL, jako je ASP.NET, nebudete mít k dispozici na všech implementace rozhraní .NET.

## <a name="base-class-libraries"></a>Základní třída knihovny

BCL poskytuje nejvíc základní typy a funkce nástroje a jsou základem všechny ostatní knihovny tříd rozhraní .NET. Jejich cílem je poskytovat velmi obecné implementace bez jakékoli odchylka žádné zatížení. Výkon je vždy důležitý faktor, vzhledem k tomu, že aplikace preferovat konkrétní zásady, například s nízkou latencí pro vysokou propustností nebo nedostatku paměti pro využití procesoru nízká. Tyto knihovny jsou určeny k obecně být vysoce výkonné a střední základů přístup podle těchto různé aspekty výkonu. Pro většinu aplikací byl tento přístup poměrně úspěšné.

## <a name="primitive-types"></a>Primitivní typy

Rozhraní .NET zahrnuje sadu primitivní typy, které se používají (na různých úrovních) ve všech aplikacích. Tyto typy obsahovat data, jako je například čísla, řetězce, bajtů a libovolné objekty. Jazyk C# obsahuje klíčová slova pro tyto typy. Ukázkové sady tyto typy je uveden níže, s odpovídající C# klíčová slova.

* <xref:System.Object?displayProperty=nameWithType>([objekt](../csharp/language-reference/keywords/object.md)) – systém typů ultimate základní třídy v modulu CLR. Je kořenem hierarchie typu.
* <xref:System.Int16?displayProperty=nameWithType>([krátké](../csharp/language-reference/keywords/short.md))-16bitové A podepsaný typ integer. Nepodepsané <xref:System.UInt16> také existuje.
* <xref:System.Int32?displayProperty=nameWithType>([int](../csharp/language-reference/keywords/int.md))-32bitová podepsaná typ integer. Nepodepsané [UInt32](../csharp/language-reference/keywords/uint.md) také existuje.
* <xref:System.Single?displayProperty=nameWithType>([float](../csharp/language-reference/keywords/float.md))-32bitová typů s plovoucí desetinnou čárkou.
* <xref:System.Decimal?displayProperty=nameWithType>([decimal](../csharp/language-reference/keywords/decimal.md))-128bitové A typ decimal.
* <xref:System.Byte?displayProperty=nameWithType>([bajtů](../csharp/language-reference/keywords/byte.md))-nepodepsané 8bitové celé číslo, představující bajtů paměti.
* <xref:System.Boolean?displayProperty=nameWithType>([bool](../csharp/language-reference/keywords/bool.md))-typem logická hodnota, která představuje `true` nebo `false`.
* <xref:System.Char?displayProperty=nameWithType>([char](../csharp/language-reference/keywords/char.md))-16bitové A číselný typ, který reprezentuje znak Unicode.
* <xref:System.String?displayProperty=nameWithType>([řetězec](../csharp/language-reference/keywords/string.md))-představuje posloupnost znaků. Jiné než `char[]`, ale umožňuje indexování do každého uživatele `char` v `string`.

## <a name="data-structures"></a>Datové struktury

Rozhraní .NET zahrnuje sadu datové struktury, které jsou workhorses téměř jakoukoli aplikací .NET. Ty jsou nejčastěji kolekce, ale také zahrnovat jiné typy.

*   <xref:System.Array>-Představuje pole důrazně typy objektů, kterým lze přistupovat pomocí indexu. Má pevnou velikost, na jeho vytváření.
*   <xref:System.Collections.Generic.List%601>-Představuje seznam objektů, kterým lze přistupovat pomocí indexu silného typu. Velikost automaticky podle potřeby.
*   <xref:System.Collections.Generic.Dictionary%602>-Reprezentuje kolekci hodnot, které jsou indexované podle klíče. Hodnoty jsou přístupné prostřednictvím klíč. Velikost automaticky podle potřeby.
*   <xref:System.Uri>-Poskytuje reprezentaci objektu identifikátor URI (URI) a snadný přístup k části identifikátoru URI.
*   <xref:System.DateTime>-Představuje okamžik v čase, obvykle vyjádřený jako datum a čas, den.

## <a name="utility-apis"></a>Rozhraní API pro nástroj

Rozhraní .NET zahrnuje sadu nástrojů rozhraní API, které poskytují funkce pro celou řadu důležitých úloh.

*   <xref:System.Net.Http.HttpClient>-Rozhraní API pro odesílání požadavků HTTP a příjem odpovědí HTTP ze zdroje identifikovaného identifikátorem URI.
*   <xref:System.Xml.Linq.XDocument>-Rozhraní API pro načítání a dotazování dokumentů XML pomocí LINQ.
*   <xref:System.IO.StreamReader>-Rozhraní API pro čtení souborů (<xref:System.IO.StringWriter>) lze použít k zápisu souborů.

## <a name="app-model-apis"></a>Rozhraní API modelu aplikace

Existuje mnoho modely aplikace, které lze použít s .NET, poskytuje několik společností.

*   [ASP.NET](http://asp.net) -poskytuje webové rozhraní pro vytváření webů a služeb. Podporované v systému Windows, Linux a systému macOS (závisí na verzi technologie ASP.NET).
