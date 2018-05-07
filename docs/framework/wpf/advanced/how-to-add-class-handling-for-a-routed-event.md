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
ms.openlocfilehash: 85c3491c9035d807b4c654659a8641121bb5709f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-class-handling-for-a-routed-event"></a>Postupy: Přidání zpracování třídy pro směrovanou událost
Směrované události mohou být zpracovány, obslužné rutiny třídy nebo instance obslužné rutiny v každém uzlu dané trasy. Obslužné rutiny třídy jsou vyvolány nejprve a lze implementace třídy potlačit události z instance zpracování nebo zavést další události konkrétní chování na události, které jsou vlastněny základní třídy. Tento příklad ukazuje dva úzce související techniky pro implementaci třídy obslužné rutiny.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá vlastní třídu na základě <xref:System.Windows.Controls.Canvas> panelu. Základním předpokladem aplikace je, že vlastní třídu zavádí chování na její podřízené elementy, včetně zachycení, které klikne na možnost žádné levým tlačítkem myši a označování, které je zpracovat, než bude volána třída podřízeného prvku nebo všechny instance obslužné rutiny na něm.  
  
 <xref:System.Windows.UIElement> Třída zpřístupní virtuální metodu, která umožňuje třída zpracování na <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> událostí, jednoduše přepsáním události. Toto je nejjednodušší způsob, jak implementovat třídu zpracování, pokud virtuální metoda je k dispozici někde v hierarchii vlastní třídy. Následující kód ukazuje <xref:System.Windows.UIElement.OnPreviewMouseLeftButtonDown%2A> implementace v "MyEditContainer" odvozený z <xref:System.Windows.Controls.Canvas>. Implementace označí událost jako zpracována v argumenty, pak přidá určitý kód umožnit source element základní viditelné změny.  
  
 [!code-csharp[ClassHandling#OnStarClassHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClassHandling/CSharp/SDKSampleLibrary/class1.cs#onstarclasshandler)]
 [!code-vb[ClassHandling#OnStarClassHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClassHandling/visualbasic/sdksamplelibrary/class1.vb#onstarclasshandler)]  
  
 Žádné virtuální je k dispozici na základní třídy, nebo pro tuto konkrétní metodu, třídu zpracování mohou být přidány přímo pomocí metoda nástroj <xref:System.Windows.EventManager> třídy <xref:System.Windows.EventManager.RegisterClassHandler%2A>. Tato metoda by měla být volána pouze v rámci statických inicializaci třídy, které přidáváte třída zpracování. Tento příklad přidá jinou obslužnou rutinu pro <xref:System.Windows.UIElement.PreviewMouseLeftButtonDown> , a v takovém případě registrované třídy je třída, která vlastní. Naproti tomu při použití virtuals, registrované třídy je ve skutečnosti <xref:System.Windows.UIElement> základní třídy. V případech, kde základní třídy a podtřídy registrovat třídu zpracování jsou vyvolány nejprve podtřídami obslužné rutiny. Chování v aplikaci bude, že nejprve by tato obslužná rutina zobrazit její okno se zprávou a potom by visual změnu v hodnotě obslužná rutina virtuální metoda zobrazí.  
  
 [!code-csharp[ClassHandling#StaticAndRegisterClassHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClassHandling/CSharp/SDKSampleLibrary/class1.cs#staticandregisterclasshandler)]
 [!code-vb[ClassHandling#StaticAndRegisterClassHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClassHandling/visualbasic/sdksamplelibrary/class1.vb#staticandregisterclasshandler)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.EventManager>  
 [Označení směrovaných událostí jako zpracovaných a zpracování tříd](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)  
 [Zpracování směrované události](../../../../docs/framework/wpf/advanced/how-to-handle-a-routed-event.md)  
 [Přehled směrovaných událostí](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
