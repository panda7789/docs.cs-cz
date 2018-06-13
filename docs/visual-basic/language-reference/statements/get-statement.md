---
title: Get – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.Get
helpviewer_keywords:
- Get statement [Visual Basic], syntax
- Get statement [Visual Basic]
- properties [Visual Basic], read-only
- read-only properties
- Get keyword [Visual Basic]
- property procedures [Visual Basic], Get statements
ms.assetid: 56b05cdc-bd64-4dfd-bb12-824eacec6f94
ms.openlocfilehash: d6a6fdfd191de76871619dea3bd1794b487698aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605105"
---
# <a name="get-statement"></a>Get – příkaz
Deklaruje `Get` procedury vlastnosti použít k získání hodnoty vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ <attributelist> ] [ accessmodifier ] Get()  
    [ statements ]  
End Get  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`attributelist`|Volitelné. V tématu [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Volitelné na maximálně jedno z `Get` a `Set` příkazy v této vlastnosti. Může být jedna z následujících akcí:<br /><br /> -   [Chráněný](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Privátní](../../../visual-basic/language-reference/modifiers/private.md)<br />-   `Protected Friend`<br /><br /> V tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`statements`|Volitelné. Jeden nebo více příkazů, které při spuštění `Get` vlastnost procedura je volána.|  
|`End Get`|Požadováno. Ukončí definice `Get` procedura property.|  
  
## <a name="remarks"></a>Poznámky  
 Všech vlastností, musí mít `Get` procedura property Pokud je vlastnost označena `WriteOnly`. `Get` Postup se používá k vrácení aktuální hodnota vlastnosti.  
  
 Visual Basic automaticky volá vlastnost `Get` procedury při výraz požadavky hodnotu vlastnosti.  
  
 Tělo deklarace vlastnosti může obsahovat pouze vlastnosti `Get` a `Set` postupy mezi [Property – příkaz](../../../visual-basic/language-reference/statements/property-statement.md) a `End Property` příkaz. Nelze uložit jakoukoli jinou hodnotu než tyto postupy. Konkrétně ho Nejde uložit aktuální hodnotu vlastnosti. Tato hodnota mimo vlastnost, musí uložit, protože pokud ukládá uvnitř buď procedury vlastností, jiné procedury vlastnosti nelze k němu přístup. Obvyklé přístup je pro uložení hodnotu v [privátní](../../../visual-basic/language-reference/modifiers/private.md) proměnná deklarována na stejné úrovni jako vlastnost. Je nutné definovat `Get` postupu uvnitř vlastnosti, na který se vztahuje.  
  
 `Get` Postup výchozí úroveň přístupu jeho obsahující vlastnosti, pokud nechcete použít `accessmodifier` v `Get` příkaz.  
  
## <a name="rules"></a>Pravidla  
  
-   **Smíšenými úrovněmi přístupu.** Pokud definujete vlastnost pro čtení a zápis, Volitelně můžete zadat úroveň různý přístup pro buď `Get` nebo `Set` postup, ale ne obojí. Pokud to uděláte, musí být úroveň přístupu postup více omezující než úroveň přístupu vlastnosti. Například, pokud je deklarovaná vlastnost `Friend`, můžou deklarovat `Get` postup `Private`, ale ne `Public`.  
  
     Pokud definujete `ReadOnly` vlastnost, `Get` představuje vlastnost celý postup. Pro přístup k jiné nelze deklarovat úrovně pro `Get`, vzhledem k tomu, který se nastavuje dvě úrovně přístupu pro vlastnost.  
  
-   **Návratový typ.** [Property – příkaz](../../../visual-basic/language-reference/statements/property-statement.md) můžou deklarovat datový typ hodnoty, vrátí hodnotu. `Get` Postup automaticky vrátí, zda datového typu. Můžete zadat jakýkoli datový typ nebo název výčtu, struktura, třídy nebo rozhraní.  
  
     Pokud `Property` příkaz neurčuje `returntype`, postup vrátí `Object`.  
  
## <a name="behavior"></a>Chování  
  
-   **Vrací z procedury.** Když `Get` postup vrátí kód volání, provádění pokračuje v rámci příkazu, který požadovaná hodnota vlastnosti.  
  
     `Get` procedury vlastností můžete vrátit hodnotu buď pomocí [příkaz Return](../../../visual-basic/language-reference/statements/return-statement.md) nebo přiřazením návratovou hodnotu pro název vlastnosti. Další informace najdete v tématu "Vrátí hodnotu" v [funkce příkaz](../../../visual-basic/language-reference/statements/function-statement.md).  
  
     `Exit Property` a `Return` příkazy způsobí okamžité ukončení z procedury vlastnosti. Libovolný počet `Exit Property` a `Return` příkazy může vyskytovat kdekoli v postupu, a je možné kombinovat `Exit Property` a `Return` příkazy.  
  
-   **Vrátí hodnotu.** Vrácení hodnoty z `Get` postup, můžete přiřadit hodnotu pro název vlastnosti nebo ji v zahrnout [příkaz Return](../../../visual-basic/language-reference/statements/return-statement.md). `Return` Příkaz současně přiřadí `Get` postup vracet hodnotu a ukončí proceduru.  
  
     Pokud používáte `Exit Property` bez přiřazení hodnoty pro název vlastnosti `Get` postup vrátí výchozí hodnota pro typ dat vlastnosti. Další informace najdete v tématu "Vrátí hodnotu" v [funkce příkaz](../../../visual-basic/language-reference/statements/function-statement.md).  
  
     Následující příklad ukazuje dva způsoby, jak vlastnost jen pro čtení `quoteForTheDay` můžete vrátit hodnotu uchovávat v soukromé proměnné `quoteValue`.  
  
     [!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_1.vb)]  
  
     [!code-vb[VbVbalrStatements#28](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_2.vb)]  
  
     [!code-vb[VbVbalrStatements#29](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_3.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Get` příkaz a vrátí hodnotu vlastnosti.  
  
 [!code-vb[VbVbalrStatements#30](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_4.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Set](../../../visual-basic/language-reference/statements/set-statement.md)  
 [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Příkaz Exit](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [Objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [Návod: Definování tříd](../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)
