---
title: 'Postupy: Animace vlastnosti pomocí scénáře'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], Storyboards
- Storyboards [WPF], animation
ms.assetid: f4a314e9-1da2-4367-85fc-1232487efa7a
ms.openlocfilehash: 7e67fb07a05d474999515a678fd72ac6b96953c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561069"
---
# <a name="how-to-animate-a-property-by-using-a-storyboard"></a>Postupy: Animace vlastnosti pomocí scénáře
Tento příklad ukazuje, jak používat <xref:System.Windows.Media.Animation.Storyboard> pro animaci vlastnosti. Pro vlastnost animaci pomocí <xref:System.Windows.Media.Animation.Storyboard>, vytvořit animace pro každou vlastnost, kterou chcete animace a také vytvořit <xref:System.Windows.Media.Animation.Storyboard> tak, aby obsahovala animací.  
  
 Typ vlastnosti určuje typ animace používat. Chcete-li například animace vlastnost, která přebírá <xref:System.Double> hodnoty, použijte <xref:System.Windows.Media.Animation.DoubleAnimation>. <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> a <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> přidružené vlastnosti zadejte objektu a vlastnosti, u které je použita animace.  
  
 Ke spuštění scénáře v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], používat <xref:System.Windows.Media.Animation.BeginStoryboard> akce a <xref:System.Windows.EventTrigger>. <xref:System.Windows.EventTrigger> Začíná <xref:System.Windows.Media.Animation.BeginStoryboard> akce při události, který je určeného jeho <xref:System.Windows.EventTrigger.RoutedEvent%2A> dojde k vlastnosti. <xref:System.Windows.Media.Animation.BeginStoryboard> Akce spustí <xref:System.Windows.Media.Animation.Storyboard>.  
  
 Následující příklad používá <xref:System.Windows.Media.Animation.Storyboard> objekty, které se použije animaci dva <xref:System.Windows.Controls.Button> ovládací prvky. Chcete-li na první tlačítko Změnit velikost, jeho <xref:System.Windows.FrameworkElement.Width%2A> je animace. Chcete, aby druhý tlačítko změnit barvu, <xref:System.Windows.Media.SolidColorBrush.Color%2A> vlastnost <xref:System.Windows.Media.SolidColorBrush> slouží k nastavení <xref:System.Windows.Controls.Control.Background%2A> tlačítka, které je animovaný.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[AnimatePropertyStoryboards#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/StoryboardExample.xaml#1)]  
  
> [!NOTE]
>  I když obě animací, můžete vybrat <xref:System.Windows.FrameworkElement> objektu, například <xref:System.Windows.Controls.Control> nebo <xref:System.Windows.Controls.Panel>a <xref:System.Windows.Freezable> objektů, jako například <xref:System.Windows.Media.Brush> nebo <xref:System.Windows.Media.Transform>, pouze elementy framework mají <xref:System.Windows.FrameworkElement.Name%2A> vlastnost. Chcete-li přiřadit název zmrazitelné, která může být cílem animace, použijte [x: Name – direktiva](../../../../docs/framework/xaml-services/x-name-directive.md), jak ukazuje předchozí příklad.  
  
 Pokud používáte kód, musíte vytvořit <xref:System.Windows.NameScope> pro <xref:System.Windows.FrameworkElement> a zaregistrujte názvy objektů k animace s třídou <xref:System.Windows.FrameworkElement>. Spusťte animací v kódu pomocí <xref:System.Windows.Media.Animation.BeginStoryboard> akce s <xref:System.Windows.EventTrigger>. Volitelně můžete obslužné rutiny události a <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metodu <xref:System.Windows.Media.Animation.Storyboard>. Následující příklad ukazuje způsob použití <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metoda.  
  
 [!code-csharp[AnimatePropertyStoryboards#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimatePropertyStoryboards/CSharp/StoryboardExample.cs#11)]
 [!code-vb[AnimatePropertyStoryboards#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AnimatePropertyStoryboards/VisualBasic/StoryboardExample.vb#11)]  
  
 Další informace o animace a scénářů najdete v tématu [animace přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
 Pokud používáte kód, nejste omezeno na použití <xref:System.Windows.Media.Animation.Storyboard> objektů, aby bylo možné animace vlastnosti. Další informace a příklady naleznete v tématu [animace vlastnosti bez použití scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md) a [animace vlastnost pomocí AnimationClock](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-an-animationclock.md).
