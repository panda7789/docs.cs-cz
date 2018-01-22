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
ms.openlocfilehash: d21d2950ed228bf588a202419c222ee86dde5b0d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
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
 [Postupy: témata posuvníku](http://msdn.microsoft.com/library/534be86c-afb2-425d-8186-631278a9925e)
