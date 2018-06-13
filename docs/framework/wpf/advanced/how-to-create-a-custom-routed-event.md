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
ms.openlocfilehash: a8aa038008ed93cedfe49fde4e0269712b4fb19a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543703"
---
# <a name="how-to-create-a-custom-routed-event"></a>Postupy: Vytvoření vlastní směrované události
Pro vaše vlastní události pro podporu směrování událostí, je třeba zaregistrovat <xref:System.Windows.RoutedEvent> pomocí <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> metoda. Tento příklad ukazuje základní informace o vytváření vlastních směrované události.  
  
## <a name="example"></a>Příklad  
 Jak je znázorněno v následujícím příkladu, nejprve zaregistrovat <xref:System.Windows.RoutedEvent> pomocí <xref:System.Windows.EventManager.RegisterRoutedEvent%2A> metoda. Podle konvence <xref:System.Windows.RoutedEvent> statické pole name musí končit příponou ***událostí***. V tomto příkladu je název události `Tap` a směrování strategie události je <xref:System.Windows.RoutingStrategy.Bubble>. Po registraci volání, můžete zadat přidat a odebrat [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] přístupových objektů událostí pro událost.  
  
 Všimněte si, že i když tato událost se vyvolá prostřednictvím `OnTap` virtuální metoda v tomto konkrétním příkladu, jak vyvolat událost nebo jak událost reaguje na změny, závisí na vašim potřebám.  
  
 Všimněte si také, že v tomto příkladu v podstatě implementuje celý podtřídou třídy <xref:System.Windows.Controls.Button>; že podtřídou je vytvořené jako samostatné sestavení a pak vytvořit instance jako vlastní třída na samostatném [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] stránky. Toto je k objasnění konceptu rozčleněné ovládací prvky, se vkládají do stromy skládá z jiných ovládacích prvků, a aby v této situaci vlastních událostí na tyto ovládací prvky velmi stejné funkce směrování událostí jako jakýkoli nativní [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] nemá element.  
  
 [!code-csharp[RoutedEventCustom#CustomClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#customclass)]
 [!code-vb[RoutedEventCustom#CustomClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#customclass)]  
  
 [!code-xaml[RoutedEventCustom#Page](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/RoutedEventCustomApp/default.xaml#page)]  
  
 Tunelové události jsou vytvořené stejný způsobem, ale s <xref:System.Windows.RoutedEvent.RoutingStrategy%2A> nastavena na <xref:System.Windows.RoutingStrategy.Tunnel> ve volání registrace. Podle konvence, tunelové propojení události v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mají předponu slovo "Náhled".  
  
 Příklad, jak probublávání události práce najdete v sekci [zpracování události směrovány](../../../../docs/framework/wpf/advanced/how-to-handle-a-routed-event.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled směrovaných událostí](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [Přehled vstupu](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [Přehled vytváření ovládacích prvků](../../../../docs/framework/wpf/controls/control-authoring-overview.md)
