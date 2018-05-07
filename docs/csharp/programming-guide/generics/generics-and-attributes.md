---
title: Obecné typy a atributy (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], attributes
- attributes [C#], with generics
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
ms.openlocfilehash: 3bfb4028fb5efce693abd83b40636b0149962e3b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="generics-and-attributes-c-programming-guide"></a>Obecné typy a atributy (Průvodce programováním v C#)
Atributy lze použít jako obecné typy stejným způsobem jako neobecné typy. Další informace o použití atributů naleznete v tématu [atributy](../../../csharp/programming-guide/concepts/attributes/index.md).  
  
 Chcete-li otevřít obecné typy, které jsou obecné typy, pro které žádný typ jsou zadané argumenty a uzavřené sestavené obecné typy, které zadat argumenty pro všechny parametry typu jsou povolená jenom vlastní atributy.  
  
 Tento vlastní atribut použít v následujících příkladech:  
  
 [!code-csharp[csProgGuideGenerics#48](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_1.cs)]  
  
 Atribut může odkazovat otevřený obecný typ.:  
  
 [!code-csharp[csProgGuideGenerics#49](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_2.cs)]  
  
 Zadejte několik parametrů typu pomocí příslušného počtu čárkami. V tomto příkladu `GenericClass2` má dva parametry typu:  
  
 [!code-csharp[csProgGuideGenerics#50](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_3.cs)]  
  
 Atribut může odkazovat uzavřené sestavené obecného typu:  
  
 [!code-csharp[csProgGuideGenerics#51](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_4.cs)]  
  
 Atribut, který odkazuje na parametr obecného typu způsobí chybu kompilace:  
  
 [!code-csharp[csProgGuideGenerics#52](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_5.cs)]  
  
 Obecný typ nemůže Zdědit z <xref:System.Attribute>:  
  
 [!code-csharp[csProgGuideGenerics#53](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-attributes_6.cs)]  
  
 Pokud chcete získat informace o obecný typ nebo parametr typu za běhu, můžete použít metody <xref:System.Reflection>. Další informace najdete v tématu [obecné typy a reflexe](../../../csharp/programming-guide/generics/generics-and-reflection.md)  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Obecné typy](../../../csharp/programming-guide/generics/index.md)  
 [Atributy](../../../../docs/standard/attributes/index.md)
