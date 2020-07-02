---
title: 'Postupy: Animace vlastnosti pomocí scénáře'
description: Enliven své uživatelské rozhraní pomocí animací a scénářů pro vlastnosti v Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], Storyboards
- Storyboards [WPF], animation
ms.assetid: f4a314e9-1da2-4367-85fc-1232487efa7a
ms.openlocfilehash: f21b606751b845905a7bde6d3a7658b214369cc6
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853745"
---
# <a name="how-to-animate-a-property-by-using-a-storyboard"></a>Postupy: Animace vlastnosti pomocí scénáře
Tento příklad ukazuje, jak použít <xref:System.Windows.Media.Animation.Storyboard> k animaci vlastností. Chcete-li animovat vlastnost pomocí <xref:System.Windows.Media.Animation.Storyboard> , vytvořte animaci pro každou vlastnost, kterou chcete animovat, a také vytvořte, <xref:System.Windows.Media.Animation.Storyboard> aby obsahovala animace.  
  
 Typ vlastnosti určuje typ animace, která se má použít. Chcete-li například animovat vlastnost, která přebírá <xref:System.Double> hodnoty, použijte <xref:System.Windows.Media.Animation.DoubleAnimation> . <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>Vlastnosti a <xref:System.Windows.Media.Animation.Storyboard.TargetProperty> připojené určují objekt a vlastnost, na které se animace aplikuje.  
  
 Chcete-li spustit scénář v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , použijte <xref:System.Windows.Media.Animation.BeginStoryboard> akci a <xref:System.Windows.EventTrigger> . <xref:System.Windows.EventTrigger>Spustí <xref:System.Windows.Media.Animation.BeginStoryboard> akci, když dojde k události, která je určena jeho <xref:System.Windows.EventTrigger.RoutedEvent%2A> vlastností. <xref:System.Windows.Media.Animation.BeginStoryboard>Akce spustí <xref:System.Windows.Media.Animation.Storyboard> .  
  
 Následující příklad používá <xref:System.Windows.Media.Animation.Storyboard> objekty pro animaci dvou <xref:System.Windows.Controls.Button> ovládacích prvků. Aby se změnila velikost prvního tlačítka, <xref:System.Windows.FrameworkElement.Width%2A> je animovaný. Chcete-li změnit barvu druhého tlačítka, <xref:System.Windows.Media.SolidColorBrush.Color%2A> vlastnost <xref:System.Windows.Media.SolidColorBrush> je použita k nastavení <xref:System.Windows.Controls.Control.Background%2A> animovaného tlačítka.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[AnimatePropertyStoryboards#1](~/samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/StoryboardExample.xaml#1)]  
  
> [!NOTE]
> Přestože animace mohou cílit jak na <xref:System.Windows.FrameworkElement> objekt, například <xref:System.Windows.Controls.Control> nebo <xref:System.Windows.Controls.Panel> , tak na <xref:System.Windows.Freezable> objekt, jako je například <xref:System.Windows.Media.Brush> nebo <xref:System.Windows.Media.Transform> , mají vlastnost pouze prvky rozhraní <xref:System.Windows.FrameworkElement.Name%2A> . Chcete-li přiřadit název Freezable, aby mohl být cílem animace, použijte [direktivu x:Name](../../../desktop-wpf/xaml-services/xname-directive.md), jak ukazuje předchozí příklad.  
  
 Použijete-li kód, musíte vytvořit <xref:System.Windows.NameScope> pro <xref:System.Windows.FrameworkElement> a zaregistrovat názvy objektů, které se mají animovat <xref:System.Windows.FrameworkElement> . Chcete-li spustit animace v kódu, použijte <xref:System.Windows.Media.Animation.BeginStoryboard> akci s <xref:System.Windows.EventTrigger> . Volitelně můžete použít obslužnou rutinu události a <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metodu <xref:System.Windows.Media.Animation.Storyboard> . Následující příklad ukazuje, jak použít <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> metodu.  
  
 [!code-csharp[AnimatePropertyStoryboards#11](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimatePropertyStoryboards/CSharp/StoryboardExample.cs#11)]
 [!code-vb[AnimatePropertyStoryboards#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AnimatePropertyStoryboards/VisualBasic/StoryboardExample.vb#11)]  
  
 Další informace o animacích a scénářích najdete v tématu [Přehled animací](animation-overview.md).  
  
 Použijete-li kód, nebudete omezeni pouze na použití objektů, aby <xref:System.Windows.Media.Animation.Storyboard> bylo možné animovat vlastnosti. Další informace a příklady naleznete v tématu [animace vlastnosti bez použití scénáře](how-to-animate-a-property-without-using-a-storyboard.md) a [animace vlastnosti pomocí AnimationClock](how-to-animate-a-property-by-using-an-animationclock.md).
