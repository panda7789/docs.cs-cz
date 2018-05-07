---
title: Friend (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Friend
helpviewer_keywords:
- Friend keyword [Visual Basic]
- Friend access modifier
- Friend keyword [Visual Basic], syntax
- Protected Friend keyword combination
- Friend keyword [Visual Basic], and Protected
ms.assetid: b664605e-1c79-4728-b996-aa59c50846bc
ms.openlocfilehash: 756a18da74ff49cbefaf6a63980302bbcb141713
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="friend-visual-basic"></a>Friend (Visual Basic)
Určuje, že jeden nebo více deklarované programovací elementy jsou k dispozici pouze v rámci sestavení, které obsahuje jejich deklarace.  
  
## <a name="remarks"></a>Poznámky  
 V řadě případů budete chtít programování elementů, jako jsou třídy a struktury má být používána celý sestavení, ne jenom komponentou, který deklaruje je. Však možné, že chcete, aby být přístupné kód mimo sestavení (například pokud aplikace je Proprietární). Pokud chcete omezit přístup k elementu tímto způsobem, je možné deklarovat pomocí `Friend` modifikátor.  
  
 Kód v jiných tříd, struktur a moduly, které jsou zkompilovány do stejného sestavení přístup k veškerým `Friend` elementů v této sestavě.  
  
 `Friend` přístup je často úroveň elementům programování aplikace v upřednostňované a `Friend` je přístup k výchozí úroveň rozhraní, modul, třídu nebo strukturu.  
  
 Můžete použít `Friend` pouze na úrovni modulu, rozhraní nebo obor názvů. Proto deklarace kontext `Friend` element musí být zdrojový soubor, obor názvů, rozhraní, modul, třídu nebo strukturu; nemůže být procedury.  
  
 Můžete použít `Friend` modifikátor ve spojení s [chráněné](../../../visual-basic/language-reference/modifiers/protected.md) modifikátor ve stejné deklaraci. Tato kombinace uděluje obě `Friend` přístup a chráněného přístupu na deklarované elementy, které jsou přístupné z libovolné místo ve stejném sestavení, ze své vlastní třídy a z odvozené třídy. Můžete zadat `Protected Friend` pouze u členů tříd.  
  
 Porovnání `Friend` a dalších přístup modifikátory, najdete v části [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
> [!NOTE]
>  Můžete určit, že je sestavení přátelského sestavení, která umožňuje přístup všechny typy a členy, které jsou označeny jako `Friend`. Další informace najdete v tématu [přátelských sestavení](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).  
  
## <a name="example"></a>Příklad  
 Následující třídy používá `Friend` modifikátor umožňující ostatní programovací elementy v rámci stejného sestavení pro přístup k určitým členům.  
  
 [!code-vb[VbVbalrAccessModifiers#1](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/friend_1.vb)]  
  
## <a name="usage"></a>Použití  
 Můžete použít `Friend` modifikátor v těchto kontextech:  
  
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
  
 [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Příkaz Structure](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [Public](../../../visual-basic/language-reference/modifiers/public.md)  
 [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
 [Private](../../../visual-basic/language-reference/modifiers/private.md)  
 [Úrovně přístupu v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
