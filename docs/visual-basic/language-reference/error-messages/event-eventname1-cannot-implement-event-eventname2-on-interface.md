---
title: Událost '<eventname1>' nemůže implementovat událost '<eventname2>' v rozhraní '<interface>' , protože se neshodují jejich typy delegátů '<delegate1>' a '<delegate2>'.
ms.date: 07/20/2015
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
ms.openlocfilehash: 3ec3e7bb2f28bf8c4dd38bc71e11193456860021
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57379754"
---
# <a name="event-eventname1-cannot-implement-event-eventname2-on-interface-interface-because-their-delegate-types-delegate1-and-delegate2-do-not-match"></a>Události "\<eventname1 >' nemůže implementovat událost '\<eventname2 >" na rozhraní "\<rozhraní >" vzhledem k tomu, jejich typy delegátů\<delegate1 > "a"\<delegate2 >' se neshodují s
Visual Basic nemůže implementovat událost, protože typ delegáta události neodpovídá typu delegáta události v rozhraní. Této chybě může dojít při definování více událostí v rozhraní a pak pokus o jejich implementaci společně se stejnou událost. Událost můžete implementovat dvě nebo více událostí pouze v případě, že vše je implementováno události jsou deklarovány pomocí `As` syntaxe a zadejte stejný typ delegáta.  
  
 **ID chyby:** BC31423  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Implementace události samostatně.  
  
     —nebo—  
  
-   Definování události pomocí rozhraní `As` syntaxe a zadejte stejný typ delegáta.  
  
## <a name="see-also"></a>Viz také:
- [Příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md)
- [Příkaz Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Události](../../../visual-basic/programming-guide/language-features/events/index.md)
