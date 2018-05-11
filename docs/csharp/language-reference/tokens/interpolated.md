---
title: $ – řetězec interpolace (referenční dokumentace jazyka C#)
description: Řetězec interpolace poskytuje čitelnější a pohodlný syntaxe k formátování výstupu řetězec než tradiční řetězec složené formátování.
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
ms.openlocfilehash: 7a2e281dfecdb7baeaeb58ad68232bcd7d371595
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2018
---
# <a name="---string-interpolation-c-reference"></a>$ – řetězec interpolace (referenční dokumentace jazyka C#)

`$` Speciální znak identifikuje řetězcový literál jako *interpolované řetězce*. Interpolované řetězce je řetězcový literál, který může obsahovat *interpolované výrazy*. Po vyřešení interpolované řetězce na řetězec výsledek položky s interpolované výrazy se nahrazují řetězcové vyjádření výsledků výrazu. Tato funkce je k dispozici v C# 6 a novější verze jazyka.

Poskytuje řetězec interpolace čitelnější a pohodlný syntaxe pro vytvoření formátované řetězce než [řetězce složené formátování](../../../standard/base-types/composite-formatting.md) funkce. Následující příklad používá k vytvoření stejný výstup obě funkce:

[!code-csharp-interactive[compare with composite formatting](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

## <a name="structure-of-an-interpolated-string"></a>Struktura interpolované řetězce

K identifikaci řetězcový literál jako interpolované řetězce, předřazení její `$` symbol. Nemůže mít žádné mezer mezi `$` a `"` , začíná řetězec. To způsobí, že chyby kompilace.

Struktura položky s interpolované výrazu je následující:

```
{<interpolatedExpression>[,<alignment>][:<formatString>]}
```

Prvky v hranatých závorkách jsou volitelné. Následující tabulka popisuje jednotlivé prvky.

|Prvek|Popis|
|-------------|-----------------|
|`interpolatedExpression`|Výraz, který vytváří výsledek, který má být formátována. Řetězec reprezentace `null` výsledkem je <xref:System.String.Empty?displayProperty=nameWithType>.|
|`alignment`|Konstantní výraz, jehož hodnota definuje minimální počet znaků v řetězcovou reprezentaci výsledek interpolované výrazu. Pokud kladné, je řetězcová reprezentace vpravo zarovnaný; záporná, je zarovnaný doleva. Další informace najdete v tématu [zarovnání součást](../../../standard/base-types/composite-formatting.md#alignment-component).|
|`formatString`|Řetězec formátu, který podporuje typ výsledku výrazu. Další informace najdete v tématu [součást řetězce formátu](../../../standard/base-types/composite-formatting.md#format-string-component).|

Následující příklad používá volitelné formátování komponent popsaných výše:

[!code-csharp-interactive[specify alignment and format string](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

## <a name="special-characters"></a>Speciální znaky

Zahrnout závorek "{" nebo "}", v textu vyprodukované interpolované řetězce, použijte dva složené závorky "{{" nebo "}}". Další informace najdete v tématu [uvozovací znaky složené závorky](../../../standard/base-types/composite-formatting.md#escaping-braces).

Jako dvojtečkou (":") má zvláštní význam v interpolované výraz položku, aby bylo možné používat [podmíněný operátor](../operators/conditional-operator.md) ve výrazu interpolované uzavřete výrazu v závorkách.

Následující příklad ukazuje, jak se zahrnuje do řetězce výsledek složená závorka a jak používat podmíněný operátor v interpolované výrazu:

[!code-csharp-interactive[example with ternary conditional operator](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

Doslovné interpolované řetězce použití `$` následuje znak `@` znak. Další informace o typu verbatim řetězců najdete v tématu [řetězec](../keywords/string.md) tématu.

> [!NOTE]
> `$` Token musí být před `@` tokenu typu verbatim interpolované řetězce.

## <a name="implicit-conversions-and-specifying-iformatprovider-implementation"></a>Implicitní převody a zadání `IFormatProvider` implementace

Existují tři implicitní převody z interpolované řetězce:

1. Interpolované řetězce pro převod <xref:System.String> instanci, která je výsledkem interpolované řetězce řešení pomocí výrazu interpolované položky nahrazován správně formátovaný řetězec reprezentace jejich výsledky. Tento převod používá aktuální jazykovou verzi.

1. Interpolované řetězce pro převod <xref:System.FormattableString> instanci, která představuje složený formátovací řetězec spolu s výsledky výrazu formátování. Což vám umožní vytvořit více řetězců výsledek s specifické pro jazykovou verzi obsahu z jedné <xref:System.FormattableString> instance. Chcete-li provést volání jednoho z následujících metod:

      - A <xref:System.FormattableString.ToString> přetížení, které vytváří výsledný řetězec pro <xref:System.Globalization.CultureInfo.CurrentCulture>.
      - <xref:System.FormattableString.Invariant%2A> Metoda, která vytváří výsledný řetězec pro <xref:System.Globalization.CultureInfo.InvariantCulture>.
      - A <xref:System.FormattableString.ToString(System.IFormatProvider)> metoda, která vytváří výsledný řetězec pro zadanou jazykovou verzi.

    Můžete taky použít <xref:System.FormattableString.ToString(System.IFormatProvider)> metody můžete zajistit na uživatelem definované implementace <xref:System.IFormatProvider> rozhraní, která podporuje vlastní formátování. Další informace najdete v tématu [vlastní formátování pomocí ICustomFormatter](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter).

1. Interpolované řetězce pro převod <xref:System.IFormattable> instanci, která umožňuje taky vytvořit více výsledek řetězce s obsahem specifické pro jazykovou verzi z jedné <xref:System.IFormattable> instance.

Následující příklad používá implicitní převod na <xref:System.FormattableString> vytvořit výsledek specifické pro jazykovou verzi řetězce:

[!code-csharp-interactive[create culture-specific result strings](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

## <a name="additional-resources"></a>Další zdroje

Pokud nový interpolace řetězec, podívejte se [řetězec interpolace v jazyce C#](../../quick-starts/interpolated-strings.yml) rychlý start. Další příklady najdete v tématu [řetězec interpolace v jazyce C#](../../tutorials/string-interpolation.md) kurzu.

## <a name="see-also"></a>Viz také  
 <xref:System.String.Format%2A?displayProperty=nameWithType>  
 <xref:System.FormattableString?displayProperty=nameWithType>  
 <xref:System.IFormattable?displayProperty=nameWithType>  
 [Složené formátování](../../../standard/base-types/composite-formatting.md)  
 [Řetězce](../../programming-guide/strings/index.md)  
 [Průvodce programováním v jazyce C#](../../programming-guide/index.md)  
 [Speciální znaky v jazyce C#](index.md)  
 [Referenční dokumentace jazyka C#](../index.md)  