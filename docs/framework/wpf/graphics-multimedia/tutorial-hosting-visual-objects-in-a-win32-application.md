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
ms.openlocfilehash: d04357e0770bbf8eebe8f40a86a19ddc9baae3ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187431"
---
# <a name="tutorial-hosting-visual-objects-in-a-win32-application"></a>Tutoriál: Hostování vizuální objektů v aplikaci Win32
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]poskytuje bohaté prostředí pro vytváření aplikací. Však pokud máte značné investice do kódu Win32, může [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] být efektivnější přidat funkce do aplikace, spíše než přepsat kód. Chcete-li poskytnout podporu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pro Win32 a grafické subsystémy používané současně v aplikaci, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje mechanismus pro hostování objektů v okně Win32.  
  
 Tento kurz popisuje, jak napsat ukázkovou aplikaci, [Test přístupů s ukázkou spolupráce Win32](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting), která hostuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vizuální objekty v okně Win32.  

<a name="requirements"></a>
## <a name="requirements"></a>Požadavky  
 Tento kurz předpokládá základní znalost obou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a Win32 programování. Základní úvod k [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programování najdete [v tématu Návod: Moje první desktopová aplikace WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md). Pro úvod do Win32 programování, viz některý z mnoha knih na toto téma, zejména *programování Windows* Charles Petzold.  
  
> [!NOTE]
> Tento kurz obsahuje řadu příkladů kódu z přidružené ukázky. Pro čitelnost však neobsahuje úplný ukázkový kód. Úplný ukázkový kód naleznete v tématu [Test přístupů s ukázkou spolupráce win32](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting).  
  
<a name="creating_the_host_win32_window"></a>
## <a name="creating-the-host-win32-window"></a>Vytvoření okna win32 hostitele  
 Klíčem k [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hostování objektů v okně Win32 je <xref:System.Windows.Interop.HwndSource> třída. Tato třída zalomí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objekty v okně Win32, což [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] umožňuje jejich začlenění do okna jako podřízené.  
  
 Následující příklad ukazuje kód pro <xref:System.Windows.Interop.HwndSource> vytvoření objektu jako okno kontejneru Win32 pro vizuální objekty. Chcete-li nastavit styl okna, pozici a další parametry pro <xref:System.Windows.Interop.HwndSourceParameters> okno Win32, použijte objekt.  
  
 [!code-csharp[VisualsHitTesting#101](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#101)]
 [!code-vb[VisualsHitTesting#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#101)]  
  
> [!NOTE]
> Hodnotu vlastnosti <xref:System.Windows.Interop.HwndSourceParameters.ExtendedWindowStyle%2A> nelze nastavit na WS_EX_TRANSPARENT. To znamená, že okno hostitele Win32 nemůže být průhledné. Z tohoto důvodu je barva pozadí okna hostitele Win32 nastavena na stejnou barvu pozadí jako nadřazené okno.  
  
<a name="adding_visual_objects_to_the_host_win32_window"></a>
## <a name="adding-visual-objects-to-the-host-win32-window"></a>Přidání vizuálních objektů do okna win32 hostitele  
 Jakmile jste vytvořili okno kontejneru hostitele Win32 pro vizuální objekty, můžete do něj přidat vizuální objekty. Budete chtít zajistit, aby všechny transformace vizuální objekty, jako jsou animace, nepřesahují hranice ohraničující obdélník okna hostitele Win32.  
  
 Následující příklad ukazuje kód pro <xref:System.Windows.Interop.HwndSource> vytvoření objektu a přidání vizuálních objektů do něj.  
  
> [!NOTE]
> Vlastnost <xref:System.Windows.Interop.HwndSource.RootVisual%2A> objektu <xref:System.Windows.Interop.HwndSource> je nastavena na první vizuální objekt přidaný do okna hostitele Win32. Kořenový vizuální objekt definuje uzel zcela nahoře ve stromu vizuálních objektů. Všechny následné vizuální objekty přidané do okna hostitele Win32 jsou přidány jako podřízené objekty.  
  
 [!code-csharp[VisualsHitTesting#100](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#100)]
 [!code-vb[VisualsHitTesting#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#100)]  
  
<a name="implementing_the_win32_message_filter"></a>
## <a name="implementing-the-win32-message-filter"></a>Implementace filtru zpráv win32  
 Okno hostitele Win32 pro vizuální objekty vyžaduje proceduru filtru zpráv okna pro zpracování zpráv, které jsou odeslány do okna z fronty aplikací. Procedura okna přijímá zprávy ze systému Win32. Mohou to být vstupní zprávy nebo zprávy správy oken. Volitelně můžete zpracovat zprávu v procedurě okna nebo předat zprávu systému pro výchozí zpracování.  
  
 Objekt, <xref:System.Windows.Interop.HwndSource> který jste definovali jako nadřazený objekt pro vizuální objekty, musí odkazovat na proceduru filtru zprávy okna, kterou zadáte. Při vytváření <xref:System.Windows.Interop.HwndSource> objektu nastavte <xref:System.Windows.Interop.HwndSourceParameters.HwndSourceHook%2A> vlastnost tak, aby odkazovala na proceduru okna.  
  
 [!code-csharp[VisualsHitTesting#102](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#102)]
 [!code-vb[VisualsHitTesting#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#102)]  
  
 Následující příklad ukazuje kód pro zpracování levé a pravé tlačítko myši nahoru zprávy. Hodnota souřadnice pozice zásahu myši je `lParam` obsažena v hodnotě parametru.  
  
 [!code-csharp[VisualsHitTesting#103](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
<a name="processing_the_win32_messages"></a>
## <a name="processing-the-win32-messages"></a>Zpracování zpráv Win32  
 Kód v následujícím příkladu ukazuje, jak se provádí test přístupů proti hierarchii vizuálních objektů obsažených v okně hostitele Win32. Můžete určit, zda je bod v rámci geometrie <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> vizuálního objektu, pomocí metody k určení kořenového vizuálního objektu a hodnoty souřadnic, proti které má být možné testovat. V tomto případě kořenový vizuální objekt <xref:System.Windows.Interop.HwndSource.RootVisual%2A> je hodnota <xref:System.Windows.Interop.HwndSource> vlastnosti objektu.  
  
 [!code-csharp[VisualsHitTesting#104](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 Další informace o testování přístupů proti vizuální objekty, naleznete [v tématu Testování přístupů ve vizuální vrstvě](hit-testing-in-the-visual-layer.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Interop.HwndSource>
- [Test přístupů s ukázkou spolupráce win32](https://github.com/microsoft/WPF-Samples/tree/master/Visual%20Layer/VisualsHitTesting)
- [Ověřování pozice ve vizuální vrstvě](hit-testing-in-the-visual-layer.md)
