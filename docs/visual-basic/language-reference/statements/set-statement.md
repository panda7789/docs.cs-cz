---
title: Set – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Set
helpviewer_keywords:
- property procedures [Visual Basic], Set statements
- Set statement [Visual Basic]
- Set statement [Visual Basic], syntax
- write-only properties
- properties [Visual Basic], write-only
ms.assetid: 9ecc27b4-df84-420d-9075-db25455fb3cd
ms.openlocfilehash: dbc48d14bac54809e4ddd12c87429bf407169950
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604832"
---
# <a name="set-statement-visual-basic"></a>Set – příkaz (Visual Basic)
Deklaruje `Set` procedura property sloužící k přidělování hodnotu vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## <a name="parts"></a>Součásti  
 `attributelist`  
 Volitelné. V tématu [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md).  
  
 `accessmodifier`  
 Volitelné na maximálně jedno z `Get` a `Set` příkazy v této vlastnosti. Může být jedna z následujících akcí:  
  
-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
-   [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
-   `Protected Friend`  
  
 V tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `value`  
 Požadováno. Parametr, který obsahuje novou hodnotu pro vlastnost.  
  
 `datatype`  
 Požadováno pokud `Option Strict` je `On`. Datový typ `value` parametr. Datový typ zadaný musí být stejný jako datový typ vlastnosti kde to `Set` příkaz je deklarován.  
  
 `statements`  
 Volitelné. Jeden nebo více příkazů, které při spuštění `Set` vlastnost procedura je volána.  
  
 `End Set`  
 Požadováno. Ukončí definice `Set` procedura property.  
  
## <a name="remarks"></a>Poznámky  
 Všech vlastností, musí mít `Set` procedura property Pokud je vlastnost označena `ReadOnly`. `Set` Postup slouží k nastavení hodnoty vlastnosti.  
  
 Visual Basic automaticky volá vlastnost `Set` procedury při příkazu přiřazení obsahuje hodnotu k uložení vlastností.  
  
 Parametr, který se předá jazyka Visual Basic `Set` postup při přiřazení vlastnosti. Pokud nezadáte parametr pro `Set`, integrované vývojové prostředí (IDE) používá implicitní parametr s názvem `value`. Parametr obsahuje hodnota, která má být přiřazeno k vlastnosti. Obvykle uložte tuto hodnotu v privátní místní proměnné a obnoví v něm vždy, když `Get` procedura je volána.  
  
 Tělo deklarace vlastnosti může obsahovat pouze vlastnosti `Get` a `Set` postupy mezi [Property – příkaz](../../../visual-basic/language-reference/statements/property-statement.md) a `End Property` příkaz. Nelze uložit jakoukoli jinou hodnotu než tyto postupy. Konkrétně ho Nejde uložit aktuální hodnotu vlastnosti. Tato hodnota mimo vlastnost, musí uložit, protože pokud ukládá uvnitř buď procedury vlastností, jiné procedury vlastnosti nelze k němu přístup. Obvyklé přístup je pro uložení hodnotu v [privátní](../../../visual-basic/language-reference/modifiers/private.md) proměnná deklarována na stejné úrovni jako vlastnost. Je nutné definovat `Set` postupu uvnitř vlastnosti, na který se vztahuje.  
  
 `Set` Postup výchozí úroveň přístupu jeho obsahující vlastnosti, pokud nechcete použít `accessmodifier` v `Set` příkaz.  
  
## <a name="rules"></a>Pravidla  
  
-   **Smíšenými úrovněmi přístupu.** Pokud definujete vlastnost pro čtení a zápis, Volitelně můžete zadat úroveň různý přístup pro buď `Get` nebo `Set` postup, ale ne obojí. Pokud to uděláte, musí být úroveň přístupu postup více omezující než úroveň přístupu vlastnosti. Například, pokud je deklarovaná vlastnost `Friend`, můžou deklarovat `Set` postup `Private`, ale ne `Public`.  
  
     Pokud definujete `WriteOnly` vlastnost, `Set` představuje vlastnost celý postup. Pro přístup k jiné nelze deklarovat úrovně pro `Set`, vzhledem k tomu, který se nastavuje dvě úrovně přístupu pro vlastnost.  
  
## <a name="behavior"></a>Chování  
  
-   **Vrácení z procedury vlastnosti.** Když `Set` postup vrátí kód volání, provádění pokračuje následující příkaz, který poskytuje hodnota, která má být uložen.  
  
     `Set` procedury vlastností může vrátit buď pomocí [příkaz Return](../../../visual-basic/language-reference/statements/return-statement.md) nebo [ukončovací příkaz](../../../visual-basic/language-reference/statements/exit-statement.md).  
  
     `Exit Property` a `Return` příkazy způsobí okamžité ukončení z procedury vlastnosti. Libovolný počet `Exit Property` a `Return` příkazy může vyskytovat kdekoli v postupu, a je možné kombinovat `Exit Property` a `Return` příkazy.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Set` příkaz nastavit hodnotu vlastnosti.  
  
 [!code-vb[VbVbalrStatements#55](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/set-statement_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Get](../../../visual-basic/language-reference/statements/get-statement.md)  
 [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Procedury vlastnosti](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
