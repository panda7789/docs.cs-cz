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
ms.openlocfilehash: cb0dc76d110f3e6a3ea3e74cc0bfb5a669b35396
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583235"
---
# <a name="set-statement-visual-basic"></a>Set – příkaz (Visual Basic)
Deklaruje proceduru vlastnosti `Set`, která slouží k přiřazení hodnoty k vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## <a name="parts"></a>Součásti  
 `attributelist`  
 Volitelné. Viz [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md).  
  
 `accessmodifier`  
 Volitelné na maximálně jeden z příkazů `Get` a `Set` v této vlastnosti. Může to být jedna z následujících:  
  
- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
  
- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
  
- [Private](../../../visual-basic/language-reference/modifiers/private.md)  
  
- `Protected Friend`  
  
 Podívejte [se na úrovně přístupu v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `value`  
 Požadováno. Parametr, který obsahuje novou hodnotu pro vlastnost.  
  
 `datatype`  
 Vyžaduje se, pokud je `Option Strict` `On`. Datový typ parametru `value`. Zadaný datový typ musí být stejný jako datový typ vlastnosti, kde je tento příkaz `Set` deklarovaný.  
  
 `statements`  
 Volitelné. Jeden nebo více příkazů, které se spouštějí při volání procedury vlastnosti `Set`.  
  
 `End Set`  
 Požadováno. Ukončí definici procedury vlastnosti `Set`.  
  
## <a name="remarks"></a>Poznámky  
 Každá vlastnost musí mít proceduru `Set` vlastnost, pokud vlastnost není označena `ReadOnly`. Procedura `Set` slouží k nastavení hodnoty vlastnosti.  
  
 Visual Basic automaticky volá proceduru `Set`, pokud příkaz přiřazení poskytuje hodnotu, která má být uložena ve vlastnosti.  
  
 Visual Basic předá do přiřazení vlastností parametr `Set` proceduře. Pokud nezadáte parametr pro `Set`, integrované vývojové prostředí (IDE) používá implicitní parametr s názvem `value`. Parametr obsahuje hodnotu, která má být přiřazena vlastnosti. Tuto hodnotu obvykle ukládáte do privátní místní proměnné a vrátíte ji pokaždé, když je volána procedura `Get`.  
  
 Tělo deklarace vlastnosti může obsahovat pouze `Get` vlastnosti a procedury `Set` mezi [příkazem Property](../../../visual-basic/language-reference/statements/property-statement.md) a příkazem `End Property`. Nemůže uložit cokoli jiného než tyto postupy. Konkrétně nemůže uložit aktuální hodnotu vlastnosti. Tuto hodnotu je nutné uložit mimo vlastnost, protože pokud ji uložíte uvnitř některého z procedur vlastnosti, druhá procedura vlastnosti k ní nemá přístup. Obvyklým přístupem je uložení hodnoty do [soukromé](../../../visual-basic/language-reference/modifiers/private.md) proměnné deklarované na stejné úrovni jako vlastnost. Musíte definovat `Set` proceduru uvnitř vlastnosti, na kterou se vztahuje.  
  
 Pokud nepoužijete `accessmodifier` v příkazu `Set`, bude výchozí hodnota `Set` nastavena na úroveň přístupu jeho obsahující vlastnosti.  
  
## <a name="rules"></a>Pravidly  
  
- **Smíšené úrovně přístupu.** Pokud definujete vlastnost pro čtení i zápis, můžete volitelně zadat jinou úroveň přístupu pro `Get` nebo `Set` postup, ale ne obojí. Pokud to uděláte, musí být úroveň přístupu k této proceduře přísnější než úroveň přístupu vlastnosti. Například pokud je vlastnost deklarována `Friend`, můžete deklarovat `Set` proceduru `Private`, ale ne `Public`.  
  
     Pokud definujete vlastnost `WriteOnly`, bude procedura `Set` představovat celou vlastnost. Pro `Set` nemůžete deklarovat jinou úroveň přístupu, protože by se pro vlastnost nastavily dvě úrovně přístupu.  
  
## <a name="behavior"></a>Předvídatelně  
  
- **Návrat z procedury vlastnosti.** Když se `Set` procedura vrátí k volajícímu kódu, provádění pokračuje po příkazu, který poskytl hodnotu, která má být uložena.  
  
     procedury vlastnosti `Set` mohou vracet buď pomocí [příkazu return](../../../visual-basic/language-reference/statements/return-statement.md) , nebo [příkazu exit](../../../visual-basic/language-reference/statements/exit-statement.md).  
  
     Příkazy `Exit Property` a `Return` způsobují bezprostřední ukončení procedury vlastnosti. Libovolný počet `Exit Property` a `Return` příkazů se může objevit kdekoli v proceduře a můžete kombinovat `Exit Property` a `Return` příkazy.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá příkaz `Set` k nastavení hodnoty vlastnosti.  
  
 [!code-vb[VbVbalrStatements#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#55)]  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Get](../../../visual-basic/language-reference/statements/get-statement.md)
- [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)
- [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Procedury vlastnosti](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
