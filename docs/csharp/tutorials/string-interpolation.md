---
title: Interpolace řetězce v jazyce C#
description: Zjistěte, jak mají být zahrnuty výsledky výraz formátovaný výsledek řetězec v jazyce C# s interpolace řetězec.
author: pkulikov
ms.date: 05/09/2018
ms.openlocfilehash: 447e87cd4aae49896f0efbb8ece6097181079266
ms.sourcegitcommit: ff1d40507b3eb6e2185478e37c66c66be6de46f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/11/2018
---
# <a name="string-interpolation-in-c"></a>Interpolace řetězce v jazyce C# #

V tomto kurzu se dozvíte, jak používat [řetězec interpolace](../language-reference/tokens/interpolated.md) můžete naformátovat a zahrňte výsledky výraz ve výsledném řetězci. Příklady předpokládají, že jste obeznámeni s základní koncepty jazyka C# a rozhraní .NET typ formátování. Pokud jste ještě interpolace řetězec nebo formátování typ rozhraní .NET, podívejte se [rychlý start interpolace interaktivní řetězec](../quick-starts/interpolated-strings.yml) první. Další informace o typy formátování v rozhraní .NET najdete v tématu [typy formátování v .NET](../../standard/base-types/formatting-types.md) tématu.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

## <a name="introduction"></a>Úvod

[Řetězec interpolace](../language-reference/tokens/interpolated.md) funkce je postavený na [složené formátování](../../standard/base-types/composite-formatting.md) funkci a poskytuje čitelnější a pohodlný syntaxe zahrnout výsledky výraz formátovaný výsledek řetězce.

K identifikaci řetězcový literál jako interpolované řetězce, předřazení její `$` symbol. Můžete vložit libovolný platný C# výraz, který vrátí hodnotu ve formátu interpolované řetězce. V následujícím příkladu při vyhodnocení výrazu svůj výsledek je převést na řetězec a součástí výsledný řetězec:

[!code-csharp-interactive[string interpolation example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#1)]

Jak ukazuje příklad patří uzavřením s složené závorky výrazu ve formátu interpolované řetězce:

```
{<interpolatedExpression>}
```

Při kompilaci, interpolované řetězce obvykle převede na <xref:System.String.Format%2A?displayProperty=nameWithType> volání metody. Který zpřístupňuje všechny možnosti [řetězce složené formátování](../../standard/base-types/composite-formatting.md) funkce, které jsou k dispozici pro použití s také interpolované řetězce.

## <a name="how-to-specify-a-format-string-for-an-interpolated-expression"></a>Jak určit řetězec formátu pro interpolované výrazu

Zadejte řetězec formátu, který je podporován typ výsledku výrazu podle interpolované výraz s dvojtečkou (":") a řetězec formátu:

```
{<interpolatedExpression>:<formatString>}
```

Následující příklad ukazuje, jak zadat standardní a vlastní formát řetězce pro výrazy, které produkují data a času nebo číselných výsledků:

[!code-csharp-interactive[format string example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#2)]

Další informace najdete v tématu [součást řetězce formátu](../../standard/base-types/composite-formatting.md#format-string-component) části [složené formátování](../../standard/base-types/composite-formatting.md) tématu. Tento oddíl obsahuje odkazy na témata, která popisují řetězce formátu Standardní a vlastní podporuje základní typy .NET.

## <a name="how-to-control-the-field-width-and-alignment-of-the-formatted-interpolated-expression"></a>Tom, jak řídit šířku pole a zarovnání formátovaný interpolované výrazu

Zadejte šířku minimální pole a zarovnání výraz formátovaný výsledek podle interpolované výraz s použitím čárky (",") a konstantní výraz:

```
{<interpolatedExpression>,<alignment>}
```

Pokud *zarovnání* hodnota je kladné, výraz formátovaný výsledek je zarovnaný doprava; záporná, je zarovnaný doleva.

Pokud potřebujete k určení zarovnání a řetězec formátu, začněte s komponentou zarovnání:

```
{<interpolatedExpression>,<alignment>:<formatString>}
```

Následující příklad ukazuje, jak k určení zarovnání a používá zřetězit znaky ("|") a tím vymezit textová pole:

[!code-csharp-interactive[alignment example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#3)]

Jako příklad výstupu zobrazí, pokud délka výsledku formátovaný výrazu překračuje zadaný šířku pole, *zarovnání* hodnota je ignorována.

Další informace najdete v tématu [zarovnání součást](../../standard/base-types/composite-formatting.md#alignment-component) části [složené formátování](../../standard/base-types/composite-formatting.md) tématu.

## <a name="how-to-use-escape-sequences-in-an-interpolated-string"></a>Použití řídicích sekvencí v interpolované řetězce

Interpolované řetězce podporují všechny řídicí sekvence, které lze použít v obyčejnou textové literály. Další informace najdete v tématu [řetězec řídicí sekvence](../programming-guide/strings/index.md#string-escape-sequences).

Řídicí sekvence interpretovat oznámena, používat [typu verbatim](../language-reference/tokens/verbatim.md) řetězcový literál. Řetězec typu verbatim interpolované začíná `$` následuje znak `@` znak.

Zahrnout závorek "{" nebo "}", ve výsledném řetězci, použijte dva složené závorky "{{" nebo "}}". Další informace najdete v tématu [uvozovací znaky složené závorky](../../standard/base-types/composite-formatting.md#escaping-braces) části [složené formátování](../../standard/base-types/composite-formatting.md) tématu.

Následující příklad ukazuje, jak chcete zahrnout do výsledku řetězec složené závorky a vytvořit typu verbatim interpolované řetězce:

[!code-csharp-interactive[escape sequence example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#4)]

## <a name="how-to-use-a-ternary-conditional-operator--in-an-interpolated-expression"></a>Jak používat Ternární podmíněný operátor `?:` ve výrazu interpolované

Jako dvojtečkou (":") má zvláštní význam v položku se interpolované výrazu, aby bylo možné používat [podmíněný operátor](../language-reference/operators/conditional-operator.md) ve výrazu, uzavřete ji v závorkách, jak ukazuje následující příklad:

[!code-csharp-interactive[conditional operator example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#5)]

## <a name="how-to-create-a-culture-specific-result-string-with-string-interpolation"></a>Postup vytvoření specifické pro jazykovou verzi výsledném řetězci s řetězec interpolace

Ve výchozím nastavení používá interpolované řetězce aktuální jazykové verze, které jsou definované <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> vlastnost pro všechny operace formátování. Implicitní převod interpolované řetězce pro použití <xref:System.FormattableString?displayProperty=nameWithType> instance a volání jeho <xref:System.FormattableString.ToString(System.IFormatProvider)> metodu pro vytvoření specifické pro jazykovou verzi výsledný řetězec. Následující příklad ukazuje, jak to udělat:

[!code-csharp-interactive[specify different cultures](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#6)]

Jak ukazuje příklad, můžete použít jednu <xref:System.FormattableString> instanci pro generování vícenásobných řetězců výsledek pro různé jazykové verze.

## <a name="how-to-create-a-result-string-using-the-invariant-culture"></a>Postup vytvoření výsledný řetězec pomocí neutrální jazykovou verzi

Spolu s <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> metodu, můžete použít statickou <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> metoda přeložit interpolované řetězce na řetězec výsledek pro <xref:System.Globalization.CultureInfo.InvariantCulture>. Následující příklad ukazuje, jak to udělat:

[!code-csharp-interactive[format with invariant culture](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#7)]

## <a name="conclusion"></a>Závěr

Tento kurz popisuje běžné scénáře řetězec interpolace využití. Další informace o řetězce interpolace najdete v tématu [řetězec interpolace](../language-reference/tokens/interpolated.md) tématu. Další informace o typy formátování v rozhraní .NET najdete v tématu [typy formátování v .NET](../../standard/base-types/formatting-types.md) a [složené formátování](../../standard/base-types/composite-formatting.md) témata.

## <a name="see-also"></a>Viz také

<xref:System.String.Format%2A?displayProperty=nameWithType>  
<xref:System.FormattableString?displayProperty=nameWithType>  
<xref:System.IFormattable?displayProperty=nameWithType>  
[Řetězce](../programming-guide/strings/index.md)  
