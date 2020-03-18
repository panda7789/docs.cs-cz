---
title: Obecné typy a atributy – průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], attributes
- attributes [C#], with generics
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
ms.openlocfilehash: 47bf4e8f07a8b6778db8fa675d745d362dc10d7d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75703023"
---
# <a name="generics-and-attributes-c-programming-guide"></a>Obecné typy a atributy (Průvodce programováním v C#)
Atributy lze použít pro obecné typy stejným způsobem jako neobecné typy. Další informace o použití atributů naleznete v [tématu Atributy](../concepts/attributes/index.md).  
  
 Vlastní atributy jsou povoleny pouze odkazovat na otevřené obecné typy, které jsou obecné typy, pro které jsou zadány žádné argumenty typu a uzavřené konstruované obecné typy, které poskytují argumenty pro všechny parametry typu.  
  
 Následující příklady používají tento vlastní atribut:  
  
 [!code-csharp[csProgGuideGenerics#48](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#48)]  
  
 Atribut může odkazovat na otevřený obecný typ:  
  
 [!code-csharp[csProgGuideGenerics#49](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#49)]  
  
 Zadejte více parametrů typu pomocí příslušného počtu čárek. V tomto `GenericClass2` příkladu má dva parametry typu:  
  
 [!code-csharp[csProgGuideGenerics#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#50)]  
  
 Atribut může odkazovat na uzavřený vytvořený obecný typ:  
  
 [!code-csharp[csProgGuideGenerics#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#51)]  
  
 Atribut, který odkazuje na parametr obecného typu, způsobí chybu v době kompilace:  
  
 [!code-csharp[csProgGuideGenerics#52](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#52)]  
  
 Obecný typ nemůže <xref:System.Attribute>dědit z :  
  
 [!code-csharp[csProgGuideGenerics#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#53)]  
  
 Chcete-li získat informace o obecném typu nebo parametru <xref:System.Reflection>typu za běhu, můžete použít metody . Další informace naleznete [v tématu Generics and Reflection](./generics-and-reflection.md)  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Obecné typy](./index.md)
- [Atributy](../../../standard/attributes/index.md)
