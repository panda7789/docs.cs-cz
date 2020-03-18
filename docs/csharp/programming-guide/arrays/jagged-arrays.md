---
title: Zubatá pole – programovací průvodce C#
ms.date: 07/20/2015
helpviewer_keywords:
- jagged arrays [C#]
- arrays [C#], jagged
ms.assetid: 537c65a6-0e0a-4a00-a2b8-086f38519c70
ms.openlocfilehash: 56013f0143d5efcb31a476909cb6e92504ff0dbc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705701"
---
# <a name="jagged-arrays-c-programming-guide"></a>Vícenásobná pole (Průvodce programováním v C#)

Vícenásobné pole je pole, jehož prvky jsou pole. Prvky zubaté pole může být různých rozměrů a velikostí. Zubaté pole se někdy nazývá "pole polí". Následující příklady ukazují, jak deklarovat, inicializovat a přistupovat k zubatý pole.  
  
 Následuje deklarace jednorozměrného pole, které má tři prvky, z nichž každý je jednorozměrné pole celá čísla:  
  
 [!code-csharp[csProgGuideArrays#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#19)]  
  
 Před použitím `jaggedArray`musí být jeho prvky inicializovány. Prvky můžete inicializovat takto:  
  
 [!code-csharp[csProgGuideArrays#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#20)]  
  
 Každý z prvků je jednorozměrné pole celá čísla. První prvek je pole 5 celá čísla, druhý je pole 4 celá čísla a třetí je pole 2 celá čísla.  
  
 Je také možné použít inicializátory vyplnit prvky pole s hodnotami, v takovém případě nepotřebujete velikost pole. Například:  
  
 [!code-csharp[csProgGuideArrays#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#21)]  
  
 Můžete také inicializovat pole při deklaraci, jako je tento:  
  
 [!code-csharp[csProgGuideArrays#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#22)]  
  
 Můžete použít následující zkrácený formulář. Všimněte si, že `new` nelze vynechat operátor z inicializace prvků, protože neexistuje žádná výchozí inicializace pro prvky:  
  
 [!code-csharp[csProgGuideArrays#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#23)]  
  
 Zubaté pole je pole polí, a proto jeho prvky jsou `null`typy odkazů a jsou inicializovány na .  
  
 Můžete přistupovat k jednotlivým prvkům pole, jako jsou tyto příklady:  
  
 [!code-csharp[csProgGuideArrays#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#24)]  
  
 Je možné kombinovat zubaté a vícerozměrné pole. Následuje deklarace a inicializace jednorozměrného zubatého pole, které obsahuje tři dvourozměrné prvky pole různých velikostí. Další informace o dvojrozměrných polích naleznete [v tématu Multidimenzionální pole](./multidimensional-arrays.md).  
  
 [!code-csharp[csProgGuideArrays#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#25)]  
  
 Můžete přistupovat k jednotlivým prvkům, jak je znázorněno v tomto příkladu, který zobrazuje hodnotu prvku `[1,0]` prvního pole (hodnota `5`):  
  
 [!code-csharp[csProgGuideArrays#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#26)]  
  
 Metoda `Length` vrátí počet polí obsažených v zubaté pole. Například za předpokladu, že jste deklarovali předchozí pole, tento řádek:  
  
 [!code-csharp[csProgGuideArrays#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#27)]  
  
 vrátí hodnotu 3.  
  
## <a name="example"></a>Příklad

 Tento příklad vytvoří pole, jehož prvky jsou samy o sobě pole. Každý jeden z prvků pole má jinou velikost.  
  
 [!code-csharp[csProgGuideArrays#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#18)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Array>
- [Programovací příručka jazyka C#](../index.md)
- [Pole](./index.md)
- [Jednorozměrná pole](./single-dimensional-arrays.md)
- [Vícerozměrná pole](./multidimensional-arrays.md)
