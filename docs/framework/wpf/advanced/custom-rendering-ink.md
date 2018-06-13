---
title: Inkoust vlastního vykreslení
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom-rendering ink
- ink [WPF], custom-rendering
- classes [WPF], InkCanvas
ms.assetid: 65c978a7-0ee0-454f-ac7f-b1bd2efecac5
ms.openlocfilehash: 2c627f757c1eccc37f57aea6880ffc8a362e5ddb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540430"
---
# <a name="custom-rendering-ink"></a>Inkoust vlastního vykreslení
<xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> Vlastnost tahu umožňuje určit vzhled tahu, například jeho velikost, barvu a tvar, ale může nastat situace, které chcete přizpůsobit vzhled nad rámec co <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> povolit. Můžete přizpůsobit vzhled rukopisu vykreslování v vzhled štětce letecké, těžba ropy Malování a mnoho dalších účinky. Windows Presentation Foundation (WPF) umožňuje, abyste vlastní vykreslení rukopisu implementací vlastní <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> a <xref:System.Windows.Ink.Stroke> objektu.  
  
 Toto téma obsahuje následující témata:  
  
-   [Architektura](#Architecture)  
  
-   [Implementace dynamických zobrazovací jednotky](#ImplementingADynamicRenderer)  
  
-   [Implementace vlastní tahy](#ImplementingCustomStrokes)  
  
-   [Implementace vlastních InkCanvas](#ImplementingACustomInkCanvas)  
  
-   [Uzavření](#Conclusion)  
  
<a name="Architecture"></a>   
## <a name="architecture"></a>Architektura  
 Vykreslování rukopisu proběhne dvakrát; Pokud uživatel zapíše rukopisu rukopisu povrch a znovu po tahu se přidá na povrch rukopisu povolena. <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> Vykreslí rukopisu, když se uživatel přesune pera na digitizéru a <xref:System.Windows.Ink.Stroke> se vykreslí po jejím přidání do elementu.  
  
 Existují tři třídy k implementaci při vykreslování dynamicky rukopisu.  
  
1.  **DynamicRenderer**: implementovat třídu odvozenou od <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>. Tato třída je speciální <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> , vykreslí tahu při kreslení. <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> Nemá vykreslování na samostatné vlákno, tak se zobrazí rukopisu prostor ke shromažďování rukopisu i v případě, že vlákno aplikace uživatelské rozhraní (UI) je blokované. Další informace o modelu vláken najdete v tématu [modelu dělení na vlákna rukopisu](../../../../docs/framework/wpf/advanced/the-ink-threading-model.md). Chcete-li přizpůsobit dynamicky vykreslování tah, přepište <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A> metoda.  
  
2.  **Tahu**: implementovat třídu odvozenou od <xref:System.Windows.Ink.Stroke>. Tato třída je zodpovědná za statickou vykreslování <xref:System.Windows.Input.StylusPoint> data po převedení do <xref:System.Windows.Ink.Stroke> objektu. Přepsání <xref:System.Windows.Ink.Stroke.DrawCore%2A> metoda zajistit, že statické vykreslování tahu je konzistentní s dynamické vykreslování.  
  
3.  **InkCanvas:** implementovat třídu odvozenou od <xref:System.Windows.Controls.InkCanvas>. Přiřadit vlastní <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> k <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> vlastnost. Přepsání <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> metoda a přidat vlastní tahu k <xref:System.Windows.Controls.InkCanvas.Strokes%2A> vlastnost. Tím se zajistí, že je konzistentní vzhled čáry.  
  
<a name="ImplementingADynamicRenderer"></a>   
## <a name="implementing-a-dynamic-renderer"></a>Implementace dynamických zobrazovací jednotky  
 I když <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> třída je standardní součástí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]k provedení více specializuje vykreslování, musíte vytvořit vlastní dynamické zobrazovací jednotky, která je odvozena z <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> a přepsat <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A> metoda.  
  
 Následující příklad ukazuje, přizpůsobený <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> který nevykresluje rukopisu s lineární štětce přechodu vliv.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#1)]
[!code-vb[AdvancedInkTopicsSamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#1)]  
  
<a name="ImplementingCustomStrokes"></a>   
## <a name="implementing-custom-strokes"></a>Implementace vlastní tahy  
 Implementovat třídu odvozenou od <xref:System.Windows.Ink.Stroke>. Tato třída je zodpovědná za vykreslování <xref:System.Windows.Input.StylusPoint> data po převedení do <xref:System.Windows.Ink.Stroke> objektu. Přepsání <xref:System.Windows.Ink.Stroke.DrawCore%2A> třída provedete skutečné kreslení.  
  
 Třídě tahu můžete také ukládat vlastní data pomocí <xref:System.Windows.Ink.Stroke.AddPropertyData%2A> metoda. Tato data jsou ukládána data tahu při.  
  
 <xref:System.Windows.Ink.Stroke> Třídy můžete také provést testování přístupů. Můžete implementovat vlastní vstupů do testování algoritmus přepsáním <xref:System.Windows.Ink.Stroke.HitTest%2A> metodu v aktuální třídě.  
  
 Následující kód C# ukazuje vlastní <xref:System.Windows.Ink.Stroke> třídu, která vykreslí <xref:System.Windows.Input.StylusPoint> data jako 3D tahu.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#2)]
[!code-vb[AdvancedInkTopicsSamples#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#2)]  
  
<a name="ImplementingACustomInkCanvas"></a>   
## <a name="implementing-a-custom-inkcanvas"></a>Implementace vlastních InkCanvas  
 Nejjednodušší způsob, jak používat vaše vlastní <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> a implementovat třídu odvozenou od tahu <xref:System.Windows.Controls.InkCanvas> a používá tyto třídy. <xref:System.Windows.Controls.InkCanvas> Má <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> vlastnost, která určuje, jak je vykreslen tahu, pokud uživatel je kreslení ho.  
  
 Pro vlastní vykreslení tahy na <xref:System.Windows.Controls.InkCanvas> postupujte takto:  
  
-   Vytvořte třídu, která je odvozena z <xref:System.Windows.Controls.InkCanvas>.  
  
-   Přiřadit vaše vlastní <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> k <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A?displayProperty=nameWithType> vlastnost.  
  
-   Přepsání <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> metoda. Tato metoda odeberte původní tahu, která byla přidána do InkCanvas. Pak vytvořte vlastního tahu, přidejte ho do <xref:System.Windows.Controls.InkCanvas.Strokes%2A> vlastnost a volání základní třídy s novou <xref:System.Windows.Controls.InkCanvasStrokeCollectedEventArgs> obsahující vlastní tahu.  
  
 Následující kód C# ukazuje vlastní <xref:System.Windows.Controls.InkCanvas> třídu, která využívá přizpůsobený <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> a shromažďuje vlastní tahy.  
  
 [!code-csharp[AdvancedInkTopicsSamples#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#9)]  
  
 <xref:System.Windows.Controls.InkCanvas> Může mít více než jeden <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>. Můžete přidat více <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> objekty ke <xref:System.Windows.Controls.InkCanvas> jejich přidáním do <xref:System.Windows.UIElement.StylusPlugIns%2A> vlastnost.  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a>Závěr  
 Můžete přizpůsobit vzhled rukopisu odvozování vlastní <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>, <xref:System.Windows.Ink.Stroke>, a <xref:System.Windows.Controls.InkCanvas> třídy. Společně tyto třídy zajistěte, aby byl vzhled tahu konzistentní když uživatel nakreslí tahu a po shromáždění zpracovat.  
  
## <a name="see-also"></a>Viz také  
 [Pokročilé zpracování rukopisu](../../../../docs/framework/wpf/advanced/advanced-ink-handling.md)
