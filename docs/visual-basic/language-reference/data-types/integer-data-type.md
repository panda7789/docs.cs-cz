---
title: "Integer – datový typ (Visual Basic)"
ms.date: 04/20/2017
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Integer
- Integer
helpviewer_keywords:
- numbers [Visual Basic], whole
- enumerated values [Visual Basic]
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- literal type characters [Visual Basic], I
- integers [Visual Basic], types
- data types [Visual Basic], integral
- '% identifier type character'
- data types [Visual Basic], assigning
- identifier type characters [Visual Basic], %
- I literal type character [Visual Basic]
- Integer data type
ms.assetid: a8f233b4-4be3-455c-861b-05af2fbb6c60
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 69c7fb6caf5d9a10c7d033d1ba0a05c9230d472c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="integer-data-type-visual-basic"></a>Integer – datový typ (Visual Basic)
Obsahuje 32bitová (4bajtová) celá čísla se znaménkem v rozsahu od -2 147 483 648 do 2 147 483 647.  
  
## <a name="remarks"></a>Poznámky
 `Integer` Datový typ poskytuje optimální výkon procesoru 32-bit. Jiné typy celých čísel se v paměti pomaleji načítají a ukládají.  
  
 Výchozí hodnota `Integer` je 0.  

## <a name="literal-assignments"></a>Literál přiřazení

Můžete deklarace a inicializace `Integer` proměnné jeho přiřazení decimal literál, hexadecimální literál, osmičková literál, nebo (počínaje 2017 Visual Basic) binární literál. Pokud literálu celé číslo je mimo rozsah `Integer` (tj. Pokud je menší než <xref:System.Int32.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.Int32.MaxValue?displayProperty=nameWithType>, dojde k chybě kompilace.

V následujícím příkladu, celá čísla rovno 16,342, která jsou reprezentovány jako decimal, šestnáctkové, a binární literály jsou přiřazeny k `Integer` hodnoty.

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Int)]  

> [!NOTE]
> Použijte předponu `&h` nebo `&H` k označení hexadecimální literál, předponu `&b` nebo `&B` k označení binární literál a předponu `&o` nebo `&O` k označení osmičková literál. Decimal literály mít žádná předpona.

Počínaje 2017 Visual Basic, můžete také použít znak podtržítka `_`, jako oddělovač číslice za účelem zlepšení čitelnosti jako následující příklad ukazuje.

[!code-vb[integer](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#IntS)]  

Číselné literály může také obsahovat `I` [znak typu](../../programming-guide\language-features\data-types/type-characters.md) k označení `Integer` datového typu, jak ukazuje následující příklad.

```vb
Dim number = &H035826I
```

## <a name="programming-tips"></a>Tipy pro programování

-   **Spolupráce aspekty.** Pokud jsou během propojení s součásti, které nejsou určeny pro rozhraní .NET Framework, jako je například objekty automatizace nebo COM, nezapomeňte, že `Integer` má odlišné datové šířku (16 bitů) v jiných prostředích. Argument 16bitové předáte pro tyto součásti, deklarujte ji jako `Short` místo `Integer` v váš nový kód jazyka Visual Basic.  
  
-   **Rozšíření.** `Integer` Datový typ rozšiřuje na `Long`, `Decimal`, `Single`, nebo `Double`. To znamená, že můžete převést `Integer` na některý z těchto typů bez zjištění <xref:System.OverflowException?displayProperty=nameWithType> chyby.  
  
-   **Znaky typu.** Připojování znak typu literálu `I` k literál vynutí, aby `Integer` datového typu. Připojování znak typu identifikátoru `%` na všechny identifikátor vynutí jeho `Integer`.  
  
-   **Typ Framework.** Typ odpovídající v rozhraní .NET Framework je <xref:System.Int32?displayProperty=nameWithType> struktura.  
  
## <a name="range"></a>Rozsah

Pokud se pokusíte nastavit proměnnou celočíselného typu na číslo, které není v rozsahu tohoto typu, dojde k chybě. Pokud se ji pokusíte nastavit na zlomek, bude číslo zaokrouhleno nahoru nebo dolů na nejbližší celočíselnou hodnotu. Pokud je číslo stejně vzdáleno od dvou celočíselných hodnot, je hodnota zaokrouhlena nejbližší sudé celé číslo. Toto chování minimalizuje zaokrouhlovací chyby, které vznikají při konzistentním zaokrouhlování střední hodnoty v jednom směru. Následující kód znázorňuje příklady zaokrouhlení.  

```vb  
' The valid range of an Integer variable is -2147483648 through +2147483647.  
Dim k As Integer  
' The following statement causes an error because the value is too large.  
k = 2147483648  
' The following statement sets k to 6.  
k = 5.9  
' The following statement sets k to 4  
k = 4.5  
' The following statement sets k to 6  
' Note, Visual Basic uses banker’s rounding (toward nearest even number)  
k = 5.5  
```

## <a name="see-also"></a>Viz také

<xref:System.Int32?displayProperty=nameWithType>   
 [Datové typy](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Long – datový typ](../../../visual-basic/language-reference/data-types/long-data-type.md)  
 [Short – datový typ](../../../visual-basic/language-reference/data-types/short-data-type.md)  
 [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Souhrn konverze](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
