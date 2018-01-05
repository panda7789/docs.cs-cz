---
title: "Postupy: Změna velikosti elementu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- scaling [WPF], elements
- graphics [WPF], scaling elements
ms.assetid: 18158d94-bbe7-4f6a-814e-84d27fa748bf
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d2bff810dc9b44b25db93c8565da27acc4f0ccc3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-scale-an-element"></a>Postupy: Změna velikosti elementu
Tento příklad ukazuje, jak používat <xref:System.Windows.Media.ScaleTransform> škálování elementu.  
  
 Použití <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> a <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> vlastnosti, které chcete změnit velikost elementu faktorem, který zadáte. Například <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> hodnotu 1.5 roztahovány až 150 procent původní šířku elementu. A <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> hodnota 0,5 zmenšuje Výška elementu o 50 procent.  
  
 Použití <xref:System.Windows.Media.ScaleTransform.CenterX%2A> a <xref:System.Windows.Media.ScaleTransform.CenterY%2A> vlastnosti k určení bodu, který je na střed operace škálování. Ve výchozím nastavení <xref:System.Windows.Media.ScaleTransform> je umístěn na střed v bodě (0,0), který odpovídá levého horního rohu obdélníku. To má za následek přesunutí elementu a také proto to vypadá větší, protože když použijete <xref:System.Windows.Media.Transform>, změníte souřadnicového prostoru, ve kterém se objekt nachází.  
  
 Následující příklad používá <xref:System.Windows.Media.ScaleTransform> dvojnásobku velikosti 50 – podle-50 <xref:System.Windows.Shapes.Rectangle>. <xref:System.Windows.Media.ScaleTransform> Má hodnotu 0 (výchozí) pro obě <xref:System.Windows.Media.ScaleTransform.CenterX%2A> a <xref:System.Windows.Media.ScaleTransform.CenterY%2A>.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[transformsSample#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#21)]  
  
 Obvykle nastavíte <xref:System.Windows.Media.ScaleTransform.CenterX%2A> a <xref:System.Windows.Media.ScaleTransform.CenterY%2A> k centru objektu, který bude změněno měřítko: (<xref:System.Windows.FrameworkElement.Width%2A>/2,  <xref:System.Windows.FrameworkElement.Height%2A> /2).  
  
 Následující příklad ukazuje další <xref:System.Windows.Shapes.Rectangle> , se používají v velikost; však to <xref:System.Windows.Media.ScaleTransform> má hodnotu 25 pro obě <xref:System.Windows.Media.ScaleTransform.CenterX%2A> a <xref:System.Windows.Media.ScaleTransform.CenterY%2A>, která odpovídá středu rámeček.  
  
 [!code-xaml[transformsSample#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#22)]  
  
 Následující obrázek ukazuje rozdíl mezi nimi <xref:System.Windows.Media.ScaleTransform> operace. Tečkovaná čára zobrazuje velikost a umístění obdélníku před škálování.  
  
 ![2 x dál škáluje s různými středy](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")  
Dvě metody ScaleTransform operace s identické hodnoty ScaleX a ScaleY ale jiné Center  
  
 Kompletní příklad, najdete v části [2-D transformací ukázka](http://go.microsoft.com/fwlink/?LinkID=158252).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.ScaleTransform>  
 [Přehled transformace](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
