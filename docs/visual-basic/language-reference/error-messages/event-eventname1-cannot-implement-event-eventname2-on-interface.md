---
title: Událost &#39; &lt;eventname1&gt; &#39; nemůže implementovat událost &#39; &lt;eventname2&gt; &#39; rozhraní &#39; &lt;rozhraní&gt; &#39; protože jejich typy delegátů &#39; &lt;delegate1&gt; &#39; a &#39; &lt;delegate2&gt; &#39; se neshodují
ms.date: 07/20/2015
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
ms.openlocfilehash: 024e260f12d3497d64f26e59521f016ad439ebb6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54638208"
---
# <a name="event-39lteventname1gt39-cannot-implement-event-39lteventname2gt39-on-interface-39ltinterfacegt39-because-their-delegate-types-39ltdelegate1gt39-and-39ltdelegate2gt39-do-not-match"></a>Událost &#39; &lt;eventname1&gt; &#39; nemůže implementovat událost &#39; &lt;eventname2&gt; &#39; rozhraní &#39; &lt;rozhraní&gt; &#39; protože jejich typy delegátů &#39; &lt;delegate1&gt; &#39; a &#39; &lt;delegate2&gt; &#39; se neshodují
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
