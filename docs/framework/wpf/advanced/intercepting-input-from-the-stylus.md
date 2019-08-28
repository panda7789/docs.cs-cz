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
ms.openlocfilehash: 2547c0aa2f3a14080868c2760fa8999eb99d3d16
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046331"
---
# <a name="intercepting-input-from-the-stylus"></a>Přijetí vstupu z pera
Architektura poskytuje mechanismus pro implementaci <xref:System.Windows.Input.Stylus> řízení nízké úrovně pro vstup a vytváření objektů digitálního inkoustu <xref:System.Windows.Ink.Stroke>. <xref:System.Windows.Input.StylusPlugIns> <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> Třída poskytuje mechanismus pro implementaci vlastního chování a jeho použití na datový proud dat přicházejících ze zařízení stylus na optimální výkon.  
  
 Toto téma obsahuje následující pododdíly:  
  
- [Architektura](#Architecture)  
  
- [Implementace modulů plug-in stylusu](#ImplementingStylusPlugins)  
  
- [Přidání modulu plug-in do InkCanvas](#AddingYourPluginToAnInkCanvas)  
  
- [Závěr](#Conclusion)  
  
<a name="Architecture"></a>   
## <a name="architecture"></a>Architektura  
 Je vývoj rozhraní API [StylusInput](https://go.microsoft.com/fwlink/?LinkId=50753&clcid=0x409) popsaných v tématu [přístup a manipulace se vstupem perem](https://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)v sadě [Microsoft Windows XP Tablet PC Edition Software Development Kit 1,7](https://go.microsoft.com/fwlink/?linkid=11782&clcid=0x409). <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>  
  
 Každé <xref:System.Windows.UIElement> <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>má vlastnost,kteráje.<xref:System.Windows.UIElement.StylusPlugIns%2A> Můžete přidat <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> do <xref:System.Windows.UIElement.StylusPlugIns%2A> vlastnosti prvku a manipulovat <xref:System.Windows.Input.StylusPoint> s daty při jejich generování. <xref:System.Windows.Input.StylusPoint>data se skládají ze všech vlastností podporovaných digitizérem systému, včetně <xref:System.Windows.Input.StylusPoint.X%2A> <xref:System.Windows.Input.StylusPoint.PressureFactor%2A> dat a bodů a <xref:System.Windows.Input.StylusPoint.Y%2A> dat.  
  
 Vaše <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> objekty jsou vloženy přímo do datového proudu dat přicházejících <xref:System.Windows.Input.Stylus> ze <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> zařízení při přidávání do <xref:System.Windows.UIElement.StylusPlugIns%2A> vlastnosti. Pořadí, ve kterém jsou moduly plug-in přidány do <xref:System.Windows.UIElement.StylusPlugIns%2A> kolekce, určuje pořadí, ve kterém budou přijímat <xref:System.Windows.Input.StylusPoint> data. Pokud například přidáte modul plug-in filtru, který omezí vstup na určitou oblast, a poté přidáte modul plug-in, který rozpozná gesta při jejich psaní, bude modul plug-in, který rozpozná gesta, přijímat filtrovaná <xref:System.Windows.Input.StylusPoint> data.  
  
<a name="ImplementingStylusPlugins"></a>   
## <a name="implementing-stylus-plug-ins"></a>Implementace modulů plug-in stylusu  
 Chcete-li implementovat modul plug-in, odvodit <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>třídu z. Tato třída se používá pro datový proud dat, jak je k dispozici v <xref:System.Windows.Input.Stylus>. V této třídě můžete upravovat hodnoty <xref:System.Windows.Input.StylusPoint> dat.  
  
> [!CAUTION]
> <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> Pokud vyvolá nebo způsobí výjimku, aplikace se zavře. Měli byste důkladně otestovat ovládací prvky, které <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> spotřebovávají a používají ovládací prvek pouze v případě, že <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> jste si jisti, že nevyvolávají výjimku.  
  
 Následující příklad znázorňuje modul plug-in, který <xref:System.Windows.Input.StylusPoint.X%2A> omezuje vstup stylusu úpravou hodnot a <xref:System.Windows.Input.StylusPoint.Y%2A> v <xref:System.Windows.Input.StylusPoint> datech, která jsou součástí ze <xref:System.Windows.Input.Stylus> zařízení.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#3](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#3)]
[!code-vb[AdvancedInkTopicsSamples#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#3)]  
  
<a name="AddingYourPluginToAnInkCanvas"></a>   
## <a name="adding-your-plug-in-to-an-inkcanvas"></a>Přidání modulu plug-in do InkCanvas  
 Nejjednodušší způsob, jak použít vlastní modul plug-in, je implementovat třídu, která je odvozena z InkCanvas a přidat ji do <xref:System.Windows.UIElement.StylusPlugIns%2A> vlastnosti.  
  
 Následující příklad ukazuje vlastní <xref:System.Windows.Controls.InkCanvas> , který filtruje rukopis.  
  
 [!code-csharp[AdvancedInkTopicsSamples#4](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#4)]  
  
 Pokud přidáte `FilterInkCanvas` do své aplikace a spustíte ji, budete si všimnout, že inkoust není omezen na oblast, dokud uživatel nedokončí tah. Důvodem je <xref:System.Windows.Controls.InkCanvas> , že <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> má <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> vlastnost, která je a je již členem <xref:System.Windows.UIElement.StylusPlugIns%2A> kolekce. Vlastní <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> přidané <xref:System.Windows.Input.StylusPoint> do kolekce obdrží data po <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> přijetí dat. <xref:System.Windows.UIElement.StylusPlugIns%2A> V <xref:System.Windows.Input.StylusPoint> důsledku toho nebudou data filtrována, dokud uživatel nezíská pero, aby ukončil tah. Chcete-li filtrovat rukopis, jak ho uživatel vykreslí, je nutné `FilterPlugin` vložit <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>před.  
  
 Následující C# kód ukazuje vlastní <xref:System.Windows.Controls.InkCanvas> , který filtruje rukopis při vykreslování.  
  
 [!code-csharp[AdvancedInkTopicsSamples#5](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#5)]  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a>Závěr  
 Odvozením vlastních <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> tříd a jejich vložením do <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> kolekcí můžete výrazně vylepšit chování digitálního inkoustu. Máte přístup k <xref:System.Windows.Input.StylusPoint> datům, když je vygenerována, a poskytuje vám možnost <xref:System.Windows.Input.Stylus> přizpůsobení vstupu. Vzhledem k tomu, že máte přístup k <xref:System.Windows.Input.StylusPoint> datům na nízké úrovni, můžete implementovat shromažďování a vykreslování rukopisu s optimálním výkonem pro vaši aplikaci.  
  
## <a name="see-also"></a>Viz také:

- [Pokročilé zpracování rukopisu](advanced-ink-handling.md)
- [Přístup k zadávání perem a manipulace s nimi](https://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)
