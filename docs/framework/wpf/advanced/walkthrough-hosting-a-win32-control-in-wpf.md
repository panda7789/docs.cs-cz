---
title: "Návod: Hostování ovládacího prvku Win32 v subsystému WPF"
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
- hosting Win32 control in WPF [WPF]
- Win32 code [WPF], WPF interoperation
ms.assetid: a676b1eb-fc55-4355-93ab-df840c41cea0
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0795875b4d5f1a91b7c570320acb078b845ae712
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-hosting-a-win32-control-in-wpf"></a>Návod: Hostování ovládacího prvku Win32 v subsystému WPF
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]poskytuje bohaté prostředí pro vytváření aplikací. Pokud však máte významné investice [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] kódu, může být efektivnější opakovaně používat alespoň některé tohoto kódu vaší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace místo přepisování je zcela. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Poskytuje přehledné mechanismus pro hostování [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stránky.  
  
 Toto téma vás provede aplikace, [hostování Win32 ListBox – ovládací prvek v ukázce WPF](http://go.microsoft.com/fwlink/?LinkID=159998), že hostitelů [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] seznamu ovládacích prvků pole. Tento obecný postup je možné rozšířit na hostování žádné [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno.  
  
  
<a name="requirements"></a>   
## <a name="requirements"></a>Požadavky  
 Toto téma předpokládá základní znalost obou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programování. Pro základní informace o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programování, najdete v části [Začínáme](../../../../docs/framework/wpf/getting-started/index.md). Úvod do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programování, by měl odkazujete některé z mnoha knih na subjektu, zejména *programování Windows* podle Charlese Petzold.  
  
 Protože vzorku, který doprovází toto téma je implementována ve [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)], ho využívá [!INCLUDE[TLA#tla_pinvoke](../../../../includes/tlasharptla-pinvoke-md.md)] k přístupu [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]. Některé znalost [!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)] je užitečné, ale není nezbytné.  
  
> [!NOTE]
>  Toto téma obsahuje některé příklady kódu z přidružených ukázky. Ale čitelnější neobsahuje úplný ukázkový kód. Můžete získat nebo zobrazit kompletní kód z [hostování Win32 ListBox – ovládací prvek v ukázce WPF](http://go.microsoft.com/fwlink/?LinkID=159998).  
  
<a name="basic_procedure"></a>   
## <a name="the-basic-procedure"></a>Základní postup  
 Tato část popisuje základní postup pro hostování [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stránky. Zbývající části projít podrobné informace o jednotlivých kroků.  
  
 Základní postup hostování je:  
  
1.  Implementace [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stránky pro hostování okna. Je vytvoření jednoho technika <xref:System.Windows.Controls.Border> element můžete vyhradit oddíl stránky pro hostované okno.  
  
2.  Implementace třídy pro hostování ovládacího prvku, který dědí z <xref:System.Windows.Interop.HwndHost>.  
  
3.  V této třídě přepsat <xref:System.Windows.Interop.HwndHost> člen třídy <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>.  
  
4.  Vytvoření okna hostované jako podřízeného okna, který obsahuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stránky. I když konvenční [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programování není nutné explicitně provádět jeho použití, hostování stránka je okno s popisovačem (HWND). Se zobrazí stránka HWND prostřednictvím `hwndParent` parametr <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A> metoda. Okno hostované by se vytvořit jako podřízený tento HWND.  
  
5.  Po vytvoření okna hostitele vrátí HWND hostované okna. Pokud chcete hostovat jeden nebo více [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ovládací prvky, obvykle vytvoříte okno hostitele jako podřízenou HWND a zkontrolujte podřízených ovládacích prvků okna tohoto hostitele. Obtékání ovládacích prvků v okně hostitel poskytuje jednoduchý způsob, jak vaše [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stránky pro příjem oznámení z ovládacích prvků, které se zabývá některé konkrétní [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] problémy s oznámeními přes hranice HWND.  
  
6.  Zpracování vybrané zprávy odeslané do okna hostitele, jako je například oznámení z podřízených ovládacích prvků. Chcete-li to provést dvěma způsoby.  
  
    -   Pokud dáváte přednost zpracování zpráv v hostující třídy, mají přednost před <xref:System.Windows.Interop.HwndHost.WndProc%2A> metodu <xref:System.Windows.Interop.HwndHost> třídy.  
  
    -   Pokud chcete, aby [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zpracování zprávy, zpracování <xref:System.Windows.Interop.HwndHost> třída <xref:System.Windows.Interop.HwndHost.MessageHook> událostí ve vašem kódu. Pro každou zprávu, která přijme okno hostované dojde k této události. Pokud zvolíte tuto možnost, je nutné přepsat <xref:System.Windows.Interop.HwndHost.WndProc%2A>, ale stačí pouze minimální implementaci.  
  
7.  Přepsání <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> a <xref:System.Windows.Interop.HwndHost.WndProc%2A> metody <xref:System.Windows.Interop.HwndHost>. Je nutné přepsat tyto metody, které by vyhovovaly <xref:System.Windows.Interop.HwndHost> kontrakt, ale může stačí zadat minimální implementaci.  
  
8.  V souboru kódu na pozadí, vytvoření instance třídy hostování ovládacího prvku a nastavit jej jako podřízenou <xref:System.Windows.Controls.Border> element, který je určena k hostování okna.  
  
9. Komunikovat s okno hostované odesláním [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] zprávy a zpracování zprávy z jeho podřízených windows, jako je například oznámení zaslaná z ovládacích prvků.  
  
<a name="page_layout"></a>   
## <a name="implement-the-page-layout"></a>Implementace rozložení stránky  
 Rozložení pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stránky, který je hostitelem ListBox – ovládací prvek se skládá ze dvou oblastí. Na levé straně stránky hostitelem několik [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky, které poskytují [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] , které umožňuje pracovat s [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ovládacího prvku. Pravém horním rohu stránky má čtvercovou oblast pro hostované ListBox – ovládací prvek.  
  
 Kód pro implementaci tohoto rozvržení je poměrně jednoduché. Kořenový element <xref:System.Windows.Controls.DockPanel> který má dva podřízené elementy. První je <xref:System.Windows.Controls.Border> element, který je hostitelem ListBox – ovládací prvek. Zabírá in 200 x 200 odmocnina. pravém horním rohu stránky. Druhý <xref:System.Windows.Controls.StackPanel> element, který obsahuje sadu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky, které zobrazují informace a umožňují pracovat s ListBox – ovládací prvek nastavením zveřejněné součinnosti vlastnosti. Pro jednotlivé prvky, které jsou podřízené objekty <xref:System.Windows.Controls.StackPanel>, najdete v části referenčního materiálu pro různé prvky používané podrobnosti o tyto prvky se nebo co dělají, ty jsou uvedené v následujícím příkladu kódu, ale nebudou jej zde popsané (základní součinnosti modelu nevyžaduje žádnou z nich, se poskytnou přidat některé interaktivity můžete k ukázce).  
  
 [!code-xaml[WPFHostingWin32Control#WPFUI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml#wpfui)]  
  
<a name="host_class"></a>   
## <a name="implement-a-class-to-host-the-microsoft-win32-control"></a>Implementace třídy pro hostování ovládacího prvku Microsoft Win32  
 Základní této ukázce je třída, která ve skutečnosti hostitelem ovládacího prvku, ControlHost.cs. Dědí z <xref:System.Windows.Interop.HwndHost>. Konstruktor přebírá dva parametry, výška a šířka, které odpovídají výška a šířka <xref:System.Windows.Controls.Border> element, který je hostitelem ListBox – ovládací prvek. Tyto hodnoty se později používá zajistit, aby velikost odpovídá ovládacího prvku <xref:System.Windows.Controls.Border> elementu.  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostclass)]
 [!code-vb[WPFHostingWin32Control#ControlHostClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostclass)]  
  
 Je také sadu konstanty. Tyto konstanty jsou převzaty z velké části z winuser a umožňují používat běžné názvy při volání metody [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] funkce.  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostConstants](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostconstants)]
 [!code-vb[WPFHostingWin32Control#ControlHostConstants](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostconstants)]  
  
<a name="buildwindowcore"></a>   
### <a name="override-buildwindowcore-to-create-the-microsoft-win32-window"></a>Přepsání BuildWindowCore vytvořit okno Microsoft Win32  
 Potlačí tuto metodu pro vytvoření [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno, které se bude hostovat stránkou a pro připojení mezi okna a stránky. Protože tato ukázka zahrnuje hostování ListBox – ovládací prvek, se vytvoří dvě okna. První je okně, které je ve skutečnosti hostované [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stránky. ListBox – ovládací prvek je vytvořen jako podřízený toto okno.  
  
 Důvody, proč tento přístup je ke zjednodušení procesu pro příjem oznámení z ovládacího prvku. <xref:System.Windows.Interop.HwndHost> Třída umožňuje zpracovávat zprávy odeslané do okna, který je hostitelem. Pokud hostujete [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] řízení přímo, zobrazí se zprávy odeslané do interní zpráva smyčky ovládacího prvku. Můžete zobrazit řízení a odesílání, které ho zprávy, ale se zobrazí oznámení, která odešle ovládacího prvku do jeho nadřazeného okna. To znamená, mimo jiné, že máte žádným způsobem zjišťování, když uživatel pracuje s ovládacím prvkem. Místo toho vytvořte okno hostitele a nastavte ovládacího prvku podřízenou toto okno. Umožňuje zpracování zpráv pro oznámení odesílaná ji pomocí ovládacího prvku včetně okno hostitele. Pro usnadnění práce protože okno hostitele je něco než jednoduché obálku pro ovládací prvek, balíček označenou jako ListBox – ovládací prvek.  
  
<a name="create_the_window_and_listbox"></a>   
#### <a name="create-the-host-window-and-listbox-control"></a>Vytvoření hostitelské okno a ListBox – ovládací prvek  
 Můžete použít [!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)] pro vytvoření hostitele okna pro ovládací prvek pomocí vytvoření a registrace třídy oken a tak dále. Je však mnohem jednodušší vytvořit okno s třídou předdefinované "statická" okno. Tím získáte pomocí procedury okna potřebují k přijímání oznámení z ovládacího prvku a vyžaduje minimální kódování.  
  
 HWND ovládacího prvku je vystaven prostřednictvím vlastnosti jen pro čtení, tak, aby stránce hostitele můžete použít k odesílání zpráv do ovládacího prvku.  
  
 [!code-csharp[WPFHostingWin32Control#IntPtrProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#intptrproperty)]
 [!code-vb[WPFHostingWin32Control#IntPtrProperty](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#intptrproperty)]  
  
 ListBox – ovládací prvek se vytvoří jako podřízeného okna hostitele. Výška a šířka systému windows jsou nastaveny na hodnoty předaný konstruktoru, výše popsané. To zajišťuje, že velikost okna hostitele a řízení identické do oblasti vyhrazené na stránce.  Po vytvoření systému windows, vrátí vzorku <xref:System.Runtime.InteropServices.HandleRef> objekt, který obsahuje HWND okna hostitele.  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCore](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcore)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCore](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcore)]  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCoreHelper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcorehelper)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCoreHelper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcorehelper)]  
  
<a name="destroywindow_wndproc"></a>   
### <a name="implement-destroywindow-and-wndproc"></a>Destroywindow – implementace a WndProc  
 Kromě <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>, je nutné přepsat <xref:System.Windows.Interop.HwndHost.WndProc%2A> a <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> metody <xref:System.Windows.Interop.HwndHost>. V tomto příkladu jsou zpracovávány zprávy pro ovládací prvek <xref:System.Windows.Interop.HwndHost.MessageHook> obslužnou rutinu, proto implementace <xref:System.Windows.Interop.HwndHost.WndProc%2A> a <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> je minimální. U <xref:System.Windows.Interop.HwndHost.WndProc%2A>, nastavte `handled` k `false` znamenat, že zpráva nebyla zpracována, a vraťte 0. Pro <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>, jednoduše zničit okno.  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroy](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroy)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroy](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroy)]  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroyHelper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroyhelper)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroyHelper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroyhelper)]  
  
<a name="host_the_control"></a>   
## <a name="host-the-control-on-the-page"></a>Hostování ovládacího prvku na stránce  
 K hostování ovládacího prvku na stránce, nejprve vytvořit novou instanci třídy `ControlHost` třídy. Předat výška a šířka ohraničení elementu, který obsahuje ovládací prvek (`ControlHostElement`) do `ControlHost` konstruktor. Tím se zajistí, že ListBox správnou velikost. Potom hostování ovládacího prvku na stránce přiřazením `ControlHost` do objektu <xref:System.Windows.Controls.Decorator.Child%2A> vlastnost hostitele <xref:System.Windows.Controls.Border>.  
  
 Ukázka připojí obslužnou rutinu do <xref:System.Windows.Interop.HwndHost.MessageHook> události `ControlHost` pro příjem zpráv z ovládacího prvku. Tato událost se vyvolá pro všechny zprávy odeslané do okna hostované. V takovém případě se tyto zprávy odeslané do okna, které zabaluje skutečný ListBox – ovládací prvek, včetně oznámení z ovládacího prvku. Ukázka volá SendMessage získat informace z ovládacího prvku a upravte jeho obsah. Podrobnosti o jak stránce komunikuje s ovládacím prvkem jsou popsané v další části.  
  
> [!NOTE]
>  Všimněte si, že existují dvě [!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)] deklarace pro SendMessage. To je nezbytné, protože jeden používá `wParam` parametr předat řetězce a dalších použije k předávání celé číslo. Je třeba samostatné prohlášení pro každý podpis zajistit, že je správně zařazeno data.  
  
 [!code-csharp[WPFHostingWin32Control#HostWindowClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#hostwindowclass)]
 [!code-vb[WPFHostingWin32Control#HostWindowClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#hostwindowclass)]  
  
 [!code-csharp[WPFHostingWin32Control#ControlMsgFilterSendMessage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#controlmsgfiltersendmessage)]
 [!code-vb[WPFHostingWin32Control#ControlMsgFilterSendMessage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#controlmsgfiltersendmessage)]  
  
<a name="communication"></a>   
## <a name="implement-communication-between-the-control-and-the-page"></a>Implementace komunikace mezi ovládacího prvku a stránky  
 Manipulace s ovládacím prvku odesláním [!INCLUDE[TLA2#tla_win](../../../../includes/tla2sharptla-win-md.md)] zprávy. Ovládací prvek vás upozorní, když uživatel pracuje s ním zasláním oznámení na jeho hostitelské okno. [Hostování Win32 ListBox – ovládací prvek v ukázce WPF](http://go.microsoft.com/fwlink/?LinkID=159998) ukázka zahrnuje uživatelského rozhraní, která poskytuje několik příkladů, jak to funguje:  
  
-   Připojte položky do seznamu.  
  
-   Odstranit vybrané položky ze seznamu  
  
-   Zobrazte text aktuálně vybrané položky.  
  
-   Zobrazí počet položek v seznamu.  
  
 Uživatele můžete také vyberte položku v seznamu kliknutím, stejně jako pro konvenční [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikace. Zobrazit data se aktualizují pokaždé, když uživatel změní stav pole se seznamem výběr, přidávání nebo připojování položku.  
  
 Připojit položky, pole se seznamem LB_ADDSTRING zprávu odešlete. Pokud chcete odstranit položky, odeslání LB_GETCURSEL získat index aktuální výběr a potom LB_DELETESTRING se odstranit položku. Vzorek také odesílá LB_GETCOUNT a aktualizovat zobrazení, který ukazuje počet položek, které používá vrácené hodnoty. Obě tyto instance SendMessage použijte jednu z [!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)] deklarace, které jsou popsané v předchozí části.  
  
 [!code-csharp[WPFHostingWin32Control#AppendDeleteText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#appenddeletetext)]
 [!code-vb[WPFHostingWin32Control#AppendDeleteText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#appenddeletetext)]  
  
 Když uživatel vybere položku nebo jejich výběru se změní, upozorní ovládacího prvku okno hostitele odesláním wm_command – zprávy, která vyvolá <xref:System.Windows.Interop.HwndHost.MessageHook> událostí pro stránku. Obslužná rutina obdrží stejné informace jako hlavní okno postup okna hostitele. Také předá odkaz na logickou hodnotu, `handled`. Nastavíte `handled` k `true` znamená, že mají zpracovává zprávy a je potřeba žádné další zpracování.  
  
 Wm_command – je odeslaných z různých důvodů, tak, aby musí zkontrolovat ID oznámení zjistit, zda je událost, která chcete zpracovávat. ID je součástí vysoké slovo z `wParam` parametr. Vzhledem k tomu [!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] nemá makro HIWORD, příklad používá k extrakci ID. bitové operátory Pokud uživatel má nebo jejich výběr změnit, bude ID LBN_SELCHANGE.  
  
 Po přijetí LBN_SELCHANGE vzorku získá index vybrané položky odesláním ovládacího prvku LB_GETCURSEL zprávy. Chcete-li získat text, je třeba nejprve vytvořit <xref:System.Text.StringBuilder>. Potom odešlete ovládacího prvku zprávu LB_GETTEXT. Předat prázdné <xref:System.Text.StringBuilder> objekt jako `wParam` parametr. Při vrácení SendMessage, <xref:System.Text.StringBuilder> bude obsahovat text vybrané položky. Toto použití SendMessage vyžaduje ještě jiné [!INCLUDE[TLA2#tla_pinvoke](../../../../includes/tla2sharptla-pinvoke-md.md)] deklarace.  
  
 Nakonec nastavte `handled` k `true` indikující, že zpráva byla zpracována.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Interop.HwndHost>  
 [Vzájemná spolupráce grafického subsystému WPF a systému Win32](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)  
 [Návod: Moje první desktopová aplikace WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)
