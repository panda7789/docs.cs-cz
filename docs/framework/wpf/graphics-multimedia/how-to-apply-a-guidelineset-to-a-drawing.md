---
title: "Postupy: Použití GuidelineSet na kresbu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GuidelineSet property [WPF], applying to drawings
- graphics [WPF], GuidelineSet property
ms.assetid: 45f3e0b4-8820-45a7-b865-b8ea5b17b0c8
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5cf689f8a7c475dbdda416297e28118d43bfdbff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-apply-a-guidelineset-to-a-drawing"></a>Postupy: Použití GuidelineSet na kresbu
Tento příklad ukazuje, jak se má použít <xref:System.Windows.Media.GuidelineSet> k <xref:System.Windows.Media.DrawingGroup>.  
  
 <xref:System.Windows.Media.DrawingGroup> Třída je jediným typem <xref:System.Windows.Media.Drawing> má <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A> vlastnost. Použít <xref:System.Windows.Media.GuidelineSet> k jinému typu služby <xref:System.Windows.Media.Drawing>, ho přidat do <xref:System.Windows.Media.DrawingGroup> a následně použít <xref:System.Windows.Media.GuidelineSet> k vaší <xref:System.Windows.Media.DrawingGroup>.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří dvě <xref:System.Windows.Media.DrawingGroup> objekty, které jsou téměř stejné; jediným rozdílem je: druhý <xref:System.Windows.Media.DrawingGroup> má <xref:System.Windows.Media.GuidelineSet> a první není.  
  
 Následující obrázek znázorňuje výstup z příkladu. Protože vykreslování nesouhlasí dva <xref:System.Windows.Media.DrawingGroup> objekty se proto jemně, jsou části výkresů zvětšení.  
  
 ![Objekt DrawingGroup s i bez vlastností GuidelineSet](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawinggroup-guidelineset.png "graphicsmm_drawinggroup_guidelineset")  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMDrawingGroupGuidelineSetExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/DrawingGroupGuidelineSetExample.cs#graphicsmmdrawinggroupguidelinesetexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#GraphicsMMDrawingGroupGuidelineSetExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/DrawingGroupGuidelineSetExample.xaml#graphicsmmdrawinggroupguidelinesetexamplewholepage)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.DrawingGroup>  
 <xref:System.Windows.Media.GuidelineSet>  
 [Přehled nakreslených objektů](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
