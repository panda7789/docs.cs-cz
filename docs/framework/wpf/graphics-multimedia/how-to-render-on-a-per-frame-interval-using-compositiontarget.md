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
ms.openlocfilehash: 8864204ccdd1e860cc910dfe8baa2f25edfb2fcc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956986"
---
# <a name="how-to-render-on-a-per-frame-interval-using-compositiontarget"></a>Postupy: Vykreslení intervalu podle snímků pomocí CompositionTarget
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Animační modul poskytuje mnoho funkcí pro vytváření animací založených na snímcích. Existují však scénáře aplikace, ve kterých potřebujete přesnější kontrolu nad vykreslováním jednotlivých snímků. <xref:System.Windows.Media.CompositionTarget> Objekt poskytuje možnost vytvářet vlastní animace na základě zpětného volání pro jednotlivé snímky.  
  
 <xref:System.Windows.Media.CompositionTarget>je statická třída, která představuje zobrazovací plochu, na které se vykreslí vaše aplikace. <xref:System.Windows.Media.CompositionTarget.Rendering> Událost je vyvolána pokaždé, když je vykreslena scéna aplikace. Frekvence snímků vykreslování je počet vykreslící scény za sekundu.  
  
> [!NOTE]
> Kompletní ukázku kódu použití <xref:System.Windows.Media.CompositionTarget>naleznete v tématu Using the [CompositionTarget Sample](https://go.microsoft.com/fwlink/?LinkID=160045).  
  
## <a name="example"></a>Příklad  
 Událost je aktivována [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] během procesu vykreslování. <xref:System.Windows.Media.CompositionTarget.Rendering> Následující příklad ukazuje, jak registrovat <xref:System.EventHandler> delegáta pro statickou <xref:System.Windows.Media.CompositionTarget.Rendering> metodu na <xref:System.Windows.Media.CompositionTarget>.  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget1](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget1)]
 [!code-vb[CompositionTargetSample#CompositionTarget1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget1)]  
  
 Můžete použít metodu obslužné rutiny události vykreslování k vytvoření vlastního obsahu výkresu. Tato metoda obslužné rutiny události se volá jednou pro každý snímek. Pokaždé, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] když se zachová trvalá data vykreslování ve vizuálním stromu napříč do grafu scény kompozice, je volána metoda obslužné rutiny události. Kromě toho, pokud změny ve vizuálním stromu vynutí aktualizace grafu scény, je volána také metoda obslužné rutiny události. Všimněte si, že vaše metoda obslužné rutiny události je volána po vypočítání rozložení. Můžete však upravit rozložení v metodě obslužné rutiny události, což znamená, že rozložení bude vypočítáno ještě více před vykreslením.  
  
 Následující příklad ukazuje, jak lze poskytnout vlastní vykreslování v <xref:System.Windows.Media.CompositionTarget> metodě obslužné rutiny události. V tomto případě <xref:System.Windows.Controls.Canvas> je barva pozadí vykreslena s hodnotou barvy v závislosti na poloze souřadnic myši. Pokud přesunete myš dovnitř <xref:System.Windows.Controls.Canvas>, změní se barva pozadí. Kromě toho se počítá průměrná frekvence snímků na základě aktuálního uplynulého času a celkového počtu vykreslených snímků.  
  
 [!code-csharp[CompositionTargetSample#CompositionTarget2](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositionTargetSample/CSharp/Window1.xaml.cs#compositiontarget2)]
 [!code-vb[CompositionTargetSample#CompositionTarget2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CompositionTargetSample/visualbasic/window1.xaml.vb#compositiontarget2)]  
  
 Můžete zjistit, že se vlastní výkres spouští na různých rychlostech v různých počítačích. Důvodem je to, že váš vlastní výkres není nezávisle na snímkovém poměru. V závislosti na systému, který používáte, a zatížení tohoto systému <xref:System.Windows.Media.CompositionTarget.Rendering> může být událost volána různě kolikrát za sekundu. Informace o určení schopnosti a výkonu hardwaru grafiky pro zařízení, na kterém běží [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace, najdete v tématu [vrstvy vykreslování grafiky](../advanced/graphics-rendering-tiers.md).  
  
 Přidání nebo odebrání delegáta <xref:System.EventHandler> vykreslování v době, kdy se událost vypíná, bude až do doby, kdy se událost dokončí, bude odložena. To je konzistentní s tím <xref:System.MulticastDelegate>, jak jsou zpracovávány události v modulu CLR (Common Language Runtime). Všimněte si také, že není zaručeno volání událostí vykreslování v žádném konkrétním pořadí. Pokud máte více <xref:System.EventHandler> delegátů, kteří spoléhají na konkrétní pořadí, měli byste zaregistrovat jednu <xref:System.Windows.Media.CompositionTarget.Rendering> událost a multiplexní delegáty ve správném pořadí.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.CompositionTarget>
- [Přehled vykreslování grafiky WPF](wpf-graphics-rendering-overview.md)
