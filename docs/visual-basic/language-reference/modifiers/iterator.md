---
title: Iterátor
ms.date: 07/20/2015
f1_keywords:
- vb.Iterator
helpviewer_keywords:
- Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
ms.openlocfilehash: bb19289c69f4c523363e88e91a58f37d232b07df
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396230"
---
# <a name="iterator-visual-basic"></a>Iterátor (Visual Basic)
Určuje, že funkce nebo `Get` přistupující objekt je iterátor.  
  
## <a name="remarks"></a>Poznámky  
 *Iterátor* provádí vlastní iteraci přes kolekci. Iterátor používá příkaz [yield](../statements/yield-statement.md) k vrácení každého prvku v kolekci v jednom okamžiku. Při `Yield` dosažení příkazu se zachová aktuální poloha v kódu. Provádění je restartováno ze zmíněného umístění pokaždé, když je zavolána funkce iterátoru.  
  
 Iterátor lze implementovat jako funkci nebo jako `Get` přistupující objekt definice vlastnosti. `Iterator`Modifikátor se zobrazí v deklaraci funkce iterátoru nebo `Get` přístupového objektu.  
  
 Můžete zavolat iterátor z klientského kódu s použitím [pro každý... Další příkaz](../statements/for-each-next-statement.md).  
  
 Návratový typ funkce iterátoru nebo `Get` přístupového objektu může být <xref:System.Collections.IEnumerable> , <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Collections.IEnumerator> nebo <xref:System.Collections.Generic.IEnumerator%601> .  
  
 Iterátor nemůže mít žádné `ByRef` parametry.  
  
 Iterátor nemůže být v události, konstruktoru instance, statickém konstruktoru nebo statickém destruktoru.  
  
 Iterátor může být anonymní funkce. Další informace najdete v tématu [iterátory](../../programming-guide/concepts/iterators.md).  
  
## <a name="usage"></a>Využití  
 `Iterator`V těchto kontextech lze použít modifikátor:  
  
- [Function – příkaz](../statements/function-statement.md)  
  
- [Property – příkaz](../statements/property-statement.md)  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje funkci iterátoru. Funkce iterátoru má `Yield` příkaz, který je uvnitř [... Další](../statements/for-next-statement.md) smyčka Každá iterace [pro každý](../statements/for-each-next-statement.md) text příkazu v `Main` vytvoří volání `Power` funkce iterátoru. Každé volání funkce iterátoru pokračuje k dalšímu provedení `Yield` příkazu, ke kterému dojde během další iterace `For…Next` smyčky.  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje `Get` přistupující objekt, který je iterátorem. `Iterator`Modifikátor je v deklaraci vlastnosti.  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 Další příklady naleznete v tématu [iterátory](../../programming-guide/concepts/iterators.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>
- [Iterátory](../../programming-guide/concepts/iterators.md)
- [Yield – příkaz](../statements/yield-statement.md)
