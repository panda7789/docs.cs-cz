---
title: 'Postupy: Vykreslení oblasti radiálním přechodem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with radial gradients
- radial gradients [WPF], painting with
- painting [WPF], with radial gradients
ms.assetid: b5d0fc8a-8986-4796-b003-a75b41a48928
ms.openlocfilehash: 75c28cd19ec0423589b6485884842468b89b5e8c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43526788"
---
# <a name="how-to-paint-an-area-with-a-radial-gradient"></a>Postupy: Vykreslení oblasti radiálním přechodem
Tento příklad ukazuje způsob použití <xref:System.Windows.Media.RadialGradientBrush> třídu pro vykreslení oblasti radiálním přechodem.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.RadialGradientBrush> k vykreslení obdélníku s paprskového přechodu, který změní z žlutá červená na modrou k Limetkově zelená.  
  
 [!code-csharp[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/RadialGradientBrushSnippet.cs#simpleradialgradientexamplewholepage)]
 [!code-vb[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/radialgradientbrushsnippet.vb#simpleradialgradientexamplewholepage)]
 [!code-xaml[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/RadialGradientBrushSnippet.xaml#simpleradialgradientexamplewholepage)]  
  
 Následující obrázek znázorňuje přechodu z předchozího příkladu. Zdůraznily zastaví přechodu.  
  
 ![Přechodové zarážky v paprskového přechodu](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")  
  
> [!NOTE]
>  Příklady v tomto tématu použijte výchozí souřadnicový systém pro stanovení kontrolních bodů. Souřadnicový systém výchozí je relativní vzhledem k ohraničujícího rámečku: 0 označuje procento ohraničujícího rámečku, 0 a 1 znamená 100 procent ohraničujícího rámečku. Tento systém souřadnic můžete změnit nastavením <xref:System.Windows.Media.GradientBrush.MappingMode%2A> k hodnotě <xref:System.Windows.Media.BrushMappingMode.Absolute>. Absolutní souřadnicový systém není vzhledem k ohraničujícího rámečku. Hodnoty jsou interpretovány přímo v místním prostoru.  
  
 Pro další <xref:System.Windows.Media.RadialGradientBrush> příkladů, najdete v článku [Ukázka štětců](https://go.microsoft.com/fwlink/?LinkID=159973). Další informace o přechody a dalších typů štětce, naleznete v tématu [Malování plnými barvami a přechody přehled](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).
