---
title: Vícenásobná pole (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- jagged arrays [C#]
- arrays [C#], jagged
ms.assetid: 537c65a6-0e0a-4a00-a2b8-086f38519c70
ms.openlocfilehash: c1825e1a731c40a5945060f8085bd612b5d62008
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="jagged-arrays-c-programming-guide"></a>Vícenásobná pole (Průvodce programováním v C#)
Vícenásobné pole je pole, jehož prvky jsou pole. Prvky Vícenásobná pole může být různými dimenzemi a velikosti. Vícenásobná pole se někdy označuje jako "pole polí." Následující příklady ukazují, jak deklarovat, inicializovat a přístup Vícenásobná pole.  
  
 Toto je deklaraci jednorozměrná pole, která má tři prvky, z nichž každý se jednorozměrná pole celých čísel:  
  
 [!code-csharp[csProgGuideArrays#19](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_1.cs)]  
  
 Než budete moci použít `jaggedArray`, jeho elementy musí být inicializován. Můžete inicializovat elementy takto:  
  
 [!code-csharp[csProgGuideArrays#20](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_2.cs)]  
  
 Jednotlivých prvků je jednorozměrná pole celých čísel. Je první prvek pole 5 celých čísel, druhý je pole 4 celých čísel a třetí je pole 2 celých čísel.  
  
 Je také možné použít k vyplnění pole prvky hodnotami inicializátory, v takovém případě nepotřebujete velikost pole. Příklad:  
  
 [!code-csharp[csProgGuideArrays#21](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_3.cs)]  
  
 Můžete také inicializovat pole po deklaraci takto:  
  
 [!code-csharp[csProgGuideArrays#22](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_4.cs)]  
  
 Můžete použít následující sdružená formuláře. Všimněte si, že nemůžete vynechat `new` operátor z elementů inicializace protože neexistuje žádný výchozí inicializace pro elementy:  
  
 [!code-csharp[csProgGuideArrays#23](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_5.cs)]  
  
 Vícenásobná pole je pole polí, a proto jeho prvky jsou odkazové typy a jsou inicializována tak, aby `null`.  
  
 Elementy jednotlivá pole jako těchto příkladech se můžete dostat:  
  
 [!code-csharp[csProgGuideArrays#24](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_6.cs)]  
  
 Je možné kombinovat vícenásobná a multidimenzionální pole. Zde je deklarace a inicializace jednorozměrná Vícenásobná pole, která obsahuje tři prvky dvourozměrná pole různých velikostí. Další informace o dvourozměrná polích najdete v tématu [vícerozměrná pole](../../../csharp/programming-guide/arrays/multidimensional-arrays.md).  
  
 [!code-csharp[csProgGuideArrays#25](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_7.cs)]  
  
 Jak je znázorněno v tomto příkladu se zobrazí hodnota elementu dostanete jednotlivé elementy `[1,0]` první pole (hodnota `5`):  
  
 [!code-csharp[csProgGuideArrays#26](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_8.cs)]  
  
 Metoda `Length` vrátí počet polí obsažených v Vícenásobná pole. Například, za předpokladu, že deklarujete předchozí pole, tento řádek:  
  
 [!code-csharp[csProgGuideArrays#27](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_9.cs)]  
  
 Vrátí hodnotu 3.  
  
## <a name="example"></a>Příklad  
 Tento příklad vytvoří pole jehož elementy jsou sami pole. Každé z nich prvků pole má různou velikost.  
  
 [!code-csharp[csProgGuideArrays#18](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_10.cs)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Array>  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Pole](../../../csharp/programming-guide/arrays/index.md)  
 [Jednorozměrná pole](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [Vícerozměrná pole](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)
