---
title: Iterátor
ms.date: 07/20/2015
f1_keywords:
- vb.Iterator
helpviewer_keywords:
- Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
ms.openlocfilehash: 9d7eaf186bae544031487ce027505e1e0d4ae0f3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351527"
---
# <a name="iterator-visual-basic"></a>Iterátor (Visual Basic)
Určuje, že se jedná o iterátor funkce nebo `Get` přístupového objektu.  
  
## <a name="remarks"></a>Poznámky  
 *Iterátor* provádí vlastní iteraci přes kolekci. Iterátor používá příkaz [yield](../../../visual-basic/language-reference/statements/yield-statement.md) k vrácení každého prvku v kolekci v jednom okamžiku. Když je dosaženo příkazu `Yield`, je zachováno aktuální umístění v kódu. Provádění je restartováno ze zmíněného umístění pokaždé, když je zavolána funkce iterátoru.  
  
 Iterátor lze implementovat jako funkci nebo jako přistupující objekt `Get` definice vlastnosti. V deklaraci funkce iterátoru nebo přístupového objektu `Get` se objeví modifikátor `Iterator`.  
  
 Můžete zavolat iterátor z klientského kódu s použitím [pro každý... Další příkaz](../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
 Návratový typ funkce iterátoru nebo přístupového objektu `Get` může být <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>nebo <xref:System.Collections.Generic.IEnumerator%601>.  
  
 Iterátor nemůže mít žádné parametry `ByRef`.  
  
 Iterátor nemůže být v události, konstruktoru instance, statickém konstruktoru nebo statickém destruktoru.  
  
 Iterátor může být anonymní funkce. Další informace najdete v tématu [iterátory](../../programming-guide/concepts/iterators.md).  
  
## <a name="usage"></a>Využití  
 V těchto kontextech lze použít modifikátor `Iterator`:  
  
- [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
- [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje funkci iterátoru. Funkce iterátoru má příkaz `Yield`, který je uvnitř [... Další](../../../visual-basic/language-reference/statements/for-next-statement.md) smyčka Každá iterace [pro každý](../../../visual-basic/language-reference/statements/for-each-next-statement.md) text příkazu v `Main` vytvoří volání funkce `Power` iterátoru. Každé volání funkce iterátoru pokračuje na další provedení příkazu `Yield`, ke kterému dojde během další iterace `For…Next` smyčky.  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje přistupující objekt `Get`, který je iterátorem. Modifikátor `Iterator` je v deklaraci vlastnosti.  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 Další příklady naleznete v tématu [iterátory](../../programming-guide/concepts/iterators.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>
- [Iterátory](../../programming-guide/concepts/iterators.md)
- [Příkaz Yield](../../../visual-basic/language-reference/statements/yield-statement.md)
