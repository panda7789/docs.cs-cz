---
title: Vícenásobná pole – Průvodce programováním v C#
description: Vícenásobné pole v jazyce C# je pole, jehož prvky jsou pole různých rozměrů a velikostí. Naučte se deklarovat, inicializovat a přistupovat k vícenásobným polím.
ms.date: 07/20/2015
helpviewer_keywords:
- jagged arrays [C#]
- arrays [C#], jagged
ms.assetid: 537c65a6-0e0a-4a00-a2b8-086f38519c70
ms.openlocfilehash: 40da9fbda34aef4e69ebf2ae20485e883b79f871
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474680"
---
# <a name="jagged-arrays-c-programming-guide"></a>Vícenásobná pole (Průvodce programováním v C#)

Vícenásobné pole je pole, jehož prvky jsou pole. Prvky vícenásobného pole mohou mít různé rozměry a velikosti. Vícenásobné pole se někdy označuje jako "pole polí". Následující příklady ukazují, jak deklarovat, inicializovat a přistupovat k vícenásobným polím.  
  
 Níže je deklarace jednorozměrného pole, které má tři prvky, z nichž každý je jednorozměrné pole celých čísel:  
  
 [!code-csharp[csProgGuideArrays#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#19)]  
  
 Než budete moci použít `jaggedArray` , musí být inicializovány jeho prvky. Prvky můžete inicializovat takto:  
  
 [!code-csharp[csProgGuideArrays#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#20)]  
  
 Každý prvek je jednorozměrné pole celých čísel. První prvek je pole o 5 celých čísel, druhým je pole o 4 celých číslech a třetí je pole o 2 celých číslech.  
  
 Je také možné použít inicializátory k vyplnění prvků pole hodnotami, v takovém případě nepotřebujete velikost pole. Příklad:  
  
 [!code-csharp[csProgGuideArrays#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#21)]  
  
 Pole můžete také inicializovat při deklaraci takto:  
  
 [!code-csharp[csProgGuideArrays#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#22)]  
  
 Můžete použít následující zkrácený tvar. Všimněte si, že nelze vynechat `new` operátor z inicializace prvků, protože neexistuje žádná výchozí inicializace pro prvky:  
  
 [!code-csharp[csProgGuideArrays#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#23)]  
  
 Vícenásobné pole je pole pole, a proto jeho prvky jsou odkazové typy a jsou inicializovány na `null` .  
  
 Můžete přistupovat k jednotlivým prvkům pole, jako jsou tyto příklady:  
  
 [!code-csharp[csProgGuideArrays#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#24)]  
  
 Je možné kombinovat zubatá a multidimenzionální pole. Následuje deklarace a inicializace jednorozměrného vícenásobného pole, které obsahuje 3 2 prvky pole s různou velikostí. Další informace o dvojrozměrnéch polích naleznete v tématu [multidimenzionální pole](./multidimensional-arrays.md).  
  
 [!code-csharp[csProgGuideArrays#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#25)]  
  
 Můžete přistupovat k jednotlivým prvkům, jak je znázorněno v tomto příkladu, který zobrazuje hodnotu prvku `[1,0]` prvního pole (hodnota `5` ):  
  
 [!code-csharp[csProgGuideArrays#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#26)]  
  
 Metoda `Length` vrátí počet polí obsažených ve vícenásobném poli. Předpokládejme například, že jste deklarovali předchozí pole, tento řádek:  
  
 [!code-csharp[csProgGuideArrays#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#27)]  
  
 Vrátí hodnotu 3.  
  
## <a name="example"></a>Příklad

 Tento příklad vytvoří pole, jehož prvky jsou sami. Každé z prvků pole má jinou velikost.  
  
 [!code-csharp[csProgGuideArrays#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#18)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Array>
- [Průvodce programováním v C#](../index.md)
- [Pole](./index.md)
- [Jednorozměrná pole](./single-dimensional-arrays.md)
- [Vícerozměrná pole](./multidimensional-arrays.md)
