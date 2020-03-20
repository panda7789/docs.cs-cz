---
title: 'Postupy: Změna velikosti elementu'
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], elements
- graphics [WPF], scaling elements
ms.assetid: 18158d94-bbe7-4f6a-814e-84d27fa748bf
ms.openlocfilehash: a383ad84f1db4d937469943092a03517f68777ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187440"
---
# <a name="how-to-scale-an-element"></a>Postupy: Změna velikosti elementu
Tento příklad ukazuje, <xref:System.Windows.Media.ScaleTransform> jak použít měřítko prvku.  
  
 Pomocí <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> vlastností a <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> změňte velikost prvku podle zadaného faktoru. Například <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> hodnota 1,5 roztáhne prvek na 150 procent jeho původní šířky. Hodnota <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> 0,5 zmenší výšku prvku o 50 procent.  
  
 Pomocí <xref:System.Windows.Media.ScaleTransform.CenterX%2A> vlastností a <xref:System.Windows.Media.ScaleTransform.CenterY%2A> určete bod, který je středem operace měřítka. Ve výchozím <xref:System.Windows.Media.ScaleTransform> nastavení je a vystředěna v bodě (0,0), což odpovídá levému hornímu rohu obdélníku. To má za následek přesunutí prvku a také jeho zobrazení větší, protože při použití <xref:System.Windows.Media.Transform>změníte souřadnicový prostor, ve kterém se objekt nachází.  
  
 Následující příklad používá <xref:System.Windows.Media.ScaleTransform> ke zdvojnásobení velikosti 50- 50 <xref:System.Windows.Shapes.Rectangle>. Má <xref:System.Windows.Media.ScaleTransform> hodnotu 0 (výchozí) pro <xref:System.Windows.Media.ScaleTransform.CenterX%2A> <xref:System.Windows.Media.ScaleTransform.CenterY%2A>oba a .  
  
## <a name="example"></a>Příklad  
 [!code-xaml[transformsSample#21](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#21)]  
  
 Obvykle nastavíte <xref:System.Windows.Media.ScaleTransform.CenterX%2A> <xref:System.Windows.Media.ScaleTransform.CenterY%2A> a do středu objektu, který<xref:System.Windows.FrameworkElement.Width%2A>je měřítko: ( /2, <xref:System.Windows.FrameworkElement.Height%2A>/2).  
  
 Následující příklad ukazuje <xref:System.Windows.Shapes.Rectangle> jiný, který je zdvojnásoben ve velikosti; však <xref:System.Windows.Media.ScaleTransform> má hodnotu 25 <xref:System.Windows.Media.ScaleTransform.CenterX%2A> pro <xref:System.Windows.Media.ScaleTransform.CenterY%2A>oba a , který odpovídá středu obdélníku.  
  
 [!code-xaml[transformsSample#22](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#22)]  
  
 Následující obrázek znázorňuje <xref:System.Windows.Media.ScaleTransform> rozdíl mezi dvěma operacemi. Tečkovaná čára zobrazuje velikost a umístění obdélníku před změnou měřítka.  
  
 ![2x váhy s různými středovými body](./media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")  
Dvě operace ScaleTransform s identickými hodnotami ScaleX a ScaleY, ale s různými centry  
  
 Kompletní ukázku naleznete v [tématu Ukázka 2D transformací](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.ScaleTransform>
- [Přehled transformace](transforms-overview.md)
- [Témata s postupy](transformations-how-to-topics.md)
