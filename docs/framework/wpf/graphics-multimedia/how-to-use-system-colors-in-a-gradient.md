---
title: 'Postupy: Použití systémových barev v přechodu'
ms.date: 03/30/2017
helpviewer_keywords:
- gradients [WPF], system colors in
- system colors in gradients [WPF]
ms.assetid: 11942e7e-6300-4b50-8ed1-f50e8d20e7d2
ms.openlocfilehash: 55c99640907a0c372f8c7bbc50b9b45c9f15ef3c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769236"
---
# <a name="how-to-use-system-colors-in-a-gradient"></a>Postupy: Použití systémových barev v přechodu
Pokud chcete použít systémové barvy v přechodu, je použít  *\<SystemColor >* barvu a  *\<SystemColor >* ColorKey statické vlastnosti <xref:System.Windows.SystemColors> třídy získat odkaz na barvu, kde  *\<SystemColor >* je název požadované systémovou barvou. Použití  *\<SystemColor >* ColorKey vlastnosti, pokud chcete vytvořit dynamické odkaz, který se aktualizuje automaticky při změně motiv systému. Jinak použijte  *\<SystemColor >* barva vlastnosti.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá dynamické systémových barev prostředků k vytvoření přechodu.  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorGradientExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemColorExample.xaml#graphicsmmdynamicsystemcolorgradientexamplewholepage)]  
  
 Následující příklad používá statickou systémových barev prostředků k vytvoření přechodu.  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorGradientExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemColorExample.xaml#graphicsmmstaticsystemcolorgradientexamplewholepage)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.SystemColors>
- [Vykreslení oblasti systémovým štětcem](how-to-paint-an-area-with-a-system-brush.md)
- [Přehled malování plnými barvami a přechody](painting-with-solid-colors-and-gradients-overview.md)
