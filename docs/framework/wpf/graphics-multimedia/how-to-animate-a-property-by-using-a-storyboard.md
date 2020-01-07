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
ms.openlocfilehash: 6cfce9a5b070a23ed9ac03473888bf572b61393b
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559635"
---
# <a name="how-to-animate-a-property-by-using-a-storyboard"></a>Postupy: Animace vlastnosti pomocí scénáře
Tento příklad ukazuje, jak použít <xref:System.Windows.Media.Animation.Storyboard> k animaci vlastností. Chcete-li animovat vlastnost pomocí <xref:System.Windows.Media.Animation.Storyboard>, vytvořte animaci pro každou vlastnost, kterou chcete animovat, a také vytvořte <xref:System.Windows.Media.Animation.Storyboard>, která bude obsahovat animace.  
  
 Typ vlastnosti určuje typ animace, která se má použít. Chcete-li například animovat vlastnost, která přijímá <xref:System.Double> hodnoty, použijte <xref:System.Windows.Media.Animation.DoubleAnimation>. Vlastnosti <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> a <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> připojené určují objekt a vlastnost, na které se animace aplikuje.  
  
 Pokud chcete začít scénář v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], použijte akci <xref:System.Windows.Media.Animation.BeginStoryboard> a <xref:System.Windows.EventTrigger>. <xref:System.Windows.EventTrigger> zahájí <xref:System.Windows.Media.Animation.BeginStoryboard> akci, když dojde k události určené vlastností <xref:System.Windows.EventTrigger.RoutedEvent%2A>. Akce <xref:System.Windows.Media.Animation.BeginStoryboard> spustí <xref:System.Windows.Media.Animation.Storyboard>.  
  
 Následující příklad používá <xref:System.Windows.Media.Animation.Storyboard> objektů pro animaci dvou ovládacích prvků <xref:System.Windows.Controls.Button>. Aby se změnila velikost prvního tlačítka, je jeho <xref:System.Windows.FrameworkElement.Width%2A> animovaný. Aby se změnila barva druhého tlačítka, použije se vlastnost <xref:System.Windows.Media.SolidColorBrush.Color%2A> <xref:System.Windows.Media.SolidColorBrush> k nastavení <xref:System.Windows.Controls.Control.Background%2A> tlačítka, které je animováno.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[AnimatePropertyStoryboards#1](~/samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/StoryboardExample.xaml#1)]  
  
> [!NOTE]
> Přestože animace mohou cílit jak na objekt <xref:System.Windows.FrameworkElement>, například <xref:System.Windows.Controls.Control> nebo <xref:System.Windows.Controls.Panel>, a objekt <xref:System.Windows.Freezable>, jako je například <xref:System.Windows.Media.Brush> nebo <xref:System.Windows.Media.Transform>, má vlastnost <xref:System.Windows.FrameworkElement.Name%2A> vlastnost pouze prvky rozhraní. Chcete-li přiřadit název Freezable, aby mohl být cílem animace, použijte [direktivu x:Name](../../../desktop-wpf/xaml-services/xname-directive.md), jak ukazuje předchozí příklad.  
  
 Používáte-li kód, je nutné vytvořit <xref:System.Windows.NameScope> pro <xref:System.Windows.FrameworkElement> a zaregistrovat názvy objektů, které mají být s tímto <xref:System.Windows.FrameworkElement>animovány. Chcete-li spustit animace v kódu, použijte <xref:System.Windows.Media.Animation.BeginStoryboard> akci s <xref:System.Windows.EventTrigger>. Volitelně můžete použít obslužnou rutinu události a metodu <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> <xref:System.Windows.Media.Animation.Storyboard>. Následující příklad ukazuje, jak použít metodu <xref:System.Windows.Media.Animation.Storyboard.Begin%2A>.  
  
 [!code-csharp[AnimatePropertyStoryboards#11](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimatePropertyStoryboards/CSharp/StoryboardExample.cs#11)]
 [!code-vb[AnimatePropertyStoryboards#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AnimatePropertyStoryboards/VisualBasic/StoryboardExample.vb#11)]  
  
 Další informace o animacích a scénářích najdete v tématu [Přehled animací](animation-overview.md).  
  
 Použijete-li kód, nebudete omezeni na použití <xref:System.Windows.Media.Animation.Storyboard> objektů, aby bylo možné animovat vlastnosti. Další informace a příklady naleznete v tématu [animace vlastnosti bez použití scénáře](how-to-animate-a-property-without-using-a-storyboard.md) a [animace vlastnosti pomocí AnimationClock](how-to-animate-a-property-by-using-an-animationclock.md).
