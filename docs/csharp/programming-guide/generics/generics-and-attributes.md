---
title: Obecné typy a atributy – Průvodce programováním v C#
description: Přečtěte si o použití atributů u obecných typů. Podívejte se na příklady kódu a zobrazte další dostupné prostředky.
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], attributes
- attributes [C#], with generics
ms.assetid: da9fc326-4648-454a-8e13-3911a2edefd7
ms.openlocfilehash: 17556af2e1bc2963de953cea242d7000509acbcd
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299874"
---
# <a name="generics-and-attributes-c-programming-guide"></a>Obecné typy a atributy (Průvodce programováním v C#)
Atributy lze použít na obecné typy stejným způsobem jako jiné než obecné typy. Další informace o použití atributů naleznete v tématu [Attributes](../concepts/attributes/index.md).  
  
 Vlastní atributy jsou povoleny pouze odkazům na otevřené obecné typy, což jsou obecné typy, pro které nejsou zadány žádné argumenty typu, a uzavřené konstruované obecné typy, které dodávají argumenty pro všechny parametry typu.  
  
 Následující příklady používají tento vlastní atribut:  
  
 [!code-csharp[csProgGuideGenerics#48](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#48)]  
  
 Atribut může odkazovat na otevřený obecný typ:  
  
 [!code-csharp[csProgGuideGenerics#49](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#49)]  
  
 Zadejte více parametrů typu pomocí vhodného počtu čárek. V tomto příkladu `GenericClass2` má dva parametry typu:  
  
 [!code-csharp[csProgGuideGenerics#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#50)]  
  
 Atribut může odkazovat na uzavřený konstruovaný obecný typ:  
  
 [!code-csharp[csProgGuideGenerics#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#51)]  
  
 Atribut, který odkazuje na parametr obecného typu, způsobí chybu při kompilaci:  
  
 [!code-csharp[csProgGuideGenerics#52](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#52)]  
  
 Obecný typ nemůže dědit z <xref:System.Attribute> :  
  
 [!code-csharp[csProgGuideGenerics#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#53)]  
  
 Chcete-li získat informace o obecném typu nebo parametru typu v době běhu, můžete použít metody <xref:System.Reflection> . Další informace naleznete v tématu [Obecné typy a reflexe](./generics-and-reflection.md) .  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v C#](../index.md)
- [Obecné typy](./index.md)
- [Atributy](../../../standard/attributes/index.md)
