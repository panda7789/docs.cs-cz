---
title: Protected (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Protected
helpviewer_keywords:
- Protected Friend keyword combination
- Protected keyword [Visual Basic], and Friend
- Protected keyword [Visual Basic], syntax
- Protected access modifier
- Protected keyword [Visual Basic]
ms.assetid: 74ad3d56-309f-49d2-b60c-1d0157d010e8
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2d0cc7a0cb626a9ec8e2a0e47abc02e5268aed56
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="protected-visual-basic"></a>Protected (Visual Basic)
Určuje, že jeden nebo více deklarované programovací elementy jsou přístupné pouze v rámci své vlastní třídy nebo z odvozené třídy.  
  
## <a name="remarks"></a>Poznámky  
 Někdy programovací element deklarovaná ve třídě obsahuje citlivá data nebo kód s omezeným přístupem, a chcete omezit přístup k elementu. Ale pokud ze třídy a očekáváte, že hierarchie odvozených tříd, může být nezbytné pro tyto odvozené třídy přistupovat k datům nebo kódu. V takovém případě budete chtít elementu, který chcete být přístupné ze základní třídy a z všechny odvozené třídy. Omezit přístup k elementu tímto způsobem, můžou deklarovat její `Protected`.  
  
## <a name="rules"></a>Pravidla  
  
-   **Kontext deklarace.** Můžete použít `Protected` jenom na úrovni třídy. To znamená kontext deklarace `Protected` element musí být třída a nesmí být zdrojový soubor, obor názvů, rozhraní, modul, struktura nebo postup.  
  
-   **Kombinovaná parametrů.** Můžete použít `Protected` modifikátor společně s [Friend](../../../visual-basic/language-reference/modifiers/friend.md) modifikátor ve stejné deklaraci. Tato kombinace umožňuje deklarované elementy přístupná odkudkoli do stejného sestavení ze své vlastní třídy a z odvozené třídy. Můžete zadat `Protected Friend` pouze u členů tříd.  
  
## <a name="behavior"></a>Chování  
  
-   **Úroveň přístupu.** Všechny kódu v třídě mají přístup k jeho elementy. Kód do třídy, která je odvozena ze základní třídy mají přístup ke všem `Protected` elementy základní třídy. To platí pro všechny generací odvození. To znamená, že třídu přístup `Protected` elementy základní třídy základní třídy a tak dále.  
  
     Chráněného přístupu není nadmnožinou nebo podmnožinu friend přístup.  
  
-   **Modifikátory přístupu.** Klíčová slova, které určují úroveň přístupu, se nazývají *přístup modifikátory*. Porovnání modifikátory přístupu najdete v tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `Protected` Modifikátor lze použít v těchto kontexty:  
  
 [Class – příkaz](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Const – příkaz](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare – příkaz](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate – příkaz](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Dim – příkaz](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum – příkaz](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Event – příkaz](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function – příkaz](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface – příkaz](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Property – příkaz](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure – příkaz](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub – příkaz](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také  
 [Veřejné](../../../visual-basic/language-reference/modifiers/public.md)  
 [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
 [Privátní](../../../visual-basic/language-reference/modifiers/private.md)  
 [Úrovně přístupu v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Postupy](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
