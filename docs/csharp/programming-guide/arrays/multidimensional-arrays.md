---
title: Multidimenzionální pole – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], multidimensional
- multidimensional arrays [C#]
ms.assetid: 020ce02e-7dff-4273-8e53-bf0b33747232
ms.openlocfilehash: eb49f4386b6106328f1613b5ec70794ac26fc9b7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715039"
---
# <a name="multidimensional-arrays-c-programming-guide"></a>Vícerozměrná pole (Průvodce programováním v C#)

Pole mohou mít více než jednu dimenzi. Například následující deklarace vytvoří dvojrozměrné pole se čtyřmi řádky a dva sloupce.  
  
 [!code-csharp[csProgGuideArrays#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#11)]  
  
 Následující deklarace vytvoří pole tří dimenzí, 4, 2 a 3.  
  
 [!code-csharp[csProgGuideArrays#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#12)]  
  
## <a name="array-initialization"></a>Inicializace pole

 Můžete inicializovat pole na základě deklarace, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[csProgGuideArrays#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#13)]  
  
 Můžete také inicializovat pole bez zadání pořadí.  
  
 [!code-csharp[csProgGuideArrays#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#14)]  
  
 Pokud se rozhodnete deklarovat proměnnou pole bez inicializace, je nutné použít operátor `new` k přiřazení pole k proměnné. V následujícím příkladu je uvedena použití `new`.  
  
 [!code-csharp[csProgGuideArrays#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#15)]  
  
 Následující příklad přiřadí hodnotu k určitému prvku pole.  
  
 [!code-csharp[csProgGuideArrays#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#16)]  
  
 Podobně následující příklad získá hodnotu konkrétního prvku pole a přiřadí ji k proměnné `elementValue`.  
  
 [!code-csharp[csProgGuideArrays#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#42)]  
  
 Následující příklad kódu inicializuje prvky pole na výchozí hodnoty (s výjimkou vícenásobných polí).  
  
 [!code-csharp[csProgGuideArrays#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#17)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Pole](./index.md)
- [Jednorozměrná pole](./single-dimensional-arrays.md)
- [Vícenásobná pole](./jagged-arrays.md)
