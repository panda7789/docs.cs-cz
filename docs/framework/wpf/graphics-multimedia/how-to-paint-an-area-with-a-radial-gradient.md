---
title: "Postupy: Vykreslení oblasti radiálním přechodem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with radial gradients
- radial gradients [WPF], painting with
- painting [WPF], with radial gradients
ms.assetid: b5d0fc8a-8986-4796-b003-a75b41a48928
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f1da933a2ee7c179a55da7d33c61539d440eabc3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-paint-an-area-with-a-radial-gradient"></a>Postupy: Vykreslení oblasti radiálním přechodem
Tento příklad ukazuje způsob použití <xref:System.Windows.Media.RadialGradientBrush> třídy Malování oblast s kruhového přechodu.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.RadialGradientBrush> k vyplnění obdélníku s kruhového přechodu, která přejde z žlutý do červené na modrou k vápna zelená.  
  
 [!code-csharp[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/RadialGradientBrushSnippet.cs#simpleradialgradientexamplewholepage)]
 [!code-vb[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/radialgradientbrushsnippet.vb#simpleradialgradientexamplewholepage)]
 [!code-xaml[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/RadialGradientBrushSnippet.xaml#simpleradialgradientexamplewholepage)]  
  
 Následující obrázek znázorňuje přechodu z předchozího příkladu. Zdůraznily má barevný přechod zastaví.  
  
 ![Přechodové zarážky v kruhového přechodu](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")  
  
> [!NOTE]
>  V příkladech v tomto tématu pomocí souřadnicový systém výchozí kontrolní body. Systém souřadnic výchozí je relativní vzhledem ke ohraničující pole: 0 znamená 0 procent ohraničujícího rámečku a 1 znamená 100 procent ohraničujícího rámečku. Tento systém souřadnic můžete změnit nastavením <xref:System.Windows.Media.GradientBrush.MappingMode%2A> vlastnost na hodnotu <xref:System.Windows.Media.BrushMappingMode.Absolute>. Absolutní souřadnicový systém není relativně k ohraničující pole. Hodnoty se interpretují přímo v místním prostoru.  
  
 Pro další <xref:System.Windows.Media.RadialGradientBrush> příklady najdete v tématu [štětce ukázka](http://go.microsoft.com/fwlink/?LinkID=159973). Další informace o přechody a dalších typů štětce najdete v tématu [vykreslování s plnou barvy a přechody přehled](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).
