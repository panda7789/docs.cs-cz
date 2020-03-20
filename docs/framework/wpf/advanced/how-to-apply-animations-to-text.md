---
title: 'Postupy: Použití animací na text'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], animations
- animation [WPF], text
ms.assetid: eec3d26c-0a21-420f-8012-671621c47089
ms.openlocfilehash: ed2f3beb904f724ac93e2c4033aa6b2eb3fa1290
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174625"
---
# <a name="how-to-apply-animations-to-text"></a>Postupy: Použití animací na text
Animace mohou změnit zobrazení a vzhled textu v aplikaci. Následující příklady používají různé typy animací ovlivnit zobrazení <xref:System.Windows.Controls.TextBlock> textu v ovládacím prvku.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.Animation.DoubleAnimation> k animaci šířky textového bloku. Hodnota šířky se změní z šířky textového bloku na 0 po dobu trvání 10 sekund a potom obrátí hodnoty šířky a pokračuje. Tento typ animace vytvoří efekt vymazání.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample1)]  
  
 Následující příklad používá <xref:System.Windows.Media.Animation.DoubleAnimation> k animaci krytí textového bloku. Hodnota krytí se změní z 1,0 na 0 po dobu trvání 5 sekund a potom obrátí hodnoty krytí a pokračuje.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample2)]  
  
 Následující diagram znázorňuje <xref:System.Windows.Controls.TextBlock> vliv ovládacího prvku, `1.00` `0.00` který mění jeho krytí z <xref:System.Windows.Media.Animation.Timeline.Duration%2A>na během intervalu 5 sekund definovaného .  
  
 ![Krytí změny textu z 1.00 na 0.00.](./media/how-to-apply-animations-to-text/faded-text-opacity-change.png)  

 Následující příklad používá <xref:System.Windows.Media.Animation.ColorAnimation> k animaci barvy popředí textového bloku. Hodnota barvy popředí se změní z jedné barvy na druhou po dobu trvání 5 sekund a potom obrátí hodnoty barev a pokračuje.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample3)]  
  
 Následující příklad používá <xref:System.Windows.Media.Animation.DoubleAnimation> k otočení textového bloku. Textový blok provádí úplné otočení po dobu 20 sekund a potom pokračuje v opakování otočení.  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample4](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample4)]  
  
## <a name="see-also"></a>Viz také

- [Přehled animace](../graphics-multimedia/animation-overview.md)
