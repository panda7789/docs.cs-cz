---
title: Interpolace řetězce vC#
description: Naučte se, jak zahrnout formátovaný výraz do výsledného řetězce C# v rámci s interpolací řetězce.
author: pkulikov
ms.date: 09/02/2019
ms.openlocfilehash: d3a3a08d5911b5323aa61c571f05318d10380339
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252927"
---
# <a name="string-interpolation-in-c"></a>Interpolace řetězce v jazyce C\#

V tomto kurzu se dozvíte, jak použít [interpolaci řetězců](../language-reference/tokens/interpolated.md) k formátování a zahrnutí výsledků výrazu do výsledného řetězce. V příkladech se předpokládá, že máte zkušenosti C# se základními koncepty a formátování typu .NET. Pokud začínáte s interpolací řetězců nebo formátováním typu .NET, přečtěte si nejprve [kurz o interpolaci interaktivních řetězců](exploration/interpolated-strings.yml) . Další informace o typech formátování v rozhraní .NET naleznete v tématu [typy formátování v rozhraní .NET](../../standard/base-types/formatting-types.md) .

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

## <a name="introduction"></a>Úvod

Funkce [interpolace řetězců](../language-reference/tokens/interpolated.md) je postavená na základě funkce [složeného formátování](../../standard/base-types/composite-formatting.md) a poskytuje čitelnější a pohodlnější syntaxi pro zahrnutí formátovaného výrazu do výsledného řetězce.

Pro identifikaci řetězcového literálu jako interpolované řetězce, předřaďte ho `$` symbolem. Můžete vložit libovolný platný C# výraz, který vrací hodnotu v interpolované řetězcové hodnotě. V následujícím příkladu, jakmile je vyhodnocen výraz, je výsledek převeden na řetězec a zahrnutý do výsledného řetězce:

[!code-csharp-interactive[string interpolation example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#1)]

Jak ukazuje příklad, zahrnete výraz do interpolované řetězcové části jeho uzavřením do složených závorek:

```csharp
{<interpolationExpression>}
```

Interpolované řetězce podporují všechny možnosti funkce [složeného formátování řetězce](../../standard/base-types/composite-formatting.md) . Díky tomu jsou čitelnější alternativa k použití <xref:System.String.Format%2A?displayProperty=nameWithType> metody.

## <a name="how-to-specify-a-format-string-for-an-interpolation-expression"></a>Určení formátovacího řetězce pro výraz interpolace

Zadejte řetězec formátu, který je podporován typem výsledku výrazu, pomocí výrazu interpolace dvojtečkou (":") a řetězcem formátu:

```csharp
{<interpolationExpression>:<formatString>}
```

Následující příklad ukazuje, jak zadat standardní a vlastní formátovací řetězce pro výrazy, které tvoří datum a čas nebo číselné výsledky:

[!code-csharp-interactive[format string example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#2)]

Další informace naleznete v části [formátovací řetězec komponenty](../../standard/base-types/composite-formatting.md#format-string-component) v tématu [složené formátování](../../standard/base-types/composite-formatting.md) . Tato část obsahuje odkazy na témata, která popisují standardní a vlastní formátovací řetězce podporované typy .NET Base.

## <a name="how-to-control-the-field-width-and-alignment-of-the-formatted-interpolation-expression"></a>Jak řídit šířku pole a zarovnání formátovaného výrazu interpolace

Určete minimální šířku pole a zarovnání formátovaného výrazu pomocí výrazu interpolace s čárkou (",") a výrazem konstanty:

```csharp
{<interpolationExpression>,<alignment>}
```

Pokud je hodnota *Zarovnání* kladná, formátovaný výsledek výrazu je zarovnán vpravo; Pokud je záporná, zůstane zarovnaná doleva.

Pokud potřebujete zadat jak zarovnání, tak formátovací řetězec, začněte součástí zarovnání:

```csharp
{<interpolationExpression>,<alignment>:<formatString>}
```

Následující příklad ukazuje, jak zadat zarovnání a použít znaky kanálu (|) k oddělení textových polí:

[!code-csharp-interactive[alignment example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#3)]

Jak ukazuje výstup, pokud délka formátovaného výsledku výrazu překročí zadanou šířku pole, hodnota *Zarovnání* se ignoruje.

Další informace naleznete v části [Zarovnání komponenty](../../standard/base-types/composite-formatting.md#alignment-component) v tématu [složené formátování](../../standard/base-types/composite-formatting.md) .

## <a name="how-to-use-escape-sequences-in-an-interpolated-string"></a>Použití řídicích sekvencí v interpolované řetězci

Interpolované řetězce podporují všechny řídicí sekvence, které lze použít v běžných řetězcových literálech. Další informace naleznete v tématu [řetězcové řídicí sekvence](../programming-guide/strings/index.md#string-escape-sequences).

Pro interpretaci řídicích sekvencí doslova pomocí [doslovného](../language-reference/tokens/verbatim.md) řetězcového literálu. Interpolované doslovné řetězce začíná `$` znakem následovaným `@` znakem. Počínaje C# 8,0 můžete použít `$` tokeny a `@` v libovolném pořadí: `$@"..."` a `@$"..."` jsou platné interpolované řetězce.

Chcete-li ve výsledném řetězci zahrnout složené závorky "{" nebo "}", použijte dvě složené závorky "{{" nebo "}}". Další informace naleznete v části [uvozovací závorky](../../standard/base-types/composite-formatting.md#escaping-braces) v tématu [složeného formátování](../../standard/base-types/composite-formatting.md) .

Následující příklad ukazuje, jak zahrnout složené závorky ve výsledném řetězci a sestavit doslovné řetězec v doslovném znění:

[!code-csharp-interactive[escape sequence example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#4)]

## <a name="how-to-use-a-ternary-conditional-operator--in-an-interpolation-expression"></a>Jak použít Ternární podmíněný operátor `?:` ve výrazu interpolace

Jako dvojtečka (":") má zvláštní význam v položce s výrazem interpolace, aby bylo možné použít [podmíněný operátor](../language-reference/operators/conditional-operator.md) ve výrazu, uzavřít jej do závorek, jak ukazuje následující příklad:

[!code-csharp-interactive[conditional operator example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#5)]

## <a name="how-to-create-a-culture-specific-result-string-with-string-interpolation"></a>Jak vytvořit výsledný řetězec specifický pro jazykovou verzi s interpolací řetězce

Ve výchozím nastavení používá interpolující řetězec aktuální jazykovou verzi definovanou <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> vlastností pro všechny operace formátování. Použijte implicitní převod interpolované řetězce na <xref:System.FormattableString?displayProperty=nameWithType> instanci a zavolejte jeho <xref:System.FormattableString.ToString(System.IFormatProvider)> metodu pro vytvoření výsledného řetězce specifického pro jazykovou verzi. Následující příklad ukazuje, jak to provést:

[!code-csharp-interactive[specify different cultures](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#6)]

Jak ukazuje příklad, můžete použít jednu <xref:System.FormattableString> instanci pro generování více výsledných řetězců pro různé jazykové verze.

## <a name="how-to-create-a-result-string-using-the-invariant-culture"></a>Postup vytvoření výsledného řetězce pomocí neutrální jazykové verze

Spolu s <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> metodou lze použít statickou <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> metodu k překladu interpolované řetězce na výsledný řetězec pro <xref:System.Globalization.CultureInfo.InvariantCulture>. Následující příklad ukazuje, jak to provést:

[!code-csharp-interactive[format with invariant culture](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#7)]

## <a name="conclusion"></a>Závěr

Tento kurz popisuje běžné scénáře použití řetězcové interpolace. Další informace o interpolaci řetězců naleznete v tématu o [interpolaci řetězce](../language-reference/tokens/interpolated.md) . Další informace o typech formátování v rozhraní .NET naleznete v tématech [typy formátování v rozhraní .NET a ve](../../standard/base-types/formatting-types.md) [složených formátováních](../../standard/base-types/composite-formatting.md) .

## <a name="see-also"></a>Viz také:

- <xref:System.String.Format%2A?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- <xref:System.IFormattable?displayProperty=nameWithType>
- [Řetězce](../programming-guide/strings/index.md)
