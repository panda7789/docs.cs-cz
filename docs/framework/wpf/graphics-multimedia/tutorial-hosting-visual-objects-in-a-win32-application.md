---
title: "Tutoriál: Hostování vizuální objektů v aplikaci Win32"
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
- visual objects in Win32 code [WPF]
- Win32 code [WPF], visual objects in
- hosting [WPF], visual objects in Win32 code
ms.assetid: f0e1600c-3217-43d5-875d-1864fa7fe628
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 753e55e644a9edea90a0a034ba2930473ef53f61
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="tutorial-hosting-visual-objects-in-a-win32-application"></a>Tutoriál: Hostování vizuální objektů v aplikaci Win32
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]poskytuje bohaté prostředí pro vytváření aplikací. Pokud však máte významné investice [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] kódu, může být efektivnější přidat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkce do vaší aplikace místo přepisu kódu. Kvůli zajištění podpory pro [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] grafiky subsystémy používat současně v aplikaci, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje mechanismus pro hostování objekty v [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno.  
  
 Tento kurz popisuje, jak psát ukázkové aplikace, [stiskněte tlačítko Test s ukázkou vzájemná spolupráce Win32](http://go.microsoft.com/fwlink/?LinkID=159995), že hostitelé [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] visual objekty v [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno.  
  

  
<a name="requirements"></a>   
## <a name="requirements"></a>Požadavky  
 Tento kurz předpokládá základní znalost obou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programování. Pro základní informace o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programování, najdete v části [návod: Můj první desktopová aplikace WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md). Úvod do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programování, zobrazit žádné množství knih na subjektu, zejména *programování Windows* podle Charlese Petzold.  
  
> [!NOTE]
>  Tento kurz zahrnuje několik příklady kódu z přidružených ukázky. Ale čitelnější neobsahuje úplný ukázkový kód. Úplný ukázkový kód, najdete v části [stiskněte tlačítko Test s ukázkou vzájemná spolupráce Win32](http://go.microsoft.com/fwlink/?LinkID=159995).  
  
<a name="creating_the_host_win32_window"></a>   
## <a name="creating-the-host-win32-window"></a>Vytvoření okna Win32 hostitele  
 Klíč k hostování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objekty v [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] je okno <xref:System.Windows.Interop.HwndSource> třídy. Tato třída zabalí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objekty v [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna, což jim umožní začlenit do vaší [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] jako podřízeného okna.  
  
 Následující příklad ukazuje kód pro vytvoření <xref:System.Windows.Interop.HwndSource> objekt jako [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna kontejner pro vizuální objekty. Nastavit okno styl, pozice a další parametry [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna, použijte <xref:System.Windows.Interop.HwndSourceParameters> objektu.  
  
 [!code-csharp[VisualsHitTesting#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#101)]
 [!code-vb[VisualsHitTesting#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#101)]  
  
> [!NOTE]
>  Hodnota <xref:System.Windows.Interop.HwndSourceParameters.ExtendedWindowStyle%2A> vlastnost nelze nastavit na ws_ex_transparent –. To znamená, že hostitel [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna nesmí být průhledná. Z tohoto důvodu barvu pozadí hostitele [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno bude nastaveno na barvu pozadí jako jeho nadřazeného okna.  
  
<a name="adding_visual_objects_to_the_host_win32_window"></a>   
## <a name="adding-visual-objects-to-the-host-win32-window"></a>Přidání vizuální objekty do okna hostitele Win32  
 Po vytvoření hostitele [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno kontejner pro vizuální objekty, můžete do něj může přidat vizuální objekty. Budete chtít zajistit všechny transformace vizuální objekty, jako je například animací, se netýkají za hranice hostitele [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno je ohraničujícího rámečku.  
  
 Následující příklad ukazuje kód pro vytvoření <xref:System.Windows.Interop.HwndSource> objektu a přidání vizuální objekty na ni.  
  
> [!NOTE]
>  <xref:System.Windows.Interop.HwndSource.RootVisual%2A> Vlastnost <xref:System.Windows.Interop.HwndSource> objektu je nastavena na první visual objekt přidaný do hostitele [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno. Kořenový objekt visual definuje nejvyšší uzel stromu vizuální objekt. Všechny následné visual objektů přidaných do hostitele [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna jsou přidány jako podřízené objekty.  
  
 [!code-csharp[VisualsHitTesting#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#100)]
 [!code-vb[VisualsHitTesting#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#100)]  
  
<a name="implementing_the_win32_message_filter"></a>   
## <a name="implementing-the-win32-message-filter"></a>Implementace filtr zpráv Win32  
 Hostitel [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna pro vizuální objekty vyžaduje procedury filtru zprávy okna pro zpracování zprávy, které se odesílají do okna z fronty aplikace. Postup okno přijímá zprávy z [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] systému. To může být vstupní zprávy nebo Správa oken zpráv. Volitelně můžete zpracovat zprávu v postupu vaší okno nebo předat systému pro výchozí zpracování zprávy.  
  
 <xref:System.Windows.Interop.HwndSource> Objekt, který je definován jako nadřazeného prvku pro vizuální objekty musí odkazovat procedury filtru zpráv okno zadáte. Při vytváření <xref:System.Windows.Interop.HwndSource> objektu, nastavte <xref:System.Windows.Interop.HwndSourceParameters.HwndSourceHook%2A> vlastnost tak, aby odkazovaly procedury okna.  
  
 [!code-csharp[VisualsHitTesting#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#102)]
 [!code-vb[VisualsHitTesting#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#102)]  
  
 Následující příklad ukazuje kód pro ošetření tlačítka vlevo a vpravo myši nahoru zprávy. Souřadnice hodnotu myš, stiskněte tlačítko pozice se nachází v hodnotě `lParam` parametr.  
  
 [!code-csharp[VisualsHitTesting#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyWindow.cs#103)]
 [!code-vb[VisualsHitTesting#103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyWindow.vb#103)]  
  
<a name="processing_the_win32_messages"></a>   
## <a name="processing-the-win32-messages"></a>Zpracování zpráv Win32  
 Kód v následujícím příkladu ukazuje, jak se provádí ověření pozice proti hierarchii visual objekty obsažené v hostiteli [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno. Zjistíte, zda bod je v rámci geometrie vizuální objekt pomocí <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metodu zadejte kořenový objekt visual a souřadnic hodnotu narazí testovací proti. V takovém případě je kořenový objekt visual hodnota <xref:System.Windows.Interop.HwndSource.RootVisual%2A> vlastnost <xref:System.Windows.Interop.HwndSource> objektu.  
  
 [!code-csharp[VisualsHitTesting#104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsHitTesting/CSharp/MyCircle.cs#104)]
 [!code-vb[VisualsHitTesting#104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsHitTesting/VisualBasic/MyCircle.vb#104)]  
  
 Další informace o počtu testování proti vizuální objekty najdete v tématu [dosáhl testování ve vrstvě Visual](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Interop.HwndSource>  
 [Stiskněte tlačítko Test s ukázkou součinnosti Win32](http://go.microsoft.com/fwlink/?LinkID=159995)  
 [Ověřování pozice ve vizuální vrstvě](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)
