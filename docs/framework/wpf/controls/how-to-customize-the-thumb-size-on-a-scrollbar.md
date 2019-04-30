---
title: 'Postupy: Přizpůsobení velikosti jezdce v prvku ScrollBar'
ms.date: 03/30/2017
helpviewer_keywords:
- ScrollBar control [WPF]
- customizing thumb size [WPF]
- thumb size [WPF]
ms.assetid: fa32b866-5ca1-4e73-85e7-2ac64b80d194
ms.openlocfilehash: 60ae7c4e95801036c5deb0c485645297509b830c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61911050"
---
# <a name="how-to-customize-the-thumb-size-on-a-scrollbar"></a>Postupy: Přizpůsobení velikosti jezdce v prvku ScrollBar
Toto téma vysvětluje, jak nastavit <xref:System.Windows.Controls.Primitives.Thumb> z <xref:System.Windows.Controls.Primitives.ScrollBar> s pevnou velikostí a jak určit minimální velikost <xref:System.Windows.Controls.Primitives.Thumb> z <xref:System.Windows.Controls.Primitives.ScrollBar>.  
  
## <a name="example"></a>Příklad  
  
## <a name="description"></a>Popis  
 Následující příklad vytvoří <xref:System.Windows.Controls.Primitives.ScrollBar> , který má <xref:System.Windows.Controls.Primitives.Thumb> s pevnou velikostí. V příkladu je nastavena <xref:System.Windows.Controls.Primitives.Track.ViewportSize%2A> vlastnost <xref:System.Windows.Controls.Primitives.Thumb> k <xref:System.Double.NaN> a nastaví výšku <xref:System.Windows.Controls.Primitives.Thumb>.  Chcete-li vytvořit vodorovnou <xref:System.Windows.Controls.Primitives.ScrollBar> s <xref:System.Windows.Controls.Primitives.Thumb> , který má pevnou šířku, nastavte šířku <xref:System.Windows.Controls.Primitives.Thumb>.  
  
## <a name="code"></a>Kód  
 [!code-xaml[ScrollBarCustomThumbSize#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollBarCustomThumbSize/CS/Window1.xaml#1)]  
  
## <a name="description"></a>Popis  
 Následující příklad vytvoří <xref:System.Windows.Controls.Primitives.ScrollBar> , který má <xref:System.Windows.Controls.Primitives.Thumb> s minimální velikostí. Příklad nastaví hodnotu <xref:System.Windows.SystemParameters.VerticalScrollBarButtonHeightKey%2A>. Chcete-li vytvořit vodorovnou <xref:System.Windows.Controls.Primitives.ScrollBar> s <xref:System.Windows.Controls.Primitives.Thumb> , který má minimální šířka, nastavte <xref:System.Windows.SystemParameters.HorizontalScrollBarButtonWidthKey%2A>.  
  
## <a name="code"></a>Kód  
 [!code-xaml[ScrollBarCustomThumbSize#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollBarCustomThumbSize/CS/Window1.xaml#2)]  
  
## <a name="see-also"></a>Viz také:

- [ScrollBar – styly a šablony](scrollbar-styles-and-templates.md)
