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
ms.openlocfilehash: 3cf0d98c40e71a380b218c76d6e52d00cdd05342
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186355"
---
# <a name="custom-rendering-ink"></a>Inkoust vlastního vykreslení
Vlastnost <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> tahu umožňuje určit vzhled tahu, například jeho velikost, barvu a tvar, ale mohou nastat časy, kdy <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> chcete vzhled přizpůsobit nad rámec toho, co umožňuje. Vzhled inkoustu můžete přizpůsobit vykreslením vzhledu vzduchového štětce, olejové barvy a mnoha dalších efektů. Windows Presentation Foundation (WPF) umožňuje vlastní vykreslení inkoustu <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> <xref:System.Windows.Ink.Stroke> implementací vlastní a objekt.  
  
 Toto téma obsahuje následující pododdíly:  
  
- [Architektura](#Architecture)  
  
- [Implementace dynamického rendereru](#ImplementingADynamicRenderer)  
  
- [Implementace vlastních tahů](#ImplementingCustomStrokes)  
  
- [Implementace vlastního plátna InkCanvas](#ImplementingACustomInkCanvas)  
  
- [Závěr](#Conclusion)  
  
<a name="Architecture"></a>
## <a name="architecture"></a>Architektura  
 K vykreslování inkoustu dochází dvakrát; když uživatel zapíše rukopis na povrch rukopisu a znovu po přidání tahu na povrch s podporou inkoustu. Vykreslí <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> rukopis, když uživatel přesune pero tabletu na <xref:System.Windows.Ink.Stroke> digitizéru a vykreslí sám, jakmile je přidán do prvku.  
  
 Existují tři třídy, které je třeba implementovat při dynamickém vykreslování inkoustu.  
  
1. **DynamicRenderer**: Implementovat třídu, která je odvozena od <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>. Tato třída je <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> specializovaná, která vykresluje tah tak, jak je nakreslena. Provádí <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> vykreslování na samostatné vlákno, takže se zdá, že povrch rukopisu shromažďuje rukopis, i když je blokováno vlákno uživatelského rozhraní aplikace .... Další informace o modelu zřetězení naleznete [v tématu Model vláken inkoustu](the-ink-threading-model.md). Chcete-li dynamicky vykreslovat tah, přepište metodu. <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A>  
  
2. **Tah**: Implementovat třídu, která je odvozena od <xref:System.Windows.Ink.Stroke>. Tato třída je zodpovědná za <xref:System.Windows.Input.StylusPoint> statické vykreslování dat poté, co byla převedena na <xref:System.Windows.Ink.Stroke> objekt. Přepište <xref:System.Windows.Ink.Stroke.DrawCore%2A> metodu, abyste zajistili, že statické vykreslování tahu je konzistentní s dynamickým vykreslováním.  
  
3. **Plátno ink:** Implementovat třídu, <xref:System.Windows.Controls.InkCanvas>která je odvozena od . Přiřaďte <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> vlastní <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> vlastnost. Přepište <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> metodu a přidejte <xref:System.Windows.Controls.InkCanvas.Strokes%2A> do vlastnosti vlastní tah. Tím je zajištěno, že vzhled inkoustu je konzistentní.  
  
<a name="ImplementingADynamicRenderer"></a>
## <a name="implementing-a-dynamic-renderer"></a>Implementace dynamického rendereru  
 Přestože <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> třída je standardní [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]součástí , provádět specializovanější vykreslování, je nutné <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> vytvořit vlastní <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A> dynamický vykreslovač, který je odvozen od a přepsat metodu.  
  
 Následující příklad ukazuje <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> vlastní, který kreslí inkoust s lineárním přechodem efekt stopy.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#1](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#1)]
[!code-vb[AdvancedInkTopicsSamples#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#1)]  
  
<a name="ImplementingCustomStrokes"></a>
## <a name="implementing-custom-strokes"></a>Implementace vlastních tahů  
 Implementovat třídu, <xref:System.Windows.Ink.Stroke>která je odvozena od . Tato třída je <xref:System.Windows.Input.StylusPoint> zodpovědná za vykreslování dat poté, co byla převedena na <xref:System.Windows.Ink.Stroke> objekt. Přepište <xref:System.Windows.Ink.Stroke.DrawCore%2A> třídu, abyste udělali skutečný výkres.  
  
 Vaše Stroke třída můžete také ukládat vlastní data pomocí <xref:System.Windows.Ink.Stroke.AddPropertyData%2A> metody. Tato data jsou uložena s daty tahu při trvalé.  
  
 Třída <xref:System.Windows.Ink.Stroke> může také provádět testování přístupů. Můžete také implementovat vlastní algoritmus testování <xref:System.Windows.Ink.Stroke.HitTest%2A> přístupů přepsáním metody v aktuální třídě.  
  
 Následující kód jazyka C# <xref:System.Windows.Ink.Stroke> ukazuje vlastní <xref:System.Windows.Input.StylusPoint> třídu, která vykresluje data jako 3D tah.  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#2](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#2)]
[!code-vb[AdvancedInkTopicsSamples#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#2)]  
  
<a name="ImplementingACustomInkCanvas"></a>
## <a name="implementing-a-custom-inkcanvas"></a>Implementace vlastního plátna InkCanvas  
 Nejjednodušší způsob, jak použít <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> vlastní a tah je implementovat <xref:System.Windows.Controls.InkCanvas> třídu, která je odvozena od a používá tyto třídy. Má <xref:System.Windows.Controls.InkCanvas> <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> vlastnost, která určuje, jak je tah vykreslen, když ji uživatel kreslí.  
  
 Chcete-li vlastní tahy vykreslení na provedení <xref:System.Windows.Controls.InkCanvas> následujícího:  
  
- Vytvořte třídu, která <xref:System.Windows.Controls.InkCanvas>je odvozena od .  
  
- Přiřaďte <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> vlastní <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A?displayProperty=nameWithType> vlastnost.  
  
- Přepsat metodu. <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> V této metodě odeberte původní tah, který byl přidán do InkCanvas. Pak vytvořte vlastní tah, <xref:System.Windows.Controls.InkCanvas.Strokes%2A> přidejte ho do vlastnosti <xref:System.Windows.Controls.InkCanvasStrokeCollectedEventArgs> a zavolejte základní třídu s novou, která obsahuje vlastní tah.  
  
 Následující kód jazyka C# <xref:System.Windows.Controls.InkCanvas> ukazuje vlastní třídu, která používá vlastní <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> a shromažďuje vlastní tahy.  
  
 [!code-csharp[AdvancedInkTopicsSamples#9](~/samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#9)]  
  
 A <xref:System.Windows.Controls.InkCanvas> může mít <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>více než jeden . Přidáním více <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> objektů do vlastnosti <xref:System.Windows.UIElement.StylusPlugIns%2A> můžete přidat více objektů. <xref:System.Windows.Controls.InkCanvas>  
  
<a name="Conclusion"></a>
## <a name="conclusion"></a>Závěr  
 Vzhled inkoustu můžete přizpůsobit odvozením vlastních <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> <xref:System.Windows.Ink.Stroke>, <xref:System.Windows.Controls.InkCanvas> a tříd. Společně tyto třídy zajistit, že vzhled tahu je konzistentní, když uživatel kreslí tah a po jeho shromáždění.  
  
## <a name="see-also"></a>Viz také

- [Upřesnění zpracování inkoustu](advanced-ink-handling.md)
