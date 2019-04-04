---
title: $ – interpolace řetězců - C# odkaz
ms.custom: seodec18
description: Interpolace řetězců poskytuje čitelné a pohodlné syntaxe pro formátování výstupní řetězec než tradiční řetězec složené formátování.
ms.date: 03/26/2018
f1_keywords:
- $_CSharpKeyword
- $
helpviewer_keywords:
- $ special character [C#]
- $ language element [C#]
- string interpolation [C#]
- interpolated string [C#]
author: pkulikov
ms.author: ronpet
ms.openlocfilehash: 64728182fe0b758f8da668d19761305e2001f1a5
ms.sourcegitcommit: a3db1a9eafca89f95ccf361bc1833b47fbb2bb30
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/04/2019
ms.locfileid: "58920893"
---
# <a name="---string-interpolation-c-reference"></a>$ – interpolace řetězců (referenční dokumentace jazyka C#)

`$` Speciální znak identifikuje řetězcového literálu jako *interpolovaný řetězec*. Interpolované řetězce se řetězcový literál, který může obsahovat *interpolovaných výrazů*. Po vyřešení interpolovaného řetězce do výsledného řetězce položky, které interpolovaných výrazů jsou nahrazené řetězcové reprezentace výsledku výrazu. Tato funkce je dostupná v jazyce C# 6 a novější verze jazyka.

Interpolace řetězců poskytuje čitelné a pohodlné syntaxe pro vytvoření formátovaného řetězce než [řetězec složené formátování](../../../standard/base-types/composite-formatting.md) funkce. Následující příklad používá obě funkce stejný výstup:

[!code-csharp-interactive[compare with composite formatting](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

## <a name="structure-of-an-interpolated-string"></a>Struktura interpolovaného řetězce

K identifikaci řetězcového literálu jako interpolovaném řetězci, předřaďte ji `$` symbol. Nemůže obsahovat žádné prázdné znaky. mezi `$` a `"` , který spouští řetězcový literál. To způsobí chybu kompilace.

Struktura položka s interpolovaného výrazu je následujícím způsobem:

```
{<interpolatedExpression>[,<alignment>][:<formatString>]}
```

Prvky v hranatých závorkách jsou volitelné. Následující tabulka popisuje jednotlivé prvky:

|Prvek|Popis|
|-------------|-----------------|
|`interpolatedExpression`|Výraz, který vytváří výsledek, který má být formátováno. Řetězcové vyjádření sady `null` výsledkem je <xref:System.String.Empty?displayProperty=nameWithType>.|
|`alignment`|Konstantní výraz, jehož hodnota definuje minimální počet znaků v řetězcovou reprezentaci výsledek interpolovaný výraz. Pokud je pozitivní, řetězcové vyjádření zarovnán doprava; záporná, je zarovnaná doleva. Další informace najdete v tématu [součást zarovnání](../../../standard/base-types/composite-formatting.md#alignment-component).|
|`formatString`|Formátovací řetězec, který je podporována typem výsledku výrazu. Další informace najdete v tématu [součást řetězec formátu](../../../standard/base-types/composite-formatting.md#format-string-component).|

Následující příklad používá volitelný formátování komponent popsaných výše:

[!code-csharp-interactive[specify alignment and format string](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

## <a name="special-characters"></a>Speciální znaky

Zahrnout závorek "{" nebo "}", text vytvořené metodou interpolovaného řetězce, použijte dva složené závorky, "{{" nebo "}}". Další informace najdete v tématu [uvozovací znaky složených závorek](../../../standard/base-types/composite-formatting.md#escaping-braces).

Jako dvojtečka (":") má zvláštní význam v položce interpolovaný výraz, aby bylo možné používat [podmiňovací operátor](../operators/conditional-operator.md) v interpolovaným výrazem, použijte tento výraz v závorkách.

Následující příklad ukazuje, jak zahrnout složené závorky do výsledného řetězce a jak pomocí podmíněného operátoru v interpolovaný výraz:

[!code-csharp-interactive[example with ternary conditional operator](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

Doslovný interpolovaný řetězec začíná `$` znak následovaný `@` znak. Další informace o doslovném řetězci, najdete v článku [řetězec](../keywords/string.md) a [Doslovný identifikátor](verbatim.md) témata.

> [!NOTE]
> `$` Token se musí nacházet před `@` token začal v doslovném interpolovaném řetězci.

## <a name="implicit-conversions-and-specifying-iformatprovider-implementation"></a>Implicitní převody a určení `IFormatProvider` implementace

Existují tři implicitní převody z interpolovaném řetězci:

1. Převod interpolované řetězce, který se <xref:System.String> instanci, která je výsledkem řešení interpolovaný řetězec s interpolovaného výrazu položky nahrazeny správně formátovaná řetězcové reprezentace jejich výsledky. Tento převod používá aktuální jazykové verze.

1. Převod interpolované řetězce, který se <xref:System.FormattableString> instanci, která představuje složený řetězec formátu spolu s výsledky výrazu, který má být formátováno. Který vám umožní vytvořit více výsledný řetězec s specifické pro jazykovou verzi obsahu z jedné <xref:System.FormattableString> instance. Provedete to, který volat jednu z následujících metod:

      - A <xref:System.FormattableString.ToString> přetížení, které vytváří výsledný řetězec pro <xref:System.Globalization.CultureInfo.CurrentCulture>.
      - <xref:System.FormattableString.Invariant%2A> Metodu, která vytváří výsledný řetězec pro <xref:System.Globalization.CultureInfo.InvariantCulture>.
      - A <xref:System.FormattableString.ToString(System.IFormatProvider)> metodu, která vytváří výsledný řetězec pro zadanou jazykovou verzi.

    Můžete také použít <xref:System.FormattableString.ToString(System.IFormatProvider)> metodu k dispozici na uživatelem definované implementace <xref:System.IFormatProvider> rozhraní, které podporuje vlastní formátování. Další informace najdete v tématu [vlastní formátování pomocí ICustomFormatter](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter).

1. Převod interpolovaného řetězce do <xref:System.IFormattable> , jež lze také vytvořit více výsledek řetězce s obsahem specifické pro jazykovou verzi z jedné <xref:System.IFormattable> instance.

Následující příklad používá implicitní převod na <xref:System.FormattableString> vytvořit specifické pro jazykovou verzi výsledný řetězec:

[!code-csharp-interactive[create culture-specific result strings](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

## <a name="additional-resources"></a>Další zdroje

Pokud jste ještě na interpolaci řetězce, najdete v článku [interpolace v C# ](../../tutorials/exploration/interpolated-strings.yml) interaktivního kurzu. Nebo si můžete vyzkoušet [interpolace v C# ](../../tutorials/string-interpolation.md) kurz místně na svém počítači.

## <a name="see-also"></a>Viz také:

- <xref:System.String.Format%2A?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- <xref:System.IFormattable?displayProperty=nameWithType>
- [Složené formátování](../../../standard/base-types/composite-formatting.md)
- [Tabulka formátování číselných výsledků](../keywords/formatting-numeric-results-table.md)
- [Řetězce](../../programming-guide/strings/index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Speciální znaky v jazyce C#](index.md)
- [Referenční dokumentace jazyka C#](../index.md)
