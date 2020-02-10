---
title: Vytvoření ovládacího prvku vstupu inkoustu
ms.date: 03/30/2017
helpviewer_keywords:
- ink strokes [WPF], managing
- managing ink strokes [WPF]
- ink input control [WPF]
- input from mouse [WPF], accepting
- mouse input [WPF], accepting
- ink [WPF], rendering
- ink strokes [WPF], collecting
- rendering ink [WPF]
- collecting ink strokes [WPF]
- DynamicRenderer objects [WPF]
- StylusPlugIn objects [WPF]
ms.assetid: c31f3a67-cb3f-4ded-af9e-ed21f6575b26
ms.openlocfilehash: 98b2abf813a232e36b80683254174b12b97659bb
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095213"
---
# <a name="creating-an-ink-input-control"></a>Vytvoření ovládacího prvku vstupu inkoustu
Můžete vytvořit vlastní ovládací prvek, který dynamicky a staticky vykresluje rukopis. To znamená, že vykreslení inkoustu jako uživatel nakreslí tah, což způsobí, že se rukopis zobrazuje jako "Flow" z tabletového pera, a po jeho přidání do ovládacího prvku se zobrazí rukopis, a to buď prostřednictvím tabletového pera, vloženého ze schránky, nebo načteného ze souboru. Pro dynamické vykreslování inkoustu musí mít ovládací prvek <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>. Aby bylo možné staticky vykreslovat rukopis, je nutné přepsat metody události stylus (<xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusMove%2A>a <xref:System.Windows.UIElement.OnStylusUp%2A>) a shromažďovat <xref:System.Windows.Input.StylusPoint> data, vytvářet tahy a přidávat je do <xref:System.Windows.Controls.InkPresenter> (který vykresluje rukopis na ovládacím prvku).  
  
 Toto téma obsahuje následující pododdíly:  
  
- [Postupy: shromažďování dat bodu pera a vytváření tahů perem](#CollectingStylusPointDataAndCreatingInkStrokes)  
  
- [Postupy: povolení zásahu vstupu z myši pomocí ovládacího prvku](#EnablingYourControlToAcceptInputTromTheMouse)  
  
- [Společné umístění](#PuttingItTogether)  
  
- [Používání dalších modulů plug-in a DynamicRenderers](#UsingAdditionalPluginsAndDynamicRenderers)  
  
- [Závěr](#AdvancedInkHandling_Conclusion)  
  
<a name="CollectingStylusPointDataAndCreatingInkStrokes"></a>   
## <a name="how-to-collect-stylus-point-data-and-create-ink-strokes"></a>Postupy: shromažďování dat bodu pera a vytváření tahů perem  
 Chcete-li vytvořit ovládací prvek, který bude shromažďovat a spravovat tahy perem, postupujte následovně:  
  
1. Odvodit třídu z <xref:System.Windows.Controls.Control> nebo jednu ze tříd odvozených z <xref:System.Windows.Controls.Control>, jako je <xref:System.Windows.Controls.Label>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#20](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
    [!code-csharp[AdvancedInkTopicsSamples#14](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#14)]  
    [!code-csharp[AdvancedInkTopicsSamples#15](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#15)]  
  
2. Přidejte <xref:System.Windows.Controls.InkPresenter> ke třídě a nastavte vlastnost <xref:System.Windows.Controls.ContentControl.Content%2A> na nový <xref:System.Windows.Controls.InkPresenter>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#16](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#16)]  
  
3. Připojte <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> k <xref:System.Windows.Controls.InkPresenter> voláním metody <xref:System.Windows.Controls.InkPresenter.AttachVisuals%2A> a přidejte <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> do kolekce <xref:System.Windows.UIElement.StylusPlugIns%2A>. Tato možnost umožňuje <xref:System.Windows.Controls.InkPresenter> Zobrazit rukopis, protože data bodu pera jsou shromažďována ovládacím prvkem.  
  
     [!code-csharp[AdvancedInkTopicsSamples#17](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#17)]  
    [!code-csharp[AdvancedInkTopicsSamples#18](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#18)]  
  
4. Přepsat metodu <xref:System.Windows.UIElement.OnStylusDown%2A>.  V této metodě zachytí Stylus s voláním <xref:System.Windows.Input.Stylus.Capture%2A>. Zachycením stylusu bude ovládací prvek nadále přijímat <xref:System.Windows.UIElement.StylusMove> a <xref:System.Windows.UIElement.StylusUp> události, i když Stylus opustí hranice ovládacího prvku. Tato možnost není naprosto povinná, ale téměř vždy je žádoucí pro dobrý zážitek uživatele. Vytvořte novou <xref:System.Windows.Input.StylusPointCollection> pro shromažďování <xref:System.Windows.Input.StylusPoint> dat. Nakonec přidejte do <xref:System.Windows.Input.StylusPointCollection>počáteční sadu dat <xref:System.Windows.Input.StylusPoint>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#7](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#7)]  
  
5. Přepište metodu <xref:System.Windows.UIElement.OnStylusMove%2A> a přidejte <xref:System.Windows.Input.StylusPoint> data do objektu <xref:System.Windows.Input.StylusPointCollection>, který jste vytvořili dříve.  
  
     [!code-csharp[AdvancedInkTopicsSamples#8](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#8)]  
  
6. Přepište metodu <xref:System.Windows.UIElement.OnStylusUp%2A> a vytvořte novou <xref:System.Windows.Ink.Stroke> s <xref:System.Windows.Input.StylusPointCollection> daty. Přidejte novou <xref:System.Windows.Ink.Stroke>, kterou jste vytvořili do kolekce <xref:System.Windows.Controls.InkPresenter.Strokes%2A> <xref:System.Windows.Controls.InkPresenter> a uvolněte záznam stylusu.  
  
     [!code-csharp[AdvancedInkTopicsSamples#10](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#10)]  
  
<a name="EnablingYourControlToAcceptInputTromTheMouse"></a>   
## <a name="how-to-enable-your-control-to-accept-input-from-the-mouse"></a>Postupy: povolení zásahu vstupu z myši pomocí ovládacího prvku  
 Pokud přidáte předchozí ovládací prvek do aplikace, spustíte ho a použijete myš jako vstupní zařízení, zjistíte, že tahy nejsou trvalé. Chcete-li zachovat tahy při použití myši jako vstupního zařízení, postupujte takto:  
  
1. Přepsat <xref:System.Windows.UIElement.OnMouseLeftButtonDown%2A> a vytvořit nové <xref:System.Windows.Input.StylusPointCollection> získat pozici myši v okamžiku, kdy k události došlo, a vytvořit <xref:System.Windows.Input.StylusPoint> pomocí dat bodu a přidat <xref:System.Windows.Input.StylusPoint> do <xref:System.Windows.Input.StylusPointCollection>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#11](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#11)]  
  
2. Přepsat metodu <xref:System.Windows.UIElement.OnMouseMove%2A>. Získat pozici myši při výskytu události a vytvořit <xref:System.Windows.Input.StylusPoint> pomocí dat bodu  Přidejte <xref:System.Windows.Input.StylusPoint> do objektu <xref:System.Windows.Input.StylusPointCollection>, který jste vytvořili dříve.  
  
     [!code-csharp[AdvancedInkTopicsSamples#12](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#12)]  
  
3. Přepsat metodu <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A>.  Vytvořte novou <xref:System.Windows.Ink.Stroke> s daty <xref:System.Windows.Input.StylusPointCollection> a přidejte novou <xref:System.Windows.Ink.Stroke>, kterou jste vytvořili do <xref:System.Windows.Controls.InkPresenter.Strokes%2A> kolekce <xref:System.Windows.Controls.InkPresenter>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#13](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#13)]  
  
<a name="PuttingItTogether"></a>   
## <a name="putting-it-together"></a>Společné umístění  
 Následující příklad je vlastní ovládací prvek, který shromažďuje rukopis, když uživatel používá myš nebo pero.  
  
 [!code-csharp[AdvancedInkTopicsSamples#20](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
[!code-csharp[AdvancedInkTopicsSamples#6](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#6)]  
  
<a name="UsingAdditionalPluginsAndDynamicRenderers"></a>   
## <a name="using-additional-plug-ins-and-dynamicrenderers"></a>Používání dalších modulů plug-in a DynamicRenderers  
 Podobně jako InkCanvas, váš vlastní ovládací prvek může mít vlastní <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> a další <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> objekty. Přidejte je do kolekce <xref:System.Windows.UIElement.StylusPlugIns%2A>. Pořadí objektů <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> v <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> ovlivňuje vzhled inkoustu při jeho vykreslení. Předpokládejme, že máte <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> s názvem `dynamicRenderer` a vlastní <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> s názvem `translatePlugin`, který posune inkoust z tabletového pera. Pokud je `translatePlugin` prvním <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> v <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>a `dynamicRenderer` je druhým, je inkoust, který "toky", posunutý, když uživatel přesune pero. Pokud je nejprve `dynamicRenderer` a `translatePlugin` je druhý, nebude rukopis posunut, dokud uživatel nezíská pero.  
  
<a name="AdvancedInkHandling_Conclusion"></a>   
## <a name="conclusion"></a>Závěr  
 Můžete vytvořit ovládací prvek, který bude shromažďovat a vykreslovat rukopis přepsáním metod události stylus. Vytvořením vlastního ovládacího prvku, odvozením vlastních tříd <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> a vložením do <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>můžete implementovat prakticky jakékoli chování, které lze předvádět pomocí digitálního inkoustu. Máte přístup k datům <xref:System.Windows.Input.StylusPoint> při jejich vygenerování, což vám dává možnost přizpůsobit <xref:System.Windows.Input.Stylus> vstupu a vykreslit ji na obrazovce, jak je to vhodné pro vaši aplikaci. Vzhledem k tomu, že máte přístup k datům <xref:System.Windows.Input.StylusPoint> na nízké úrovni, můžete implementovat kolekci rukopisu a vykreslit ji s optimálním výkonem pro vaši aplikaci.  
  
## <a name="see-also"></a>Viz také

- [Pokročilé zpracování rukopisu](advanced-ink-handling.md)
- [Přístup k zadávání perem a manipulace s nimi](https://docs.microsoft.com/previous-versions/ms818317(v=msdn.10))
