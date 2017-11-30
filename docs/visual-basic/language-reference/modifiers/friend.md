---
title: Friend (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Friend
helpviewer_keywords:
- Friend keyword [Visual Basic]
- Friend access modifier
- Friend keyword [Visual Basic], syntax
- Protected Friend keyword combination
- Friend keyword [Visual Basic], and Protected
ms.assetid: b664605e-1c79-4728-b996-aa59c50846bc
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 32f993e4b9bcd126ebb6d70310fc0781e8b137b9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="friend-visual-basic"></a>Friend (Visual Basic)
Určuje, že jeden nebo více deklarované programovací elementy jsou k dispozici pouze v rámci sestavení, které obsahuje jejich deklarace.  
  
## <a name="remarks"></a>Poznámky  
 V řadě případů budete chtít programování elementů, jako jsou třídy a struktury má být používána celý sestavení, ne jenom komponentou, který deklaruje je. Však možné, že chcete, aby být přístupné kód mimo sestavení (například pokud aplikace je Proprietární). Pokud chcete omezit přístup k elementu tímto způsobem, je možné deklarovat pomocí `Friend` modifikátor.  
  
 Kód v jiných tříd, struktur a moduly, které jsou zkompilovány do stejného sestavení přístup k veškerým `Friend` elementů v této sestavě.  
  
 `Friend`přístup je často úroveň elementům programování aplikace v upřednostňované a `Friend` je přístup k výchozí úroveň rozhraní, modul, třídu nebo strukturu.  
  
 Můžete použít `Friend` pouze na úrovni modulu, rozhraní nebo obor názvů. Proto deklarace kontext `Friend` element musí být zdrojový soubor, obor názvů, rozhraní, modul, třídu nebo strukturu; nemůže být procedury.  
  
 Můžete použít `Friend` modifikátor ve spojení s [chráněné](../../../visual-basic/language-reference/modifiers/protected.md) modifikátor ve stejné deklaraci. Tato kombinace uděluje obě `Friend` přístup a chráněného přístupu na deklarované elementy, které jsou přístupné z libovolné místo ve stejném sestavení, ze své vlastní třídy a z odvozené třídy. Můžete zadat `Protected Friend` pouze u členů tříd.  
  
 Porovnání `Friend` a dalších přístup modifikátory, najdete v části [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
> [!NOTE]
>  Můžete určit, že je sestavení přátelského sestavení, která umožňuje přístup všechny typy a členy, které jsou označeny jako `Friend`. Další informace najdete v tématu [přátelských sestavení](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055).  
  
## <a name="example"></a>Příklad  
 Následující třídy používá `Friend` modifikátor umožňující ostatní programovací elementy v rámci stejného sestavení pro přístup k určitým členům.  
  
 [!code-vb[VbVbalrAccessModifiers#1](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/friend_1.vb)]  
  
## <a name="usage"></a>Použití  
 Můžete použít `Friend` modifikátor v těchto kontextech:  
  
 [Class – příkaz](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Const – příkaz](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare – příkaz](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate – příkaz](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Dim – příkaz](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum – příkaz](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Event – příkaz](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function – příkaz](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface – příkaz](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Module – příkaz](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [Property – příkaz](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure – příkaz](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub – příkaz](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [Veřejné](../../../visual-basic/language-reference/modifiers/public.md)  
 [Chráněný](../../../visual-basic/language-reference/modifiers/protected.md)  
 [Privátní](../../../visual-basic/language-reference/modifiers/private.md)  
 [Úrovně přístupu v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Postupy](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
