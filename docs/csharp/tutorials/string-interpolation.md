---
title: Interpolace řetězců v jazyce C#
description: Zjistěte, jak mají být zahrnuty výsledky výrazu formátovaný výsledný řetězec v jazyce C# pomocí interpolace řetězců.
author: pkulikov
ms.date: 05/09/2018
ms.openlocfilehash: 5a66ba9215579a459b543a24ece338ffbbfd9aea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675673"
---
# <a name="string-interpolation-in-c"></a>Interpolace řetězců v jazyce C\#

V tomto kurzu se dozvíte, jak používat [interpolace](../language-reference/tokens/interpolated.md) formátování a zahrňte výsledky výrazu do výsledného řetězce. V příkladech se předpokládá, že máte zkušenosti s základní koncepty jazyka C# a .NET typ formátování. Pokud jste ještě interpolace řetězců nebo formátování typu .NET, podívejte se [kurzu interpolace řetězce interaktivní](exploration/interpolated-strings.yml) první. Další informace o formátování typy v rozhraní .NET najdete v tématu [formátovací typy v .NET](../../standard/base-types/formatting-types.md) tématu.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

## <a name="introduction"></a>Úvod

[Interpolace](../language-reference/tokens/interpolated.md) funkce je založená na horní [složené formátování](../../standard/base-types/composite-formatting.md) běží na procesorech a poskytuje čitelné a pohodlné syntaxe zahrnout výsledky výrazu formátovaný výsledný řetězec.

K identifikaci řetězcového literálu jako interpolovaném řetězci, předřaďte ji `$` symbol. Můžete vložit libovolný platný C# výraz, který vrací hodnotu v interpolovaném řetězci. V následujícím příkladu při vyhodnocování výrazu výsledek je převedena na řetězec a součástí výsledného řetězce:

[!code-csharp-interactive[string interpolation example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#1)]

Jak ukazuje příklad, patří uzavřením závorek výrazu v interpolovaném řetězci:

```
{<interpolatedExpression>}
```

V době kompilace, interpolovaném řetězci se obvykle transformuje na <xref:System.String.Format%2A?displayProperty=nameWithType> volání metody. Díky tomu se všechny funkce [řetězec složené formátování](../../standard/base-types/composite-formatting.md) funkce je k dispozici pro použití s interpolovanými řetězci najdete také.

Kompilátor může nahradit <xref:System.String.Format%2A?displayProperty=nameWithType> pro <xref:System.String.Concat%2A?displayProperty=nameWithType> Pokud analyzovat chování by ekvivalentní zřetězení.

## <a name="how-to-specify-a-format-string-for-an-interpolated-expression"></a>Jak určit řetězec formátu pro interpolovaný výraz

Zadejte řetězec formátu, který je podporována typem výsledku výrazu podle interpolovaný výraz s čárkou (":") a nakonec formátovací řetězec:

```
{<interpolatedExpression>:<formatString>}
```

Následující příklad ukazuje, jak určit standardních a vlastních formátovacích řetězců pro výrazy, které produkují data a času nebo číselné výsledky:

[!code-csharp-interactive[format string example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#2)]

Další informace najdete v tématu [součást řetězec formátu](../../standard/base-types/composite-formatting.md#format-string-component) část [složené formátování](../../standard/base-types/composite-formatting.md) tématu. Tento oddíl poskytuje odkazy na témata, které popisují standardní a vlastní formátovací řetězce podporuje základní typy .NET.

## <a name="how-to-control-the-field-width-and-alignment-of-the-formatted-interpolated-expression"></a>Jak řídit šířku pole a zarovnání formátovaného interpolovaný výraz

Zadejte šířku minimální pole a zarovnání formátovaného výraz výsledku podle interpolovaný výraz s čárkou (",") a konstantní výraz:

```
{<interpolatedExpression>,<alignment>}
```

Pokud *zarovnání* hodnota je pozitivní, výraz formátovaný výsledek je zarovnaný doprava; záporná, je zarovnaná doleva.

Pokud je třeba zadat zarovnání a řetězec formátu, začněte s komponentou zarovnání:

```
{<interpolatedExpression>,<alignment>:<formatString>}
```

Následující příklad ukazuje, jak určit zarovnání a používá kanálem znaky ("|") pro vymezení textová pole:

[!code-csharp-interactive[alignment example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#3)]

Jako příklad ukazuje výstup, pokud výraz formátovaný výsledek délka je větší než zadaná šířka pole *zarovnání* hodnota se ignoruje.

Další informace najdete v tématu [součást zarovnání](../../standard/base-types/composite-formatting.md#alignment-component) část [složené formátování](../../standard/base-types/composite-formatting.md) tématu.

## <a name="how-to-use-escape-sequences-in-an-interpolated-string"></a>Použití řídicích sekvencí v interpolovaném řetězci

Interpolované řetězce podporují všechny řídicí sekvence, které lze použít v běžném řetězcové literály. Další informace najdete v tématu [řetězec řídící sekvence](../programming-guide/strings/index.md#string-escape-sequences).

Interpretace doslova řídicí sekvence, použijte [verbatim](../language-reference/tokens/verbatim.md) řetězcový literál. Doslovný interpolovaný řetězec začíná `$` znak následovaný `@` znak.

Zahrnout závorek "{" nebo "}", do výsledného řetězce, použijte dva složené závorky, "{{" nebo "}}". Další informace najdete v tématu [uvozovací znaky složených závorek](../../standard/base-types/composite-formatting.md#escaping-braces) část [složené formátování](../../standard/base-types/composite-formatting.md) tématu.

Následující příklad ukazuje, jak zahrnout složené závorky do výsledného řetězce a sestavit verbatim interpolovaný řetězec:

[!code-csharp-interactive[escape sequence example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#4)]

## <a name="how-to-use-a-ternary-conditional-operator--in-an-interpolated-expression"></a>Jak používat Ternární podmiňovací operátor `?:` v interpolovaným výrazem

Jako dvojtečka (":") má zvláštní význam v položce s interpolovaným výrazem, aby bylo možné používat [podmiňovací operátor](../language-reference/operators/conditional-operator.md) ve výrazu, uzavřete ho do závorek, jako v následujícím příkladu:

[!code-csharp-interactive[conditional operator example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#5)]

## <a name="how-to-create-a-culture-specific-result-string-with-string-interpolation"></a>Jak vytvořit specifické pro jazykovou verzi výsledný řetězec pomocí interpolace řetězců

Ve výchozím nastavení používá interpolovaném řetězci aktuální jazykové verze, které jsou definované <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> vlastnosti pro všechny operace formátování. Použít implicitní převod interpolované řetězce, který se <xref:System.FormattableString?displayProperty=nameWithType> instance a volání jeho <xref:System.FormattableString.ToString(System.IFormatProvider)> metodu pro vytvoření specifické pro jazykovou verzi výsledného řetězce. Následující příklad ukazuje, jak to udělat:

[!code-csharp-interactive[specify different cultures](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#6)]

Jak ukazuje příklad, můžete použít jednu <xref:System.FormattableString> instance ke generování více výsledný řetězec pro různé jazykové verze.

## <a name="how-to-create-a-result-string-using-the-invariant-culture"></a>Postup vytvoření výsledného řetězce pomocí neutrální jazykové verze

Spolu s <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> metodu, můžete použít statické <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> metoda přeložit interpolovaném řetězci na výsledný řetězec pro <xref:System.Globalization.CultureInfo.InvariantCulture>. Následující příklad ukazuje, jak to udělat:

[!code-csharp-interactive[format with invariant culture](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#7)]

## <a name="conclusion"></a>Závěr

Tento kurz popisuje běžné scénáře použití interpolace řetězců. Další informace o interpolace řetězců, najdete v článku [interpolace](../language-reference/tokens/interpolated.md) tématu. Další informace o formátování typy v rozhraní .NET najdete v tématu [formátovací typy v .NET](../../standard/base-types/formatting-types.md) a [složené formátování](../../standard/base-types/composite-formatting.md) témata.

## <a name="see-also"></a>Viz také:

- <xref:System.String.Format%2A?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- <xref:System.IFormattable?displayProperty=nameWithType>
- [Řetězce](../programming-guide/strings/index.md)
