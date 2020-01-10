---
title: 'Tutoriál: Hostování vizuální objektů v aplikaci Win32'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- visual objects in Win32 code [WPF]
- Win32 code [WPF], visual objects in
- hosting [WPF], visual objects in Win32 code
ms.assetid: f0e1600c-3217-43d5-875d-1864fa7fe628
ms.openlocfilehash: 621684e14f9d1b599c4ef60e3731f0f58f31aacd
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740158"
---
# <a name="tutorial-hosting-visual-objects-in-a-win32-application"></a>Tutoriál: Hostování vizuální objektů v aplikaci Win32
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje bohatou prostředí pro vytváření aplikací. Nicméně pokud máte významnou investici do kódu Win32, může být efektivnější přidat funkce [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do aplikace namísto přepisu kódu. Pro zajištění podpory pro systémy Win32 a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] grafické subsystémy, které se používají současně v aplikaci, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje mechanismus pro hostování objektů v okně Win32.  
  
 V tomto kurzu se dozvíte, jak napsat ukázkovou aplikaci, spustit [test s ukázkou meziprovozu Win32](https://go.microsoft.com/fwlink/?LinkID=159995), který hostuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vizuální objekty v okně Win32.  

<a name="requirements"></a>   
## <a name="requirements"></a>Požadavky  
 V tomto kurzu se předpokládá základní znalost jak pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], tak pro programování v prostředí Win32. Základní úvodní informace o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programování naleznete v tématu [Návod: Moje první desktopová aplikace WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md). Úvod do programování v systému Win32 najdete v jakékoli z mnoha knih v předmětu, zejména v *oknech programování* podle Charles Petzold.  
  
> [!NOTE]
> Tento kurz obsahuje několik příkladů kódu z přidruženého vzorku. Pro čitelnost ale nezahrnuje kompletní vzorový kód. Úplný vzorový kód naleznete v tématu [test volání s ukázkou meziprovozu Win32](https://go.microsoft.com/fwlink/?LinkID=159995).  
  
<a name="creating_the_host_win32_window"></a>   
## <a name="creating-the-host-win32-window"></a>Vytvoření hostitelského okna systému Win32  
 Klíč pro hostování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objektů v okně Win32 je třída <xref:System.Windows.Interop.HwndSource>. Tato třída zalomí objekty [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v okně Win32 a umožňuje jejich zahrnutí do [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] jako podřízené okno.  
  
 Následující příklad ukazuje kód pro vytvoření objektu <xref:System.Windows.Interop.HwndSource> jako okno kontejneru Win32 pro vizuální objekty. Chcete-li nastavit styl okna, umístění a další parametry okna Win32, použijte objekt <xref:System.Windows.Interop.HwndSourceParameters>.  
  
 [!code-csharp[VisualsHitTesting#101](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#101)]
 [!code-vb[VisualsHitTesting#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#101)]  
  
> [!NOTE]
> Hodnotu vlastnosti <xref:System.Windows.Interop.HwndSourceParameters.ExtendedWindowStyle%2A> nelze nastavit na WS_EX_TRANSPARENT. To znamená, že hostitelské okno Win32 nemůže být transparentní. Z tohoto důvodu je barva pozadí okna hostitele systému Win32 nastavena na stejnou barvu pozadí jako své nadřazené okno.  
  
<a name="adding_visual_objects_to_the_host_win32_window"></a>   
## <a name="adding-visual-objects-to-the-host-win32-window"></a>Přidání vizuálních objektů do hostitelského okna systému Win32  
 Po vytvoření hostitelského okna kontejneru Win32 pro vizuální objekty můžete do něj přidat vizuální objekty. Budete chtít zajistit, aby všechny transformace vizuálních objektů, jako jsou animace, nerozšířily hranice ohraničujícího obdélníku okna hostitele v systému Win32.  
  
 Následující příklad ukazuje kód pro vytvoření objektu <xref:System.Windows.Interop.HwndSource> a přidání vizuálních objektů do něj.  
  
> [!NOTE]
> Vlastnost <xref:System.Windows.Interop.HwndSource.RootVisual%2A> objektu <xref:System.Windows.Interop.HwndSource> je nastavena na první vizuální objekt přidaný do okna hostitele Win32. Kořenový vizuální objekt definuje uzel ve stromové struktuře vizuálního objektu nejvíce nahoře. Všechny následné vizuální objekty přidané do okna hostitele Win32 jsou přidány jako podřízené objekty.  
  
 [!code-csharp[VisualsHitTesting#100](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#100)]
 [!code-vb[VisualsHitTesting#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#100)]  
  
<a name="implementing_the_win32_message_filter"></a>   
## <a name="implementing-the-win32-message-filter"></a>Implementace filtru zpráv Win32  
 Okno hostitelského systému Win32 pro vizuální objekty vyžaduje postup filtru zprávy okna, který zpracovává zprávy odesílané do okna z fronty aplikace. Procedura okna přijímá zprávy ze systému Win32. Můžou to být vstupní zprávy nebo zprávy správy oken. Volitelně můžete zpracovat zprávu v proceduře okna nebo předat systému zprávu pro výchozí zpracování.  
  
 Objekt <xref:System.Windows.Interop.HwndSource>, který jste definovali jako nadřízený pro vizuální objekty, musí odkazovat na proceduru filtru zprávy okna, kterou zadáte. Při vytváření objektu <xref:System.Windows.Interop.HwndSource> nastavte vlastnost <xref:System.Windows.Interop.HwndSourceParameters.HwndSourceHook%2A> na odkaz na proceduru okna.  
  
 [!code-csharp[VisualsHitTesting#102](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#102)]
 [!code-vb[VisualsHitTesting#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#102)]  
  
 Následující příklad ukazuje kód pro zpracování zpráv levého a pravého tlačítka myši. Hodnota souřadnic pozice kurzoru myši je obsažena v hodnotě parametru `lParam`.  
  
 [!code-csharp[VisualsHitTesting#103](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
<a name="processing_the_win32_messages"></a>   
## <a name="processing-the-win32-messages"></a>Zpracování zpráv Win32  
 Kód v následujícím příkladu ukazuje, jak je proveden test volání proti hierarchii vizuálních objektů obsažených v hostitelském okně systému Win32. Můžete určit, zda je bod v geometrii vizuálního objektu, pomocí metody <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> pro určení kořenového vizuálního objektu a hodnoty souřadnice pro dosažení testu. V tomto případě je kořenový objekt vizuálu hodnotou vlastnosti <xref:System.Windows.Interop.HwndSource.RootVisual%2A> objektu <xref:System.Windows.Interop.HwndSource>.  
  
 [!code-csharp[VisualsHitTesting#104](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 Další informace o testování přístupů u vizuálních objektů naleznete v tématu [testování přístupů ve vizuální vrstvě](hit-testing-in-the-visual-layer.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Interop.HwndSource>
- [Test volání s ukázkovou meziprovozu Win32](https://go.microsoft.com/fwlink/?LinkID=159995)
- [Ověřování pozice ve vizuální vrstvě](hit-testing-in-the-visual-layer.md)
