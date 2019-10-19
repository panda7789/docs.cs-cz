---
title: Datové typy konstanty a literálu (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declaring constants [Visual Basic], literal data types
- data types [Visual Basic], declaring
- constants [Visual Basic], declaring
- explicit declarations
- literals [Visual Basic], coercing data type
- declarations [Visual Basic], data types
ms.assetid: 057206d2-3a5b-40b9-b3af-57446f9b52fa
ms.openlocfilehash: 9db7fa3f36021a39fafe6cf3da5af7070f0b5b0d
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582980"
---
# <a name="constant-and-literal-data-types-visual-basic"></a>Datové typy konstanty a literálu (Visual Basic)
Literál je hodnota, která je vyjádřena jako samotná, nikoli jako hodnota proměnné nebo výsledek výrazu, například číslo 3 nebo řetězec "Hello". Konstanta je smysluplný název, který přebírá místo literálu a uchovává stejnou hodnotu v celém programu, na rozdíl od proměnné, jejíž hodnota se může změnit.  
  
 Je-li [možnost odvozena](../../../../visual-basic/language-reference/statements/option-infer-statement.md) `Off` a [možnost Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) je `On`, je nutné explicitně deklarovat všechny konstanty s datovým typem. V následujícím příkladu je datový typ `MyByte` explicitně deklarován jako datový typ `Byte`:  
  
 [!code-vb[VbVbalrConstants#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#1)]  
  
 Pokud je `Option Infer` `On` nebo `Option Strict` `Off`, můžete deklarovat konstantu bez určení datového typu s klauzulí `As`. Kompilátor určuje typ konstanty z typu výrazu. Číselný celočíselný literál je ve výchozím nastavení převeden na datový typ `Integer`. Výchozí datový typ pro čísla s plovoucí desetinnou čárkou je `Double` a klíčová slova `True` a `False` určují `Boolean`ou konstantu.  
  
## <a name="literals-and-type-coercion"></a>Literály a převod typu  
 V některých případech můžete chtít vynutit literál na určitý datový typ; například při přiřazování zvláště velké celočíselné literálové hodnoty proměnné typu `Decimal`. Následující příklad vytvoří chybu:  
  
```vb  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 Chyba je výsledkem reprezentace literálu. @No__t_0 datový typ může obsahovat hodnotu, která je větší, ale literál je implicitně reprezentován jako `Long`, což nemůže.  
  
 Literál můžete převést na konkrétní datový typ dvěma způsoby: připojením znaku typu k tomuto typu nebo jeho umístěním do ohraničujících znaků. Znak typu nebo ohraničující znaky musí bezprostředně předcházet nebo následovat po literálu, bez mezer nebo znaků jakéhokoliv druhu.  
  
 Chcete-li provést předchozí příklad práce, můžete k literálu připojit `D` typ znaku, který způsobí, že bude reprezentován jako `Decimal`:  
  
 [!code-vb[VbVbalrConstants#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#2)]  
  
 Následující příklad ukazuje správné použití znaků typu a ohraničující znaky:  
  
 [!code-vb[VbVbalrConstants#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#3)]  
  
 V následující tabulce jsou uvedeny ohraničující znaky a znaky, které jsou k dispozici v Visual Basic.  
  
|Datový typ|Ohraničující znak|Znak připojeného typu|  
|---|---|---|  
|`Boolean`|nTato|nTato|  
|`Byte`|nTato|nTato|  
|`Char`|"|C|  
|`Date`|#|nTato|  
|`Decimal`|nTato|D nebo @|  
|`Double`|nTato|R nebo #|  
|`Integer`|nTato|I nebo%|  
|`Long`|nTato|L nebo &|  
|`Short`|nTato|S|  
|`Single`|nTato|F nebo!|  
|`String`|"|nTato|  
  
## <a name="see-also"></a>Viz také:

- [Uživatelem definované konstanty](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)
- [Postupy: Deklarace konstanty](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)
- [Přehled konstant](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [Příkaz Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Příkaz Option Explicit](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Přehled výčtů](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [Postupy: deklarace výčtu](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Výčty a kvalifikace názvu](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Datové typy](../../../../visual-basic/language-reference/data-types/index.md)
- [Konstanty a výčty](../../../../visual-basic/language-reference/constants-and-enumerations.md)
