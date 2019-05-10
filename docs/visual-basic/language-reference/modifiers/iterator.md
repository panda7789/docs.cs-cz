---
title: Iterátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Iterator
helpviewer_keywords:
- Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
ms.openlocfilehash: 4f42cf864e836c53cff5e7d620f4bdfa43c4c7ec
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64661287"
---
# <a name="iterator-visual-basic"></a>Iterátor (Visual Basic)
Určuje, že funkce nebo `Get` přístupový objekt je iterátor.  
  
## <a name="remarks"></a>Poznámky  
 *Iterátoru* provádí vlastní iterace nad kolekcí. Iterátor používá [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) příkaz k vrácení každého prvku v kolekci, jeden po druhém. Když `Yield` je dosažen příkaz, je zachováno aktuální umístění v kódu. Provádění je restartováno ze zmíněného umístění pokaždé, když je zavolána funkce iterátoru.  
  
 Iterátor je možné implementovat jako funkci nebo `Get` přístupový objekt pro definici vlastnosti. `Iterator` Modifikátor se zobrazí v deklaraci funkce iterátoru nebo `Get` přistupujícího objektu.  
  
 Můžete volat iterátor z klientského kódu s použitím [For Each... Další příkaz](../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
 Návratový typ funkce iterátoru nebo `Get` přistupující objekt může být <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, nebo <xref:System.Collections.Generic.IEnumerator%601>.  
  
 Iterátor nesmí obsahovat žádné `ByRef` parametry.  
  
 V události, konstruktor instance, statický konstruktor nebo statická destruktor nemůže dojít k iterátoru.  
  
 Iterátor může být anonymní funkce. Další informace najdete v tématu [iterátory](../../programming-guide/concepts/iterators.md).  
  
## <a name="usage"></a>Použití  
 `Iterator` Modifikátor lze použít v těchto kontextech:  
  
- [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
- [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje funkce iterátoru. Má funkce iterátoru `Yield` , který se nachází uvnitř [pro... Další](../../../visual-basic/language-reference/statements/for-next-statement.md) smyčky. Každá iterace [pro každou](../../../visual-basic/language-reference/statements/for-each-next-statement.md) tělo s příkazy v `Main` vytváří volání `Power` funkce iterátoru. Každé volání funkce iterátoru pokračuje do dalšího provedení příkazu `Yield` prohlášení, které nastane při další iteraci `For…Next` smyčky.  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje `Get` přístupovou metodu iterátoru. `Iterator` Modifikátor je v deklaraci vlastnosti.  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 Další příklady najdete v tématu [iterátory](../../programming-guide/concepts/iterators.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>
- [Iterátory](../../programming-guide/concepts/iterators.md)
- [Příkaz Yield](../../../visual-basic/language-reference/statements/yield-statement.md)
