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
ms.openlocfilehash: 76976f1599ecbbaf7405d7941f66aa2c5f955565
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64598958"
---
# <a name="intercepting-input-from-the-stylus"></a>Přijetí vstupu z pera
<xref:System.Windows.Input.StylusPlugIns> Architektura poskytuje mechanismus pro implementaci nízké úrovně řízení nad <xref:System.Windows.Input.Stylus> vstup a vytváření digitálních inkoust <xref:System.Windows.Ink.Stroke> objekty. <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> Třída poskytuje mechanismus pro implementaci vlastního chování a použít na datový proud množství dat přicházejících z stylus zařízení k zajištění optimálního výkonu.  
  
 Toto téma obsahuje následující témata:  
  
- [Architektura](#Architecture)  
  
- [Implementace Stylus moduly plug-in](#ImplementingStylusPlugins)  
  
- [Přidat modul Plug-in k objektu InkCanvas](#AddingYourPluginToAnInkCanvas)  
  
- [Závěr](#Conclusion)  
  
<a name="Architecture"></a>   
## <a name="architecture"></a>Architektura  
 <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> Navazuje [StylusInput](https://go.microsoft.com/fwlink/?LinkId=50753&clcid=0x409) rozhraní API, je popsáno v [přístup k a manipulaci s perem](https://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)v [Microsoft Windows XP Tablet PC Edition softwaru Vývojová sada 1.7](https://go.microsoft.com/fwlink/?linkid=11782&clcid=0x409).  
  
 Každý <xref:System.Windows.UIElement> má <xref:System.Windows.UIElement.StylusPlugIns%2A> vlastnost, která je <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>. Můžete přidat <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> na prvek <xref:System.Windows.UIElement.StylusPlugIns%2A> vlastnost k manipulaci s <xref:System.Windows.Input.StylusPoint> dat, protože je generován. <xref:System.Windows.Input.StylusPoint> data se skládá ze všech vlastností podporovaných digitizér systému, včetně <xref:System.Windows.Input.StylusPoint.X%2A> a <xref:System.Windows.Input.StylusPoint.Y%2A> bod dat, stejně jako <xref:System.Windows.Input.StylusPoint.PressureFactor%2A> data.  
  
 Vaše <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> objekty jsou vloženy přímo do datového proudu množství dat přicházejících z <xref:System.Windows.Input.Stylus> zařízení přidáte <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> k <xref:System.Windows.UIElement.StylusPlugIns%2A> vlastnost. Pořadí, ve které moduly plug-in jsou přidány do <xref:System.Windows.UIElement.StylusPlugIns%2A> kolekce určuje pořadí, ve kterém se mu <xref:System.Windows.Input.StylusPoint> data. Například pokud přidáte filtr modulu plug-in, který omezí vstup na konkrétní oblasti a poté přidejte modul plug-in, který rozpoznává gesta, jak jsou psány, modul plug-in, který rozpoznává gesta obdrží filtrované <xref:System.Windows.Input.StylusPoint> data.  
  
<a name="ImplementingStylusPlugins"></a>   
## <a name="implementing-stylus-plug-ins"></a>Implementace Stylus moduly plug-in  
 K implementaci modulu plug-in, odvoďte třídu z <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn>. Tato třída je použité o datový proud s daty příchozí z <xref:System.Windows.Input.Stylus>. V této třídě můžete upravit hodnoty <xref:System.Windows.Input.StylusPoint> data.  
  
> [!CAUTION]
>  Pokud <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> vyvolá nebo způsobí výjimku, tato aplikace se zavřít. Měli byste důkladně otestovat ovládací prvky, které využívají <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> a pouze použití ovládacího prvku, pokud jste si jisti <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> nebude vyvolat výjimku.  
  
 Následující příklad ukazuje modul plug-in, který omezuje vstupu jehly úpravou <xref:System.Windows.Input.StylusPoint.X%2A> a <xref:System.Windows.Input.StylusPoint.Y%2A> hodnoty v <xref:System.Windows.Input.StylusPoint> dat při pocházejí z <xref:System.Windows.Input.Stylus> zařízení.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#3](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#3)]
[!code-vb[AdvancedInkTopicsSamples#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#3)]  
  
<a name="AddingYourPluginToAnInkCanvas"></a>   
## <a name="adding-your-plug-in-to-an-inkcanvas"></a>Přidat modul Plug-in k objektu InkCanvas  
 Nejjednodušší způsob, jak používat vaše vlastní modul plug-in je implementovat třídu, která je odvozena z inkcanvas – a přidejte ji tak <xref:System.Windows.UIElement.StylusPlugIns%2A> vlastnost.  
  
 Následující příklad ukazuje vlastní <xref:System.Windows.Controls.InkCanvas> , která filtruje rukopisu.  
  
 [!code-csharp[AdvancedInkTopicsSamples#4](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#4)]  
  
 Pokud chcete přidat `FilterInkCanvas` do vaší aplikace a spusťte ho, všimnete si, že není rukopis s omezeným přístupem v oblasti až poté, co uživatel vykoná tah. Důvodem je, že <xref:System.Windows.Controls.InkCanvas> má <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> vlastnost, která je <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> a je již členem skupiny <xref:System.Windows.UIElement.StylusPlugIns%2A> kolekce. Vlastní <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> jste přidali do <xref:System.Windows.UIElement.StylusPlugIns%2A> kolekce přijímá <xref:System.Windows.Input.StylusPoint> data po <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> přijímá data. V důsledku toho <xref:System.Windows.Input.StylusPoint> data se nebudou filtrovat až poté, co uživatel zruší pero na konec tah. K filtrování rukopis jako uživatel nakreslí ho, vložte `FilterPlugin` před <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>.  
  
 Následující kód jazyka C# ukazuje vlastní <xref:System.Windows.Controls.InkCanvas> rukopisu, která filtruje podle jeho vykreslení.  
  
 [!code-csharp[AdvancedInkTopicsSamples#5](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#5)]  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a>Závěr  
 Odvozením vlastních <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> třídy a vkládání do <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> kolekcí, můžete výrazně vylepšit chování digitálních inkoust. Máte přístup k <xref:System.Windows.Input.StylusPoint> dat, jako je generováno, získáte tak možnost přizpůsobit <xref:System.Windows.Input.Stylus> vstupu. Protože máte takový přístup nízké úrovně ke <xref:System.Windows.Input.StylusPoint> data, kolekce inkoustů a vykreslování poskytovaly optimální výkon můžete implementovat pro vaši aplikaci.  
  
## <a name="see-also"></a>Viz také:

- [Pokročilé zpracování rukopisu](advanced-ink-handling.md)
- [Přístup k a manipulaci s vstup pomocí pera](https://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)
