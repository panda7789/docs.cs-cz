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
ms.openlocfilehash: 269045dcfec14fafe878c2716490c93e79efe3d7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978212"
---
# <a name="constant-and-literal-data-types-visual-basic"></a>Datové typy konstanty a literálu (Visual Basic)
Literál je hodnota, která je vyjádřena jako samotný, nikoli jako hodnota proměnné nebo výsledku výrazu, například číslo 3 nebo řetězec "Hello". Konstanta je smysluplný název, který probíhá literály a ponechá tato stejná hodnota v celém programu, na rozdíl od proměnné, jejíž hodnota se může změnit.  
  
 Když [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) je `Off` a [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) je `On`, je třeba deklarovat všechny konstanty explicitně s datovým typem. V následujícím příkladu, datový typ `MyByte` je explicitně deklarována jako datový typ `Byte`:  
  
 [!code-vb[VbVbalrConstants#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#1)]  
  
 Když `Option Infer` je `On` nebo `Option Strict` je `Off`, je možné deklarovat konstanty bez zadání datový typ s `As` klauzuli. Kompilátor Určuje typ konstanty z typu výrazu. Ve výchozím nastavení je přetypování číselné celočíselný literál `Integer` datového typu. Výchozí datový typ pro čísla s plovoucí desetinnou čárkou je `Double`a klíčová slova `True` a `False` zadat `Boolean` konstantní.  
  
## <a name="literals-and-type-coercion"></a>Literály a převod typu  
 V některých případech můžete chtít vynutit literál na konkrétní datový typ; například při přiřazování k proměnné typu zejména velkou celočíselnou hodnotu literálu `Decimal`. Následující příklad generuje chybu:  
  
```  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 Chyba výsledků z reprezentace literál. `Decimal` Datový typ může obsahovat hodnotu velké, ale literálu je implicitně reprezentována jako `Long`, které nemohou.  
  
 Můžete vynucení literál na konkrétní datový typ dvěma způsoby: přidáním znaku typu nebo tak, že v rámci nadřazené znaků. Znak typu nebo orámování znaků musí bezprostředně předcházet nebo postupujte podle literál bez použité místo nebo znaky jakéhokoli druhu.  
  
 Aby předchozí příklad pracovat, můžete připojit `D` zadejte znak pro literál, který způsobí, že aby se dala vyjádřit jako `Decimal`:  
  
 [!code-vb[VbVbalrConstants#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#2)]  
  
 Následující příklad ukazuje správné použití typu a nadřazeného znaků:  
  
 [!code-vb[VbVbalrConstants#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#3)]  
  
 Následující tabulka uvádí nadřazeného znaky a znaky typu, které jsou k dispozici v jazyce Visual Basic.  
  
|Datový typ|Vnější znak|Znak typu připojený|  
|---|---|---|  
|`Boolean`|(žádné)|(žádné)|  
|`Byte`|(žádné)|(žádné)|  
|`Char`|"|C|  
|`Date`|#|(žádné)|  
|`Decimal`|(žádné)|D nebo @|  
|`Double`|(žádné)|R nebo #|  
|`Integer`|(žádné)|Nebo %|  
|`Long`|(žádné)|L nebo &|  
|`Short`|(žádné)|S|  
|`Single`|(žádné)|F nebo!|  
|`String`|"|(žádné)|  
  
## <a name="see-also"></a>Viz také:
- [Uživatelem definované konstanty](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)
- [Postupy: Deklarace konstanty](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)
- [Přehled konstant](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [Příkaz Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Příkaz Option Explicit](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [Přehled výčtů](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [Postupy: Deklarace výčtů](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [Výčty a kvalifikace názvu](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [Datové typy](../../../../visual-basic/language-reference/data-types/index.md)
- [Konstanty a výčty](../../../../visual-basic/language-reference/constants-and-enumerations.md)
