---
title: "Postupy: Přizpůsobení dílků na posuvníku"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TickBar [WPF]
- Slider control [WPF], creating with TickBar
ms.assetid: 4fa694f2-a620-4b15-be78-5f4286f89361
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 610fa829b4d2c49d0c3ae760f5601610bd2a0c46
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-customize-the-ticks-on-a-slider"></a>Postupy: Přizpůsobení dílků na posuvníku
Tento příklad ukazuje, jak vytvořit <xref:System.Windows.Controls.Slider> ovládací prvek, který má osové značky.  
  
## <a name="example"></a>Příklad  
 <xref:System.Windows.Controls.Primitives.TickBar> Zobrazí, když nastavíte <xref:System.Windows.Controls.Slider.TickPlacement%2A> vlastnost na hodnotu jinou než <xref:System.Windows.Controls.Primitives.TickPlacement.None>, což je výchozí hodnota.  
  
 Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Controls.Slider> s <xref:System.Windows.Controls.Primitives.TickBar> , zobrazí osové značky. <xref:System.Windows.Controls.Slider.TickPlacement%2A> a <xref:System.Windows.Controls.Slider.TickFrequency%2A> vlastnosti definovat umístění značek a interval mezi nimi. Když přesunete <xref:System.Windows.Controls.Primitives.Thumb>, popisy tlačítek Zobrazit hodnotu <xref:System.Windows.Controls.Slider>. <xref:System.Windows.Controls.Slider.AutoToolTipPlacement%2A> Vlastnost definuje, kde se popisky tlačítek probíhat. <xref:System.Windows.Controls.Primitives.Thumb> Pohybů odpovídají umístění značek, protože <xref:System.Windows.Controls.Slider.IsSnapToTickEnabled%2A> je nastaven na `true`.  
  
 Následující příklad ukazuje, jak používat <xref:System.Windows.Controls.Slider.Ticks%2A> vlastnost vytvořit osové značky společně <xref:System.Windows.Controls.Slider> nepravidelných intervalech.  
  
 [!code-xaml[Slider#4](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Slider/xaml/window1.xaml#4)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.Slider>  
 <xref:System.Windows.Controls.Primitives.TickBar>  
 <xref:System.Windows.Controls.Slider.TickPlacement%2A>  
 [Postupy: témata posuvníku](http://msdn.microsoft.com/en-us/534be86c-afb2-425d-8186-631278a9925e)
