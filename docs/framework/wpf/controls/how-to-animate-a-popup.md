---
title: "Postupy: Animace překryvného objektu "
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Popup control [WPF], animating
- animation [WPF], Popup controls
ms.assetid: acaa2a0a-6137-4efd-9cd1-75ece222e390
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 276c1a54cfdddcde84c0702f4e84f1dc6174bbda
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-a-popup"></a>Postupy: Animace překryvného objektu 
Tento příklad ukazuje dva způsoby, jak animace <xref:System.Windows.Controls.Primitives.Popup> ovládacího prvku.  
  
## <a name="example"></a>Příklad  
 Následující příklad nastavuje <xref:System.Windows.Controls.Primitives.PopupAnimation> vlastnost na hodnotu <xref:System.Windows.Controls.Primitives.PopupAnimation.Slide>, který spustí <xref:System.Windows.Controls.Primitives.Popup> k "snímku in" Pokud se zobrazí.  
  
 Chcete-li otočit <xref:System.Windows.Controls.Primitives.Popup>, tento příklad přiřadí <xref:System.Windows.Media.RotateTransform> k <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost <xref:System.Windows.Controls.Canvas>, tedy o podřízený prvek <xref:System.Windows.Controls.Primitives.Popup>.  
  
 Pro transformaci fungovala správně, musíte nastavit na příklad <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> vlastnost `true`. Kromě toho <xref:System.Windows.FrameworkElement.Margin%2A> na <xref:System.Windows.Controls.Canvas> obsahu musíte zadat dostatek místa pro <xref:System.Windows.Controls.Primitives.Popup> otočení.  
  
 [!code-xaml[AnimatedPopup#RotateTransform2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform2)]  
  
 Následující příklad ukazuje způsob <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událost, ke které dojde při <xref:System.Windows.Controls.Button> po kliknutí na, aktivační události <xref:System.Windows.Media.Animation.Storyboard> animace bude spuštěna, který.  
  
 [!code-xaml[AnimatedPopup#RotateTransform1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform1)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.UIElement.RenderTransform%2A>  
 <xref:System.Windows.Controls.Primitives.BulletDecorator>  
 <xref:System.Windows.Media.RotateTransform>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 <xref:System.Windows.Controls.Primitives.Popup>  
 [Postupy: témata](../../../../docs/framework/wpf/controls/popup-how-to-topics.md)  
 [Přehled místní nabídka](../../../../docs/framework/wpf/controls/popup-overview.md)
