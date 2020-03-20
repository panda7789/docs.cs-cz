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
ms.openlocfilehash: 394318488b0afb8e043389e0abc3f51dce8604c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186286"
---
# <a name="creating-an-ink-input-control"></a>Vytvoření ovládacího prvku vstupu inkoustu
Můžete vytvořit vlastní ovládací prvek, který dynamicky a staticky vykresluje inkoust. To znamená, že vykreslení rukopisu jako uživatel nakreslí tah, což způsobí, že rukopis se zobrazí "tok" z pera tabletu a zobrazí rukopis po přidání do ovládacího prvku, a to buď prostřednictvím pera tabletu, vložit ze schránky nebo načten ze souboru. Chcete-li dynamicky vykreslovat inkoust, musí ovládací prvek používat <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>. Chcete-li staticky vykreslit inkoust, musíte přepsat<xref:System.Windows.UIElement.OnStylusDown%2A> <xref:System.Windows.UIElement.OnStylusMove%2A>metody <xref:System.Windows.UIElement.OnStylusUp%2A>událostí stylusu ( , , a ) shromažďovat <xref:System.Windows.Input.StylusPoint> data, vytvářet tahy a přidávat je do (která <xref:System.Windows.Controls.InkPresenter> vykresluje inkoust v ovládacím prvku).  
  
 Toto téma obsahuje následující pododdíly:  
  
- [Postup: Shromažďování dat bodu stylusu a vytváření tahů perem](#CollectingStylusPointDataAndCreatingInkStrokes)  
  
- [Postup: Povolte ovládacímu prvku přijímat vstup z myši](#EnablingYourControlToAcceptInputTromTheMouse)  
  
- [Dát to dohromady](#PuttingItTogether)  
  
- [Použití dalších modulů plug-in a dynamických rendererů](#UsingAdditionalPluginsAndDynamicRenderers)  
  
- [Závěr](#AdvancedInkHandling_Conclusion)  
  
<a name="CollectingStylusPointDataAndCreatingInkStrokes"></a>
## <a name="how-to-collect-stylus-point-data-and-create-ink-strokes"></a>Postup: Shromažďování dat bodu stylusu a vytváření tahů perem  
 Chcete-li vytvořit ovládací prvek, který shromažďuje a spravuje tahy perem, postupujte takto:  
  
1. Odvodit <xref:System.Windows.Controls.Control> třídu z nebo <xref:System.Windows.Controls.Control>jednu <xref:System.Windows.Controls.Label>z tříd odvozených z , například .  
  
     [!code-csharp[AdvancedInkTopicsSamples#20](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
    [!code-csharp[AdvancedInkTopicsSamples#14](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#14)]  
    [!code-csharp[AdvancedInkTopicsSamples#15](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#15)]  
  
2. Přidejte <xref:System.Windows.Controls.InkPresenter> do třídy <xref:System.Windows.Controls.ContentControl.Content%2A> a nastavte <xref:System.Windows.Controls.InkPresenter>vlastnost na nový .  
  
     [!code-csharp[AdvancedInkTopicsSamples#16](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#16)]  
  
3. <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> <xref:System.Windows.Controls.InkPresenter> <xref:System.Windows.Controls.InkPresenter.AttachVisuals%2A> <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> Připojte k volání metody a přidejte do <xref:System.Windows.UIElement.StylusPlugIns%2A> kolekce. <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> To umožňuje <xref:System.Windows.Controls.InkPresenter> zobrazit inkoust jako ukázkový bod dat je shromažďována ovládacím prvkem.  
  
     [!code-csharp[AdvancedInkTopicsSamples#17](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#17)]  
    [!code-csharp[AdvancedInkTopicsSamples#18](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#18)]  
  
4. Přepsat metodu. <xref:System.Windows.UIElement.OnStylusDown%2A>  V této metodě zachyťte <xref:System.Windows.Input.Stylus.Capture%2A>stylus s voláním . Zachycením stylus, bude ovládací prvek nadále přijímat <xref:System.Windows.UIElement.StylusMove> a <xref:System.Windows.UIElement.StylusUp> události i v případě, že stylus opustí hranice ovládacího prvku. To není přísně povinné, ale téměř vždy žádoucí pro dobrou uživatelskou zkušenost. Vytvořte <xref:System.Windows.Input.StylusPointCollection> nový <xref:System.Windows.Input.StylusPoint> shromažďovat data. Nakonec přidejte počáteční <xref:System.Windows.Input.StylusPoint> sadu dat <xref:System.Windows.Input.StylusPointCollection>do .  
  
     [!code-csharp[AdvancedInkTopicsSamples#7](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#7)]  
  
5. Přepište <xref:System.Windows.UIElement.OnStylusMove%2A> metodu a <xref:System.Windows.Input.StylusPoint> přidejte <xref:System.Windows.Input.StylusPointCollection> data do objektu, který jste vytvořili dříve.  
  
     [!code-csharp[AdvancedInkTopicsSamples#8](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#8)]  
  
6. Přepište <xref:System.Windows.UIElement.OnStylusUp%2A> metodu a <xref:System.Windows.Ink.Stroke> vytvořte <xref:System.Windows.Input.StylusPointCollection> novou s daty. Přidejte <xref:System.Windows.Ink.Stroke> nové, které <xref:System.Windows.Controls.InkPresenter.Strokes%2A> jste <xref:System.Windows.Controls.InkPresenter> vytvořili, do kolekce zachycení pera a verze.  
  
     [!code-csharp[AdvancedInkTopicsSamples#10](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#10)]  
  
<a name="EnablingYourControlToAcceptInputTromTheMouse"></a>
## <a name="how-to-enable-your-control-to-accept-input-from-the-mouse"></a>Postup: Povolte ovládacímu prvku přijímat vstup z myši  
 Pokud přidáte předchozí ovládací prvek do aplikace, spusťte jej a použít myš jako vstupní zařízení, zjistíte, že tahy nejsou trvalé. Chcete-li zachovat tahy při použití myši jako vstupní zařízení provést následující:  
  
1. Přepsat <xref:System.Windows.UIElement.OnMouseLeftButtonDown%2A> a vytvořit nový <xref:System.Windows.Input.StylusPointCollection> Získat pozici myši, když došlo k <xref:System.Windows.Input.StylusPoint> události a vytvořit <xref:System.Windows.Input.StylusPoint> pomocí <xref:System.Windows.Input.StylusPointCollection>bodu data a přidejte do .  
  
     [!code-csharp[AdvancedInkTopicsSamples#11](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#11)]  
  
2. Přepsat metodu. <xref:System.Windows.UIElement.OnMouseMove%2A> Získejte pozici myši, když došlo k <xref:System.Windows.Input.StylusPoint> události a vytvořte pomocí dat bodu.  Přidejte <xref:System.Windows.Input.StylusPoint> k <xref:System.Windows.Input.StylusPointCollection> objektu, který jste vytvořili dříve.  
  
     [!code-csharp[AdvancedInkTopicsSamples#12](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#12)]  
  
3. Přepsat metodu. <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A>  Vytvořte <xref:System.Windows.Ink.Stroke> nový <xref:System.Windows.Input.StylusPointCollection> s daty a <xref:System.Windows.Ink.Stroke> přidejte <xref:System.Windows.Controls.InkPresenter.Strokes%2A> nové, <xref:System.Windows.Controls.InkPresenter>které jste vytvořili do kolekce .  
  
     [!code-csharp[AdvancedInkTopicsSamples#13](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#13)]  
  
<a name="PuttingItTogether"></a>
## <a name="putting-it-together"></a>Dát to dohromady  
 Následující příklad je vlastní ovládací prvek, který shromažďuje rukopis, když uživatel používá myš nebo pero.  
  
 [!code-csharp[AdvancedInkTopicsSamples#20](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
[!code-csharp[AdvancedInkTopicsSamples#6](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#6)]  
  
<a name="UsingAdditionalPluginsAndDynamicRenderers"></a>
## <a name="using-additional-plug-ins-and-dynamicrenderers"></a>Použití dalších modulů plug-in a dynamických rendererů  
 Stejně jako InkCanvas, vlastní <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> ovládací <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> prvek může mít vlastní a další objekty. Přidejte je <xref:System.Windows.UIElement.StylusPlugIns%2A> do kolekce. Pořadí <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> objektů v objektech <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> ovlivňuje vzhled inkoustu při vykreslení. Předpokládejme, <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> že `dynamicRenderer` máte <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> volaný a vlastní volaný, `translatePlugin` který odsazuje rukopis z pera tabletu. Pokud `translatePlugin` je <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> první <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>v `dynamicRenderer` , a je druhý, rukopis, který "toky" bude posunuta jako uživatel přesune pero. Pokud `dynamicRenderer` je první `translatePlugin` a je druhý, rukopis nebude posunut, dokud uživatel zvedne pero.  
  
<a name="AdvancedInkHandling_Conclusion"></a>
## <a name="conclusion"></a>Závěr  
 Ovládací prvek, který shromažďuje a vykresluje inkoust, můžete vytvořit přepsáním metod událostí stylusu. Vytvořením vlastního ovládacího prvku, odvozením vlastních <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> tříd <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>a jejich vložením do aplikace můžete implementovat prakticky jakékoli chování, které si lze představit pomocí digitálního inkoustu. Máte přístup k <xref:System.Windows.Input.StylusPoint> datům tak, jak jsou generována, což vám dává možnost přizpůsobit <xref:System.Windows.Input.Stylus> vstup a vykreslit je na obrazovce podle potřeby pro vaši aplikaci. Vzhledem k tomu, že <xref:System.Windows.Input.StylusPoint> máte takový nízkoúrovňový přístup k datům, můžete implementovat kolekci inkoustů a vykreslit ji s optimálním výkonem pro vaši aplikaci.  
  
## <a name="see-also"></a>Viz také

- [Upřesnění zpracování inkoustu](advanced-ink-handling.md)
- [Přístup ke vstupu pera a manipulace s ním](https://docs.microsoft.com/previous-versions/ms818317(v=msdn.10))
