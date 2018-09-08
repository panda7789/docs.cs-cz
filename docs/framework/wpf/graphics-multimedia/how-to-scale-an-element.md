---
title: 'Postupy: Změna velikosti elementu'
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], elements
- graphics [WPF], scaling elements
ms.assetid: 18158d94-bbe7-4f6a-814e-84d27fa748bf
ms.openlocfilehash: 44c638b58d828e5beb0b9de5c7bb0b67c8e82d87
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44195236"
---
# <a name="how-to-scale-an-element"></a>Postupy: Změna velikosti elementu
Tento příklad ukazuje způsob použití <xref:System.Windows.Media.ScaleTransform> škálování elementu.  
  
 Použití <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> a <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> vlastnosti, které chcete změnit velikost elementu faktorem, který zadáte. Například <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> hodnotu 1.5 roztáhne na 150 procento původní šířku elementu. A <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> hodnota 0,5 zmenšuje výšku prvku o 50 procent.  
  
 Použití <xref:System.Windows.Media.ScaleTransform.CenterX%2A> a <xref:System.Windows.Media.ScaleTransform.CenterY%2A> vlastnosti k určení bodu, který je Centrum operace škálování. Ve výchozím nastavení <xref:System.Windows.Media.ScaleTransform> je zarovnaný na střed v okamžiku (0; 0), která odpovídá levého horního rohu obdélníku. Tato akce nemá vliv přesunutí elementu a také díky tomu se zobrazí větší, protože při použití <xref:System.Windows.Media.Transform>, změníte souřadnicového prostoru, ve kterém se objekt nachází.  
  
 Následující příklad používá <xref:System.Windows.Media.ScaleTransform> na dvojnásobek velikosti 50podle-50 <xref:System.Windows.Shapes.Rectangle>. <xref:System.Windows.Media.ScaleTransform> Má hodnotu 0 (výchozí) pro obě <xref:System.Windows.Media.ScaleTransform.CenterX%2A> a <xref:System.Windows.Media.ScaleTransform.CenterY%2A>.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[transformsSample#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#21)]  
  
 Obvykle nastavena <xref:System.Windows.Media.ScaleTransform.CenterX%2A> a <xref:System.Windows.Media.ScaleTransform.CenterY%2A> do středu objektu, který je škálovat: (<xref:System.Windows.FrameworkElement.Width%2A>/2,  <xref:System.Windows.FrameworkElement.Height%2A> /2).  
  
 Následující příklad ukazuje jiné <xref:System.Windows.Shapes.Rectangle> , který se zdvojnásobí velikost; však to <xref:System.Windows.Media.ScaleTransform> má hodnotu 25 pro obě <xref:System.Windows.Media.ScaleTransform.CenterX%2A> a <xref:System.Windows.Media.ScaleTransform.CenterY%2A>, která odpovídá na střed obdélníku.  
  
 [!code-xaml[transformsSample#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#22)]  
  
 Následující ilustrace ukazuje rozdíl mezi těmito dvěma <xref:System.Windows.Media.ScaleTransform> operace. Tečkovaná čára ukazuje velikost a umístění obdélníku, před Škálováním.  
  
 ![2 x škáluje s různými středy](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")  
Dvě operace ScaleTransform – identické ScaleX a ScaleY hodnoty, ale jiné centra  
  
 Úplnou ukázku najdete v tématu [2D transformace ukázka](https://go.microsoft.com/fwlink/?LinkID=158252).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.ScaleTransform>  
 [Přehled transformace](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
