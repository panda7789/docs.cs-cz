---
title: 'Postupy: Vykreslení intervalu podle snímků pomocí CompositionTarget'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CompositionTarget objects [WPF], rendering per frame
- rendering per frame using CompositionTarget objects [WPF]
ms.assetid: 701246cd-66b7-4d69-ada9-17b3b433d95d
ms.openlocfilehash: 00b416d423a4bdc8bab576add2d77fd305ea6e0f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59089409"
---
# <a name="how-to-render-on-a-per-frame-interval-using-compositiontarget"></a>Postupy: Vykreslení intervalu podle snímků pomocí CompositionTarget
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Animace modul obsahuje řadu funkcí pro vytváření založených na snímcích animace. Existují však aplikačních scénářů, ve kterých je nutné citlivější kontrolu nad vykreslování na základě na rámce. <xref:System.Windows.Media.CompositionTarget> Objekt poskytuje možnost vytvářet vlastní animace založené na zpětné volání na rámce.  
  
 <xref:System.Windows.Media.CompositionTarget> je statická třída, která představuje zobrazovacím povrchu, na kterém je vykreslen vaší aplikace. <xref:System.Windows.Media.CompositionTarget.Rendering> Událost je vyvolána pokaždé, když je vykreslení scény vaší aplikace. Snímková frekvence vykreslování je počet průchodů za sekundu je vykreslení scény.  
  
> [!NOTE]
>  Pro kompletní kód ukázkový používání <xref:System.Windows.Media.CompositionTarget>, naleznete v tématu [ukázka CompositionTarget](https://go.microsoft.com/fwlink/?LinkID=160045).  
  
## <a name="example"></a>Příklad  
 <xref:System.Windows.Media.CompositionTarget.Rendering> Událost aktivuje při [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] proces vykreslování. Následující příklad ukazuje, jak zaregistrovat <xref:System.EventHandler> delegovat na statické <xref:System.Windows.Media.CompositionTarget.Rendering> metodu na <xref:System.Windows.Media.CompositionTarget>.  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget1](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget1)]
 [!code-vb[CompositionTargetSample#CompositionTarget1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget1)]  
  
 Vaše metoda obslužné rutiny události vykreslování můžete použít k vytvoření vlastního vykreslování obsahu. Tato metoda obslužné rutiny události volána jednou pro každý snímek. Pokaždé, když, který [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] marshals se nazývá trvalý vykreslování data ve vizuálním stromu napříč složení graf scén, vaše metoda obslužné rutiny události. Kromě toho pokud se změny vizuálního stromu vynutí aktualizace graf scén složení, vaše metoda obslužné rutiny události se také nazývá. Všimněte si, že vaše metoda obslužné rutiny události se volá, když byl vypočítán rozložení. Však můžete změnit rozložení ve své metodě obslužné rutiny událostí, což znamená, že toto rozložení se vypočítá jednou před vykreslením.  
  
 Následující příklad ukazuje, jak můžete zadat vlastní kreslení v <xref:System.Windows.Media.CompositionTarget> metoda obslužné rutiny události. V takovém případě barvu pozadí <xref:System.Windows.Controls.Canvas> je vykreslen s hodnotu barvy na základě souřadnici pozice myši. Pokud posunete myší uvnitř <xref:System.Windows.Controls.Canvas>, jeho změny barev na pozadí. Kromě toho se vypočítá průměrná Snímková frekvence, na základě aktuální uplynulý čas a celkový počet vykreslené snímky.  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget2](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget2)]
 [!code-vb[CompositionTargetSample#CompositionTarget2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget2)]  
  
 Zjistíte, že běží při různých rychlostech vlastního vykreslení na různých počítačích. Důvodem je, že vaše vlastní kreslení není Snímková frekvence nezávislé. V závislosti na systému spustíte a daného zatížení systému <xref:System.Windows.Media.CompositionTarget.Rendering> události může být volána jiný počet za sekundu. Informace o určení grafické hardwaru možnosti a výkon pro zařízení se systémem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace, najdete v článku [vrstvy vykreslování grafiky](../advanced/graphics-rendering-tiers.md).  
  
 Přidání nebo odebrání vykreslení <xref:System.EventHandler> delegáta, když událost je vyvolávána, bude odložena až do po dokončení události ohlásí. To je konzistentní s jak <xref:System.MulticastDelegate>– na základě události jsou zpracovávány v Common Language Runtime (CLR). Všimněte si také, že události vykreslování nemusí být volána v libovolném pořadí. Pokud máte více <xref:System.EventHandler> delegáty, které jsou závislé na určitém pořadí, byste měli zaregistrovat jediné <xref:System.Windows.Media.CompositionTarget.Rendering> událostí a multiplexovaný do delegátů ve správné pořadí sami.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.CompositionTarget>
- [Přehled vykreslování grafiky WPF](wpf-graphics-rendering-overview.md)
