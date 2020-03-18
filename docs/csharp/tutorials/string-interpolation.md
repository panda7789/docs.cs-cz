---
title: 'Interpolace řetězců v C #'
description: Zjistěte, jak zahrnout formátovaný výraz výsledky ve výsledku řetězce v C# s řetězci interpolace.
author: pkulikov
ms.technology: csharp-fundamentals
ms.date: 09/02/2019
ms.openlocfilehash: b901ae661ebd4af625d9f3c999b0eb50dda1990d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73039215"
---
# <a name="string-interpolation-in-c"></a>Interpolace řetězců v C\#

Tento kurz ukazuje, jak používat [interpolaci řetězce](../language-reference/tokens/interpolated.md) k formátování a zahrnutí výsledků výrazu do výsledného řetězce. Příklady předpokládají, že jste obeznámeni se základními koncepty jazyka C# a formátováním typu .NET. Pokud s interpolací řetězců nebo formátováním typu .NET teprve začínáte, podívejte se nejprve na [kurz interaktivní interpolace řetězců.](exploration/interpolated-strings.yml) Další informace o formátování typů v rozhraní .NET naleznete v tématu [Typy formátování v rozhraní .NET.](../../standard/base-types/formatting-types.md)

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

## <a name="introduction"></a>Úvod

Funkce [interpolace řetězců](../language-reference/tokens/interpolated.md) je postavena na funkci [složeného formátování](../../standard/base-types/composite-formatting.md) a poskytuje čitelnější a pohodlnější syntaxi pro zahrnutí formátovaného výrazu do výsledného řetězce.

Chcete-li identifikovat literál řetězce jako interpolovaný řetězec, předřávejte jej symbolem. `$` Můžete vložit libovolný platný výraz Jazyka C#, který vrátí hodnotu v interpolovaném řetězci. V následujícím příkladu, jakmile je výraz vyhodnocen, jeho výsledek je převeden na řetězec a zahrnuty do výsledkového řetězce:

[!code-csharp-interactive[string interpolation example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#1)]

Jak ukazuje příklad, zahrnete výraz do interpolovaného řetězce tím, že jej ohraničujete závorkami:

```csharp
{<interpolationExpression>}
```

Interpolované řetězce podporují všechny možnosti funkce [složeného formátování řetězce.](../../standard/base-types/composite-formatting.md) To z nich dělá čitelnější alternativu <xref:System.String.Format%2A?displayProperty=nameWithType> k použití metody.

## <a name="how-to-specify-a-format-string-for-an-interpolation-expression"></a>Jak zadat formátovací řetězec pro výraz interpolace

Formátovací řetězec, který je podporován typem výsledku výrazu, určíte podle výrazu interpolace s dvojtečkou (":") a formátovacím řetězcem:

```csharp
{<interpolationExpression>:<formatString>}
```

Následující příklad ukazuje, jak zadat standardní a vlastní formátovací řetězce pro výrazy, které vytvářejí datum a čas nebo číselné výsledky:

[!code-csharp-interactive[format string example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#2)]

Další informace naleznete v části [Komponenta formátovacího řetězce](../../standard/base-types/composite-formatting.md#format-string-component) v tématu [Složené formátování.](../../standard/base-types/composite-formatting.md) Tato část obsahuje odkazy na témata, která popisují standardní a vlastní formátovací řetězce podporované základními typy rozhraní .NET.

## <a name="how-to-control-the-field-width-and-alignment-of-the-formatted-interpolation-expression"></a>Jak řídit šířku pole a zarovnání formátovaného interpolačního výrazu

Minimální šířku pole a zarovnání výsledku formátovaného výrazu určíte tak, že se budete řídit interpolačním výrazem s čárkou (",") a konstantním výrazem:

```csharp
{<interpolationExpression>,<alignment>}
```

Pokud je hodnota *zarovnání* kladná, výsledek formátovaného výrazu je zarovnán doprava; Pokud je záporná, je zarovnána doleva.

Pokud potřebujete zadat zarovnání i formátovací řetězec, začněte komponentou zarovnání:

```csharp
{<interpolationExpression>,<alignment>:<formatString>}
```

Následující příklad ukazuje, jak určit zarovnání a používá znaky kanálu ("|") k vymezení textových polí:

[!code-csharp-interactive[alignment example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#3)]

Jak ukazuje ukázkový výstup, pokud délka výsledku formátovaného výrazu překročí zadanou šířku pole, hodnota *zarovnání* bude ignorována.

Další informace naleznete v části [Součást zarovnání](../../standard/base-types/composite-formatting.md#alignment-component) v tématu [Složené formátování.](../../standard/base-types/composite-formatting.md)

## <a name="how-to-use-escape-sequences-in-an-interpolated-string"></a>Použití řídicích sekvencí v interpolovaném řetězci

Interpolované řetězce podporují všechny sekvence escape, které lze použít v běžných řetězcových literálech. Další informace naleznete v [tématu String escape sequences](../programming-guide/strings/index.md#string-escape-sequences).

Chcete-li interpretovat escape sekvence doslova, použijte [doslovný](../language-reference/tokens/verbatim.md) řetězec literál. Interpolovaný doslovný řetězec začíná `$` znakem následovaným znakem. `@` Počínaje C# 8.0, můžete `$` použít `@` a tokeny v `$@"..."` `@$"..."` libovolném pořadí: oba a jsou platné interpolované doslovné řetězce.

Chcete-li zahrnout závorku {" nebo "}", použijte do výsledného řetězce dvě závorky{{" nebo "}}". Další informace naleznete v části [Escaping Braces](../../standard/base-types/composite-formatting.md#escaping-braces) v tématu [složené formátování.](../../standard/base-types/composite-formatting.md)

Následující příklad ukazuje, jak zahrnout složené závorky do výsledného řetězce a vytvořit doslovný interpolovaný řetězec:

[!code-csharp-interactive[escape sequence example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#4)]

## <a name="how-to-use-a-ternary-conditional-operator--in-an-interpolation-expression"></a>Použití ternárního podmíněného `?:` operátoru ve výrazu interpolace

Jako dvojtečka (":") má zvláštní význam v položce s výrazem interpolace, aby bylo možné použít [podmíněný operátor](../language-reference/operators/conditional-operator.md) ve výrazu, uzavřete jej do závorek, jak ukazuje následující příklad:

[!code-csharp-interactive[conditional operator example](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#5)]

## <a name="how-to-create-a-culture-specific-result-string-with-string-interpolation"></a>Jak vytvořit výsledný řetězec specifický pro jazykovou verzi s interpolací řetězců

Ve výchozím nastavení používá interpolovaný řetězec aktuální <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType> jazykovou verzi definovanou vlastností pro všechny operace formátování. Použijte implicitní převod interpolovaného <xref:System.FormattableString?displayProperty=nameWithType> řetězce na <xref:System.FormattableString.ToString(System.IFormatProvider)> instanci a zavolejte její metodu k vytvoření výsledného řetězce specifického pro jazykovou verzi. Následující příklad ukazuje, jak to udělat:

[!code-csharp-interactive[specify different cultures](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#6)]

Jak ukazuje příklad, můžete <xref:System.FormattableString> použít jednu instanci ke generování více řetězců výsledků pro různé jazykové verze.

## <a name="how-to-create-a-result-string-using-the-invariant-culture"></a>Jak vytvořit výsledný řetězec pomocí invariantní jazykové verze

Spolu s <xref:System.FormattableString.ToString(System.IFormatProvider)?displayProperty=nameWithType> metodou můžete použít <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> statickou metodu k vyřešení interpolovaného <xref:System.Globalization.CultureInfo.InvariantCulture>řetězce na výsledný řetězec pro . Následující příklad ukazuje, jak to udělat:

[!code-csharp-interactive[format with invariant culture](~/samples/snippets/csharp/tutorials/string-interpolation/Program.cs#7)]

## <a name="conclusion"></a>Závěr

Tento kurz popisuje běžné scénáře použití interpolace řetězce. Další informace o interpolaci řetězců naleznete v tématu [Interpolace řetězce.](../language-reference/tokens/interpolated.md) Další informace o typech formátování v rozhraní .NET naleznete v tématech Typy formátování v tématech [rozhraní .NET](../../standard/base-types/formatting-types.md) a [Složené formátování.](../../standard/base-types/composite-formatting.md)

## <a name="see-also"></a>Viz také

- <xref:System.String.Format%2A?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- <xref:System.IFormattable?displayProperty=nameWithType>
- [Řetězce](../programming-guide/strings/index.md)
