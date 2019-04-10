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
ms.openlocfilehash: b41ded25bd4eb704c6f0d67c8da1c0e6643cac5b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59323717"
---
# <a name="custom-rendering-ink"></a>Inkoust vlastního vykreslení
<xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> Vlastností tahu vám umožní určit vzhled tah, jako je například její velikost, barvu a tvar, ale může nastat situace, které chcete přizpůsobit vzhled nad rámec co <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> povolit. Můžete chtít přizpůsobit vzhled inkoustu vykreslování v vzhled vzduchová pistole, energetika Malování a mnoho dalších účinky. Windows Presentation Foundation (WPF), umožňuje vám vlastní vykreslení inkoustu pomocí implementace vlastní <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> a <xref:System.Windows.Ink.Stroke> objektu.  
  
 Toto téma obsahuje následující témata:  
  
-   [Architektura](#Architecture)  
  
-   [Implementace dynamických zobrazovací jednotky](#ImplementingADynamicRenderer)  
  
-   [Implementace vlastního tahy](#ImplementingCustomStrokes)  
  
-   [Implementace vlastního InkCanvas](#ImplementingACustomInkCanvas)  
  
-   [Závěr](#Conclusion)  
  
<a name="Architecture"></a>   
## <a name="architecture"></a>Architektura  
 Vykreslení inkoustu vyskytuje dvakrát; Pokud uživatel zapíše inkoustu rukopisu plochu a znovu po tahu se přidá na plochu rukopisu povolené. <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> Vykreslí rukopis, když uživatel přesune na digitizéru, pera a <xref:System.Windows.Ink.Stroke> vykreslí až ho přidáte do elementu.  
  
 Existují tři třídy k implementaci při vykreslování dynamicky rukopisu.  
  
1. **DynamicRenderer**: Implementace, která je odvozena z třídy <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>. Tato třída je specializovaný <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> , který vykreslí tahu jako jeho vykreslení. <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> Nemá vykreslování v samostatném vlákně, tak ke shromáždění inkoustu i v případě, že je blokované vlákno uživatelského rozhraní (UI) aplikace se zobrazí pera surface. Další informace o modelu vláken naleznete v tématu [The Model vláken inkoustu](the-ink-threading-model.md). Přizpůsobení dynamicky vykreslování tah, přepsat <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A> metody.  
  
2. **Protože byl zdvih**: Implementace, která je odvozena z třídy <xref:System.Windows.Ink.Stroke>. Tato třída je zodpovědný za statické vykreslování <xref:System.Windows.Input.StylusPoint> dat poté, co bude převeden do <xref:System.Windows.Ink.Stroke> objektu. Přepsat <xref:System.Windows.Ink.Stroke.DrawCore%2A> je konzistentní s dynamické vykreslování metody k zajištění tohoto statické vykreslování objektu stroke.  
  
3. **InkCanvas:** Implementace, která je odvozena z třídy <xref:System.Windows.Controls.InkCanvas>. Přiřadit upravené <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> k <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> vlastnost. Přepsat <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> metoda a přidejte vlastní tah na <xref:System.Windows.Controls.InkCanvas.Strokes%2A> vlastnost. Tím se zajistí, že je konzistentní vzhled čáry.  
  
<a name="ImplementingADynamicRenderer"></a>   
## <a name="implementing-a-dynamic-renderer"></a>Implementace dynamických zobrazovací jednotky  
 I když <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> třída je standardní součástí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], provádět více specializovaný, vykreslování, je třeba vytvořit vlastní dynamické renderer, který je odvozen z <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> a přepsat <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A> metody.  
  
 Následující příklad ukazuje vlastní <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> , který vykreslí rukopis s efektem štětec lineárního přechodu.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#1](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#1)]
[!code-vb[AdvancedInkTopicsSamples#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#1)]  
  
<a name="ImplementingCustomStrokes"></a>   
## <a name="implementing-custom-strokes"></a>Implementace vlastního tahy  
 Implementace, která je odvozena z třídy <xref:System.Windows.Ink.Stroke>. Tato třída je zodpovědný za vykreslování <xref:System.Windows.Input.StylusPoint> dat poté, co bude převeden do <xref:System.Windows.Ink.Stroke> objektu. Přepsat <xref:System.Windows.Ink.Stroke.DrawCore%2A> třídě, aby provedl skutečné kreslení.  
  
 Vaše Stroke – třída může také ukládat vlastní data pomocí <xref:System.Windows.Ink.Stroke.AddPropertyData%2A> metody. Tato data se ukládají s stroke datům, když se jako trvalý.  
  
 <xref:System.Windows.Ink.Stroke> Třídy můžete také provést testování přístupů. Můžete také implementovat vlastní přístupů k testování algoritmus tak, že přepíšete <xref:System.Windows.Ink.Stroke.HitTest%2A> metoda v aktuální třídě.  
  
 Následující C# kódu ukazuje vlastní <xref:System.Windows.Ink.Stroke> třídu, která vykreslí <xref:System.Windows.Input.StylusPoint> data jako 3D stroke.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#2](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#2)]
[!code-vb[AdvancedInkTopicsSamples#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#2)]  
  
<a name="ImplementingACustomInkCanvas"></a>   
## <a name="implementing-a-custom-inkcanvas"></a>Implementace vlastního InkCanvas  
 Nejjednodušší způsob, jak používat vaše vlastní <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> a implementace, která je odvozena z třídy stroke <xref:System.Windows.Controls.InkCanvas> a používá tyto třídy. <xref:System.Windows.Controls.InkCanvas> Má <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> vlastnost, která určuje, jak je vykreslen tahu při jeho vykreslení uživatele.  
  
 Na vlastní vykreslení tahy <xref:System.Windows.Controls.InkCanvas> postupujte takto:  
  
-   Vytvořte třídu, která je odvozena z <xref:System.Windows.Controls.InkCanvas>.  
  
-   Přiřadit upraveném <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> k <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A?displayProperty=nameWithType> vlastnost.  
  
-   Přepsat <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> metody. V této metodě odeberte původní tahu, která byla přidána k InkCanvas. Vytvořte vlastní stroke, přidejte ji do <xref:System.Windows.Controls.InkCanvas.Strokes%2A> vlastnosti a volání základní třídy s novou <xref:System.Windows.Controls.InkCanvasStrokeCollectedEventArgs> , který obsahuje vlastní stroke.  
  
 Následující C# kódu ukazuje vlastní <xref:System.Windows.Controls.InkCanvas> třídu, která používá vlastní <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> a shromažďuje vlastní tahů.  
  
 [!code-csharp[AdvancedInkTopicsSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#9)]  
  
 <xref:System.Windows.Controls.InkCanvas> Může mít více než jeden <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>. Můžete přidat více <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> objektů <xref:System.Windows.Controls.InkCanvas> jejich přidáním do <xref:System.Windows.UIElement.StylusPlugIns%2A> vlastnost.  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a>Závěr  
 Můžete přizpůsobit vzhled ink odvozením vlastních <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>, <xref:System.Windows.Ink.Stroke>, a <xref:System.Windows.Controls.InkCanvas> třídy. Společně tyto třídy zkontrolujte, že vzhled objektu stroke konzistentní uživatel nakreslí tahu až po shromáždění zpracovat.  
  
## <a name="see-also"></a>Viz také:

- [Upřesnění zpracování inkoustu](advanced-ink-handling.md)
