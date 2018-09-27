---
title: Vícenásobná pole (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- jagged arrays [C#]
- arrays [C#], jagged
ms.assetid: 537c65a6-0e0a-4a00-a2b8-086f38519c70
ms.openlocfilehash: 2e4988439000712f4d1bd9b5abe412e7fd5d43eb
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2018
ms.locfileid: "47396874"
---
# <a name="jagged-arrays-c-programming-guide"></a>Vícenásobná pole (Průvodce programováním v C#)

Vícenásobné pole je pole, jehož prvky jsou pole. Prvky vícenásobného pole mohou být různé dimenze a velikostí. Vícenásobné pole se někdy označuje jako "pole polí." Následující příklady ukazují, jak deklarovat, inicializovat a přístup Vícenásobná pole.  
  
 Následuje deklaraci jednorozměrné pole s, která má tři prvky, z nichž každý je jednorozměrné pole celých čísel:  
  
 [!code-csharp[csProgGuideArrays#19](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_1.cs)]  
  
 Než budete moct použít `jaggedArray`, jeho prvky musí být inicializován. Můžete inicializovat prvky takto:  
  
 [!code-csharp[csProgGuideArrays#20](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_2.cs)]  
  
 Každý prvek je jednorozměrné pole celých čísel. Prvním prvkem je pole 5 celých čísel, druhá je pole 4 celých čísel a třetí je pole 2 celých čísel.  
  
 Je také možné použít inicializátory k vyplnění hodnot prvků pole, v takovém případě nepotřebujete velikost pole. Příklad:  
  
 [!code-csharp[csProgGuideArrays#21](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_3.cs)]  
  
 Můžete také inicializovat pole při deklaraci takto:  
  
 [!code-csharp[csProgGuideArrays#22](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_4.cs)]  
  
 Můžete použít následující Zkrácený tvar. Všimněte si, že nemůžete vynechat `new` operátor od inicializace prvků vzhledem k tomu, že neexistuje žádná výchozí inicializace pro prvky:  
  
 [!code-csharp[csProgGuideArrays#23](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_5.cs)]  
  
 Vícenásobné pole je pole polí, a proto jeho prvky jsou odkazové typy a jsou inicializovány na hodnotu `null`.  
  
 Můžete přistupovat k prvkům jednotlivá pole jako v těchto příkladech:  
  
 [!code-csharp[csProgGuideArrays#24](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_6.cs)]  
  
 Je možné kombinovat vícenásobného a vícedimenzionální pole. Následuje deklaraci a inicializaci jednorozměrné vícenásobného pole, která obsahuje tři prvky dvourozměrné pole různých velikostí. Další informace o dvojrozměrné pole najdete v tématu [vícerozměrná pole](../../../csharp/programming-guide/arrays/multidimensional-arrays.md).  
  
 [!code-csharp[csProgGuideArrays#25](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_7.cs)]  
  
 Jak je znázorněno v tomto příkladu, který se zobrazí hodnota elementu, který můžete přístup ke jednotlivým prvkům `[1,0]` první pole (hodnotu `5`):  
  
 [!code-csharp[csProgGuideArrays#26](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_8.cs)]  
  
 Metoda `Length` vrátí počet polí obsažených v vícenásobného pole. Například za předpokladu, že je deklarován předchozí pole, tento řádek:  
  
 [!code-csharp[csProgGuideArrays#27](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_9.cs)]  
  
 Vrátí hodnotu 3.  
  
## <a name="example"></a>Příklad

 Tento příklad vytvoří pole, jehož prvky jsou samotné pole. Prvky pole každé z nich má jinou velikost.  
  
 [!code-csharp[csProgGuideArrays#18](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_10.cs)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Array>  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Pole](../../../csharp/programming-guide/arrays/index.md)  
- [Jednorozměrná pole](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
- [Vícerozměrná pole](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)
