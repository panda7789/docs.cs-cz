---
title: Private (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
ms.openlocfilehash: d6e28e5e87c3a88e4db3fc81177894683dbb0908
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61920442"
---
# <a name="private-visual-basic"></a>Private (Visual Basic)
Určuje, že nejmíň jeden deklarovaný programový prvek je přístupný jenom v rámci kontextu jejich prohlášení, včetně z v rámci žádné typy obsažené.  
  
## <a name="remarks"></a>Poznámky  
 Pokud programovací element představuje speciálních funkcí, nebo obsahuje důvěrná data, obvykle chcete omezit přístup k němu jako přísně. Dosažení maximálního omezení tím, že pouze modul, třídu nebo strukturu, která definuje se k němu přistupovat. Omezení přístupu k elementu tímto způsobem je možné deklarovat s `Private`.  

> [!NOTE]
> Můžete také použít [Private Protected](private-protected.md) modifikátor přístupu, který zpřístupňuje člen z v rámci třídy a z odvozených tříd, které jsou umístěné v jeho obsahující sestavení.

## <a name="rules"></a>pravidla  

- **Místní deklarace.** Můžete použít `Private` pouze na úrovni modulu. To znamená, že deklarace kontext `Private` elementu musí být modulu, třídy nebo struktury a nemůže být zdrojový soubor, obor názvů, rozhraní nebo proceduru.  
  
## <a name="behavior"></a>Chování  
  
- **Úroveň přístupu.** Veškerý kód v rámci kontextu deklarace můžete přístup k jeho `Private` elementy. To zahrnuje kód v rámci omezením typu, jako je vnořená třída nebo výrazu přiřazení ve výčtu. Žádný kód mimo kontext deklarace můžete získat přístup k jeho `Private` elementy.  
  
- **Modifikátory přístupu.** Klíčová slova, které určují úroveň přístupu se nazývají *modifikátorů přístupu*. Porovnání přístupu modifikátory přístupu najdete v tématu [úrovní v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `Private` Modifikátor lze použít v těchto kontextech:  
  
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
- [Protected Friend](./protected-friend.md)[přístup úrovně v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
