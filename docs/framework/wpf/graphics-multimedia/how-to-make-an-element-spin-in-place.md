---
title: 'Postupy: Zarovnání číselníku'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], spinning elements
- spinning elements [WPF]
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
ms.openlocfilehash: a1b515822391de08ec8ed8ff0ff1f0086874dc02
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112073"
---
# <a name="how-to-make-an-element-spin-in-place"></a>Postupy: Zarovnání číselníku
Tento příklad ukazuje, jak provést otočení <xref:System.Windows.Media.RotateTransform> prvku <xref:System.Windows.Media.Animation.DoubleAnimation>pomocí a .  
  
 Následující příklad platí <xref:System.Windows.Media.RotateTransform> pro <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost prvku. Příklad používá <xref:System.Windows.Media.Animation.DoubleAnimation> animovat <xref:System.Windows.Media.RotateTransform.Angle%2A> <xref:System.Windows.Media.RotateTransform>. Chcete-li prvek rotovat na místě, příklad nastaví <xref:System.Windows.UIElement.RenderTransformOrigin%2A> vlastnost prvku do bodu (0,5, 0,5).  
  
## <a name="example"></a>Příklad  
 [!code-xaml[transformanimations_snip#11](~/samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 Pro kompletní vzorek, který obsahuje další příklady transformace, viz [2D transformace Ukázka](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms).  
  
## <a name="see-also"></a>Viz také

- [Přehled animace](animation-overview.md)
- [Přehled transformace](transforms-overview.md)
