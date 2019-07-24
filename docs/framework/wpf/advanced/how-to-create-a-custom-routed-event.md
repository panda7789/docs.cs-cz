---
title: 'Postupy: Vytvoření vlastní směrované události'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- routed events [WPF], creating
- events [WPF], routing
ms.assetid: b79f459a-1c3f-4045-b2d4-1659cc8eaa3c
ms.openlocfilehash: cbfb88af4e35e3f090248982bb14d6b7a3a03cef
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401464"
---
# <a name="how-to-create-a-custom-routed-event"></a>Postupy: Vytvoření vlastní směrované události
Aby vaše vlastní událost podporovala směrování událostí, je nutné ji zaregistrovat <xref:System.Windows.RoutedEvent> <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> pomocí metody. Tento příklad ukazuje základy vytvoření vlastní směrované události.  
  
## <a name="example"></a>Příklad  
 Jak je znázorněno v následujícím příkladu, nejprve zaregistrujete <xref:System.Windows.RoutedEvent> <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> pomocí metody. Podle konvence <xref:System.Windows.RoutedEvent> by měl název statického pole končit ***událostí***přípony. V tomto příkladu je název události `Tap` a strategie směrování události je. <xref:System.Windows.RoutingStrategy.Bubble> Po volání registrace můžete pro událost zadat doplňky pro přístup k modulům CLR (Common Language Runtime) a odebrat je.  
  
 Všimněte si, že i když se událost vyvolá prostřednictvím `OnTap` virtuální metody v tomto konkrétním příkladu, jak vyvoláte událost nebo jak vaše událost reaguje na změny, závisí na vašich potřebách.  
  
 Všimněte si také, že tento příklad v podstatě implementuje celou podtřídu <xref:System.Windows.Controls.Button>třídy; tato podtřída je sestavena jako samostatné sestavení a poté vytvořena instance jako vlastní třída na samostatné [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] stránce. To je znázornění konceptu, který mohou být ovládací prvky podtříd vloženy do stromů složených z jiných ovládacích prvků a v této situaci mají vlastní události na těchto ovládacích prvcích stejné možnosti směrování událostí jako všechny nativní [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] prvky.  
  
 [!code-csharp[RoutedEventCustom#CustomClass](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#customclass)]
 [!code-vb[RoutedEventCustom#CustomClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#customclass)]  
  
 [!code-xaml[RoutedEventCustom#Page](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/RoutedEventCustomApp/default.xaml#page)]  
  
 Události tunelového propojení jsou vytvářeny stejným způsobem, ale <xref:System.Windows.RoutedEvent.RoutingStrategy%2A> s nastavením <xref:System.Windows.RoutingStrategy.Tunnel> na při volání registrace. Podle konvence jsou události tunelu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v v předponě ve slově Preview.  
  
 Příklad toho, jak fungují události probublávání, najdete v tématu [zpracování směrované události](how-to-handle-a-routed-event.md).  
  
## <a name="see-also"></a>Viz také:

- [Přehled směrovaných událostí](routed-events-overview.md)
- [Přehled vstupu](input-overview.md)
- [Přehled vytváření ovládacích prvků](../controls/control-authoring-overview.md)
