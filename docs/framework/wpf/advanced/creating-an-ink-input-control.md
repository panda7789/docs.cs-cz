---
title: "Vytvoření ovládacího prvku vstupu inkoustu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7054728e8bf54a7cf7b71ea1224cab6a352176d4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="creating-an-ink-input-control"></a>Vytvoření ovládacího prvku vstupu inkoustu
Můžete vytvořit vlastní ovládací prvek, dynamicky a staticky vykreslí rukopisu. To znamená vykreslit element ink jako uživatel nevykresluje tah, způsobuje rukopisu se objeví "toku" z pera a zobrazí rukopisu po jeho se přidá do ovládacího prvku, buď pomocí pera, vložené ze schránky, nebo načíst ze souboru. Chcete-li dynamicky vykreslit rukopisu, musíte použít vlastní ovládací prvek <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>. K vykreslení staticky rukopisu, je nutné přepsat metodu pera událostí (<xref:System.Windows.UIElement.OnStylusDown%2A>, <xref:System.Windows.UIElement.OnStylusMove%2A>, a <xref:System.Windows.UIElement.OnStylusUp%2A>) ke shromažďování <xref:System.Windows.Input.StylusPoint> data, vytvořte tahy a přidat je do <xref:System.Windows.Controls.InkPresenter> (která vykreslí element ink na ovládací prvek).  
  
 Toto téma obsahuje následující témata:  
  
-   [Postupy: shromažďování dat bodu pera a vytvořit tahy](#CollectingStylusPointDataAndCreatingInkStrokes)  
  
-   [Postupy: povolení ovládacího prvku tak, aby přijímal vstup z myši](#EnablingYourControlToAcceptInputTromTheMouse)  
  
-   [Jeho uvedení společně](#PuttingItTogether)  
  
-   [Pomocí další moduly plug-in a DynamicRenderers](#UsingAdditionalPluginsAndDynamicRenderers)  
  
-   [Uzavření](#AdvancedInkHandling_Conclusion)  
  
<a name="CollectingStylusPointDataAndCreatingInkStrokes"></a>   
## <a name="how-to-collect-stylus-point-data-and-create-ink-strokes"></a>Postupy: shromažďování dat bodu pera a vytvořit tahy  
 Vytvoření ovládacího prvku, který shromažďuje a spravuje rukopisu tahy takto:  
  
1.  Odvození třídy z <xref:System.Windows.Controls.Control> nebo jeden z třídy odvozené od <xref:System.Windows.Controls.Control>, jako například <xref:System.Windows.Controls.Label>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
    [!code-csharp[AdvancedInkTopicsSamples#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#14)]  
    [!code-csharp[AdvancedInkTopicsSamples#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#15)]  
  
2.  Přidat <xref:System.Windows.Controls.InkPresenter> do třídy a nastavte <xref:System.Windows.Controls.ContentControl.Content%2A> vlastnost k novému <xref:System.Windows.Controls.InkPresenter>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#16](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#16)]  
  
3.  Připojení <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.RootVisual%2A> z <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> k <xref:System.Windows.Controls.InkPresenter> voláním <xref:System.Windows.Controls.InkPresenter.AttachVisuals%2A> metoda a přidejte <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> k <xref:System.Windows.UIElement.StylusPlugIns%2A> kolekce. To umožňuje <xref:System.Windows.Controls.InkPresenter> pro zobrazení rukopisu jako shromažďuje data bodu pera, vlastní ovládací prvek.  
  
     [!code-csharp[AdvancedInkTopicsSamples#17](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#17)]  
    [!code-csharp[AdvancedInkTopicsSamples#18](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControlSnippets.cs#18)]  
  
4.  Přepsání <xref:System.Windows.UIElement.OnStylusDown%2A> metoda.  Tato metoda zaznamenat pera pomocí volání <xref:System.Windows.Input.Stylus.Capture%2A>. Zachytáváním pera, vlastní ovládací prvek bude nadále přijímat <xref:System.Windows.UIElement.StylusMove> a <xref:System.Windows.UIElement.StylusUp> události, i když pera opustí hranice ovládacího prvku. Nejedná striktně povinné, ale prakticky vždy požadované pro vhodné uživatelské prostředí. Vytvořte novou <xref:System.Windows.Input.StylusPointCollection> získat <xref:System.Windows.Input.StylusPoint> data. Nakonec přidejte prvotní sady <xref:System.Windows.Input.StylusPoint> data <xref:System.Windows.Input.StylusPointCollection>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#7)]  
  
5.  Přepsání <xref:System.Windows.UIElement.OnStylusMove%2A> metoda a přidejte <xref:System.Windows.Input.StylusPoint> data <xref:System.Windows.Input.StylusPointCollection> objekt, který jste vytvořili dříve.  
  
     [!code-csharp[AdvancedInkTopicsSamples#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#8)]  
  
6.  Přepsání <xref:System.Windows.UIElement.OnStylusUp%2A> metoda a vytvořte novou <xref:System.Windows.Ink.Stroke> s <xref:System.Windows.Input.StylusPointCollection> data. Přidejte nové <xref:System.Windows.Ink.Stroke> jste vytvořili na <xref:System.Windows.Controls.InkPresenter.Strokes%2A> kolekce <xref:System.Windows.Controls.InkPresenter> a verzí pera zachycení.  
  
     [!code-csharp[AdvancedInkTopicsSamples#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#10)]  
  
<a name="EnablingYourControlToAcceptInputTromTheMouse"></a>   
## <a name="how-to-enable-your-control-to-accept-input-from-the-mouse"></a>Postupy: povolení ovládacího prvku tak, aby přijímal vstup z myši  
 Pokud přidáte předchozí ovládacího prvku do vaší aplikace, spouštět a používat jako vstupní zařízení, si všimnete, že nejsou tahy trvalé. Chcete-li zachovat tahy při Myš slouží jako vstupní zařízení takto:  
  
1.  Přepsat <xref:System.Windows.UIElement.OnMouseLeftButtonDown%2A> a vytvořte novou <xref:System.Windows.Input.StylusPointCollection> získat polohu myši při výskytu události a vytvořit <xref:System.Windows.Input.StylusPoint> pomocí data bodu a přidat <xref:System.Windows.Input.StylusPoint> k <xref:System.Windows.Input.StylusPointCollection>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#11)]  
  
2.  Přepsání <xref:System.Windows.UIElement.OnMouseMove%2A> metoda. Získá pozici myši při výskytu události a vytvořit <xref:System.Windows.Input.StylusPoint> pomocí datového bodu.  Přidat <xref:System.Windows.Input.StylusPoint> k <xref:System.Windows.Input.StylusPointCollection> objekt, který jste vytvořili dříve.  
  
     [!code-csharp[AdvancedInkTopicsSamples#12](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#12)]  
  
3.  Přepsání <xref:System.Windows.UIElement.OnMouseLeftButtonUp%2A> metoda.  Vytvořte novou <xref:System.Windows.Ink.Stroke> s <xref:System.Windows.Input.StylusPointCollection> dat a přidejte nové <xref:System.Windows.Ink.Stroke> jste vytvořili na <xref:System.Windows.Controls.InkPresenter.Strokes%2A> kolekce <xref:System.Windows.Controls.InkPresenter>.  
  
     [!code-csharp[AdvancedInkTopicsSamples#13](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#13)]  
  
<a name="PuttingItTogether"></a>   
## <a name="putting-it-together"></a>Jeho uvedení společně  
 V následujícím příkladu je vlastní ovládací prvek, který shromažďuje rukopisu, když uživatel používá myši nebo pera.  
  
 [!code-csharp[AdvancedInkTopicsSamples#20](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#20)]  
[!code-csharp[AdvancedInkTopicsSamples#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/StylusControl.cs#6)]  
  
<a name="UsingAdditionalPluginsAndDynamicRenderers"></a>   
## <a name="using-additional-plug-ins-and-dynamicrenderers"></a>Pomocí další moduly plug-in a DynamicRenderers  
 Jako InkCanvas, může mít vlastní ovládací prvek vlastní <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> a další <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> objekty. Přidat do <xref:System.Windows.UIElement.StylusPlugIns%2A> kolekce. Pořadí <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> objekty v <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection> ovlivňuje vzhled čáry, je vykreslen. Předpokládejme, že máte <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> názvem `dynamicRenderer` a vlastní <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> názvem `translatePlugin` , posun očistí od pera. Pokud `translatePlugin` je první <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> v <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>, a `dynamicRenderer` je druhá, jako uživatel přesune pera budou posunuty rukopisu, který "tok". Pokud `dynamicRenderer` je první, a `translatePlugin` je druhý, rukopisu nebude posun, dokud uživatel zruší pera.  
  
<a name="AdvancedInkHandling_Conclusion"></a>   
## <a name="conclusion"></a>Závěr  
 Můžete vytvořit ovládací prvek, který shromažďuje a vykreslí element ink přepsáním metody pera události. Vytvořením vlastního ovládacího prvku odvozování vlastní <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> třídy a jejich vložení na do <xref:System.Windows.Input.StylusPlugIns.StylusPlugInCollection>, můžete implementovat prakticky libovolný chování vůbec digitální barvou. Máte přístup k <xref:System.Windows.Input.StylusPoint> data, jako je generován, budete moci přizpůsobit <xref:System.Windows.Input.Stylus> vstup a vykreslit ho na obrazovce podle potřeby pro vaši aplikaci. Vzhledem k tomu, že máte takový nízké úrovně přístup k <xref:System.Windows.Input.StylusPoint> data, můžete implementovat rozpoznávání rukopisu a vykreslit ho s optimální výkon pro vaši aplikaci.  
  
## <a name="see-also"></a>Viz také  
 [Pokročilé zpracování rukopisu](../../../../docs/framework/wpf/advanced/advanced-ink-handling.md)  
 [Přístup k informacím a manipulace s vstup pomocí pera](http://go.microsoft.com/fwlink/?LinkId=50752&clcid=0x409)
