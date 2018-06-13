---
title: 'Postupy: Použití animací na text'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], animations
- animation [WPF], text
ms.assetid: eec3d26c-0a21-420f-8012-671621c47089
ms.openlocfilehash: 56a12ca915cc320619a094df38d118eabf202734
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545435"
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
 [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
