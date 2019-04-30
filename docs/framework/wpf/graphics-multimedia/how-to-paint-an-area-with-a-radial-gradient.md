---
title: 'Postupy: Vykreslení oblasti paprskovým přechodem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with radial gradients
- radial gradients [WPF], painting with
- painting [WPF], with radial gradients
ms.assetid: b5d0fc8a-8986-4796-b003-a75b41a48928
ms.openlocfilehash: c3bcc11dea4b1f223f629415591ab03588881dde
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921824"
---
# <a name="how-to-paint-an-area-with-a-radial-gradient"></a>Postupy: Vykreslení oblasti paprskovým přechodem
Tento příklad ukazuje způsob použití <xref:System.Windows.Media.RadialGradientBrush> třídu pro vykreslení oblasti radiálním přechodem.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.RadialGradientBrush> k vykreslení obdélníku s paprskového přechodu, který změní z žlutá červená na modrou k Limetkově zelená.  
  
 [!code-csharp[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/RadialGradientBrushSnippet.cs#simpleradialgradientexamplewholepage)]
 [!code-vb[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/radialgradientbrushsnippet.vb#simpleradialgradientexamplewholepage)]
 [!code-xaml[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/RadialGradientBrushSnippet.xaml#simpleradialgradientexamplewholepage)]  
  
 Následující obrázek znázorňuje přechodu z předchozího příkladu. Zdůraznily zastaví přechodu.  
  
 ![Přechodové zarážky v paprskového přechodu](./media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")  
  
> [!NOTE]
>  Příklady v tomto tématu použijte výchozí souřadnicový systém pro stanovení kontrolních bodů. Systém souřadnic výchozí je relativní vzhledem k ohraničujícího rámečku: 0 označuje procento ohraničujícího rámečku, 0 a 1 znamená 100 procent ohraničujícího rámečku. Tento systém souřadnic můžete změnit nastavením <xref:System.Windows.Media.GradientBrush.MappingMode%2A> k hodnotě <xref:System.Windows.Media.BrushMappingMode.Absolute>. Absolutní souřadnicový systém není vzhledem k ohraničujícího rámečku. Hodnoty jsou interpretovány přímo v místním prostoru.  
  
 Pro další <xref:System.Windows.Media.RadialGradientBrush> příkladů, najdete v článku [Ukázka štětců](https://go.microsoft.com/fwlink/?LinkID=159973). Další informace o přechody a dalších typů štětce, naleznete v tématu [Malování plnými barvami a přechody přehled](painting-with-solid-colors-and-gradients-overview.md).
