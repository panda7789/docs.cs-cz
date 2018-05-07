---
title: Události náhledu
ms.date: 03/30/2017
helpviewer_keywords:
- Preview events [WPF]
- suppressing events [WPF]
- events [WPF], Preview
- events [WPF], suppressing
ms.assetid: b5032308-aa9c-4d02-af11-630ecec8df7e
ms.openlocfilehash: 2d6c1ab32cb43730af2f935f4bd4405059994c12
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="preview-events"></a>Události náhledu
Události náhledu, také známé jako tunelování události, jsou směrované události, kde směr trasy, která přenáší z kořenového adresáře aplikace směrem k elementu, který vyvolá událost a hlásí jako zdroj v datech události. Ne všechny události scénáře podporovat nebo vyžadují události náhledu; Toto téma popisuje situace, kdy události náhledu existují, jak aplikace nebo součásti pracovat, a případy, kdy vytvoření události náhledu ve vlastních součástech nebo třídy může být vhodné.  
  
## <a name="preview-events-and-input"></a>Události náhledu a vstup  
 Při zpracování události obecně platí, buďte opatrní Preview označení události zpracovává události data. Zpracování událostí Preview u libovolného elementu jiné než elementu, který vyvolá ho (element, který je hlášen jako zdroj v datech události) má za následek element není poskytuje možnost zpracovat událost, která je vytvořena. V některých případech jde o požadovaný výsledek, zvlášť pokud je nejistá elementy v vztahy v rámci skládání ovládacího prvku.  
  
 Pro vstupní události konkrétně události náhledu taky sdílet instance dat událostí s ekvivalentní probublávání události. Pokud používáte obslužná rutina události – třída Preview označit vstupní událost zpracovat, nebude vyvolat probublávání třídu obslužné rutiny vstupní události. Nebo, pokud používáte obslužnou rutinu události instance Preview označit zpracovává událost, nebudou obslužné rutiny pro probublávání události obvykle vyvolat. Obslužné rutiny třídy nebo instance obslužné rutiny můžete zaregistrovat nebo připojené k možnost vyvolat i v případě, že událost je označena zpracovávaný, ale tato technika se obvykle nepoužívá.  
  
 Další informace o zpracování třídy a jak se týká události náhledu najdete v části [označení směrované události jako Handled a třída zpracování](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md).  
  
### <a name="working-around-event-suppression-by-controls"></a>Alternativní řešení potlačení událostí z ovládacích prvků  
 Jeden scénář, kde události náhledu běžně se používají se pro kompletní složený řízení zpracování vstupních událostech. V některých případech autora ovládacího prvku potlačí daných událostí z pocházející z jejich ovládacího prvku, třeba, aby bylo možné nahradit definována součást událostí, který představuje další informace nebo znamená více konkrétní chování. Například [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.Button> potlačí <xref:System.Windows.UIElement.MouseLeftButtonDown> a <xref:System.Windows.UIElement.MouseLeftButtonDown> probublávání události vyvolané službou <xref:System.Windows.Controls.Button> nebo jeho složených prvků považuje zachycení myši a vyvolávání <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událost, která je vždy aktivováno <xref:System.Windows.Controls.Button> sám sebe. Události a jeho data i nadále pokračovat na trase, ale protože <xref:System.Windows.Controls.Button> označí jako data události <xref:System.Windows.RoutedEventArgs.Handled%2A>, pouze obslužné rutiny pro událost, která se specificky uvedené by měla fungovat v `handledEventsToo` jsou vyvolány případu.  Pokud další prvky směrem kořenového adresáře aplikace stále chtěli příležitost zpracování události Potlačené ovládací prvek, jeden alternativou je připojení obslužné rutiny v kódu s `handledEventsToo` zadaný jako `true`. Ale často je jednodušší postup změnit směr směrování zpracovat vstupní události odpovídá verzi Preview. Například pokud ovládacího prvku potlačí <xref:System.Windows.UIElement.MouseLeftButtonDown>, zkuste připojení obslužnou rutinu pro <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> místo. Tento postup funguje jenom pro base element vstupní události, jako <xref:System.Windows.UIElement.MouseLeftButtonDown>. Tyto události vstupní používají dvojice tunelové propojení nebo bublin, vyvolávání obou událostí a sdílet data události.  
  
 Každý z těchto postupů má vedlejší účinky nebo omezení. Vedlejším účinkem zpracování události Preview je, že zpracování události v daném okamžiku může zakázat obslužných rutin, které očekávají, že zpracování probublávání události, a proto omezení na je, že je obvykle není vhodné k označení událostí zpracovává sice ještě na Previ část ové trasy. Omezení `handledEventsToo` technika je, že nemůžete zadat `handledEventsToo` obslužné rutiny v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jako atribut, je nutné zaregistrovat obslužné rutiny události v kódu po získání odkaz na objekt k elementu, kde má být připojen obslužná rutina.  
  
## <a name="see-also"></a>Viz také  
 [Označení směrovaných událostí jako zpracovaných a zpracování tříd](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)  
 [Přehled směrovaných událostí](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
