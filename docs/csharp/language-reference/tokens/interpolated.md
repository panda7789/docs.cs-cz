---
title: $ - interpolace řetězce - c# odkaz
description: Interpolace řetězců poskytuje čitelnější a pohodlnější syntaxi pro formátování výstupu řetězce než tradiční složené formátování řetězců.
ms.date: 09/02/2019
f1_keywords:
- $_CSharpKeyword
- $
helpviewer_keywords:
- $ special character [C#]
- string interpolation [C#]
- interpolated string [C#]
author: pkulikov
ms.openlocfilehash: 97bc606569b83bd14cd3b32495deb8e529747e9c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76980116"
---
# <a name="---string-interpolation-c-reference"></a>$ - interpolace řetězce (odkaz C#)

Speciální `$` znak identifikuje literál řetězce jako *interpolovaný řetězec*. Interpolovaný řetězec je řetězcový literál, který může obsahovat *interpolační výrazy*. Když je interpolovaný řetězec přeložen na výsledný řetězec, položky s interpolačními výrazy jsou nahrazeny řetězcovými reprezentacemi výsledků výrazu. Tato funkce je k dispozici počínaje C# 6.

Interpolace řetězců poskytuje čitelnější a pohodlnější syntaxi pro vytvoření formátovaných řetězců než funkce [složeného formátování řetězce.](../../../standard/base-types/composite-formatting.md) Následující příklad používá oba prvky k vytvoření stejného výstupu:

[!code-csharp-interactive[compare with composite formatting](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

## <a name="structure-of-an-interpolated-string"></a>Struktura interpolovaného řetězce

Chcete-li identifikovat literál řetězce jako interpolovaný řetězec, předřávejte jej symbolem. `$` Mezi `$` a, `"` která spustí literál řetězce, nelze mít žádné prázdné místo.

Struktura položky s interpolačním výrazem je následující:

```csharp
{<interpolationExpression>[,<alignment>][:<formatString>]}
```

Prvky v hranatých závorkách jsou volitelné. Následující tabulka popisuje každý prvek:

|Element|Popis|
|-------------|-----------------|
|`interpolationExpression`|Výraz, který vytváří výsledek, který má být formátován. Řetězcová `null` reprezentace is <xref:System.String.Empty?displayProperty=nameWithType>.|
|`alignment`|Konstantní výraz, jehož hodnota definuje minimální počet znaků v řetězcové reprezentaci výsledku výrazu. Pokud je kladná, reprezentace řetězce je zarovnána doprava; Pokud je záporná, je zarovnána doleva. Další informace naleznete v [tématu Součást zarovnání](../../../standard/base-types/composite-formatting.md#alignment-component).|
|`formatString`|Formátovací řetězec podporovaný typem výsledku výrazu. Další informace naleznete v [tématu Format String Component](../../../standard/base-types/composite-formatting.md#format-string-component).|

Následující příklad používá volitelné formátovací součásti popsané výše:

[!code-csharp-interactive[specify alignment and format string](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

## <a name="special-characters"></a>Speciální znaky

Chcete-li zahrnout závorku "{" nebo "}", do textu vytvořeného interpolovaným řetězcem použijte dvě závorky,{{" nebo "}}". Další informace naleznete v [tématu Escaping Braces](../../../standard/base-types/composite-formatting.md#escaping-braces).

Jako dvojtečka (":") má zvláštní význam v položce výrazu interpolace, aby bylo možné použít [podmíněný operátor](../operators/conditional-operator.md) ve výrazu interpolace, uzavřete tento výraz do závorek.

Následující příklad ukazuje, jak zahrnout složenou závorku do výsledného řetězce a jak použít podmíněný operátor ve výrazu interpolace:

[!code-csharp-interactive[example with ternary conditional operator](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

Interpolovaný doslovný řetězec začíná `$` znakem následovaným znakem. `@` Další informace o doslovných řetězcích naleznete v tématech [řetězce](../builtin-types/reference-types.md) a [doslovného identifikátoru.](verbatim.md)

> [!NOTE]
> Počínaje C# 8.0, můžete `$` použít `@` a tokeny v `$@"..."` `@$"..."` libovolném pořadí: oba a jsou platné interpolované doslovné řetězce. V dřívějších verzích `$` jazyka C# `@` token musí zobrazit před token.

## <a name="implicit-conversions-and-how-to-specify-iformatprovider-implementation"></a>Implicitní převody a `IFormatProvider` jak určit implementaci

Existují tři implicitní převody z interpolovaného řetězce:

1. Převod interpolovaného řetězce na <xref:System.String> instanci, která je výsledkem interpolovaného rozlišení řetězce s položkami exprese interpolace, které jsou nahrazeny správně formátovanými řetězcovými reprezentacemi jejich výsledků. Tento převod <xref:System.Globalization.CultureInfo.CurrentCulture> používá k formátování výsledků výrazu.

1. Převod interpolovaného řetězce na <xref:System.FormattableString> instanci, která představuje složený formátovací řetězec spolu s výsledky výrazu, které mají být formátovány. To umožňuje vytvořit více řetězců výsledků s obsahem <xref:System.FormattableString> specifickým pro jazykovou verzi z jedné instance. Chcete-li to provést, zavolejte jednu z následujících metod:

      - Přetížení, <xref:System.FormattableString.ToString> které vytváří výsledný řetězec <xref:System.Globalization.CultureInfo.CurrentCulture>pro .
      - Metoda, <xref:System.FormattableString.Invariant%2A> která vytváří výsledný řetězec <xref:System.Globalization.CultureInfo.InvariantCulture>pro .
      - Metoda, <xref:System.FormattableString.ToString(System.IFormatProvider)> která vytváří výsledný řetězec pro zadanou jazykovou verzi.

    Tuto metodu <xref:System.FormattableString.ToString(System.IFormatProvider)> můžete také použít k poskytnutí <xref:System.IFormatProvider> uživatelem definované implementace rozhraní, které podporuje vlastní formátování. Další informace naleznete v části [Vlastní formátování s iCustomFormatter](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter) v části Typy formátování v článku [rozhraní .NET.](../../../standard/base-types/formatting-types.md)

1. Převod interpolovaného řetězce na <xref:System.IFormattable> instanci, která také umožňuje vytvořit více řetězců výsledků <xref:System.IFormattable> s obsahem specifickým pro jazykovou verzi z jedné instance.

Následující příklad používá implicitní převod k <xref:System.FormattableString> vytvoření řetězců výsledků specifických pro jazykovou verzi:

[!code-csharp-interactive[create culture-specific result strings](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

## <a name="additional-resources"></a>Další zdroje

Pokud jste novým řetězce interpolace, naleznete [řetězec interpolace v C#](../../tutorials/exploration/interpolated-strings.yml) interaktivní kurz. Můžete také zkontrolovat jiný [řetězec interpolace v kurzu Jazyka C#,](../../tutorials/string-interpolation.md) který ukazuje, jak používat interpolované řetězce k výrobě formátovaných řetězců.

## <a name="compilation-of-interpolated-strings"></a>Kompilace interpolovaných řetězců

Pokud interpolovaný řetězec má `string`typ , je obvykle transformována do volání <xref:System.String.Format%2A?displayProperty=nameWithType> metody. Kompilátor může <xref:System.String.Format%2A?displayProperty=nameWithType> <xref:System.String.Concat%2A?displayProperty=nameWithType> nahradit, pokud by analyzované chování bylo ekvivalentní zřetězení.

Pokud interpolovaný řetězec má <xref:System.IFormattable> typ <xref:System.FormattableString>nebo , kompilátor generuje <xref:System.Runtime.CompilerServices.FormattableStringFactory.Create%2A?displayProperty=nameWithType> volání metody.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [Interpolované řetězce](~/_csharplang/spec/expressions.md#interpolated-strings) [ve specifikaci jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [C# speciální znaky](index.md)
- [Řetězce](../../programming-guide/strings/index.md)
- [Standardní číselné formátovací řetězce](../../../standard/base-types/standard-numeric-format-strings.md)
- [Složené formátování](../../../standard/base-types/composite-formatting.md)
- <xref:System.String.Format%2A?displayProperty=nameWithType>
