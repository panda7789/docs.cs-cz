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
ms.openlocfilehash: f6d043dc2975770fe9111c6266096eefb3fe15b0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54671691"
---
# <a name="how-to-create-a-custom-routed-event"></a>Postupy: Vytvoření vlastní směrované události
Pro vaše vlastní událost, podporu směrování událostí, budete muset zaregistrovat <xref:System.Windows.RoutedEvent> pomocí <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> metody. Tento příklad ukazuje základní informace o vytvoření vlastní směrované události.  
  
## <a name="example"></a>Příklad  
 Jak je znázorněno v následujícím příkladu, nejprve zaregistrovat <xref:System.Windows.RoutedEvent> pomocí <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> metody. Podle konvence <xref:System.Windows.RoutedEvent> statické pole Název musí končit příponou ***události***. V tomto příkladu je název události `Tap` a strategie směrování události je <xref:System.Windows.RoutingStrategy.Bubble>. Po volání registrace může poskytnout přidávat a odebírat [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] přístupových objektů událostí pro událost.  
  
 Všimněte si, že i když se vyvolá událost prostřednictvím `OnTap` virtuální metoda v tomto konkrétním příkladu, jak vyvolat události nebo jak událost reaguje na změny závisí na požadavcích.  
  
 Všimněte si také, že v tomto příkladu v podstatě implementuje celý podtřídou třídy <xref:System.Windows.Controls.Button>; tento podtřídy je vytvořen jako samostatné sestavení a pak vytvořit instanci jako vlastní třídu na samostatném [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] stránky. Toto je pro ilustraci koncepci, že rozčleněné ovládací prvky mohou být zařazeny do stromové struktury skládá z jiných ovládacích prvků a, v takovém případě vlastní události do těchto ovládacích prvků mají stejné možnosti směrování událostí jako nativní [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] nemá element.  
  
 [!code-csharp[RoutedEventCustom#CustomClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#customclass)]
 [!code-vb[RoutedEventCustom#CustomClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#customclass)]  
  
 [!code-xaml[RoutedEventCustom#Page](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/RoutedEventCustomApp/default.xaml#page)]  
  
 Tunelového propojení budou vytvořeny události, stejný způsobem, ale s <xref:System.Windows.RoutedEvent.RoutingStrategy%2A> nastavena na <xref:System.Windows.RoutingStrategy.Tunnel> při volání metody registrace. Podle konvence, tunelové propojení událostí v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mají předponu slovo "Verze Preview".  
  
 Příkladem práce jak šíření událostí najdete v tématu [zpracování události směrovat](../../../../docs/framework/wpf/advanced/how-to-handle-a-routed-event.md).  
  
## <a name="see-also"></a>Viz také:
- [Přehled směrovaných událostí](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
- [Přehled vstupu](../../../../docs/framework/wpf/advanced/input-overview.md)
- [Přehled vytváření ovládacích prvků](../../../../docs/framework/wpf/controls/control-authoring-overview.md)
