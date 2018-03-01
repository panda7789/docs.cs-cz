---
title: "Postupy: Provádění opožděné inicializace objektů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lazy initialization in .NET, how to perform
ms.assetid: 8cd68620-dcc3-4f20-8835-c728a6820e71
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1728165dbed9a011afe6e621df86be7b372a684f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-perform-lazy-initialization-of-objects"></a><span data-ttu-id="5d6bf-102">Postupy: Provádění opožděné inicializace objektů</span><span class="sxs-lookup"><span data-stu-id="5d6bf-102">How to: Perform Lazy Initialization of Objects</span></span>
<span data-ttu-id="5d6bf-103"><xref:System.Lazy%601?displayProperty=nameWithType> Třída zjednodušuje práci při provádění opožděné inicializace a vytváření instancí objektů.</span><span class="sxs-lookup"><span data-stu-id="5d6bf-103">The <xref:System.Lazy%601?displayProperty=nameWithType> class simplifies the work of performing lazy initialization and instantiation of objects.</span></span> <span data-ttu-id="5d6bf-104">Inicializace objektů opožděné způsobem, můžete vyhnout, museli vytvářet je vůbec, pokud jsou potřeba nikdy nebo jejich inicializace můžete odložit, dokud jsou nejprve přístupná.</span><span class="sxs-lookup"><span data-stu-id="5d6bf-104">By initializing objects in a lazy manner, you can avoid having to create them at all if they are never needed, or you can postpone their initialization until they are first accessed.</span></span> <span data-ttu-id="5d6bf-105">Další informace najdete v tématu [opožděné inicializace](../../../docs/framework/performance/lazy-initialization.md).</span><span class="sxs-lookup"><span data-stu-id="5d6bf-105">For more information, see [Lazy Initialization](../../../docs/framework/performance/lazy-initialization.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d6bf-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="5d6bf-106">Example</span></span>  
 <span data-ttu-id="5d6bf-107">Následující příklad ukazuje, jak k chybě při inicializaci hodnotu s <xref:System.Lazy%601>.</span><span class="sxs-lookup"><span data-stu-id="5d6bf-107">The following example shows how to initialize a value with <xref:System.Lazy%601>.</span></span> <span data-ttu-id="5d6bf-108">Předpokládejme, že proměnnou opožděné nemusí být potřeba, v závislosti na jiný kód, který nastaví `someCondition` proměnné na hodnotu true nebo false.</span><span class="sxs-lookup"><span data-stu-id="5d6bf-108">Assume that the lazy variable might not be needed, depending on some other code that sets the `someCondition` variable to true or false.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="5d6bf-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="5d6bf-109">Example</span></span>  
 <span data-ttu-id="5d6bf-110">Následující příklad ukazuje způsob použití <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> třídě pro inicializaci typ, který je viditelná jenom pro aktuální instanci objektu na aktuální vlákno.</span><span class="sxs-lookup"><span data-stu-id="5d6bf-110">The following example shows how to use the <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> class to initialize a type that is visible only to the current object instance on the current thread.</span></span>  
  
 [!code-csharp[CDS#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds2.cs#13)]
 [!code-vb[CDS#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/lazyhowto.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="5d6bf-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="5d6bf-111">See Also</span></span>  
 <xref:System.Threading.LazyInitializer?displayProperty=nameWithType>  
 [<span data-ttu-id="5d6bf-112">Opožděná inicializace</span><span class="sxs-lookup"><span data-stu-id="5d6bf-112">Lazy Initialization</span></span>](../../../docs/framework/performance/lazy-initialization.md)
