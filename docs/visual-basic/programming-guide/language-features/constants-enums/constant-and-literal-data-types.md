---
title: "Datové typy konstanty a literálu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declaring constants [Visual Basic], literal data types
- data types [Visual Basic], declaring
- constants [Visual Basic], declaring
- explicit declarations
- literals [Visual Basic], coercing data type
- declarations [Visual Basic], data types
ms.assetid: 057206d2-3a5b-40b9-b3af-57446f9b52fa
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 554753e26d185593ce43b741b3b2f9e3cb1ad6dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="constant-and-literal-data-types-visual-basic"></a>Datové typy konstanty a literálu (Visual Basic)
Literál je hodnota, která je vyjádřena jako samotný a nikoli jako hodnota proměnné nebo výsledek výrazu, například číslo 3 nebo text "Hello". Konstanta je smysluplný název, který přebírá místo literál a uchovává tento stejnou hodnotu v rámci programu, a proměnnou, jehož hodnota může změnit.  
  
 Když [Option Infer –](../../../../visual-basic/language-reference/statements/option-infer-statement.md) je `Off` a [možnost striktní](../../../../visual-basic/language-reference/statements/option-strict-statement.md) je `On`, musíte deklarovat všechny konstanty explicitně s datovým typem. V následujícím příkladu, datový typ `MyByte` explicitně je deklarován jako datový typ `Byte`:  
  
 [!code-vb[VbVbalrConstants#1](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_1.vb)]  
  
 Když `Option Infer` je `On` nebo `Option Strict` je `Off`, můžou deklarovat konstanta bez zadání datový typ s `As` klauzule. Kompilátor Určuje typ konstanty z typu výraz. Ve výchozím nastavení je přetypovat celé číselný literál číslo `Integer` datového typu. Výchozí datový typ pro čísla s plovoucí desetinnou čárkou je `Double`a klíčová slova `True` a `False` zadejte `Boolean` konstantní.  
  
## <a name="literals-and-type-coercion"></a>Literály a převod typu  
 V některých případech můžete chtít vynutit literál na konkrétní typ; například při přiřazování zvlášť velké integrální literálovou hodnotou proměnné typu `Decimal`. Následující příklad vytvoří chybu:  
  
```  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 Chyba výsledků reprezentace literál. `Decimal` Datový typ může obsahovat hodnotu velké, ale literálové implicitně vyjádřené `Long`, který nelze.  
  
 Můžete coerce literál na konkrétní typ. dvěma způsoby: připojením – znak typu k němu nebo tím, že v rámci uzavření znaků. – Znak typu nebo uzavření znaky musí okamžitě předcházet nebo postupujte podle literál bez použité místo nebo znaků jakéhokoli druhu.  
  
 Chcete-li předchozí příklad fungovat, můžete připojit `D` zadejte znak, který má literál, což způsobí, že mohla být reprezentován jako `Decimal`:  
  
 [!code-vb[VbVbalrConstants#2](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_2.vb)]  
  
 Následující příklad ukazuje správné použití typu znaků a nadřazených znaků:  
  
 [!code-vb[VbVbalrConstants#3](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_3.vb)]  
  
 Následující tabulka uvádí nadřazených znaků a typů znaků k dispozici v [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
|Datový typ|Nadřazených znak|Znak připojením typu|  
|---|---|---|  
|`Boolean`|(žádný)|(žádný)|  
|`Byte`|(žádný)|(žádný)|  
|`Char`|"|C|  
|`Date`|#|(žádný)|  
|`Decimal`|(žádný)|D nebo @|  
|`Double`|(žádný)|R nebo #|  
|`Integer`|(žádný)|I nebo %|  
|`Long`|(žádný)|L nebo &|  
|`Short`|(žádný)|S|  
|`Single`|(žádný)|F nebo!|  
|`String`|"|(žádný)|  
  
## <a name="see-also"></a>Viz také  
 [Uživatelem definované konstanty](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)  
 [Postupy: deklarace konstanty](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)  
 [Přehled konstant](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [Option Strict – příkaz](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Option Explicit – příkaz](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [Přehled výčtů](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)  
 [Postupy: deklarace výčtů](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [Výčty a kvalifikace názvu](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [Datové typy](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Konstanty a výčty](../../../../visual-basic/language-reference/constants-and-enumerations.md)
