---
title: 'Kurz: Hostování vizuálních objektů v aplikaci Win32'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- visual objects in Win32 code [WPF]
- Win32 code [WPF], visual objects in
- hosting [WPF], visual objects in Win32 code
ms.assetid: f0e1600c-3217-43d5-875d-1864fa7fe628
ms.openlocfilehash: c8baefbf01467a65626a77f300f34a145d5c7281
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962878"
---
# <a name="tutorial-hosting-visual-objects-in-a-win32-application"></a>Kurz: Hostování vizuálních objektů v aplikaci Win32
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]poskytuje bohatý prostředí pro vytváření aplikací. Nicméně pokud máte významnou investici do [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] kódu, může být efektivnější přidat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkce do aplikace namísto přepisu kódu. Chcete-li poskytnout [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] podporu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a subsystémy grafiky používané současně v aplikaci, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] poskytuje mechanismus pro hostování objektů v okně.  
  
 V tomto kurzu se dozvíte, jak napsat ukázkovou aplikaci, spustit [test s ukázkou meziprovozu Win32](https://go.microsoft.com/fwlink/?LinkID=159995), který [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hostuje [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] vizuální objekty v okně.  

<a name="requirements"></a>   
## <a name="requirements"></a>Požadavky  
 V tomto kurzu se [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] předpokládá základní znalost i programování. Základní Úvod do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programování naleznete v tématu [Návod: Moje první desktopová aplikace](../getting-started/walkthrough-my-first-wpf-desktop-application.md)WPF. Úvod do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programování naleznete v libovolné řadě knih v předmětu, zejména v *oknech programování* podle Charles Petzold.  
  
> [!NOTE]
> Tento kurz obsahuje několik příkladů kódu z přidruženého vzorku. Pro čitelnost ale nezahrnuje kompletní vzorový kód. Úplný vzorový kód naleznete v tématu [test volání s ukázkou meziprovozu Win32](https://go.microsoft.com/fwlink/?LinkID=159995).  
  
<a name="creating_the_host_win32_window"></a>   
## <a name="creating-the-host-win32-window"></a>Vytvoření hostitelského okna systému Win32  
 Klíč pro hostování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objektů [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] v okně je <xref:System.Windows.Interop.HwndSource> třída. Tato třída obaluje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objekty [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] v okně, což umožňuje jejich zahrnutí do vašeho [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] podřízeného okna.  
  
 Následující příklad ukazuje kód pro vytvoření <xref:System.Windows.Interop.HwndSource> objektu [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] jako okno kontejneru pro vizuální objekty. Chcete-li nastavit styl okna, umístění a další parametry [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna, <xref:System.Windows.Interop.HwndSourceParameters> použijte objekt.  
  
 [!code-csharp[VisualsHitTesting#101](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#101)]
 [!code-vb[VisualsHitTesting#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#101)]  
  
> [!NOTE]
> Hodnotu <xref:System.Windows.Interop.HwndSourceParameters.ExtendedWindowStyle%2A> vlastnosti nelze nastavit na WS_EX_TRANSPARENT. To znamená, že hostitelské [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno nemůže být transparentní. Z tohoto důvodu je barva pozadí okna hostitele [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] nastavena na stejnou barvu pozadí jako své nadřazené okno.  
  
<a name="adding_visual_objects_to_the_host_win32_window"></a>   
## <a name="adding-visual-objects-to-the-host-win32-window"></a>Přidání vizuálních objektů do hostitelského okna systému Win32  
 Po vytvoření hostitelského [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna kontejneru pro objekty vizuálu můžete do něj přidat vizuální objekty. Budete chtít zajistit, aby všechny transformace vizuálních objektů, jako jsou animace, nerozšířily hranice ohraničujícího obdélníku hostitelského [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna.  
  
 Následující příklad ukazuje kód pro vytvoření <xref:System.Windows.Interop.HwndSource> objektu a přidání vizuálních objektů do něj.  
  
> [!NOTE]
> Vlastnost objektu je nastavena na první vizuální objekt přidaný do okna hostitele [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]. <xref:System.Windows.Interop.HwndSource.RootVisual%2A> <xref:System.Windows.Interop.HwndSource> Kořenový vizuální objekt definuje uzel ve stromové struktuře vizuálního objektu nejvíce nahoře. Všechny následné vizuální objekty přidané do hostitelského [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna jsou přidány jako podřízené objekty.  
  
 [!code-csharp[VisualsHitTesting#100](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#100)]
 [!code-vb[VisualsHitTesting#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#100)]  
  
<a name="implementing_the_win32_message_filter"></a>   
## <a name="implementing-the-win32-message-filter"></a>Implementace filtru zpráv Win32  
 Okno hostitelů [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] pro vizuální objekty vyžaduje postup filtru zprávy okna, který zpracovává zprávy odesílané do okna z fronty aplikace. Procedura okna přijímá zprávy ze [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] systému. Můžou to být vstupní zprávy nebo zprávy správy oken. Volitelně můžete zpracovat zprávu v proceduře okna nebo předat systému zprávu pro výchozí zpracování.  
  
 <xref:System.Windows.Interop.HwndSource> Objekt, který jste definovali jako nadřízený pro vizuální objekty, musí odkazovat na proceduru filtru zprávy okna, kterou zadáte. Při vytváření <xref:System.Windows.Interop.HwndSource> objektu <xref:System.Windows.Interop.HwndSourceParameters.HwndSourceHook%2A> nastavte vlastnost na odkaz na proceduru okna.  
  
 [!code-csharp[VisualsHitTesting#102](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#102)]
 [!code-vb[VisualsHitTesting#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#102)]  
  
 Následující příklad ukazuje kód pro zpracování zpráv levého a pravého tlačítka myši. Hodnota souřadnic pozice kurzoru myši je obsažena v hodnotě `lParam` parametru.  
  
 [!code-csharp[VisualsHitTesting#103](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
<a name="processing_the_win32_messages"></a>   
## <a name="processing-the-win32-messages"></a>Zpracování zpráv Win32  
 Kód v následujícím příkladu ukazuje, jak je proveden test volání proti hierarchii vizuálních objektů obsažených v hostitelském [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okně. Můžete určit, zda je bod v geometrii vizuálního objektu, pomocí <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody pro určení kořenového vizuálního objektu a hodnoty souřadnice pro dosažení testu. V tomto případě je kořenový objekt vizuálu hodnotou <xref:System.Windows.Interop.HwndSource.RootVisual%2A> vlastnosti <xref:System.Windows.Interop.HwndSource> objektu.  
  
 [!code-csharp[VisualsHitTesting#104](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 Další informace o testování přístupů u vizuálních objektů naleznete v tématu [testování přístupů ve vizuální vrstvě](hit-testing-in-the-visual-layer.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Interop.HwndSource>
- [Test volání s ukázkovou meziprovozu Win32](https://go.microsoft.com/fwlink/?LinkID=159995)
- [Ověřování pozice ve vizuální vrstvě](hit-testing-in-the-visual-layer.md)
