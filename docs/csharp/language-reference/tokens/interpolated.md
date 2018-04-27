---
title: $ – řetězec interpolace (referenční dokumentace jazyka C#)
description: Řetězec interpolace poskytuje čitelnější a pohodlný syntaxe k formátování výstupu řetězec než tradiční řetězec složené formátování.
ms.date: 03/26/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- $_CSharpKeyword
- $
helpviewer_keywords:
- $ special character [C#]
- $ language element [C#]
- string interpolation [C#]
- interpolated string [C#]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cabb40c9c449780c8c2a504aad3e53938e2ed957
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="---string-interpolation-c-reference"></a>$ – řetězec interpolace (referenční dokumentace jazyka C#)

`$` Speciální znak identifikuje řetězcový literál jako *interpolované řetězce*. Interpolované řetězec vypadá jako řetězec šablony, která obsahuje *interpolované výrazy*. Po vyřešení interpolované řetězce na řetězec výsledek položky s interpolované výrazy se nahrazují řetězcové vyjádření výsledků výrazu. Tato funkce je k dispozici v C# 6 a novější verze.

Poskytuje řetězec interpolace čitelnější a pohodlný syntaxe pro vytvoření formátované řetězce než [řetězce složené formátování](../../../standard/base-types/composite-formatting.md) funkce. Následující příklad používá k vytvoření stejný výstup obě funkce:

[!code-csharp-interactive[compare with composite formatting](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

> [!NOTE]
> Nemůže mít žádné mezer mezi `$` a `"` , začíná řetězec. To způsobí, že chyby kompilace.

Struktura položky s interpolované výrazu je následující:

```
{<interpolatedExpression>[,<alignment>][:<formatString>]}
```

Prvky v hranatých závorkách jsou volitelné. Následující tabulka popisuje jednotlivé prvky.

|Prvek|Popis|
|-------------|-----------------|
|`interpolatedExpression`|Výraz k vyhodnocení k získání výsledku, který má být formátována. Řetězec reprezentace `null` výsledkem je <xref:System.String.Empty?displayProperty=nameWithType>.|
|`alignment`|Konstantní výraz, jehož hodnota definuje minimální počet znaků v řetězcovou reprezentaci výsledek interpolované výrazu. Pokud kladné, je řetězcová reprezentace vpravo zarovnaný; záporná, je zarovnaný doleva. Další informace najdete v tématu [zarovnání součást](../../../standard/base-types/composite-formatting.md#alignment-component).|
|`formatString`|Řetězec standardní nebo vlastní formát, který podporuje typ výsledku výrazu. Další informace najdete v tématu [součást řetězce formátu](../../../standard/base-types/composite-formatting.md#format-string-component).|

Následující příklad používá volitelné formátování komponent popsaných výše:

[!code-csharp-interactive[specify alignment and format string](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

Zahrnout složená závorka ("{" nebo "}") v textu vyprodukované interpolované řetězce, použijte dva složené závorky "{{" nebo "}}". Další informace najdete v tématu [uvozovací znaky složené závorky](../../../standard/base-types/composite-formatting.md#escaping-braces).

Dvojtečkou (:) má zvláštní význam interpolované výraz položku, aby bylo možné používat [podmíněný operátor](../operators/conditional-operator.md) ve výrazu interpolované uzavřete výrazu v závorkách.

Následující příklad ukazuje, jak se zahrnuje do řetězce výsledek složená závorka a jak používat podmíněný operátor v interpolované výrazu:

[!code-csharp-interactive[example with ternary conditional operator](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

Doslovné interpolované řetězce použití `$` následuje znak `@` znak. Další informace o typu verbatim řetězců najdete v tématu [řetězec](../keywords/string.md) tématu.

> [!NOTE]
> `$` Token musí být před `@` tokenu typu verbatim interpolované řetězce.

Existují tři implicitní převody z interpolované řetězce:

1. Interpolované řetězce pro převod <xref:System.String> instanci, která je výsledkem interpolované řetězce řešení pomocí výrazu interpolované položky nahrazován správně formátovaný řetězec reprezentace jejich výsledky. Tento převod používá aktuální jazykovou verzi.

1. Interpolované řetězce pro převod <xref:System.FormattableString> instanci, která představuje složený formátovací řetězec spolu s výsledky výrazu formátování. Což vám umožní vytvořit více řetězců výsledek s specifické pro jazykovou verzi obsahu z jedné <xref:System.FormattableString> instance. Chcete-li provést volání jednoho z následujících metod:

      - A <xref:System.FormattableString.ToString> přetížení, které vytváří výsledný řetězec pro <xref:System.Globalization.CultureInfo.CurrentCulture>.
      - A <xref:System.FormattableString.Invariant%2A> metoda, která vytváří výsledný řetězec pro <xref:System.Globalization.CultureInfo.InvariantCulture>.
      - A <xref:System.FormattableString.ToString(System.IFormatProvider)> metoda, která vytváří výsledný řetězec pro zadanou jazykovou verzi.

1. Interpolované řetězce pro převod <xref:System.IFormattable> instanci, která umožňuje taky vytvořit více výsledek řetězce s obsahem specifické pro jazykovou verzi z jedné <xref:System.IFormattable> instance.

Následující příklad používá implicitní převod na <xref:System.FormattableString> vytvořit výsledek specifické pro jazykovou verzi řetězce:

[!code-csharp-interactive[create culture-specific result strings](../../../../samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

Pokud začínáte interpolace řetězec, podívejte se [řetězec interpolace v jazyce C#](../../quick-starts/interpolated-strings.yml) rychlý start. Další příklady najdete v tématu [řetězec interpolace kurzu](../../tutorials/string-interpolation.md).

## <a name="see-also"></a>Viz také  
 <xref:System.String.Format%2A?displayProperty=nameWithType>  
 <xref:System.FormattableString?displayProperty=nameWithType>  
 <xref:System.IFormattable?displayProperty=nameWithType>  
 [Složené formátování](../../../standard/base-types/composite-formatting.md)  
 [Řetězce](../../../csharp/programming-guide/strings/index.md)  
 [Speciální znaky v jazyce C#](../../../csharp/language-reference/tokens/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  