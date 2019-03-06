---
title: 'Kurz: Hostování vizuální objektů v aplikaci Win32'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- visual objects in Win32 code [WPF]
- Win32 code [WPF], visual objects in
- hosting [WPF], visual objects in Win32 code
ms.assetid: f0e1600c-3217-43d5-875d-1864fa7fe628
ms.openlocfilehash: 68241d679b0f788423b09badfa549a660da0d106
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377253"
---
# <a name="tutorial-hosting-visual-objects-in-a-win32-application"></a>Kurz: Hostování vizuální objektů v aplikaci Win32
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje bohaté prostředí pro vytváření aplikací. Pokud však máte značné investice [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] kódu, může být mnohem efektivnější přidat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkce, které vaše aplikace místo revize kódu. K zajištění podpory pro [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] subsystémy grafiky v aplikaci používat současně [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje mechanismus pro hostování objektů v [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna.  
  
 Tento kurz popisuje, jak psát ukázkovou aplikaci, [spuštění testu s ukázkou Win32 vzájemná spolupráce grafického subsystému](https://go.microsoft.com/fwlink/?LinkID=159995), že hostitelé [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] visual objekty v [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno.  
  

  
<a name="requirements"></a>   
## <a name="requirements"></a>Požadavky  
 V tomto kurzu se předpokládá základní znalost obou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programování. Pro základní informace o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programování, naleznete v tématu [názorný postup: Moje první desktopová aplikace WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md). Úvod do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programování, naleznete v některém z mnoha knihy k tomuto tématu, zejména *programování Windows* podle Charles Petzold.  
  
> [!NOTE]
>  Tento kurz obsahuje některé příklady kódů z přidružené ukázkové. Ale pro lepší čitelnost, neobsahuje úplnou ukázku kódu. Úplný ukázkový kód, naleznete v tématu [spuštění testu s ukázkou vzájemná spolupráce grafického subsystému Win32](https://go.microsoft.com/fwlink/?LinkID=159995).  
  
<a name="creating_the_host_win32_window"></a>   
## <a name="creating-the-host-win32-window"></a>Vytvoření okna hostitele Win32  
 Klíčem k hostování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objekty v [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] je okno <xref:System.Windows.Interop.HwndSource> třídy. Zabalí tuto třídu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objekty v [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno, kterým má být zahrnut do vaší [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] jako podřízeného okna.  
  
 Následující příklad ukazuje kód pro vytvoření <xref:System.Windows.Interop.HwndSource> objektu jako [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno kontejner pro vizuální objekty. Chcete-li nastavit styl okna, umístění a dalších parametrů pro [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno, použijte <xref:System.Windows.Interop.HwndSourceParameters> objektu.  
  
 [!code-csharp[VisualsHitTesting#101](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#101)]
 [!code-vb[VisualsHitTesting#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#101)]  
  
> [!NOTE]
>  Hodnota <xref:System.Windows.Interop.HwndSourceParameters.ExtendedWindowStyle%2A> WS_EX_TRANSPARENT nelze nastavit vlastnost. To znamená, že hostitel [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno nemůže být průhledná. Z tohoto důvodu barvu pozadí hostitele [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno bude nastaveno na stejnou barvu pozadí jako jeho nadřazenému oknu.  
  
<a name="adding_visual_objects_to_the_host_win32_window"></a>   
## <a name="adding-visual-objects-to-the-host-win32-window"></a>Přidání vizuální objekty do okna hostitele Win32  
 Po vytvoření hostitele [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno kontejner pro vizuální objekty, budete do něj přidávat vizuální objekty. Budete chtít zajistit, že všechny transformace vizuální objekty, jako je například animace, ne přesáhne hranice hostitele [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno ohraničovacího rámečku.  
  
 Následující příklad ukazuje kód pro vytvoření <xref:System.Windows.Interop.HwndSource> objekt a přidání vizuálních objektů do něj.  
  
> [!NOTE]
>  <xref:System.Windows.Interop.HwndSource.RootVisual%2A> Vlastnost <xref:System.Windows.Interop.HwndSource> je nastaven na první vizuální objekty přidány do hostitele [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna. Kořenový objekt visual definuje nejvyšší uzel stromu vizuální objekty. Všechny následné vizuální objekty přidané do hostitele [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna jsou přidány jako podřízené objekty.  
  
 [!code-csharp[VisualsHitTesting#100](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#100)]
 [!code-vb[VisualsHitTesting#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#100)]  
  
<a name="implementing_the_win32_message_filter"></a>   
## <a name="implementing-the-win32-message-filter"></a>Implementace filtru zpráv Win32  
 Hostitel [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno pro vizuální objekty vyžaduje procedury filtru zprávy okna pro zpracování zprávy z fronty aplikace odeslané do okna. Proceduru okna přijímá zprávy z [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] systému. Může to být vstupní zprávy nebo zprávy okna správy. Volitelně můžete zpracovávat zprávy v okně procedury nebo předat zprávu systému pro výchozí zpracování.  
  
 <xref:System.Windows.Interop.HwndSource> Objekt, který jste definovali jako nadřazený pro vizuální objekty musí odkazovat na procedury filtru zprávy okna je zadat. Při vytváření <xref:System.Windows.Interop.HwndSource> objektu, nastaven <xref:System.Windows.Interop.HwndSourceParameters.HwndSourceHook%2A> vlastnost tak, aby odkazovaly proceduru okna.  
  
 [!code-csharp[VisualsHitTesting#102](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#102)]
 [!code-vb[VisualsHitTesting#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#102)]  
  
 Následující příklad ukazuje kód pro ošetření tlačítka myši doleva a doprava nahoru zprávy. Hodnotu souřadnice myši přístupů pozice je obsažen v hodnotě `lParam` parametru.  
  
 [!code-csharp[VisualsHitTesting#103](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
<a name="processing_the_win32_messages"></a>   
## <a name="processing-the-win32-messages"></a>Zpracování zpráv systému Win32  
 Kód v následujícím příkladu ukazuje, jak se provádí ověření pozice na hierarchii vizuální objekty obsažené v hostiteli [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna. Můžete určit, jestli je bod v rámci geometrie vizuální objekty s použitím <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody k určení visual kořenový objekt a pro spuštění testu oproti souřadnic hodnotu. V tomto případě visual kořenový objekt je hodnota <xref:System.Windows.Interop.HwndSource.RootVisual%2A> vlastnost <xref:System.Windows.Interop.HwndSource> objektu.  
  
 [!code-csharp[VisualsHitTesting#104](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 Další informace o volání testování proti vizuálních objektů najdete v tématu [spuštění testování ve vizuální vrstvě](hit-testing-in-the-visual-layer.md).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Interop.HwndSource>
- [Spuštění testu s ukázkou Win32 vzájemné spolupráce](https://go.microsoft.com/fwlink/?LinkID=159995)
- [Ověřování pozice ve vizuální vrstvě](hit-testing-in-the-visual-layer.md)
