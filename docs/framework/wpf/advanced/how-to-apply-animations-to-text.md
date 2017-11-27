---
title: "Postupy: Použití animací na text"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- typography [WPF], animations
- animation [WPF], text
ms.assetid: eec3d26c-0a21-420f-8012-671621c47089
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0298462db5897e955bf0a2551cca7fc81bb27d89
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-apply-animations-to-text"></a>Postupy: Použití animací na text
Animace můžete změnit vzhled textu v aplikaci a zobrazení. Následující příklady používají různé typy animací ovlivnit zobrazení textu v <xref:System.Windows.Controls.TextBlock> ovládacího prvku.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.Animation.DoubleAnimation> pro animaci šířku bloku textu. Hodnota width změní z šířka textového bloku na hodnotu 0 na dobu trvání 10 sekund a pak obrátí width hodnot a pokračuje. Tento typ animace vytvoří efekt vymazání.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample1)]  
  
 Následující příklad používá <xref:System.Windows.Media.Animation.DoubleAnimation> pro animaci krytí bloku textu. Hodnota neprůhlednosti změní z 1.0 0 přes v délce 5 sekund a pak obrátí hodnoty krytí a pokračuje.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample2)]  
  
 Následující diagram znázorňuje účinku <xref:System.Windows.Controls.TextBlock> změna jeho krytí z ovládacího prvku `1.00` k `0.00` během 5 sekund intervalu definované <xref:System.Windows.Media.Animation.Timeline.Duration%2A>.  
  
 ![Text Změna krytí z 1,00 na 0,00](../../../../docs/framework/wpf/advanced/media/fadedtext01.png "FadedText01")  
Změna z 1,00 na 0,00 krytí textu  
  
 Následující příklad používá <xref:System.Windows.Media.Animation.ColorAnimation> pro animaci barvu popředí bloku textu. Hodnota barvu popředí změní z jedné barvy na druhou barvu přes v délce 5 sekund a pak obrátí hodnoty barev a pokračuje.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample3)]  
  
 Následující příklad používá <xref:System.Windows.Media.Animation.DoubleAnimation> otočení bloku textu. Blok textu provede úplné otočení na dobu trvání 20 sekund a poté pokračuje opakování je oběh.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample4)]  
  
## <a name="see-also"></a>Viz také  
 [Animace – přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
