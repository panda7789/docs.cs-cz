---
title: 'Postupy: Použití prvku GuidelineSet na kresbu'
ms.date: 03/30/2017
helpviewer_keywords:
- GuidelineSet property [WPF], applying to drawings
- graphics [WPF], GuidelineSet property
ms.assetid: 45f3e0b4-8820-45a7-b865-b8ea5b17b0c8
ms.openlocfilehash: 134236c5beca806b747d45f20764cc82ddd8a4e8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59217806"
---
# <a name="how-to-apply-a-guidelineset-to-a-drawing"></a>Postupy: Použití prvku GuidelineSet na kresbu
Tento příklad ukazuje způsob použití <xref:System.Windows.Media.GuidelineSet> k <xref:System.Windows.Media.DrawingGroup>.  
  
 <xref:System.Windows.Media.DrawingGroup> Třída je jediným typem <xref:System.Windows.Media.Drawing> , který má <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> vlastnost. Použít <xref:System.Windows.Media.GuidelineSet> k jinému typu služby <xref:System.Windows.Media.Drawing>, ho přidat do <xref:System.Windows.Media.DrawingGroup> a následně použít <xref:System.Windows.Media.GuidelineSet> do vaší <xref:System.Windows.Media.DrawingGroup>.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří dva <xref:System.Windows.Media.DrawingGroup> objekty, které jsou téměř shodné; jediným rozdílem je: druhý <xref:System.Windows.Media.DrawingGroup> má <xref:System.Windows.Media.GuidelineSet> a není první.  
  
 Výstup z příkladu ukazuje následující obrázek. Protože vykreslování rozdíl mezi těmito dvěma <xref:System.Windows.Media.DrawingGroup> objekty se proto malý, jsou části výkresů zvětšené.  
  
 ![DrawingGroup – a nemusíte GuidelineSet](./media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMDrawingGroupGuidelineSetExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupGuidelineSetExample.cs#graphicsmmdrawinggroupguidelinesetexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMDrawingGroupGuidelineSetExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupGuidelineSetExample.xaml#graphicsmmdrawinggroupguidelinesetexamplewholepage)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.DrawingGroup>
- <xref:System.Windows.Media.GuidelineSet>
- [Přehled vykreslovaných objektů](drawing-objects-overview.md)
