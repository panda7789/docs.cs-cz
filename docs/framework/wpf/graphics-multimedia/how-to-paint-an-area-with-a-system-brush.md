---
title: 'Postupy: Vykreslení oblasti systémovým štětcem'
ms.date: 03/30/2017
helpviewer_keywords:
- system brushes [WPF], painting with
- painting [WPF], with system brushes
- brushes [WPF], painting with system brushes [WPF]
ms.assetid: 5141a763-9235-42cb-a6bb-afc75513eac7
ms.openlocfilehash: e713903e2cfbb63cb64ceb94621317f9e76dea70
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59195043"
---
# <a name="how-to-paint-an-area-with-a-system-brush"></a>Postupy: Vykreslení oblasti systémovým štětcem
<xref:System.Windows.SystemColors> Třídě poskytuje přístup k systémových štětců a barvy, jako například <xref:System.Windows.SystemColors.ControlBrush%2A>, <xref:System.Windows.SystemColors.ControlBrushKey%2A>, a <xref:System.Windows.SystemColors.DesktopBrush%2A>. Je systém štětce <xref:System.Windows.Media.SolidColorBrush> objekt, který vykreslí oblasti barvou zadaný systém. Systémové štětce vždy vytváří plné barvy; nelze použít k vytvoření přechodu.  
  
 Systémových štětců slouží jako statická nebo dynamická prostředek. Použít dynamický prostředek štětce, který se automaticky aktualizovat, pokud uživatel změní štětce systému, jako je aplikace spuštěna; Jinak použijte statických prostředků. Třída SystemColors obsahuje širokou škálu statické vlastnosti, které následují přísné zásady vytváření názvů:  
  
-   *\<SystemColor >* štětce  
  
     Získá statický odkaz na <xref:System.Windows.Media.SolidColorBrush> zadaný systém barvy.  
  
-   *\<SystemColor>* BrushKey  
  
     Získá odkaz na dynamické <xref:System.Windows.Media.SolidColorBrush> zadaný systém barvy.  
  
-   *\<SystemColor>* Color  
  
     Získá statický odkaz na <xref:System.Windows.Media.Color> struktury zadané systémovou barvou.  
  
-   *\<SystemColor >* ColorKey  
  
     Získá odkaz na dynamické <xref:System.Windows.Media.Color> struktury zadané systémovou barvou.  
  
 Systémové barvy je <xref:System.Windows.Media.Color> struktura, která slouží ke konfiguraci štětce. Například můžete vytvořit pomocí nastavení systémových barev přechod <xref:System.Windows.Media.GradientStop.Color%2A> vlastnosti <xref:System.Windows.Media.LinearGradientBrush> objektu Přechodové zarážky pomocí systémových barev. Příklad najdete v tématu [použití systémových barev v gradientu](how-to-use-system-colors-in-a-gradient.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá odkaz štětce dynamickým nastavit pozadí tlačítka.  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorDesktopBrushKeyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemBrushExample.xaml#graphicsmmdynamicsystemcolordesktopbrushkeyexamplewholepage)]  
  
 Následující příklad používá statický systém štětce odkaz nastavení pozadí tlačítka.  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorDesktopBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemBrushExample.xaml#graphicsmmstaticsystemcolordesktopbrushexamplewholepage)]  
  
 Příklad ukazující způsob použití systémových barev v gradientu najdete v tématu [použití systémových barev v gradientu](how-to-use-system-colors-in-a-gradient.md).  
  
## <a name="see-also"></a>Viz také:

- [Použití systémových barev v přechodu](how-to-use-system-colors-in-a-gradient.md)
- [Přehled malování plnými barvami a přechody](painting-with-solid-colors-and-gradients-overview.md)
