---
title: Short – datový typ
ms.date: 01/31/2018
f1_keywords:
- vb.Short
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- S literal type character [Visual Basic]
- Short data type
- literal type characters [Visual Basic], S
ms.assetid: 65fcbcf3-a841-400e-885e-301497729a8b
ms.openlocfilehash: 8dfdfb56de32e4b3a96729b09ccf46a6fee9a424
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400727"
---
# <a name="short-data-type-visual-basic"></a>Krátký datový typ (Visual Basic)

Pojme podepsaná 16bitová (2bajtová) celá čísla, která se pohybují v hodnotě od -32 768 do 32 767.  
  
## <a name="remarks"></a>Poznámky  

 Pomocí `Short` datového typu můžete obsahovat celočíselné hodnoty, `Integer`které nevyžadují úplnou šířku dat aplikace . V některých případech může běžný jazyk `Short` runtime pečlivě zabalit proměnné a ušetřit spotřebu paměti.  
  
 Výchozí hodnota `Short` je 0.  
  
## <a name="literal-assignments"></a>Doslovná přiřazení

Proměnnou `Short` můžete deklarovat a inicializovat přiřazením desetinného literálu, šestnáctkového literálu, osmičkového literálu nebo (počínaje jazykem Visual Basic 2017) binárníliterál. Pokud celé číslo literál je `Short` mimo rozsah (to znamená, <xref:System.Int16.MinValue?displayProperty=nameWithType> pokud <xref:System.Int16.MaxValue?displayProperty=nameWithType>je menší než nebo větší než , dojde k chybě kompilace.

V následujícím příkladu jsou celá čísla rovna 1 034, která jsou reprezentována jako desetinné, šestnáctkové a binární literály, implicitně převedeny z [Integer](integer-data-type.md) na `Short` hodnoty.

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> Předponu nebo `&h` `&H` k označení šestnáctkového `&b` literálu, předpony nebo `&B` k označení binárního literálu `&o` a `&O` předpony nebo k označení osmičkového literálu. Desetinné literály nemají předponu.

Počínaje visual basicem 2017, můžete také `_`použít znak podtržítko , jako oddělovač číslic pro zvýšení čitelnosti, jak ukazuje následující příklad.

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

Počínaje jazykem Visual Basic 15.5 můžete také`_`použít znak podtržítka ( ) jako úvodní oddělovač mezi předponou a šestnáctkovými, binárními nebo osmičkovými číslicemi. Například:

```vb
Dim number As Short = &H_3264
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

Číselné literály mohou `S` také obsahovat `Short` znak [typu](../../programming-guide/language-features/data-types/type-characters.md) pro označení datového typu, jak ukazuje následující příklad.

```vb
Dim number = &H_3264S
```

## <a name="programming-tips"></a>Tipy k programování

- **Rozšíření.** Datový `Short` typ se `Integer`rozšiřuje `Long` `Decimal`na `Single`, `Double`, , , nebo . To znamená, `Short` že můžete převést na některý <xref:System.OverflowException?displayProperty=nameWithType> z těchto typů bez výskytu chyby.  
  
- **Zadejte znaky.** Připojení znaku `S` typu literálu k literálu jej vynutí na `Short` datový typ. `Short`nemá žádný znak typu identifikátoru.  
  
- **Typ rámce.** Odpovídající typ v rozhraní .NET <xref:System.Int16?displayProperty=nameWithType> Framework je struktura.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Int16?displayProperty=nameWithType>
- [Datové typy](../../../visual-basic/language-reference/data-types/index.md)
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Souhrn převodu](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Integer – datový typ](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [Datový typ Long](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
