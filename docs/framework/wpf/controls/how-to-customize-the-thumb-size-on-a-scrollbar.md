---
title: "Postupy: Přizpůsobení velikosti jezdce v objektu ScrollBar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ScrollBar control [WPF]
- customizing thumb size [WPF]
- thumb size [WPF]
ms.assetid: fa32b866-5ca1-4e73-85e7-2ac64b80d194
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e88a7afb9c98179fbcb4a67217edd411d4fe9567
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-customize-the-thumb-size-on-a-scrollbar"></a>Postupy: Přizpůsobení velikosti jezdce v objektu ScrollBar
Toto téma vysvětluje, jak nastavit <xref:System.Windows.Controls.Primitives.Thumb> z <xref:System.Windows.Controls.Primitives.ScrollBar> s pevnou velikostí a určení minimální velikost <xref:System.Windows.Controls.Primitives.Thumb> z <xref:System.Windows.Controls.Primitives.ScrollBar>.  
  
## <a name="example"></a>Příklad  
  
## <a name="description"></a>Popis  
 Následující příklad vytvoří <xref:System.Windows.Controls.Primitives.ScrollBar> má <xref:System.Windows.Controls.Primitives.Thumb> s pevnou velikostí. V příkladu je nastavena <xref:System.Windows.Controls.Primitives.Track.ViewportSize%2A> vlastnost <xref:System.Windows.Controls.Primitives.Thumb> k <xref:System.Double.NaN> a nastaví výšku <xref:System.Windows.Controls.Primitives.Thumb>.  Chcete-li vytvořit vodorovných <xref:System.Windows.Controls.Primitives.ScrollBar> s <xref:System.Windows.Controls.Primitives.Thumb> s pevnou šířkou, nastavte šířku <xref:System.Windows.Controls.Primitives.Thumb>.  
  
## <a name="code"></a>Kód  
 [!code-xaml[ScrollBarCustomThumbSize#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollBarCustomThumbSize/CS/Window1.xaml#1)]  
  
## <a name="description"></a>Popis  
 Následující příklad vytvoří <xref:System.Windows.Controls.Primitives.ScrollBar> má <xref:System.Windows.Controls.Primitives.Thumb> s minimální velikostí. V příkladu nastaví hodnotu <xref:System.Windows.SystemParameters.VerticalScrollBarButtonHeightKey%2A>. Chcete-li vytvořit vodorovných <xref:System.Windows.Controls.Primitives.ScrollBar> s <xref:System.Windows.Controls.Primitives.Thumb> má minimální šířka, nastavte <xref:System.Windows.SystemParameters.HorizontalScrollBarButtonWidthKey%2A>.  
  
## <a name="code"></a>Kód  
 [!code-xaml[ScrollBarCustomThumbSize#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollBarCustomThumbSize/CS/Window1.xaml#2)]  
  
## <a name="see-also"></a>Viz také  
 [ScrollBar – styly a šablony](../../../../docs/framework/wpf/controls/scrollbar-styles-and-templates.md)
