---
title: 'Postupy: Vyčíslení vykreslovaného vizuálního obsahu'
ms.date: 03/30/2017
helpviewer_keywords:
- retrieving the DrawingGroup value of a Visual [WPF]
- enumerating the contents of a Visual [WPF]
ms.assetid: 2974ddb3-2997-4713-8fd2-e93d549c58a8
ms.openlocfilehash: 4f0afc1075fe66c7f154fcef3cd883709db55316
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947469"
---
# <a name="how-to-enumerate-drawing-content-of-a-visual"></a>Postupy: Vyčíslení vykreslovaného vizuálního obsahu
<xref:System.Windows.Media.Drawing> Objekt neposkytuje objektový model pro vytvoření výčtu obsah <xref:System.Windows.Media.Visual>.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> metodu pro načtení <xref:System.Windows.Media.DrawingGroup> hodnotu <xref:System.Windows.Media.Visual> a výčet ho.  
  
> [!NOTE]
>  Když jsou výčet obsah vizuálu, jsou načítání <xref:System.Windows.Media.Drawing> objekty a není základní reprezentace dat vykreslení jako seznam vektorové grafiky instrukce. Další informace najdete v tématu [přehled vykreslování grafiky WPF](wpf-graphics-rendering-overview.md).  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.Drawing>
- <xref:System.Windows.Media.DrawingGroup>
- <xref:System.Windows.Media.VisualTreeHelper>
- [Přehled nakreslených objektů](drawing-objects-overview.md)
- [Přehled vykreslování grafiky WPF](wpf-graphics-rendering-overview.md)
