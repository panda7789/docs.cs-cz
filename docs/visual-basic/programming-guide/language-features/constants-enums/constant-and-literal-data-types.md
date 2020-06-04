---
title: Datové typy konstanty a literálu
ms.date: 07/20/2015
helpviewer_keywords:
- declaring constants [Visual Basic], literal data types
- data types [Visual Basic], declaring
- constants [Visual Basic], declaring
- explicit declarations
- literals [Visual Basic], coercing data type
- declarations [Visual Basic], data types
ms.assetid: 057206d2-3a5b-40b9-b3af-57446f9b52fa
ms.openlocfilehash: b94259326b42104db05d9fc5bb09f686075d0759
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414528"
---
# <a name="constant-and-literal-data-types-visual-basic"></a>Datové typy konstanty a literálu (Visual Basic)
Literál je hodnota, která je vyjádřena jako samotná, nikoli jako hodnota proměnné nebo výsledek výrazu, například číslo 3 nebo řetězec "Hello". Konstanta je smysluplný název, který přebírá místo literálu a uchovává stejnou hodnotu v celém programu, na rozdíl od proměnné, jejíž hodnota se může změnit.  
  
 Pokud je [možnost odvoditelné](../../../language-reference/statements/option-infer-statement.md) `Off` a [Option Strict](../../../language-reference/statements/option-strict-statement.md) `On` , je nutné explicitně deklarovat všechny konstanty s datovým typem. V následujícím příkladu je datový typ `MyByte` explicitně deklarován jako datový typ `Byte` :  
  
 [!code-vb[VbVbalrConstants#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#1)]  
  
 Když `Option Infer` je `On` nebo `Option Strict` `Off` , můžete deklarovat konstantu bez zadání datového typu s `As` klauzulí. Kompilátor určuje typ konstanty z typu výrazu. Číselný celočíselný literál je ve výchozím nastavení převeden na `Integer` datový typ. Výchozí datový typ pro čísla s plovoucí desetinnou čárkou je `Double` a klíčová slova `True` a `False` určují `Boolean` konstantu.  
  
## <a name="literals-and-type-coercion"></a>Literály a převod typu  
 V některých případech můžete chtít vynutit literál na určitý datový typ; například při přiřazování zvláště velké celočíselné literálové hodnoty proměnné typu `Decimal` . Následující příklad vytvoří chybu:  
  
```vb  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 Chyba je výsledkem reprezentace literálu. `Decimal`Datový typ může obsahovat hodnotu, která je větší, ale literál je implicitně reprezentován jako `Long` , což nemůže.  
  
 Literál můžete převést na konkrétní datový typ dvěma způsoby: připojením znaku typu k tomuto typu nebo jeho umístěním do ohraničujících znaků. Znak typu nebo ohraničující znaky musí bezprostředně předcházet nebo následovat po literálu, bez mezer nebo znaků jakéhokoliv druhu.  
  
 Chcete-li provést předchozí příklad práce, můžete `D` k literálu připojit znak typu, což způsobí, že bude reprezentován jako `Decimal` :  
  
 [!code-vb[VbVbalrConstants#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#2)]  
  
 Následující příklad ukazuje správné použití znaků typu a ohraničující znaky:  
  
 [!code-vb[VbVbalrConstants#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#3)]  
  
 V následující tabulce jsou uvedeny ohraničující znaky a znaky, které jsou k dispozici v Visual Basic.  
  
|Datový typ|Ohraničující znak|Znak připojeného typu|  
|---|---|---|  
|`Boolean`|(žádná)|(žádná)|  
|`Byte`|(žádná)|(žádná)|  
|`Char`|"|C|  
|`Date`|#|(žádná)|  
|`Decimal`|(žádná)|D nebo @|  
|`Double`|(žádná)|R nebo #|  
|`Integer`|(žádná)|I nebo%|  
|`Long`|(žádná)|L nebo &|  
|`Short`|(žádná)|S|  
|`Single`|(žádná)|F nebo!|  
|`String`|"|(žádná)|  
  
## <a name="see-also"></a>Viz také

- [Uživatelem definované konstanty](user-defined-constants.md)
- [Postupy: Deklarace konstanty](how-to-declare-a-constant.md)
- [Přehled konstant](constants-overview.md)
- [Option Strict – příkaz](../../../language-reference/statements/option-strict-statement.md)
- [Option Explicit – příkaz](../../../language-reference/statements/option-explicit-statement.md)
- [Přehled výčtů](enumerations-overview.md)
- [Postupy: deklarace výčtu](how-to-declare-enumerations.md)
- [Výčty a kvalifikace názvu](enumerations-and-name-qualification.md)
- [Datové typy](../../../language-reference/data-types/index.md)
- [Konstanty a výčty](../../../language-reference/constants-and-enumerations.md)
