---
title: 'Postupy: Použití GuidelineSet na kresbu'
ms.date: 03/30/2017
helpviewer_keywords:
- GuidelineSet property [WPF], applying to drawings
- graphics [WPF], GuidelineSet property
ms.assetid: 45f3e0b4-8820-45a7-b865-b8ea5b17b0c8
ms.openlocfilehash: 4bd2ee349f2c1855a9af6b4c00f2630cd50a9108
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54493375"
---
# <a name="how-to-apply-a-guidelineset-to-a-drawing"></a>Postupy: Použití GuidelineSet na kresbu
Tento příklad ukazuje způsob použití <xref:System.Windows.Media.GuidelineSet> k <xref:System.Windows.Media.DrawingGroup>.  
  
 <xref:System.Windows.Media.DrawingGroup> Třída je jediným typem <xref:System.Windows.Media.Drawing> , který má <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> vlastnost. Použít <xref:System.Windows.Media.GuidelineSet> k jinému typu služby <xref:System.Windows.Media.Drawing>, ho přidat do <xref:System.Windows.Media.DrawingGroup> a následně použít <xref:System.Windows.Media.GuidelineSet> do vaší <xref:System.Windows.Media.DrawingGroup>.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří dva <xref:System.Windows.Media.DrawingGroup> objekty, které jsou téměř shodné; jediným rozdílem je: druhý <xref:System.Windows.Media.DrawingGroup> má <xref:System.Windows.Media.GuidelineSet> a není první.  
  
 Výstup z příkladu ukazuje následující obrázek. Protože vykreslování rozdíl mezi těmito dvěma <xref:System.Windows.Media.DrawingGroup> objekty se proto malý, jsou části výkresů zvětšené.  
  
 ![DrawingGroup – a nemusíte GuidelineSet](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMDrawingGroupGuidelineSetExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupGuidelineSetExample.cs#graphicsmmdrawinggroupguidelinesetexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMDrawingGroupGuidelineSetExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupGuidelineSetExample.xaml#graphicsmmdrawinggroupguidelinesetexamplewholepage)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Media.DrawingGroup>
- <xref:System.Windows.Media.GuidelineSet>
- [Přehled nakreslených objektů](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
