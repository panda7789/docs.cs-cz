---
title: 'Postupy: Přidání zpracování třídy pro směrovanou událost'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- routed events [WPF], class handlers
- task_core_add_class_handling_routed_properties [WPF]
- class handlers [WPF], routed events
ms.assetid: 15b7b06c-9112-4ee5-b30a-65d10c5c5df6
ms.openlocfilehash: 7b897954cbdab461dc0305c6290e67c1af5282c3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59224265"
---
# <a name="how-to-add-class-handling-for-a-routed-event"></a>Postupy: Přidání zpracování třídy pro směrovanou událost
Směrované události mohou být zpracovávány obslužné rutiny třídy nebo instance obslužné rutiny na libovolném daného uzlu v této trase. Obslužné rutiny třídy jsou vyvolány nejprve a je možné pomocí implementace třídy potlačení událostí z instance zpracování nebo zavést další události konkrétní chování na události, které jsou vlastněny základní třídy. Tento příklad ukazuje dva úzce související postupy pro implementaci obslužné rutiny třídy.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá vlastní třídu založenou na <xref:System.Windows.Controls.Canvas> panel. Základní premisu aplikace je, že vlastní třídu zavádí chování na jeho podřízené prvky, včetně zachycení, která klikne jakékoli levým tlačítkem myši a označování, které je zpracována, předtím, než bude vyvolána Třída podřízeného prvku nebo všechny instance obslužné rutiny na něm.  
  
 <xref:System.Windows.UIElement> Třída zveřejňuje virtuální metody, která umožňuje zpracování na třídy <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> událost, jednoduše přepsáním události. Toto je nejjednodušší způsob, jak implementovat třídu zpracování, pokud je k dispozici někde v hierarchii vaší třídy virtuální metody. Následující kód ukazuje <xref:System.Windows.UIElement.OnPreviewMouseLeftButtonDown%2A> implementace "MyEditContainer", který je odvozen z <xref:System.Windows.Controls.Canvas>. Implementace označí události jako zpracované v argumentech a pak přidá určitý kód poskytnout source element základní viditelné změny.  
  
 [!code-csharp[ClassHandling#OnStarClassHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/ClassHandling/CSharp/SDKSampleLibrary/class1.cs#onstarclasshandler)]
 [!code-vb[ClassHandling#OnStarClassHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ClassHandling/visualbasic/sdksamplelibrary/class1.vb#onstarclasshandler)]  
  
 Pokud ne virtuální je k dispozici na základní třídy nebo pro konkrétní metody, třídy zpracování lze přidat přímo pomocí metody nástroj <xref:System.Windows.EventManager> třídy, <xref:System.Windows.EventManager.RegisterClassHandler%2A>. Tuto metodu lze volat pouze v rámci Statická inicializace třídy, které jsou přidání zpracování třídy. V tomto příkladu přidá jinou obslužnou rutinu pro <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> , a v tomto případě registrované třídy je vlastní třídy. Naopak při použití virtuální, registrované třídy je ve skutečnosti <xref:System.Windows.UIElement> základní třídy. V případech, kdy základních tříd a podtříd zaregistrovat zpracování třídy jsou vyvolány nejprve podtřídy obslužné rutiny. Chování v aplikaci bude, že nejprve tuto obslužnou rutinu by zobrazil jeho okno se zprávou a pak by se zobrazovat vizuální změny v obslužné rutině virtuální metody.  
  
 [!code-csharp[ClassHandling#StaticAndRegisterClassHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/ClassHandling/CSharp/SDKSampleLibrary/class1.cs#staticandregisterclasshandler)]
 [!code-vb[ClassHandling#StaticAndRegisterClassHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ClassHandling/visualbasic/sdksamplelibrary/class1.vb#staticandregisterclasshandler)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.EventManager>
- [Označení směrovaných událostí jako zpracovaných a zpracování tříd](marking-routed-events-as-handled-and-class-handling.md)
- [Zpracování směrované události](how-to-handle-a-routed-event.md)
- [Přehled směrovaných událostí](routed-events-overview.md)
