---
title: "Postupy: Zarovnání číselníku"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [WPF], spinning elements
- spinning elements [WPF]
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ae76d33a30853107cbecf0749230aefce77a866d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-make-an-element-spin-in-place"></a>Postupy: Zarovnání číselníku
Tento příklad ukazuje, jak k nastavení vzhledu elementu číselníku pomocí <xref:System.Windows.Media.RotateTransform> a <xref:System.Windows.Media.Animation.DoubleAnimation>.  
  
 Následující příklad se vztahuje <xref:System.Windows.Media.RotateTransform> k <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost elementu. V příkladu se používá <xref:System.Windows.Media.Animation.DoubleAnimation> pro animaci <xref:System.Windows.Media.RotateTransform.Angle%2A> z <xref:System.Windows.Media.RotateTransform>. Chcete-li element číselníku na místě, nastaví v příkladu <xref:System.Windows.UIElement.RenderTransformOrigin%2A> vlastnost elementu bodu (0,5, 0,5).  
  
## <a name="example"></a>Příklad  
 [!code-xaml[transformanimations_snip#11](../../../../samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 Kompletní příklad, který obsahuje další příklady transformace, najdete v části [2-D transformací ukázka](http://go.microsoft.com/fwlink/?LinkID=158252).  
  
## <a name="see-also"></a>Viz také  
 [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Přehled transformace](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
