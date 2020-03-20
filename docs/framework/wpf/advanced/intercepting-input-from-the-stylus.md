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
ms.openlocfilehash: 17cf42a9d6d94d6ea12399561af5647df3b4d8c2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181922"
---
# <a name="intercepting-input-from-the-stylus"></a>Přijetí vstupu z pera
Architektura <xref:System.Windows.Input.StylusPlugIns> poskytuje mechanismus pro implementaci nízkoúrovňové kontroly nad <xref:System.Windows.Input.Stylus> <xref:System.Windows.Ink.Stroke> vstupem a vytváření objektů digitálních inkoustů. Třída <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> poskytuje mechanismus pro implementaci vlastní chování a použít jej pro datový proud dat pocházejících ze zařízení stylus pro optimální výkon.  
  
 Toto téma obsahuje následující pododdíly:  
  
- [Architektura](#Architecture)  
  
- [Implementace modulů plug-in stylusu](#ImplementingStylusPlugins)  
  
- [Přidání modulu plug-in na plátno inkcanvas](#AddingYourPluginToAnInkCanvas)  
  
- [Závěr](#Conclusion)  
  
<a name="Architecture"></a>
## <a name="architecture"></a>Architektura  
 Je <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> vývoj [StylusInput](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms574861(v=vs.90)) API, popsané v [přístupu a manipulaci pero vstup](https://docs.microsoft.com/previous-versions/ms818317(v%3dmsdn.10)).  
  
 Každý <xref:System.Windows.UIElement> má <xref:System.Windows.UIElement.StylusPlugIns%2A> vlastnost, <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>která je . Můžete přidat <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> do <xref:System.Windows.UIElement.StylusPlugIns%2A> vlastnosti prvku pro <xref:System.Windows.Input.StylusPoint> manipulaci s daty při jejich generování. <xref:System.Windows.Input.StylusPoint>data se skládají ze všech vlastností podporovaných <xref:System.Windows.Input.StylusPoint.X%2A> <xref:System.Windows.Input.StylusPoint.Y%2A> systémovým digitizérem, včetně dat a bodů, stejně jako <xref:System.Windows.Input.StylusPoint.PressureFactor%2A> dat.  
  
 Vaše <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> objekty jsou vloženy přímo do <xref:System.Windows.Input.Stylus> datového proudu <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> dat <xref:System.Windows.UIElement.StylusPlugIns%2A> přicházejících ze zařízení při přidání do vlastnosti. Pořadí, ve kterém jsou přidány moduly plug-in do <xref:System.Windows.UIElement.StylusPlugIns%2A> kolekce <xref:System.Windows.Input.StylusPoint> určuje pořadí, ve kterém budou přijímat data. Pokud například přidáte modul plug-in filtru, který omezí vstup do určité oblasti, a potom přidáte modul plug-in, který rozpozná gesta při <xref:System.Windows.Input.StylusPoint> jejich zápisu, modul plug-in, který rozpozná gesta, obdrží filtrovaná data.  
  
<a name="ImplementingStylusPlugins"></a>
## <a name="implementing-stylus-plug-ins"></a>Implementace modulů plug-in stylusu  
 Chcete-li implementovat modul plug-in, odvodit třídu z <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>. Tato třída se použije o datový proud dat, jak přichází z <xref:System.Windows.Input.Stylus>. V této třídě můžete upravit <xref:System.Windows.Input.StylusPoint> hodnoty dat.  
  
> [!CAUTION]
> Pokud <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> vyvolá nebo způsobí výjimku, aplikace se zavře. Měli byste důkladně otestovat <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> ovládací prvky, které spotřebovávají a používat pouze ovládací prvek, pokud jste si jisti, <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> nebude vyvolat výjimku.  
  
 Následující příklad ukazuje modul plug-in, který omezuje vstup pera <xref:System.Windows.Input.StylusPoint.Y%2A> úpravou <xref:System.Windows.Input.StylusPoint> hodnot <xref:System.Windows.Input.StylusPoint.X%2A> a v <xref:System.Windows.Input.Stylus> datech při jeho vstupu ze zařízení.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#3](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#3)]
[!code-vb[AdvancedInkTopicsSamples#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#3)]  
  
<a name="AddingYourPluginToAnInkCanvas"></a>
## <a name="adding-your-plug-in-to-an-inkcanvas"></a>Přidání modulu plug-in na plátno inkcanvas  
 Nejjednodušší způsob, jak použít vlastní modul plug-in je implementovat třídu, která <xref:System.Windows.UIElement.StylusPlugIns%2A> je odvozena od InkCanvas a přidat ji do vlastnosti.  
  
 Následující příklad ukazuje vlastní, <xref:System.Windows.Controls.InkCanvas> který filtruje inkoust.  
  
 [!code-csharp[AdvancedInkTopicsSamples#4](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#4)]  
  
 Pokud přidáte `FilterInkCanvas` do aplikace a spustíte ji, zjistíte, že inkoust není omezen na oblast, dokud uživatel nedokončí tah. Důvodem <xref:System.Windows.Controls.InkCanvas> je, <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> že má vlastnost, která je <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> a <xref:System.Windows.UIElement.StylusPlugIns%2A> je již členem kolekce. Vlastní, <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> které jste <xref:System.Windows.UIElement.StylusPlugIns%2A> přidali <xref:System.Windows.Input.StylusPoint> do <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> kolekce obdrží data po přijetí dat. V důsledku toho <xref:System.Windows.Input.StylusPoint> nebudou data filtrována, dokud uživatel nezvedne pero a ukončí tah. Chcete-li filtrovat inkoust při nakreslování, je nutné vložit `FilterPlugin` před . <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>  
  
 Následující kód jazyka C# <xref:System.Windows.Controls.InkCanvas> ukazuje vlastní, který filtruje inkoust, jak je nakreslena.  
  
 [!code-csharp[AdvancedInkTopicsSamples#5](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#5)]  
  
<a name="Conclusion"></a>
## <a name="conclusion"></a>Závěr  
 Odvozením vlastních <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> tříd a jejich <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> vložením do kolekcí můžete výrazně zlepšit chování digitálního inkoustu. Máte přístup k <xref:System.Windows.Input.StylusPoint> datům při jejich generování, což vám <xref:System.Windows.Input.Stylus> dává možnost přizpůsobit vstup. Vzhledem k tomu, že <xref:System.Windows.Input.StylusPoint> máte takový nízkoúrovňový přístup k datům, můžete implementovat shromažďování a vykreslování inkoustu s optimálním výkonem pro vaši aplikaci.  
  
## <a name="see-also"></a>Viz také

- [Upřesnění zpracování inkoustu](advanced-ink-handling.md)
- [Přístup ke vstupu pera a manipulace s ním](https://docs.microsoft.com/previous-versions/ms818317(v%3dmsdn.10))
