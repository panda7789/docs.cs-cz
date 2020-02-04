---
title: $-odinterpolace řetězců C# – referenční informace
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
ms.openlocfilehash: 97bc606569b83bd14cd3b32495deb8e529747e9c
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980116"
---
# <a name="---string-interpolation-c-reference"></a>$-Řetězcová interpolaceC# (Referenční dokumentace)

`$` speciální znak identifikuje řetězcový literál jako *interpolovaná řetězec*. Interpolovaná řetězcová konstanta je řetězcový literál, který může obsahovat *výrazy interpolace*. Když je interpolovaná řetězcová událost přeložena na výsledný řetězec, položky s výrazy interpolace jsou nahrazeny řetězcovými reprezentacemi výsledků výrazu. Tato funkce je k dispozici C# od 6.

Interpolace řetězců poskytuje čitelnější a pohodlný Syntax pro vytváření formátovaných řetězců, než je funkce [složeného formátování řetězce](../../../standard/base-types/composite-formatting.md) . Následující příklad používá obě funkce k produkci stejného výstupu:

[!code-csharp-interactive[compare with composite formatting](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

## <a name="structure-of-an-interpolated-string"></a>Struktura interpolované řetězce

Pro identifikaci řetězcového literálu jako interpolované řetězce, předřaďte ho symbolem `$`. Mezi `$` a `"`, které začínají řetězcovým literálem, nelze mít žádné prázdné znaky.

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

Interpolované doslovné řetězce začíná znakem `$` následovaným `@` znakem. Další informace o doslovnéch řetězcích naleznete v tématech [řetězec](../builtin-types/reference-types.md) a [doslovného identifikátoru](verbatim.md) .

> [!NOTE]
> Počínaje C# 8,0 můžete použít tokeny `$` a `@` v libovolném pořadí: `$@"..."` i `@$"..."` jsou platné interpolované řetězce. V dřívějších C# verzích musí být token `$` před tokenem `@`.

## <a name="implicit-conversions-and-how-to-specify-iformatprovider-implementation"></a>Implicitní převody a určení `IFormatProvider` implementace

Existují tři implicitní převody z interpolované řetězce:

1. Převod interpolované řetězcové na <xref:System.String> instanci, která je výsledkem interpolované řetězcové překladu s položkami výrazu interpolace, které se nahrazují správně formátovanými řetězcovými reprezentacemi jejich výsledků. Tento převod používá <xref:System.Globalization.CultureInfo.CurrentCulture> k formátování výsledků výrazu.

1. Konverze interpolované řetězcové instance na <xref:System.FormattableString>, která představuje složený řetězec formátu společně s výsledky výrazu, který má být formátován. To umožňuje vytvořit více výsledných řetězců s obsahem specifickým pro jazykovou verzi z jedné instance <xref:System.FormattableString>. Chcete-li to provést, zavolejte jednu z následujících metod:

      - <xref:System.FormattableString.ToString> přetížení, které vytváří výsledný řetězec pro <xref:System.Globalization.CultureInfo.CurrentCulture>.
      - Metoda <xref:System.FormattableString.Invariant%2A>, která vytváří výsledný řetězec pro <xref:System.Globalization.CultureInfo.InvariantCulture>.
      - <xref:System.FormattableString.ToString(System.IFormatProvider)> metoda, která vytváří výsledný řetězec pro určenou jazykovou verzi.

    Můžete také použít metodu <xref:System.FormattableString.ToString(System.IFormatProvider)> k poskytnutí uživatelsky definované implementace rozhraní <xref:System.IFormatProvider>, která podporuje vlastní formátování. Další informace naleznete v části [vlastní formátování pomocí ICustomFormatter](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter) oddílu [typy formátování v článku .NET](../../../standard/base-types/formatting-types.md) .

1. Převod interpolované řetězcové instance na <xref:System.IFormattable>, která umožňuje také vytvořit více výsledných řetězců s obsahem specifickým pro jazykovou verzi z jedné instance <xref:System.IFormattable>.

Následující příklad používá implicitní převod na <xref:System.FormattableString> k vytvoření řetězců výsledků specifických pro jazykovou verzi:

[!code-csharp-interactive[create culture-specific result strings](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

## <a name="additional-resources"></a>Další materiály a zdroje informací

Pokud s interpolací řetězce začínáte, přečtěte si téma o [interpolaci C# řetězce v](../../tutorials/exploration/interpolated-strings.yml) interaktivním kurzu. Můžete také [v C# kurzu ověřit jinou řetězcovou interpolaci](../../tutorials/string-interpolation.md) , která ukazuje, jak použít interpolované řetězce pro vytváření formátovaných řetězců.

## <a name="compilation-of-interpolated-strings"></a>Kompilace interpolovaná řetězce

Pokud má interpolující řetězec typ `string`, je obvykle transformovaná na volání metody <xref:System.String.Format%2A?displayProperty=nameWithType>. Kompilátor může nahradit <xref:System.String.Format%2A?displayProperty=nameWithType> <xref:System.String.Concat%2A?displayProperty=nameWithType>, pokud bylo analyzované chování ekvivalentní zřetězení.

Pokud má interpolující řetězec typ <xref:System.IFormattable> nebo <xref:System.FormattableString>, kompilátor vygeneruje volání metody <xref:System.Runtime.CompilerServices.FormattableStringFactory.Create%2A?displayProperty=nameWithType>.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [interpolované řetězce](~/_csharplang/spec/expressions.md#interpolated-strings) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Speciální znaky v jazyce C#](index.md)
- [Řetězce](../../programming-guide/strings/index.md)
- [Řetězce standardního číselného formátu](../../../standard/base-types/standard-numeric-format-strings.md)
- [Složené formátování](../../../standard/base-types/composite-formatting.md)
- <xref:System.String.Format%2A?displayProperty=nameWithType>
