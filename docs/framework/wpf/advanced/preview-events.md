---
title: Události náhledu
ms.date: 03/30/2017
helpviewer_keywords:
- Preview events [WPF]
- suppressing events [WPF]
- events [WPF], Preview
- events [WPF], suppressing
ms.assetid: b5032308-aa9c-4d02-af11-630ecec8df7e
ms.openlocfilehash: d57f2a59a9ab54003e3627787785741b3d0fdb11
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54529054"
---
# <a name="preview-events"></a>Události náhledu
Události náhledu, označované také jako tunelové propojení událostí, jsou směrované události kde směru trasy, která přenáší z kořenového adresáře aplikace směrem k elementu, který vyvolal událost a hlásí jako zdroj dat události. Ne všechny události scénáře podporovalo nebo vyžadovalo události ve verzi preview. Toto téma popisuje situace, kdy události náhledu existují, způsob, jakým aplikace nebo součásti pracovat, a případy, kdy vytváření událostí ve verzi preview ve vlastních součástech nebo třídy může být vhodné.  
  
## <a name="preview-events-and-input"></a>Události náhledu a vstup  
 Při zpracování ve verzi Preview události obecně platí, buďte opatrní při označení události zpracovává události data. Zpracování událostí ve verzi Preview na libovolný element než element, který vyvolal ho (prvku, který je hlášen jako zdroj dat události) má vliv na neposkytují element zpracovat událost, která pochází. V některých případech jde o požadovaný výsledek, zejména v případě, že dotyčný elementy existovala v relace v rámci skládání ovládacího prvku.  
  
 Pro vstupní události konkrétně události ve verzi Preview také sdílet instance dat události s ekvivalentní šíření událostí. Pokud se používá k označení vstupní události zpracována obslužnou rutinu události třídy ve verzi Preview, nebude vyvolána třídy obslužnou rutinu šíření vstupní události. Nebo, pokud se používá k označení zpracovat událost obslužné rutiny události instance ve verzi Preview, nebudou obslužné rutiny pro šíření událostí obvykle vyvolány. Obslužné rutiny třídy nebo instance obslužné rutiny můžou být registrováno nebo připojené možnost vyvolat i, pokud události je označena jako zpracovaná, ale tato technika se obvykle nepoužívá.  
  
 Další informace o zpracování třídy a toho, jak souvisí události ve verzi Preview najdete v části [označení směrované události jako Handled a zpracování tříd](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md).  
  
### <a name="working-around-event-suppression-by-controls"></a>Obejít potlačení událostí ovládací prvky  
 Jeden scénář, kde se běžně používají události ve verzi Preview je pro složené ovládací prvek zpracování vstupních událostí. Autorem tohoto ovládacího prvku v některých případech potlačí určité události z pocházející z jejich ovládacího prvku, třeba, aby bylo možné nahradit události definované součásti, která přenáší informace by výslovně nebo implicitně konkrétnější chování. Pro instanci [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> potlačí <xref:System.Windows.UIElement.MouseLeftButtonDown> a <xref:System.Windows.UIElement.MouseLeftButtonDown> šíření událostí vyvolaných <xref:System.Windows.Controls.Button> nebo jeho složené prvky ve prospěch zachycení myši a vyvolávání <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událost, která je vždy vyvoláno <xref:System.Windows.Controls.Button> samotný. Události a data stále na trase, ale protože <xref:System.Windows.Controls.Button> označí jako data události <xref:System.Windows.RoutedEventArgs.Handled%2A>, pouze obslužné rutiny pro události, která výslovně uvedeno, by měla fungovat v `handledEventsToo` případ jsou vyvolány.  Pokud další prvky směrem k kořenového adresáře aplikace stále chtěla příležitost zpracování události Potlačené ovládacího prvku, jeden alternativou je připojení obslužných rutin v kódu s `handledEventsToo` zadané jako `true`. Ale často je jednodušší postup změnit směrování směr popisovače ekvivalent ve verzi Preview vstupní události. Například pokud ovládací prvek potlačí <xref:System.Windows.UIElement.MouseLeftButtonDown>, připojte obslužné rutiny pro <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> místo. Tento postup funguje jenom pro base element vstupní události jako <xref:System.Windows.UIElement.MouseLeftButtonDown>. Tyto události vstupu použít páry tunelového propojení/bublin, vyvolání obou událostí a sdílet data události.  
  
 Každý z následujících postupů má vedlejší účinky nebo omezení. Vedlejším účinkem zpracování událostí ve verzi Preview je, že zpracování událostí v tomto okamžiku může zakázat obslužných rutin, které očekávají, že zpracování šíření události, a proto omezení je, že není obvykle vhodné k označení události zpracovány, i když je stále na Previ nové části trasy. Omezení `handledEventsToo` technikou je, že nelze zadat `handledEventsToo` obslužné rutiny v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jako atribut, musíte zaregistrovat obslužnou rutinu události v kódu po získání odkaz na objekt na prvek, kde má být připojen obslužné rutiny.  
  
## <a name="see-also"></a>Viz také:
- [Označení směrovaných událostí jako zpracovaných a zpracování tříd](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)
- [Přehled směrovaných událostí](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
