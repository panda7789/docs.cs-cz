---
title: 'Postupy: Animace velikosti FrameworkElement'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], FrameworkElement size
- FrameworkElement [WPF], animating size of
ms.assetid: d4cd5a13-c20d-4a6f-a2ba-14f2c9ce4cef
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 17882494e48c5d692c8a774e6d77408557976c71
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-animate-the-size-of-a-frameworkelement"></a>Postupy: Animace velikosti FrameworkElement
Pro animaci velikost <xref:System.Windows.FrameworkElement>, můžete buď animace jeho <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastnosti nebo použijte animovaný <xref:System.Windows.Media.ScaleTransform>.  
  
 V následujícím příkladu animuje velikost dvě tlačítka, pomocí těchto dvou přístupů. Jedno tlačítko změní velikost animace jeho <xref:System.Windows.FrameworkElement.Width%2A> vlastností a druhou změní velikost animace <xref:System.Windows.Media.ScaleTransform> u jeho <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost. Každé tlačítko obsahuje část textu. Na začátku hledaný text zobrazuje stejné v obou tlačítek, ale jako tlačítka se změní velikost, je poškozený, text v druhé tlačítko.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[transformanimations_snip#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/AnimatingSizeExample.xaml#1)]  
  
 Když prvku transformujete, jsou transformovány celý elementu a jeho obsah. Při přímo změnit velikost elementu, stejně jako na první tlačítko nejsou v obsahu elementu změnit, pokud jejich velikost a umístění závisí na velikosti jeho nadřazený element.  
  
 Animace velikost elementu s použitím animovaný transformaci, která jeho <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost poskytuje lepší výkon než animovaný jeho <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> přímo, protože <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost neaktivuje průchodu rozložení.  
  
 Další informace o animaci vlastnosti najdete v tématu [animace přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md). Další informace o transformací, najdete v článku [transformuje přehled](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).
