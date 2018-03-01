---
title: "Iterátor (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Iterator
helpviewer_keywords:
- Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fd6c0b1fa422dc4ab659d8c59472e5c098c729bc
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="iterator-visual-basic"></a>Iterátor (Visual Basic)
Určuje, že funkce nebo `Get` přistupujícího objektu je iterátor.  
  
## <a name="remarks"></a>Poznámky  
 *Iterator* provede vlastní iteraci přes kolekci. Iterátor používá [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) příkaz vrátit každý prvek v kolekci, jeden v čase. Když `Yield` příkaz je dosaženo, se uchovávají aktuální umístění v kódu. Provádění je restartováno ze zmíněného umístění pokaždé, když je zavolána funkce iterátoru.  
  
 Iterátor můžete implementovat, nebo jako funkci `Get` přistupujícího objektu vlastnosti definice. `Iterator` Modifikátor se zobrazí v deklaraci funkce iterator nebo `Get` přistupujícího objektu.  
  
 Volání iterovat z kódu klienta pomocí [For Each... Další příkaz](../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
 Návratový typ funkce iterator nebo `Get` přistupujícího objektu může být <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, nebo <xref:System.Collections.Generic.IEnumerator%601>.  
  
 Iterator nemají žádné `ByRef` parametry.  
  
 Iterátor nemohou být v události, konstruktoru instance, statického konstruktoru nebo statické destruktor.  
  
 Iterace může být anonymní funkce. Další informace najdete v tématu [iterátory](../../programming-guide/concepts/iterators.md).  
  
## <a name="usage"></a>Použití  
 `Iterator` Modifikátor lze použít v těchto kontexty:  
  
-   [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje funkce iterator. Funkce iterator má `Yield` příkaz, který je uvnitř [pro... Další](../../../visual-basic/language-reference/statements/for-next-statement.md) smyčky. Každé iteraci [pro každou](../../../visual-basic/language-reference/statements/for-each-next-statement.md) těla příkazu v `Main` vytvoří volání `Power` iterator funkce. Každé volání funkce iterator pokračuje dalším spuštění `Yield` příkaz, který spadá další iterace `For…Next` smyčky.  
  
 [!code-vb[VbVbalrStatements#98](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/iterator_1.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje `Get` přistupujícího objektu, který je iterátor. `Iterator` Se modifikátor v deklarace vlastnosti.  
  
 [!code-vb[VbVbalrStatements#99](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/iterator_2.vb)]  
  
 Další příklady najdete v tématu [iterátory](../../programming-guide/concepts/iterators.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>  
 [Iterátory](../../programming-guide/concepts/iterators.md)  
 [Příkaz Yield](../../../visual-basic/language-reference/statements/yield-statement.md)
