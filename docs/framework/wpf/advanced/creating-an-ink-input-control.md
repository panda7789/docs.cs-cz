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
ms.openlocfilehash: 3113b953c1c547035883a4f4b51f53e4aefdf0a6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43392419"
---
# <a name="creating-an-ink-input-control"></a>Vytvoření ovládacího prvku vstupu inkoustu
Můžete vytvořit vlastní ovládací prvek, který dynamicky a staticky vykreslí rukopis. To znamená vykreslení inkoustu jako uživatel nakreslí tah, způsobí rukopisu se zobrazí "tok" z pera a zobrazit inkoustu po jeho přidání do ovládacího prvku, buď prostřednictvím pera, vložili ze schránky nebo načtena ze souboru. Dynamicky vykreslit rukopisu, musíte použít ovládací prvek <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>. Staticky vykreslení inkoustu, je nutné přepsat stylus metody událostí (<xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusMove%2A>, a <xref:System.Windows.UIElement.OnStylusUp%2A>) ke shromažďování <xref:System.Windows.Input.StylusPoint> data, vytvářet tahy a přidat je do <xref:System.Windows.Controls.InkPresenter> (která vykreslí rukopis na ovládací prvek).  
  
 Toto téma obsahuje následující témata:  
  
-   [Postupy: shromažďování dat bodu Stylus a vytvořit inkoustových tahů](#CollectingStylusPointDataAndCreatingInkStrokes)  
  
-   [Postupy: povolení ovládacího prvku tak, aby přijímal vstup z myši](#EnablingYourControlToAcceptInputTromTheMouse)  
  
-   [Jeho uvedení společně](#PuttingItTogether)  
  
-   [Další moduly plug-in a DynamicRenderers](#UsingAdditionalPluginsAndDynamicRenderers)  
  
-   [Závěr](#AdvancedInkHandling_Conclusion)  
  
<a name="CollectingStylusPointDataAndCreatingInkStrokes"></a>   
## <a name="how-to-collect-stylus-point-data-and-create-ink-strokes"></a>Postupy: shromažďování dat bodu Stylus a vytvořit inkoustových tahů  
 Chcete-li vytvořit ovládací prvek, který shromažďuje a spravuje inkoustu tahy takto:  
  
1.  Odvodit třídu z <xref:System.Windows.Controls.Control> nebo jedné ze tříd odvozených z <xref:System.Windows.Controls.Control>, jako například <xref:System.Windows.Controls.Label>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
    [!code-csharp[AdvancedInkTopicsSamples#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#14)]  
    [!code-csharp[AdvancedInkTopicsSamples#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#15)]  
  
2.  Přidat <xref:System.Windows.Controls.InkPresenter> do třídy a nastavte <xref:System.Windows.Controls.ContentControl.Content%2A> vlastnost k novému <xref:System.Windows.Controls.InkPresenter>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#16)]  
  
3.  Připojit <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> z <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> k <xref:System.Windows.Controls.InkPresenter> voláním <xref:System.Windows.Controls.InkPresenter.AttachVisuals%2A> metoda a přidejte <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> k <xref:System.Windows.UIElement.StylusPlugIns%2A> kolekce. Díky tomu <xref:System.Windows.Controls.InkPresenter> zobrazíte rukopisu, jak se shromažďují data bodu stylus váš ovládací prvek.  
  
     [!code-csharp[AdvancedInkTopicsSamples#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#17)]  
    [!code-csharp[AdvancedInkTopicsSamples#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#18)]  
  
4.  Přepsat <xref:System.Windows.UIElement.OnStylusDown%2A> metody.  V této metodě zachycení stylusu voláním <xref:System.Windows.Input.Stylus.Capture%2A>. Zachytáváním stylus váš ovládací prvek bude nadále přijímat <xref:System.Windows.UIElement.StylusMove> a <xref:System.Windows.UIElement.StylusUp> události, i když se stylus opustí hranice ovládacího prvku. To není nezbytně povinné, ale téměř vždy požadované pro bezproblémový. Vytvořte nový <xref:System.Windows.Input.StylusPointCollection> shromažďovat <xref:System.Windows.Input.StylusPoint> data. Nakonec přidejte počáteční sadu <xref:System.Windows.Input.StylusPoint> data <xref:System.Windows.Input.StylusPointCollection>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#7)]  
  
5.  Přepsat <xref:System.Windows.UIElement.OnStylusMove%2A> metoda a přidejte <xref:System.Windows.Input.StylusPoint> data <xref:System.Windows.Input.StylusPointCollection> objekt, který jste vytvořili dříve.  
  
     [!code-csharp[AdvancedInkTopicsSamples#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#8)]  
  
6.  Přepsat <xref:System.Windows.UIElement.OnStylusUp%2A> metoda a vytvořte nový <xref:System.Windows.Ink.Stroke> s <xref:System.Windows.Input.StylusPointCollection> data. Přidejte nové <xref:System.Windows.Ink.Stroke> jste vytvořili za účelem <xref:System.Windows.Controls.InkPresenter.Strokes%2A> kolekce <xref:System.Windows.Controls.InkPresenter> a vydání nazachytí stylus.  
  
     [!code-csharp[AdvancedInkTopicsSamples#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#10)]  
  
<a name="EnablingYourControlToAcceptInputTromTheMouse"></a>   
## <a name="how-to-enable-your-control-to-accept-input-from-the-mouse"></a>Postupy: povolení ovládacího prvku tak, aby přijímal vstup z myši  
 Pokud přidáte předchozí ovládací prvek do vaší aplikace, spusťte ji a pomocí myši jako vstupní zařízení, si všimnete, že nejsou trvalé strokes. Zachování tahy, když ukazatel myši se používá jako vstupní zařízení, postupujte takto:  
  
1.  Přepsat <xref:System.Windows.UIElement.OnMouseLeftButtonDown%2A> a vytvořte nový <xref:System.Windows.Input.StylusPointCollection> získat polohu myši při výskytu události a vytvořit <xref:System.Windows.Input.StylusPoint> datový bod a přidat <xref:System.Windows.Input.StylusPoint> k <xref:System.Windows.Input.StylusPointCollection>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#11)]  
  
2.  Přepsat <xref:System.Windows.UIElement.OnMouseMove%2A> metody. Získá pozice myši při výskytu události a vytvořit <xref:System.Windows.Input.StylusPoint> pomocí datového bodu.  Přidat <xref:System.Windows.Input.StylusPoint> k <xref:System.Windows.Input.StylusPointCollection> objekt, který jste vytvořili dříve.  
  
     [!code-csharp[AdvancedInkTopicsSamples#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#12)]  
  
3.  Přepsat <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A> metody.  Vytvořte nový <xref:System.Windows.Ink.Stroke> s <xref:System.Windows.Input.StylusPointCollection> dat a přidejte nové <xref:System.Windows.Ink.Stroke> jste vytvořili pro <xref:System.Windows.Controls.InkPresenter.Strokes%2A> kolekce <xref:System.Windows.Controls.InkPresenter>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#13)]  
  
<a name="PuttingItTogether"></a>   
## <a name="putting-it-together"></a>Jeho uvedení společně  
 Následující příklad je vlastní ovládací prvek, který shromažďuje rukopisu, když uživatel použije myši nebo pera.  
  
 [!code-csharp[AdvancedInkTopicsSamples#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
[!code-csharp[AdvancedInkTopicsSamples#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#6)]  
  
<a name="UsingAdditionalPluginsAndDynamicRenderers"></a>   
## <a name="using-additional-plug-ins-and-dynamicrenderers"></a>Další moduly plug-in a DynamicRenderers  
 Stejně jako InkCanvas, vlastní ovládací prvek může mít vlastní <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> a další <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> objekty. Přidat do <xref:System.Windows.UIElement.StylusPlugIns%2A> kolekce. Pořadí <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> objekty v <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> má vliv na vzhled čáry při vykreslení. Předpokládejme, že máte <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> volá `dynamicRenderer` a vlastní <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> volá `translatePlugin` , který posouvá ink z pera. Pokud `translatePlugin` je první <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> v <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>, a `dynamicRenderer` tím dokončím inkoustu přenášené "" budou posunuty, jak uživatel pohybuje pera. Pokud `dynamicRenderer` je první, a `translatePlugin` je navíc rukopis nebude posun, dokud uživatel zruší pera.  
  
<a name="AdvancedInkHandling_Conclusion"></a>   
## <a name="conclusion"></a>Závěr  
 Můžete vytvořit ovládací prvek, který shromažďuje a vykreslí rukopis přepsáním metody událostí stylus. Tím, že vytvoříte vlastní ovládací prvek odvozený vlastní <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> třídy a jejich vložení do <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>, můžete implementovat prakticky jakoukoli vůbec pomocí digitálních inkoust chování. Máte přístup k <xref:System.Windows.Input.StylusPoint> dat, jako je generováno, získáte tak možnost přizpůsobit <xref:System.Windows.Input.Stylus> vstup a vykreslit ho na obrazovce v závislosti na vaší aplikace. Protože máte takový přístup nízké úrovně ke <xref:System.Windows.Input.StylusPoint> data, můžete implementovat kolekce inkoustů a vykreslit poskytovaly optimální výkon pro vaši aplikaci.  
  
## <a name="see-also"></a>Viz také  
 [Pokročilé zpracování rukopisu](../../../../docs/framework/wpf/advanced/advanced-ink-handling.md)  
 [Přístup k a manipulaci s vstup pomocí pera](https://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)
