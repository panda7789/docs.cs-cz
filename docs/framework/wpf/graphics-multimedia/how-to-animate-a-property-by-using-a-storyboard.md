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
ms.openlocfilehash: a7a2656d84d37d3e2726df009a07ccf29661df07
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963046"
---
# <a name="how-to-animate-a-property-by-using-a-storyboard"></a>Postupy: Animace vlastnosti pomocí scénáře
Tento příklad ukazuje, jak použít <xref:System.Windows.Media.Animation.Storyboard> k animaci vlastností. Chcete-li animovat vlastnost pomocí <xref:System.Windows.Media.Animation.Storyboard>, vytvořte animaci pro každou vlastnost, kterou chcete animovat, a také <xref:System.Windows.Media.Animation.Storyboard> vytvořte, aby obsahovala animace.  
  
 Typ vlastnosti určuje typ animace, která se má použít. Chcete-li například animovat vlastnost, která přebírá <xref:System.Double> hodnoty, <xref:System.Windows.Media.Animation.DoubleAnimation>použijte. Vlastnosti <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> a<xref:System.Windows.Media.Animation.Storyboard.TargetProperty> připojené určují objekt a vlastnost, na které se animace aplikuje.  
  
 Chcete-li spustit scénář [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]v, <xref:System.Windows.Media.Animation.BeginStoryboard> použijte akci a <xref:System.Windows.EventTrigger>. Spustí akci, když dojde k události, která je určena jeho <xref:System.Windows.EventTrigger.RoutedEvent%2A> vlastností. <xref:System.Windows.Media.Animation.BeginStoryboard> <xref:System.Windows.EventTrigger> <xref:System.Windows.Media.Animation.BeginStoryboard> Akce<xref:System.Windows.Media.Animation.Storyboard>spustí.  
  
 Následující příklad používá <xref:System.Windows.Media.Animation.Storyboard> objekty pro animaci dvou <xref:System.Windows.Controls.Button> ovládacích prvků. Aby se změnila velikost prvního tlačítka, <xref:System.Windows.FrameworkElement.Width%2A> je animovaný. Chcete-li změnit barvu druhého tlačítka, <xref:System.Windows.Media.SolidColorBrush.Color%2A> vlastnost <xref:System.Windows.Media.SolidColorBrush> <xref:System.Windows.Controls.Control.Background%2A> je použita k nastavení animovaného tlačítka.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[AnimatePropertyStoryboards#1](~/samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/StoryboardExample.xaml#1)]  
  
> [!NOTE]
> Přestože animace mohou cílit jak na <xref:System.Windows.FrameworkElement> objekt, například <xref:System.Windows.Controls.Control> nebo <xref:System.Windows.Controls.Panel>, tak na <xref:System.Windows.Freezable> objekt <xref:System.Windows.FrameworkElement.Name%2A> , jako je <xref:System.Windows.Media.Brush> například nebo <xref:System.Windows.Media.Transform>, mají vlastnost pouze prvky rozhraní. Chcete-li přiřadit název Freezable, aby mohl být cílem animace, použijte [direktivu x:Name](../../xaml-services/x-name-directive.md), jak ukazuje předchozí příklad.  
  
 Použijete-li kód, musíte vytvořit <xref:System.Windows.NameScope> <xref:System.Windows.FrameworkElement> pro a zaregistrovat názvy objektů, <xref:System.Windows.FrameworkElement>které se mají animovat. Chcete-li spustit animace v kódu, použijte <xref:System.Windows.Media.Animation.BeginStoryboard> akci <xref:System.Windows.EventTrigger>s. Volitelně můžete použít obslužnou rutinu události a <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> <xref:System.Windows.Media.Animation.Storyboard>metodu. Následující příklad ukazuje, jak použít <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metodu.  
  
 [!code-csharp[AnimatePropertyStoryboards#11](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimatePropertyStoryboards/CSharp/StoryboardExample.cs#11)]
 [!code-vb[AnimatePropertyStoryboards#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AnimatePropertyStoryboards/VisualBasic/StoryboardExample.vb#11)]  
  
 Další informace o animacích a scénářích najdete v tématu [Přehled animací](animation-overview.md).  
  
 Použijete-li kód, nebudete omezeni <xref:System.Windows.Media.Animation.Storyboard> pouze na použití objektů, aby bylo možné animovat vlastnosti. Další informace a příklady naleznete v tématu [animace vlastnosti bez použití scénáře](how-to-animate-a-property-without-using-a-storyboard.md) a [animace vlastnosti pomocí AnimationClock](how-to-animate-a-property-by-using-an-animationclock.md).
