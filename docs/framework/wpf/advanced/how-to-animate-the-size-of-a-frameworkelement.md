---
title: 'Postupy: Animace velikosti FrameworkElement'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], FrameworkElement size
- FrameworkElement [WPF], animating size of
ms.assetid: d4cd5a13-c20d-4a6f-a2ba-14f2c9ce4cef
ms.openlocfilehash: d1995deec5ab2c9bf405911af43b4d242d599119
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776906"
---
# <a name="how-to-animate-the-size-of-a-frameworkelement"></a>Postupy: Animace velikosti FrameworkElement
Animování velikost <xref:System.Windows.FrameworkElement>, můžete buď animovat jeho <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastnosti nebo použití animovaného <xref:System.Windows.Media.ScaleTransform>.  
  
 V následujícím příkladu animuje velikost dvě tlačítka pomocí těchto dvou přístupů. Jedno tlačítko se změnila velikost animace jeho <xref:System.Windows.FrameworkElement.Width%2A> vlastnost a druhý se změnila velikost animace <xref:System.Windows.Media.ScaleTransform> u jeho <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost. Každé tlačítko obsahuje nějaký text. Na začátku text se zobrazí stejné v obou tlačítka, ale jak se mění velikost tlačítka, text v druhé tlačítko je poškozený.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[transformanimations_snip#1](~/samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/AnimatingSizeExample.xaml#1)]  
  
 Při transformaci elementu jsou transformovány celý prvek a jeho obsah. Při přímo měnit velikost prvku, jako v případě na první tlačítko v obsahu elementu nejsou velikost, pokud jejich velikost a umístění závisí na velikosti jejich nadřazeného elementu.  
  
 Animace velikosti elementu s použitím animací transformace na jeho <xref:System.Windows.UIElement.RenderTransform%2A> poskytuje lepší výkon než animovat vlastnost jeho <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> přímo, protože <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost neaktivuje předání rozložení.  
  
 Další informace o animace vlastností najdete v tématu [přehled animace](../graphics-multimedia/animation-overview.md). Další informace o transformacích, najdete v článku [transformuje přehled](../graphics-multimedia/transforms-overview.md).
