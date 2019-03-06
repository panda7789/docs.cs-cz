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
ms.openlocfilehash: 1e6dbaa9201d5c9cd902412797b2427ec488d014
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57371408"
---
# <a name="friend-visual-basic"></a>Friend (Visual Basic)
Určuje, že nejmíň jeden deklarovaný programový prvek je přístupný pouze z v rámci sestavení, které obsahuje jeho deklaraci.  
  
## <a name="remarks"></a>Poznámky  
 V mnoha případech chcete programovací prvky, jako například třídy a struktury celé sestavení používané výhradně komponenty, který je deklaruje. Však nemusí je chcete být přístupné kódem mimo sestavení (například pokud je vlastní aplikace). Pokud chcete omezit přístup k prvku tímto způsobem, je možné deklarovat s použitím `Friend` modifikátor.  
  
 Kód v jiné třídy, struktury a moduly, které jsou kompilovány do stejného sestavení můžete přistupovat ke všem `Friend` prvky v tomto sestavení.  
  
 `Friend` přístup je často upřednostňovanou úroveň pro programovací prvky aplikace, a `Friend` je přístup k výchozím úrovně rozhraní, modulu, třídy nebo struktury.  
  
 Můžete použít `Friend` pouze na úrovni modulu, rozhraní nebo oboru názvů. Proto deklarace kontext `Friend` element musí být zdrojový soubor, obor názvů, rozhraní, modulu, třídy nebo struktury; nemůže být procedury.  

> [!NOTE]
> Můžete také použít [Protected Friend](protected-friend.md) modifikátor přístupu, který zpřístupňuje člen třídy z v rámci této třídy z odvozené třídy a ze stejného sestavení, ve kterém je třída definovaná. Chcete-li omezit přístup ke členovi v rámci své třídy a z odvozených tříd ve stejném sestavení, je použít [Private Protected](private-protected.md) modifikátor přístupu.

 Porovnání `Friend` a dalších modifikátorů přístupu, najdete v článku [úrovní v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
> [!NOTE]
>  Můžete určit, že jiné sestavení je sestavení typu friend, což umožňuje přístup ke všem typy a členy, které jsou označeny jako `Friend`. Další informace najdete v tématu [přátelských sestavení](../../../standard/assembly/friend-assemblies.md).  
  
## <a name="example"></a>Příklad  
 Následující třídy používá `Friend` modifikátor umožňující dalších programovacích prvků v rámci stejného sestavení pro přístup k určitým členům.  
  
 [!code-vb[VbVbalrAccessModifiers#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalraccessmodifiers/vb/class1.vb#1)]  
  
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
  
## <a name="see-also"></a>Viz také:
- <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>
- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Private Protected](./private-protected.md)
- [Protected Friend](./protected-friend.md)
- [Úrovně přístupu v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
