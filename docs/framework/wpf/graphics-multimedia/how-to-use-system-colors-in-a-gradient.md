---
title: 'Postupy: Použití systémových barev v gradientu'
ms.date: 03/30/2017
helpviewer_keywords:
- gradients [WPF], system colors in
- system colors in gradients [WPF]
ms.assetid: 11942e7e-6300-4b50-8ed1-f50e8d20e7d2
ms.openlocfilehash: 44dfd30dc8d21e638855a383f1c9360a61ce81f9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54726413"
---
# <a name="how-to-use-system-colors-in-a-gradient"></a>Postupy: Použití systémových barev v gradientu
Pokud chcete použít systémové barvy v přechodu, je použít  *\<SystemColor >* barvu a  *\<SystemColor >* ColorKey statické vlastnosti <xref:System.Windows.SystemColors> třídy získat odkaz na barvu, kde  *\<SystemColor >* je název požadované systémovou barvou. Použití  *\<SystemColor >* ColorKey vlastnosti, pokud chcete vytvořit dynamické odkaz, který se aktualizuje automaticky při změně motiv systému. Jinak použijte  *\<SystemColor >* barva vlastnosti.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá dynamické systémových barev prostředků k vytvoření přechodu.  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemColorExample.xaml#graphicsmmdynamicsystemcolorgradientexamplewholepage)]  
  
 Následující příklad používá statickou systémových barev prostředků k vytvoření přechodu.  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemColorExample.xaml#graphicsmmstaticsystemcolorgradientexamplewholepage)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.SystemColors>
- [Vykreslení oblasti systémovým štětcem](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)
- [Přehled malování plnými barvami a přechody](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
