---
title: Protected (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Protected
helpviewer_keywords:
- Protected Friend keyword combination
- Protected keyword [Visual Basic], and Friend
- Protected keyword [Visual Basic], syntax
- Protected access modifier
- Protected keyword [Visual Basic]
ms.assetid: 74ad3d56-309f-49d2-b60c-1d0157d010e8
ms.openlocfilehash: a80e504cc8e88dfc8968f70fee2c17991b28aff5
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929460"
---
# <a name="protected-visual-basic"></a>Protected (Visual Basic)
Modifikátor přístupu ke členu, který určuje, že nejmíň jeden deklarovaný programový prvek je přístupný jenom v rámci své vlastní třídy nebo z odvozené třídy.  
  
## <a name="remarks"></a>Poznámky  
 V některých případech programovací element deklarovaný ve třídě obsahuje citlivá data nebo omezený kód a vy chcete omezit přístup k elementu. Nicméně, pokud je třída děděna a očekáváte hierarchii odvozených tříd, může být nutné, aby tyto odvozené třídy měly přístup k datům nebo kódu. V takovém případě chcete, aby byl prvek přístupný jak ze základní třídy, tak ze všech odvozených tříd. Chcete-li omezit přístup k prvku tímto způsobem, můžete jej deklarovat pomocí `Protected`.  

> [!NOTE]
> Modifikátor `Protected` přístupu lze kombinovat se dvěma dalšími modifikátory:
>
> - [Chráněný modifikátor Friend](protected-friend.md) zpřístupňuje člena třídy v rámci této třídy, z odvozených tříd a ze stejného sestavení, ve kterém je třída definovaná. 
> - Modifikátor [Private protecter](private-protected.md) zpřístupňuje člena třídy, který je přístupný odvozeným typům, ale pouze v rámci jeho nadřazeného sestavení.
  
## <a name="rules"></a>Pravidly  
  
- **Kontext deklarace** Můžete použít `Protected` pouze na úrovni třídy. To znamená, že kontext deklarace pro `Protected` prvek musí být třída a nemůže se jednat o zdrojový soubor, obor názvů, rozhraní, modul, strukturu nebo proceduru.  

## <a name="behavior"></a>Chování  
  
- **Úroveň přístupu.** Veškerý kód ve třídě má přístup k jeho prvkům. Kód v jakékoli třídě, která je odvozena od základní třídy, má přístup `Protected` ke všem prvkům základní třídy. To platí pro všechny generace odvození. To znamená, že třída může přistupovat `Protected` k prvkům základní třídy základní třídy a tak dále.  
  
     Protected Access není nadmnožinou ani podmnožinou přístupu typu Friend.  
  
- **Modifikátory přístupu.** Klíčová slova, která určují úroveň přístupu, se nazývají *modifikátory přístupu*. Porovnání modifikátorů přístupu najdete [v tématu úrovně přístupu v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 V těchto kontextech lze použít Modifikátor:`Protected`  
  
 [Příkaz Class](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Příkaz Const](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Příkaz Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Příkaz Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Příkaz Enum](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Příkaz Interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Příkaz Structure](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také:

- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Private Protected](private-protected.md)
- [Protected Friend](protected-friend.md)
- [Úrovně přístupu v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
