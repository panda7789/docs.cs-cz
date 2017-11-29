---
title: "Postupy: Vykreslení oblasti systémovým štětcem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- system brushes [WPF], painting with
- painting [WPF], with system brushes
- brushes [WPF], painting with system brushes [WPF]
ms.assetid: 5141a763-9235-42cb-a6bb-afc75513eac7
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 355df3718d90768cdfa8bc9780c44c19eb4bf9bf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-paint-an-area-with-a-system-brush"></a>Postupy: Vykreslení oblasti systémovým štětcem
<xref:System.Windows.SystemColors> Třída poskytuje přístup k systému štětce a barvy, například <xref:System.Windows.SystemColors.ControlBrush%2A>, <xref:System.Windows.SystemColors.ControlBrushKey%2A>, a <xref:System.Windows.SystemColors.DesktopBrush%2A>. Je systém štětce <xref:System.Windows.Media.SolidColorBrush> objekt, který vybarví oblast s barvu zadaný systém. Štětce systému vždy vytvoří plnou výplň; nelze použít k vytvoření přechodu.  
  
 Štětce systému můžete použít jako statické nebo dynamické prostředků. Pomocí dynamického prostředku, pokud chcete, aby štětce k aktualizaci automaticky, pokud uživatel změní štětce systému, jako je aplikace spuštěna; Jinak použijte statické prostředků. Třída SystemColors obsahuje celou řadu statické vlastnosti, které následují striktní zásady vytváření názvů:  
  
-   *\<SystemColor >*štětce  
  
     Získá statický odkaz na <xref:System.Windows.Media.SolidColorBrush> barvy zadaný systému.  
  
-   *\<SystemColor >*BrushKey  
  
     Získá odkaz na dynamické <xref:System.Windows.Media.SolidColorBrush> barvy zadaný systému.  
  
-   *\<SystemColor >*barev  
  
     Získá statický odkaz na <xref:System.Windows.Media.Color> struktura barvu zadaný systém.  
  
-   *\<SystemColor >*ColorKey  
  
     Získá dynamické odkaz na <xref:System.Windows.Media.Color> struktura barvu zadaný systém.  
  
 Barva systému je <xref:System.Windows.Media.Color> struktura, která můžete použít ke konfiguraci štětce. Například můžete vytvořit pomocí nastavení barvy systému přechod <xref:System.Windows.Media.GradientStop.Color%2A> vlastnosti <xref:System.Windows.Media.LinearGradientBrush> objektu Přechodové zarážky pomocí systému barev. Příklad, naleznete v části [použití systému barev v přechodu](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá dynamický systém štětce odkaz nastavit na pozadí tlačítka.  
  
 [!code-xaml[brushsamples_snip#GraphicsMMDynamicSystemColorDesktopBrushKeyExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/DynamicSystemBrushExample.xaml#graphicsmmdynamicsystemcolordesktopbrushkeyexamplewholepage)]  
  
 Další příklad používá k nastavení pozadí tlačítko odkaz štětce statický systém.  
  
 [!code-xaml[brushsamples_snip#GraphicsMMStaticSystemColorDesktopBrushExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/StaticSystemBrushExample.xaml#graphicsmmstaticsystemcolordesktopbrushexamplewholepage)]  
  
 Příkladem zobrazujícím postup používání systémové barvy v přechodu, najdete v části [používat barvy systému v přechodu](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md).  
  
## <a name="see-also"></a>Viz také  
 [Použití systému barvy v přechodu](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-system-colors-in-a-gradient.md)  
 [Malování s plnou barvy a přechody – přehled](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
