---
title: 'Postupy: Vyčíslení vykreslovaného vizuálního obsahu'
ms.date: 03/30/2017
helpviewer_keywords:
- retrieving the DrawingGroup value of a Visual [WPF]
- enumerating the contents of a Visual [WPF]
ms.assetid: 2974ddb3-2997-4713-8fd2-e93d549c58a8
ms.openlocfilehash: 19c37ec7df3542eb46b182f4790059eb16fef90b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-enumerate-drawing-content-of-a-visual"></a>Postupy: Vyčíslení vykreslovaného vizuálního obsahu
<xref:System.Windows.Media.Drawing> Objekt zadejte objektový model pro vytvoření výčtu obsah <xref:System.Windows.Media.Visual>.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> metoda pro načtení <xref:System.Windows.Media.DrawingGroup> hodnotu <xref:System.Windows.Media.Visual> a výčet ho.  
  
> [!NOTE]
>  Při vytváření obsahu vizuálu jsou výčtu, jsou načítání <xref:System.Windows.Media.Drawing> objekty a není základní znázornění dat, vykreslení jako seznam vektorové grafiky instrukcí. Další informace najdete v tématu [vykreslování přehled grafiky WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Drawing>  
 <xref:System.Windows.Media.DrawingGroup>  
 <xref:System.Windows.Media.VisualTreeHelper>  
 [Přehled nakreslených objektů](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [Přehled vykreslování grafiky WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)
