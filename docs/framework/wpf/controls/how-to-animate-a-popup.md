---
title: 'Postupy: Animace prvku Popup'
ms.date: 03/30/2017
helpviewer_keywords:
- Popup control [WPF], animating
- animation [WPF], Popup controls
ms.assetid: acaa2a0a-6137-4efd-9cd1-75ece222e390
ms.openlocfilehash: b70d9c4cb1bca26a6c77d3a7c50add517ca8ef92
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61911284"
---
# <a name="how-to-animate-a-popup"></a>Postupy: Animace prvku Popup
Tento příklad ukazuje dva způsoby, jak animovat <xref:System.Windows.Controls.Primitives.Popup> ovládacího prvku.  
  
## <a name="example"></a>Příklad  
 Následující příklad nastaví <xref:System.Windows.Controls.Primitives.PopupAnimation> vlastnost na hodnotu <xref:System.Windows.Controls.Primitives.PopupAnimation.Slide>, které způsobí, že <xref:System.Windows.Controls.Primitives.Popup> "snímku – v" když se objeví.  
  
 Aby bylo možné otočit <xref:System.Windows.Controls.Primitives.Popup>, přiřadí tento příklad <xref:System.Windows.Media.RotateTransform> k <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost <xref:System.Windows.Controls.Canvas>, tedy podřízený prvek <xref:System.Windows.Controls.Primitives.Popup>.  
  
 Pro transformace fungovala správně, musíte nastavit v příkladu <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> vlastnost `true`. Kromě toho <xref:System.Windows.FrameworkElement.Margin%2A> na <xref:System.Windows.Controls.Canvas> obsahu musíte zadat dostatek místa pro <xref:System.Windows.Controls.Primitives.Popup> otočí.  
  
 [!code-xaml[AnimatedPopup#RotateTransform2](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform2)]  
  
 Následující příklad ukazuje jak <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událost, ke které dojde při <xref:System.Windows.Controls.Button> dojde ke kliknutí na, aktivační události <xref:System.Windows.Media.Animation.Storyboard> , který spouští animace.  
  
 [!code-xaml[AnimatedPopup#RotateTransform1](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.UIElement.RenderTransform%2A>
- <xref:System.Windows.Controls.Primitives.BulletDecorator>
- <xref:System.Windows.Media.RotateTransform>
- <xref:System.Windows.Media.Animation.Storyboard>
- <xref:System.Windows.Controls.Primitives.Popup>
- [Témata s postupy](popup-how-to-topics.md)
- [Přehled prvku Popup](popup-overview.md)
