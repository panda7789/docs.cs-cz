---
title: 'Postupy: Provádění opožděné inicializace objektů'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lazy initialization in .NET, how to perform
ms.assetid: 8cd68620-dcc3-4f20-8835-c728a6820e71
ms.openlocfilehash: 6efc89e5c22f53d9b2c48e535c783d488df16462
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130328"
---
# <a name="how-to-perform-lazy-initialization-of-objects"></a>Postupy: Provádění opožděné inicializace objektů
Třída <xref:System.Lazy%601?displayProperty=nameWithType> zjednodušuje práci provádění opožděné inicializace a vytváření instancí objektů. Inicializací objektů opožděným způsobem je možné se vyhnout nutnosti jejich vytváření vůbec, pokud nejsou zapotřebí, nebo můžete svou inicializaci odložit, dokud nebudou poprvé k dispozici. Další informace naleznete v tématu [opožděná inicializace](lazy-initialization.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak inicializovat hodnotu pomocí <xref:System.Lazy%601>. Předpokládat, že opožděná proměnná nemusí být potřebná, v závislosti na nějakém jiném kódu, který nastaví `someCondition` proměnnou na hodnotu true nebo false.  
  
```vb  
Dim someCondition As Boolean = False  
  
Sub Main()  
    'Initializing a value with a big computation, computed in parallel  
    Dim _data As Lazy(Of Integer) = New Lazy(Of Integer)(Function()  
                                                             Dim result =  
                                                                 ParallelEnumerable.Range(0, 1000).  
                                                                 Aggregate(Function(x, y)  
                                                                               Return x + y  
                                                                           End Function)  
                                                             Return result  
                                                         End Function)  
  
    '  do work that may or may not set someCondition to True  
    ' ...  
    '  Initialize the data only if needed  
    If someCondition = True Then  
  
        If (_data.Value > 100) Then  
  
            Console.WriteLine("Good data")  
        End If  
    End If  
End Sub  
```  
  
```csharp  
  static bool someCondition = false;    
  //Initializing a value with a big computation, computed in parallel  
  Lazy<int> _data = new Lazy<int>(delegate  
  {  
      return ParallelEnumerable.Range(0, 1000).  
          Select(i => Compute(i)).Aggregate((x,y) => x + y);  
  }, LazyExecutionMode.EnsureSingleThreadSafeExecution);  
  
  // Do some work that may or may not set someCondition to true.  
  //  ...  
  // Initialize the data only if necessary  
  if (someCondition)  
  {  
    if (_data.Value > 100)  
      {  
          Console.WriteLine("Good data");  
      }  
  }  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít třídu <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> k inicializaci typu, který je viditelný pouze pro aktuální instanci objektu v aktuálním vlákně.  
  
 [!code-csharp[CDS#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds2.cs#13)]
 [!code-vb[CDS#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/lazyhowto.vb#13)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading.LazyInitializer?displayProperty=nameWithType>
- [Opožděná inicializace](lazy-initialization.md)
