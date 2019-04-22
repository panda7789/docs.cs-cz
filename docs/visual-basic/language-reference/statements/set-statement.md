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
ms.openlocfilehash: 0a8d95ffbabf03a0e6c9d88edb28c248b60f3252
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58839077"
---
# <a name="set-statement-visual-basic"></a>Set – příkaz (Visual Basic)
Deklaruje `Set` procedury vlastnosti použít pro přiřazení hodnoty k vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## <a name="parts"></a>Součásti  
 `attributelist`  
 Volitelné. Zobrazit [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md).  
  
 `accessmodifier`  
 Volitelné na nanejvýš jeden z `Get` a `Set` příkazy v této vlastnosti. Může být jedna z následujících akcí:  
  
-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
-   [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
-   `Protected Friend`  
  
 Zobrazit [úrovní v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `value`  
 Povinný parametr. Parametr, který obsahuje novou hodnotu pro vlastnost.  
  
 `datatype`  
 Požadováno pokud `Option Strict` je `On`. Datový typ `value` parametru. Zadaný datový typ musí být stejné jako datový typ vlastnosti kde to `Set` příkaz je deklarována.  
  
 `statements`  
 Volitelné. Jeden nebo více příkazů, které při spuštění `Set` volání procedury vlastnosti.  
  
 `End Set`  
 Povinný parametr. Ukončí definici `Set` procedura property.  
  
## <a name="remarks"></a>Poznámky  
 Každou vlastnost musí mít `Set` procedura property Pokud je vlastnost označena `ReadOnly`. `Set` Postup slouží k nastavení hodnoty vlastnosti.  
  
 Visual Basic automaticky volá vlastnosti `Set` postup po příkazu přiřazení poskytuje hodnotu uložená ve vlastnosti.  
  
 Visual Basic předá parametr `Set` postupu během přiřazení vlastnosti. Pokud nezadáte parametr `Set`, integrované vývojové prostředí (IDE) používá implicitní parametr s názvem `value`. Parametr obsahuje hodnotu pro přiřazení k vlastnosti. Obvykle tuto hodnotu v privátní místní proměnné a vrácení pokaždé, když `Get` volání procedury.  
  
 Text deklarace vlastnosti může obsahovat pouze vlastnosti `Get` a `Set` postupy mezi [Property – příkaz](../../../visual-basic/language-reference/statements/property-statement.md) a `End Property` příkazu. Nejde uložit nic jiného než tyto postupy. Konkrétně to nejde uložit aktuální hodnota vlastnosti. Tato hodnota mimo vlastnost, musí uložit, protože pokud ukládat v některé z vlastností, jiné procedury vlastnosti nejde získat přístup. Obvyklým přístupem je uložení hodnoty [privátní](../../../visual-basic/language-reference/modifiers/private.md) proměnná deklarovaná na stejné úrovni jako vlastnost. Je nutné definovat `Set` postupu uvnitř vlastnosti, ke kterému se vztahuje.  
  
 `Set` Postup výchozí úroveň přístupu její nadřazenou vlastnost, pokud nechcete použít `accessmodifier` v `Set` příkazu.  
  
## <a name="rules"></a>pravidla  
  
-   **Smíšenými úrovněmi přístupu.** Pokud definujete vlastnosti pro čtení i zápis, Volitelně můžete zadat úroveň různý přístup pro buď `Get` nebo `Set` postup, ale ne obojí. Pokud to uděláte, musí být více omezující než úroveň přístupu vlastnosti úroveň řízení přístupu. Například, pokud je deklarována vlastnost `Friend`, lze deklarovat `Set` postup `Private`, ale ne `Public`.  
  
     Pokud definujete `WriteOnly` vlastnost, `Set` postup představuje celou vlastnost. Nelze deklarovat různý přístup úroveň `Set`, protože dvě úrovně přístupu pro vlastnost, která byste nastavili.  
  
## <a name="behavior"></a>Chování  
  
-   **Návrat z procedury vlastnosti.** Když `Set` postup vrátí volajícímu kódu, provádění pokračuje po příkazu, který poskytuje hodnota, která má být uložena.  
  
     `Set` procedury vlastnosti může vrátit buď pomocí [příkaz Return](../../../visual-basic/language-reference/statements/return-statement.md) nebo [příkaz Exit](../../../visual-basic/language-reference/statements/exit-statement.md).  
  
     `Exit Property` a `Return` příkazy způsobit okamžité ukončení z procedury vlastnosti. Libovolný počet `Exit Property` a `Return` příkazů může vyskytovat kdekoli v postupu, a je možné kombinovat `Exit Property` a `Return` příkazy.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Set` příkaz k nastavení hodnoty vlastnosti.  
  
 [!code-vb[VbVbalrStatements#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#55)]  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Get](../../../visual-basic/language-reference/statements/get-statement.md)
- [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)
- [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Procedury vlastnosti](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
