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
ms.openlocfilehash: f6064368b4f5e4fa8324b4039d734d4430cd9174
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364707"
---
# <a name="how-to-animate-a-property-by-using-a-storyboard"></a>Postupy: Animace vlastnosti pomocí scénáře
Tento příklad ukazuje způsob použití <xref:System.Windows.Media.Animation.Storyboard> pro animaci vlastnosti. Animovat vlastnost pomocí <xref:System.Windows.Media.Animation.Storyboard>, vytvořit animaci pro každou vlastnost, kterou chcete animace a také vytvořit <xref:System.Windows.Media.Animation.Storyboard> tak, aby obsahovala animací.  
  
 Typ vlastnosti určuje typ animace použít. Chcete-li například animovat vlastnost, která přebírá <xref:System.Double> hodnoty, použijte <xref:System.Windows.Media.Animation.DoubleAnimation>. <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> a <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> připojené vlastnosti zadat objekt a vlastnosti, na který je použita animace.  
  
 Pro spuštění scénáře v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], použití <xref:System.Windows.Media.Animation.BeginStoryboard> akce a <xref:System.Windows.EventTrigger>. <xref:System.Windows.EventTrigger> Začíná <xref:System.Windows.Media.Animation.BeginStoryboard> akci, když událost, která je určená jeho <xref:System.Windows.EventTrigger.RoutedEvent%2A> dojde k vlastnosti. <xref:System.Windows.Media.Animation.BeginStoryboard> Spustí akce <xref:System.Windows.Media.Animation.Storyboard>.  
  
 Následující příklad používá <xref:System.Windows.Media.Animation.Storyboard> objekty animace dvě <xref:System.Windows.Controls.Button> ovládacích prvků. Abyste měli na první tlačítko Změnit velikost, jeho <xref:System.Windows.FrameworkElement.Width%2A> je animovaný. Chcete-li na druhé tlačítko změnit barvu, <xref:System.Windows.Media.SolidColorBrush.Color%2A> vlastnost <xref:System.Windows.Media.SolidColorBrush> slouží k nastavení <xref:System.Windows.Controls.Control.Background%2A> tlačítka, který je animovaný.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[AnimatePropertyStoryboards#1](~/samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/StoryboardExample.xaml#1)]  
  
> [!NOTE]
>  I když můžete animace cílí na obě <xref:System.Windows.FrameworkElement> objektu, například <xref:System.Windows.Controls.Control> nebo <xref:System.Windows.Controls.Panel>a <xref:System.Windows.Freezable> objektu, například <xref:System.Windows.Media.Brush> nebo <xref:System.Windows.Media.Transform>, pouze elementy framework mají <xref:System.Windows.FrameworkElement.Name%2A> vlastnost. Chcete-li přiřadit název zablokovatelného objektu, která může být cílem animace, použijte [x: Name – direktiva](../../xaml-services/x-name-directive.md), jak ukazuje předchozí příklad.  
  
 Pokud kód použít, musíte vytvořit <xref:System.Windows.NameScope> pro <xref:System.Windows.FrameworkElement> a zaregistrujte názvy objektů pro animaci s ním <xref:System.Windows.FrameworkElement>. Chcete-li spustit animací v kódu, použijte <xref:System.Windows.Media.Animation.BeginStoryboard> akce s <xref:System.Windows.EventTrigger>. Volitelně můžete použít obslužnou rutinu události a <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metoda <xref:System.Windows.Media.Animation.Storyboard>. Následující příklad ukazuje způsob použití <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metody.  
  
 [!code-csharp[AnimatePropertyStoryboards#11](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimatePropertyStoryboards/CSharp/StoryboardExample.cs#11)]
 [!code-vb[AnimatePropertyStoryboards#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AnimatePropertyStoryboards/VisualBasic/StoryboardExample.vb#11)]  
  
 Další informace o animace a scénáře, naleznete v tématu [přehled animace](animation-overview.md).  
  
 Pokud používáte kód, nejste omezeni pomocí <xref:System.Windows.Media.Animation.Storyboard> objektů, aby bylo možné animace vlastností. Další informace a příklady najdete v tématu [animace vlastnosti bez pomoci scénáře](how-to-animate-a-property-without-using-a-storyboard.md) a [animace vlastnosti pomocí AnimationClock](how-to-animate-a-property-by-using-an-animationclock.md).
