---
title: Privátní
ms.date: 07/20/2015
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
ms.openlocfilehash: 5600744aeca79a54f51a1f9ecd0ef00fed4b00fd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351334"
---
# <a name="private-visual-basic"></a>Private (Visual Basic)
Určuje, že nejmíň jeden deklarovaný programový prvek je přístupný jenom v rámci svého kontextu deklarace, včetně v rámci libovolných obsažených typů.  
  
## <a name="remarks"></a>Poznámky  
 Pokud programovací element představuje proprietární funkce nebo obsahuje důvěrné údaje, obvykle chcete omezit přístup k němu, co je to možné. Dosáhnete maximálního omezení tím, že povolíte pouze modul, třídu nebo strukturu, které ji definují k přístupu. Chcete-li omezit přístup k prvku tímto způsobem, můžete jej deklarovat pomocí `Private`.  

> [!NOTE]
> Můžete také použít modifikátor [privátního chráněného](private-protected.md) přístupu, který zpřístupňuje člena v rámci této třídy a z odvozených tříd umístěných v jeho obsahujícím sestavení.

## <a name="rules"></a>Pravidla  

- **Kontext deklarace** `Private` můžete použít jenom na úrovni modulu. To znamená, že kontext deklarace pro prvek `Private` musí být modul, třída nebo struktura a nemůže se jednat o zdrojový soubor, obor názvů, rozhraní nebo proceduru.  
  
## <a name="behavior"></a>Chování  
  
- **Úroveň přístupu.** Veškerý kód v kontextu deklarace má přístup k jeho prvkům `Private`. To zahrnuje kód v rámci obsaženého typu, jako je vnořená třída nebo výraz přiřazení ve výčtu. Žádný kód mimo kontext deklarace má přístup k jeho prvkům `Private`.  
  
- **Modifikátory přístupu.** Klíčová slova, která určují úroveň přístupu, se nazývají *modifikátory přístupu*. Porovnání modifikátorů přístupu najdete [v tématu úrovně přístupu v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 V těchto kontextech lze použít modifikátor `Private`:  
  
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
- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)
- [Private Protected](./private-protected.md)
- [Chráněné](./protected-friend.md)    [úrovně přístupu typu Friend v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
