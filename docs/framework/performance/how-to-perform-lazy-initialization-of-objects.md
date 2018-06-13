---
title: 'Postupy: Provádění opožděné inicializace objektů'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lazy initialization in .NET, how to perform
ms.assetid: 8cd68620-dcc3-4f20-8835-c728a6820e71
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d33dcb2b060d1d453ae17a48d2765d489de0038
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33394472"
---
# <a name="how-to-perform-lazy-initialization-of-objects"></a>Postupy: Provádění opožděné inicializace objektů
<xref:System.Lazy%601?displayProperty=nameWithType> Třída zjednodušuje práci při provádění opožděné inicializace a vytváření instancí objektů. Inicializace objektů opožděné způsobem, můžete vyhnout, museli vytvářet je vůbec, pokud jsou potřeba nikdy nebo jejich inicializace můžete odložit, dokud jsou nejprve přístupná. Další informace najdete v tématu [opožděné inicializace](../../../docs/framework/performance/lazy-initialization.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak k chybě při inicializaci hodnotu s <xref:System.Lazy%601>. Předpokládejme, že proměnnou opožděné nemusí být potřeba, v závislosti na jiný kód, který nastaví `someCondition` proměnné na hodnotu true nebo false.  
  
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
 Následující příklad ukazuje způsob použití <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> třídě pro inicializaci typ, který je viditelná jenom pro aktuální instanci objektu na aktuální vlákno.  
  
 [!code-csharp[CDS#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds2.cs#13)]
 [!code-vb[CDS#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/lazyhowto.vb#13)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Threading.LazyInitializer?displayProperty=nameWithType>  
 [Opožděná inicializace](../../../docs/framework/performance/lazy-initialization.md)
