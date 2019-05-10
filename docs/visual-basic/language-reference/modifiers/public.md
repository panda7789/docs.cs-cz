---
title: Public (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Public
helpviewer_keywords:
- Public keyword [Visual Basic]
- Public keyword [Visual Basic], syntax
- Public access modifier
ms.assetid: 284c9e1b-ed23-499b-9bc9-ad87c11485a5
ms.openlocfilehash: 0b8c31facc3605ff5a77aecf7b11456b33fbab72
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647737"
---
# <a name="public-visual-basic"></a>Public (Visual Basic)
Určuje, že nejmíň jeden deklarovaný programový prvek nemá žádné omezení přístupu.  
  
## <a name="remarks"></a>Poznámky  
 Pokud publikujete komponenta nebo sadu komponent, jako je například knihovny tříd, obvykle vhodné programovací prvky, které mají být přístupné pro jakýkoli kód, který spolupracuje s vaší sestavení. Přenést taková neomezený přístup elementu, je možné deklarovat s `Public`.  
  
 Veřejný přístup je normální úroveň pro programovací prvek, pokud nepotřebujete omezit přístup k němu. Všimněte si, že úroveň přístupu elementu deklarované v rámci rozhraní, modulu, třídy nebo struktury výchozí hodnota je `Public` je-li ho jinak není deklarována.  
  
## <a name="rules"></a>pravidla  
  
- **Místní deklarace.** Můžete použít `Public` pouze na úrovni modulu, rozhraní nebo oboru názvů. To znamená, že deklarace kontext `Public` elementu musí být zdrojový soubor, obor názvů, rozhraní, modulu, třídy nebo struktury a nemůže být procedurou.  
  
## <a name="behavior"></a>Chování  
  
- **Úroveň přístupu.** Veškerý kód, který může přistupovat k modulu, třídy nebo struktury lze přistupovat k jeho `Public` elementy.  
  
- **Výchozí přístup.** Místní proměnná uvnitř procedury výchozí veřejný přístup, a nemůže používat žádné modifikátory přístupu na nich.  
  
- **Modifikátory přístupu.** Klíčová slova, které určují úroveň přístupu se nazývají *modifikátorů přístupu*. Porovnání přístupu modifikátory přístupu najdete v tématu [úrovní v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `Public` Modifikátor lze použít v těchto kontextech:  
  
 [Příkaz Class](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Příkaz Const](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Příkaz Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Příkaz Dim](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Příkaz Enum](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Příkaz Interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Příkaz Module](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [Příkaz Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Příkaz Structure](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také:

- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Private Protected](private-protected.md)
- [Protected Friend](protected-friend.md)
- [Úrovně přístupu v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
