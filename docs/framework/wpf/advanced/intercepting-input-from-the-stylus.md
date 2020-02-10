---
title: Přijetí vstupu z pera
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 'architecture [WPF], '
- ', '
- ', '
- ', '
ms.assetid: 791bb2f0-4e5c-4569-ac3c-211996808d44
ms.openlocfilehash: 7629843730a82584e94448ceac1ea574906876c9
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095135"
---
# <a name="intercepting-input-from-the-stylus"></a>Přijetí vstupu z pera
Architektura <xref:System.Windows.Input.StylusPlugIns> poskytuje mechanismus pro implementaci řízení nízké úrovně nad <xref:System.Windows.Input.Stylus> vstupu a vytváření objektů <xref:System.Windows.Ink.Stroke> digitálního inkoustu. Třída <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> poskytuje mechanizmus pro implementaci vlastního chování a jeho použití na datový proud dat přicházejících ze zařízení stylus pro zajištění optimálního výkonu.  
  
 Toto téma obsahuje následující pododdíly:  
  
- [Architektura](#Architecture)  
  
- [Implementace modulů plug-in stylusu](#ImplementingStylusPlugins)  
  
- [Přidání modulu plug-in do InkCanvas](#AddingYourPluginToAnInkCanvas)  
  
- [Závěr](#Conclusion)  
  
<a name="Architecture"></a>   
## <a name="architecture"></a>Architektura  
 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> je vývoj rozhraní API [StylusInput](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms574861(v=vs.90)) popsaných v tématu [přístup a manipulace se vstupem perem](https://docs.microsoft.com/previous-versions/ms818317(v%3dmsdn.10)).  
  
 Každý <xref:System.Windows.UIElement> má vlastnost <xref:System.Windows.UIElement.StylusPlugIns%2A>, která je <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>. Můžete přidat <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> do vlastnosti <xref:System.Windows.UIElement.StylusPlugIns%2A> elementu pro manipulaci s <xref:System.Windows.Input.StylusPoint>mi daty při jejich generování. data <xref:System.Windows.Input.StylusPoint> se skládají ze všech vlastností podporovaných digitalizačním systémem, včetně dat <xref:System.Windows.Input.StylusPoint.X%2A> a <xref:System.Windows.Input.StylusPoint.Y%2A> bodu, a také <xref:System.Windows.Input.StylusPoint.PressureFactor%2A> dat.  
  
 Objekty <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> jsou vloženy přímo do datového proudu dat přicházejících ze <xref:System.Windows.Input.Stylus> zařízení při přidání <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> do vlastnosti <xref:System.Windows.UIElement.StylusPlugIns%2A>. Pořadí, ve kterém jsou moduly plug-in přidány do kolekce <xref:System.Windows.UIElement.StylusPlugIns%2A>, určuje pořadí, ve kterém budou přijímána <xref:System.Windows.Input.StylusPoint> data. Například pokud přidáte modul plug-in filtru, který omezí vstup na určitou oblast, a pak přidáte modul plug-in, který rozpozná gesta při jejich psaní, modul plug-in, který rozpozná gesta, obdrží filtrovaná <xref:System.Windows.Input.StylusPoint> data.  
  
<a name="ImplementingStylusPlugins"></a>   
## <a name="implementing-stylus-plug-ins"></a>Implementace modulů plug-in stylusu  
 Chcete-li implementovat modul plug-in, odvodit třídu z <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>. Tato třída se používá pro datový proud dat, jak se nachází v <xref:System.Windows.Input.Stylus>. V této třídě můžete upravit hodnoty dat <xref:System.Windows.Input.StylusPoint>.  
  
> [!CAUTION]
> Pokud <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> vyvolá nebo způsobí výjimku, aplikace se zavře. Měli byste důkladně otestovat ovládací prvky, které používají <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> a použít pouze ovládací prvek, pokud jste si jisti, že <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> nevyvolá výjimku.  
  
 Následující příklad demonstruje modul plug-in, který omezuje vstup stylusu změnou <xref:System.Windows.Input.StylusPoint.X%2A> a <xref:System.Windows.Input.StylusPoint.Y%2A> hodnot v <xref:System.Windows.Input.StylusPoint>ch datech tak, jak se nachází v <xref:System.Windows.Input.Stylus>m zařízení.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#3](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#3)]
[!code-vb[AdvancedInkTopicsSamples#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#3)]  
  
<a name="AddingYourPluginToAnInkCanvas"></a>   
## <a name="adding-your-plug-in-to-an-inkcanvas"></a>Přidání modulu plug-in do InkCanvas  
 Nejjednodušší způsob, jak použít vlastní modul plug-in, je implementovat třídu, která je odvozena z InkCanvas a přidat ji do vlastnosti <xref:System.Windows.UIElement.StylusPlugIns%2A>.  
  
 Následující příklad ukazuje vlastní <xref:System.Windows.Controls.InkCanvas>, který filtruje rukopis.  
  
 [!code-csharp[AdvancedInkTopicsSamples#4](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#4)]  
  
 Pokud přidáte `FilterInkCanvas` do své aplikace a spustíte ji, budete si všimnout, že inkoust není omezen na oblast, dokud uživatel nedokončí tah. Důvodem je, že <xref:System.Windows.Controls.InkCanvas> má vlastnost <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A>, která je <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> a je již členem kolekce <xref:System.Windows.UIElement.StylusPlugIns%2A>. Vlastní <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>, kterou jste přidali do kolekce <xref:System.Windows.UIElement.StylusPlugIns%2A>, obdrží data <xref:System.Windows.Input.StylusPoint> po <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> obdrží data. V důsledku toho nebudou data <xref:System.Windows.Input.StylusPoint> filtrovaná, dokud uživatel nezíská pero, aby ukončil tah. Chcete-li filtrovat rukopis, jak ho uživatel vykreslí, je nutné vložit `FilterPlugin` před <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>.  
  
 Následující C# kód ukazuje vlastní <xref:System.Windows.Controls.InkCanvas>, který filtruje inkoust při vykreslování.  
  
 [!code-csharp[AdvancedInkTopicsSamples#5](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#5)]  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a>Závěr  
 Odvozením vlastních tříd <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> a jejich vložením do kolekcí <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> můžete výrazně vylepšit chování digitálního inkoustu. Máte přístup k datům <xref:System.Windows.Input.StylusPoint> při jejich vygenerování, což vám dává možnost přizpůsobit <xref:System.Windows.Input.Stylus> vstupu. Vzhledem k tomu, že máte přístup k datům <xref:System.Windows.Input.StylusPoint> na nízké úrovni, můžete implementovat shromažďování a vykreslování rukopisu s optimálním výkonem pro vaši aplikaci.  
  
## <a name="see-also"></a>Viz také

- [Pokročilé zpracování rukopisu](advanced-ink-handling.md)
- [Přístup k zadávání perem a manipulace s nimi](https://docs.microsoft.com/previous-versions/ms818317(v%3dmsdn.10))
