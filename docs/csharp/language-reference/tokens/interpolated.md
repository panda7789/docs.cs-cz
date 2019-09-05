---
title: $-odinterpolace řetězců C# – referenční informace
ms.custom: seodec18
description: Interpolace řetězců poskytuje čitelnější a pohodlný Syntax pro formátování výstupu řetězce než tradiční složené formátování řetězce.
ms.date: 09/02/2019
f1_keywords:
- $_CSharpKeyword
- $
helpviewer_keywords:
- $ special character [C#]
- string interpolation [C#]
- interpolated string [C#]
author: pkulikov
ms.author: ronpet
ms.openlocfilehash: 53a8938a373136df65e23c162b94c4d8dc1f30b4
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253866"
---
# <a name="---string-interpolation-c-reference"></a>$-Řetězcová interpolaceC# (Referenční dokumentace)

Speciální znak identifikuje řetězcový literál jako *interpolovaná řetězec.* `$` Interpolovaná řetězcová konstanta je řetězcový literál, který může obsahovat *výrazy interpolace*. Když je interpolovaná řetězcová událost přeložena na výsledný řetězec, položky s výrazy interpolace jsou nahrazeny řetězcovými reprezentacemi výsledků výrazu. Tato funkce je k dispozici C# od 6.

Interpolace řetězců poskytuje čitelnější a pohodlný Syntax pro vytváření formátovaných řetězců, než je funkce [složeného formátování řetězce](../../../standard/base-types/composite-formatting.md) . Následující příklad používá obě funkce k produkci stejného výstupu:

[!code-csharp-interactive[compare with composite formatting](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

## <a name="structure-of-an-interpolated-string"></a>Struktura interpolované řetězce

Pro identifikaci řetězcového literálu jako interpolované řetězce, předřaďte ho `$` symbolem. Mezi `$` znakem `"` a, který začíná řetězcovým literálem, nelze zadat prázdný znak.

Struktura položky s výraz interpolace je následující:

```csharp
{<interpolationExpression>[,<alignment>][:<formatString>]}
```

Prvky v hranatých závorkách jsou volitelné. V následující tabulce jsou popsány jednotlivé prvky:

|Prvek|Popis|
|-------------|-----------------|
|`interpolationExpression`|Výraz, který generuje výsledek, který má být formátován. Řetězcová reprezentace `null` je <xref:System.String.Empty?displayProperty=nameWithType>.|
|`alignment`|Konstantní výraz, jehož hodnota určuje minimální počet znaků v řetězcové reprezentaci výsledku výrazu. Je-li kladné, Řetězcová reprezentace je zarovnána doprava; Pokud je záporná, zůstane zarovnaná doleva. Další informace najdete v tématu [součást zarovnání](../../../standard/base-types/composite-formatting.md#alignment-component).|
|`formatString`|Řetězec formátu, který je podporován typem výsledku výrazu. Další informace naleznete v tématu [formátovací řetězec – komponenta](../../../standard/base-types/composite-formatting.md#format-string-component).|

Následující příklad používá volitelné formátovací komponenty popsané výše:

[!code-csharp-interactive[specify alignment and format string](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

## <a name="special-characters"></a>Speciální znaky

Chcete-li do textu vytvořeného interpolované řetězce zahrnout složené závorky "{" nebo "}", použijte dvě složené závorky "{{" nebo "}}". Další informace naleznete v tématu [uvozovací závorky](../../../standard/base-types/composite-formatting.md#escaping-braces).

Jelikož dvojtečka (":") má zvláštní význam v položce výrazu interpolace, aby bylo možné použít [podmíněný operátor](../operators/conditional-operator.md) ve výrazu interpolace, vložte tento výraz do závorek.

Následující příklad ukazuje, jak zahrnout složenou závorku ve výsledném řetězci a jak používat podmíněný operátor ve výrazu interpolace:

[!code-csharp-interactive[example with ternary conditional operator](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

Interpolované doslovné řetězce začíná `$` znakem následovaným `@` znakem. Další informace o doslovnéch řetězcích naleznete v tématech [řetězec](../keywords/string.md) a [doslovného identifikátoru](verbatim.md) .

> [!NOTE]
> Počínaje C# 8,0 můžete použít `$` tokeny a `@` v libovolném pořadí: `$@"..."` a `@$"..."` jsou platné interpolované řetězce. V dřívějších C# verzích `$` se token `@` musí vyskytovat před tokenem.

## <a name="implicit-conversions-and-how-to-specify-iformatprovider-implementation"></a>Implicitní převody a určení `IFormatProvider` implementace

Existují tři implicitní převody z interpolované řetězce:

1. Převod interpolované řetězcové na <xref:System.String> instanci, která je výsledkem interpolované řetězcové překladu s položkami výrazu interpolace, které se nahrazují správně formátovanými řetězcovými reprezentacemi jejich výsledků. Tento převod používá <xref:System.Globalization.CultureInfo.CurrentCulture> k formátování výsledků výrazu.

1. Převod interpolované řetězcové na <xref:System.FormattableString> instanci, která představuje složený řetězec formátu společně s výsledky výrazu, který má být formátován. To umožňuje vytvořit více výsledných řetězců s obsahem specifickým pro jazykovou verzi z <xref:System.FormattableString> jedné instance. Chcete-li to provést, zavolejte jednu z následujících metod:

      - Přetížení, které vytváří výsledný řetězec <xref:System.Globalization.CultureInfo.CurrentCulture>pro. <xref:System.FormattableString.ToString>
      - Metoda, která vytváří výsledný řetězec <xref:System.Globalization.CultureInfo.InvariantCulture>pro. <xref:System.FormattableString.Invariant%2A>
      - <xref:System.FormattableString.ToString(System.IFormatProvider)> Metoda, která vytváří výsledný řetězec pro zadanou jazykovou verzi.

    Můžete také použít <xref:System.FormattableString.ToString(System.IFormatProvider)> metodu k poskytnutí uživatelsky definované implementace <xref:System.IFormatProvider> rozhraní, které podporuje vlastní formátování. Další informace naleznete v části [vlastní formátování pomocí ICustomFormatter](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter) oddílu [typy formátování v článku .NET](../../../standard/base-types/formatting-types.md) .

1. Převod interpolované řetězce na <xref:System.IFormattable> instanci, která také umožňuje vytvořit více výsledných řetězců s obsahem specifickým pro jazykovou verzi z jedné <xref:System.IFormattable> instance.

Následující příklad používá implicitní převod na <xref:System.FormattableString> k vytvoření řetězců výsledků specifických pro jazykovou verzi:

[!code-csharp-interactive[create culture-specific result strings](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

## <a name="additional-resources"></a>Další zdroje

Pokud s interpolací řetězce začínáte, přečtěte si téma o [interpolaci C# řetězce v](../../tutorials/exploration/interpolated-strings.yml) interaktivním kurzu. Můžete také [v C# kurzu ověřit jinou řetězcovou interpolaci](../../tutorials/string-interpolation.md) , která ukazuje, jak použít interpolované řetězce pro vytváření formátovaných řetězců.

## <a name="compilation-of-interpolated-strings"></a>Kompilace interpolovaná řetězce

Pokud má interpolující řetězec typ `string`, je obvykle transformovaná <xref:System.String.Format%2A?displayProperty=nameWithType> na volání metody. Kompilátor může nahradit <xref:System.String.Format%2A?displayProperty=nameWithType> , <xref:System.String.Concat%2A?displayProperty=nameWithType> Pokud bylo analyzované chování ekvivalentní zřetězení.

Pokud má interpolující řetězec typ <xref:System.IFormattable> nebo <xref:System.FormattableString>, kompilátor <xref:System.Runtime.CompilerServices.FormattableStringFactory.Create%2A?displayProperty=nameWithType> vygeneruje volání metody.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [interpolované řetězce](~/_csharplang/spec/expressions.md#interpolated-strings) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Speciální znaky v jazyce C#](index.md)
- [Řetězce](../../programming-guide/strings/index.md)
- [Tabulka formátování číselných výsledků](../keywords/formatting-numeric-results-table.md)
- [Složené formátování](../../../standard/base-types/composite-formatting.md)
- <xref:System.String.Format%2A?displayProperty=nameWithType>
