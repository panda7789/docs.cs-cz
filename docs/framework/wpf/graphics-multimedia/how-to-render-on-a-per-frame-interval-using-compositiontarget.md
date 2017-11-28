---
title: "Postupy: Vykreslení intervalu podle snímků pomocí CompositionTarget"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CompositionTarget objects [WPF], rendering per frame
- rendering per frame using CompositionTarget objects [WPF]
ms.assetid: 701246cd-66b7-4d69-ada9-17b3b433d95d
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7616a418b9f2f6b175b925e4385322c42546e9bc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-render-on-a-per-frame-interval-using-compositiontarget"></a>Postupy: Vykreslení intervalu podle snímků pomocí CompositionTarget
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Animace modul poskytuje mnoho funkcí pro vytváření na základě snímků animace. Existují však scénáře aplikací, ve kterých potřebujete citlivější kontrolu nad vykreslování rámce za den. <xref:System.Windows.Media.CompositionTarget> Objekt poskytuje možnost vytvářet vlastní animace podle zpětného volání za rámce.  
  
 <xref:System.Windows.Media.CompositionTarget>je statická třída, která představuje zobrazení prostor, na kterém se přitahuje vaší aplikace. <xref:System.Windows.Media.CompositionTarget.Rendering> Událost se vyvolá pokaždé, když se nevykreslí scény aplikace. Obnovovací frekvence vykreslování je počet, kolikrát scény vykreslením za sekundu.  
  
> [!NOTE]
>  Pro dokončení kódu ukázka pomocí <xref:System.Windows.Media.CompositionTarget>, najdete v části [pomocí ukázkových CompositionTarget](http://go.microsoft.com/fwlink/?LinkID=160045).  
  
## <a name="example"></a>Příklad  
 <xref:System.Windows.Media.CompositionTarget.Rendering> Událost se aktivuje při [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] proces vykreslování. Následující příklad ukazuje, jak zaregistrovat <xref:System.EventHandler> delegovat na statické <xref:System.Windows.Media.CompositionTarget.Rendering> metodu <xref:System.Windows.Media.CompositionTarget>.  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget1)]
 [!code-vb[CompositionTargetSample#CompositionTarget1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget1)]  
  
 Vykreslování metodu obslužné rutiny událostí můžete použít k vytvoření vlastní vykreslení obsahu. Tato metoda obslužné rutiny události získá volá se jednou za snímek. Každý čas, který [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] marshals trvalou vykreslování data ve vizuální strojové struktuře napříč do grafu, scény složení, metodu obslužné rutiny událostí je volána. Kromě toho pokud změny vizuálním stromu vynutit aktualizace do grafu scény složení, metodu obslužné rutiny událostí je také označován. Všimněte si, že vaše metoda obslužné rutiny události je volána po rozložení je poškozený. Rozložení však lze upravit v metodu obslužná rutina události, což znamená, že se jednou před vykreslením počítaný tohoto rozložení.  
  
 Následující příklad ukazuje, jak můžete zadat vlastní kreslení v <xref:System.Windows.Media.CompositionTarget> obslužná rutina události. V tomto případě barva pozadí <xref:System.Windows.Controls.Canvas> vykreslením s hodnotou barvu podle souřadnice polohy myši. Při přesunutí myši uvnitř <xref:System.Windows.Controls.Canvas>, jeho pozadí změny barev. Kromě toho se vypočítává průměrné snímků za sekundu, na základě aktuální uplynulý čas a celkový počet vykreslené rámce.  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget2)]
 [!code-vb[CompositionTargetSample#CompositionTarget2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget2)]  
  
 Může se stát, že vlastní kreslení běží při různých rychlostech na různých počítačích. Důvodem je, že vlastní kreslení není obnovovací frekvence nezávislé. V závislosti na systému, kterou používáte a zatížením tohoto systému <xref:System.Windows.Media.CompositionTarget.Rendering> událost může být volána jiný počet za sekundu. Další informace o určování grafiky schopnost hardwaru a výkon pro zařízení se systémem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace, najdete v části [vrstev vykreslování grafiky](../../../../docs/framework/wpf/advanced/graphics-rendering-tiers.md).  
  
 Přidání nebo odebrání vykreslování <xref:System.EventHandler> delegáta, když se aktivuje událost se odloží až po dokončení událost aktivuje. To je konzistentní s postupy <xref:System.MulticastDelegate>-založené na události jsou zpracovávány v Common Language Runtime (CLR). Všimněte si také, že vykreslování události se nezaručuje, že má být volána v libovolném pořadí. Pokud máte více <xref:System.EventHandler> delegáti, které jsou závislé na konkrétní pořadí, byste měli zaregistrovat jedné <xref:System.Windows.Media.CompositionTarget.Rendering> událostí a multiplexovaný do delegáty ve správné pořadí sami.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.CompositionTarget>  
 [Přehled vykreslování grafiky WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)
