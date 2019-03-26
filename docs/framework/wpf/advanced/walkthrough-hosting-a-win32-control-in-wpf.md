---
title: 'Návod: Hostování ovládacího prvku Win32 v subsystému WPF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Win32 control in WPF [WPF]
- Win32 code [WPF], WPF interoperation
ms.assetid: a676b1eb-fc55-4355-93ab-df840c41cea0
ms.openlocfilehash: 13845eb662064e0ac1db913bedc0b21214292db5
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2019
ms.locfileid: "58412315"
---
# <a name="walkthrough-hosting-a-win32-control-in-wpf"></a>Návod: Hostování ovládacího prvku Win32 v subsystému WPF
Windows Presentation Foundation (WPF) poskytuje bohaté prostředí pro vytváření aplikací. Ale pokud máte značné investice v kódu Win32, může být efektivnější opakovaně používat alespoň některé tohoto kódu v aplikaci WPF spíše než přepíše zcela. WPF poskytuje jednoduchý mechanismus pro hostování okně Win32, na stránce WPF.  
  
 Toto téma vás provede aplikace, [hostování ovládacím prvku Win32 v ukázce WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control), že ovládací prvek pole se seznamem Win32 hostitele. Tento obecný postup je možné rozšířit na hostování jakékoli okno Win32.  
  
  
<a name="requirements"></a>   
## <a name="requirements"></a>Požadavky  
 Toto téma předpokládá základní znalost WPF a Windows API programování. Základní informace o programování WPF, naleznete v tématu [Začínáme](../getting-started/index.md). Úvod k programování v rozhraní Windows API, naleznete v některém z mnoha knihy k tomuto tématu, zejména *programování Windows* podle Charles Petzold.  
  
 Protože vzorku, který doprovází toto téma je implementována v C#, ho využívá platformu vyvolání služby (PInvoke) pro přístup k rozhraní API Windows. Některé znalost PInvoke je užitečné, ale není nutná.  
  
> [!NOTE]
>  Toto téma obsahuje několik příkladů kódu z ukázky přidružené. Ale pro lepší čitelnost, neobsahuje úplnou ukázku kódu. Můžete získat nebo zobrazit kompletní kód z [hostování ovládacím prvku Win32 v ukázce WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control).  
  
<a name="basic_procedure"></a>   
## <a name="the-basic-procedure"></a>Základní postup  
 Tato část popisuje základní postup pro hostování okně Win32 na stránce WPF. Zbývající části projít podrobnosti o jednotlivých kroků.  
  
 Základní postup hostingu je:  
  
1.  Implementace stránky WPF pro hostování v okně. Je jednou z metod vytvoření <xref:System.Windows.Controls.Border> element rezervovat oddíl na stránce pro okno prostředí.  
  
2.  Implementace třídy pro hostování ovládacího prvku, který dědí z <xref:System.Windows.Interop.HwndHost>.  
  
3.  V této třídě přepsat <xref:System.Windows.Interop.HwndHost> člena třídy <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>.  
  
4.  Vytvoření okna prostředí jako podřízená položka okna, která obsahuje stránku WPF. I když není potřeba explicitně vytvořit konvenční programování WPF využít, stránka hostingu je okno s popisovačem (HWND). Se zobrazí stránka HWND prostřednictvím `hwndParent` parametr <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A> metody. V okně prostředí musí být vytvořené jako podřízený objekt tento HWND.  
  
5.  Po vytvoření okno hostitele vrací HWND okno prostředí. Pokud chcete hostovat jeden nebo více ovládacích prvků systému Win32, obvykle vytvoříte okno hostitele jako podřízený objekt HWND a ujistěte se, podřízené ovládací prvky tohoto okna hostitele. Obtékání ovládacích prvků v okně hostitel poskytuje jednoduchý způsob WPF stránky pro příjem oznámení z ovládacích prvků, která se zabývá některé konkrétní Win32 problémy s oznámeními hranice HWND.  
  
6.  Zpracování vybrané zprávy odeslané do okna hostitele, jako jsou oznámení z podřízených ovládacích prvků. Existují dva způsoby, jak to provést.  
  
    -   Pokud chcete zpracovávat zprávy v hostující třídy, má přednost před <xref:System.Windows.Interop.HwndHost.WndProc%2A> metodu <xref:System.Windows.Interop.HwndHost> třídy.  
  
    -   Pokud chcete mít WPF slouží ke zpracování zpráv, nastavte popisovač <xref:System.Windows.Interop.HwndHost> třídy <xref:System.Windows.Interop.HwndHost.MessageHook> události do vašeho kódu. Pro každou zprávu, která se zobrazila v okně prostředí dojde k této události. Pokud zvolíte tuto možnost, je nutné přepsat <xref:System.Windows.Interop.HwndHost.WndProc%2A>, ale potřebujete jenom minimální implementaci.  
  
7.  Přepsat <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> a <xref:System.Windows.Interop.HwndHost.WndProc%2A> metody <xref:System.Windows.Interop.HwndHost>. Je nutné přepsat tyto metody splňovat <xref:System.Windows.Interop.HwndHost> smlouvy, ale může být pouze nutné zadat minimální implementaci.  
  
8.  V souboru kódu na pozadí, vytvořte instanci hostující třídy ovládacího prvku a nastavte ji podřízený <xref:System.Windows.Controls.Border> element, který je určena k hostování okna.  
  
9. Komunikovat s hostovanou okna a odeslat ho [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] zprávy a zpracování zprávy z jeho podřízených oken, jako je například oznámení zaslaná z ovládacích prvků.  
  
<a name="page_layout"></a>   
## <a name="implement-the-page-layout"></a>Implementace rozložení stránky  
 Rozložení pro stránku WPF, který je hostitelem ListBox – ovládací prvek se skládá ze dvou oblastech. Levé straně stránky hostitelem několik ovládacích prvků WPF, které poskytují [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] , který umožňuje manipulaci s ovládacího prvku Win32. Pravém horním rohu stránky má Čtvereček oblast pro hostované ListBox – ovládací prvek.  
  
 Kód pro implementaci toto rozložení je poměrně jednoduché. Kořenový element <xref:System.Windows.Controls.DockPanel> , který má dva podřízené prvky. První je <xref:System.Windows.Controls.Border> element, který je hostitelem ListBox – ovládací prvek. Zabírá Čtvereček in 200 x 200 pravém horním rohu stránky. Druhým je <xref:System.Windows.Controls.StackPanel> element, který obsahuje sadu ovládacích prvků WPF, které zobrazují informace a umožňují manipulovat s ListBox – ovládací prvek tak, že nastavíte vystavený součinnosti vlastnosti. Pro každý z prvků, které jsou podřízené <xref:System.Windows.Controls.StackPanel>, naleznete v tématu referenční materiál pro různé prvky používá pro podrobnosti o tyto prvky jsou nebo co dělají, ty jsou uvedené ve níže uvedeného ukázkového kódu, ale nebudou je zde vysvětleno (na úrovni basic vzájemné spolupráce modelu nevyžaduje žádnou z nich, jsou poskytovány přidat některé interaktivitu k ukázce).  
  
 [!code-xaml[WPFHostingWin32Control#WPFUI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml#wpfui)]  
  
<a name="host_class"></a>   
## <a name="implement-a-class-to-host-the-microsoft-win32-control"></a>Implementace třídy pro hostování ovládacího prvku Microsoft Win32  
 Jádrem této ukázce je třída, která ve skutečnosti hostuje ovládací prvek, ControlHost.cs. Dědí z <xref:System.Windows.Interop.HwndHost>. Konstruktor přijímá dva parametry, výšku a šířku, které odpovídají výšku a šířku <xref:System.Windows.Controls.Border> element, který je hostitelem ListBox – ovládací prvek. Tyto hodnoty se později použijí k Ujistěte se, že velikost odpovídá ovládacího prvku <xref:System.Windows.Controls.Border> elementu.  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostClass](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostclass)]
 [!code-vb[WPFHostingWin32Control#ControlHostClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostclass)]  
  
 Existuje také sada konstanty. Tyto konstanty do značné míry pocházejí ze winuser a umožňují používat běžné názvy při volání funkce Win32.  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostConstants](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostconstants)]
 [!code-vb[WPFHostingWin32Control#ControlHostConstants](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostconstants)]  
  
<a name="buildwindowcore"></a>   
### <a name="override-buildwindowcore-to-create-the-microsoft-win32-window"></a>Přepsat BuildWindowCore se vytvořit okno Microsoft Win32  
 Můžete přepsat tuto metodu za účelem vytvoření okně Win32, které budou hostovány stránky a vytvoření připojení mezi oknem a na stránce. Vzhledem k tomu, že tento příklad zahrnuje hostování ovládacího prvku ListBox, se vytvoří dvě okna. První je okno, které je ve skutečnosti hostované na stránce WPF. ListBox – ovládací prvek je vytvořen jako podřízený objekt tohoto okna.  
  
 Důvod pro tento přístup je ke zjednodušení procesu pro příjem oznámení z ovládacího prvku. <xref:System.Windows.Interop.HwndHost> Třída umožňuje zpracovávat zprávy odeslané do okna, který je hostitelem. Pokud hostitele Win32 řídit přímo, zobrazí se zprávy odeslané do smyčky zpráv interní ovládacího prvku. Můžete zobrazit ovládací prvek a pošlete ji zprávy, ale neobdržíte oznámení, které ovládací prvek odešle nezašle nadřazenému oknu. To znamená, mimo jiné, že nemůžete nijak zjistit při interakci uživatele s ovládacím prvkem. Místo toho vytvořte okno hostitele a aby byl ovládací prvek podřízeným prvkem tohoto okna. To umožňuje zpracovávat zprávy pro okno hostitele, včetně oznámení odesílat ovládacím prvkem. Pro usnadnění práce protože okno hostitele je trochu více než jednoduché obálky ovládacího prvku balíček bude odkazovat jako ovládací prvek ListBox.  
  
<a name="create_the_window_and_listbox"></a>   
#### <a name="create-the-host-window-and-listbox-control"></a>Vytvořit okno hostitele a ListBox – ovládací prvek  
 Můžete použít k vytvoření do hostitelského okna pro ovládací prvek tak, že vytvoření a registrace tříd oken PInvoke a tak dále. Je však mnohem jednodušší přístup vytvořit okno s třídou předdefinované "statických" okna. To vám poskytne proceduru okna potřebovat k přijímání oznámení z ovládacího prvku a vyžaduje minimální kódování.  
  
 HWND ovládací prvek je přístupný prostřednictvím vlastnosti jen pro čtení, tak, aby stránka hostitele můžete použít k odesílání zpráv do ovládacího prvku.  
  
 [!code-csharp[WPFHostingWin32Control#IntPtrProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#intptrproperty)]
 [!code-vb[WPFHostingWin32Control#IntPtrProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#intptrproperty)]  
  
 ListBox – ovládací prvek je vytvořen jako podřízená položka okna hostitele. Výšku a šířku windows jsou nastaveny na hodnoty předané do konstruktoru, bylo uvedeno výše. Tím se zajistí, že velikost okna hostitele a ovládací prvek je stejné jako vyhrazené oblasti na stránce.  Po vytvoření okna vrátí vzorek <xref:System.Runtime.InteropServices.HandleRef> objekt, který obsahuje HWND okno hostitele.  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCore](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcore)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCore](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcore)]  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCoreHelper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcorehelper)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCoreHelper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcorehelper)]  
  
<a name="destroywindow_wndproc"></a>   
### <a name="implement-destroywindow-and-wndproc"></a>Destroywindow – implementace a WndProc  
 Kromě <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>, musí také přepsat <xref:System.Windows.Interop.HwndHost.WndProc%2A> a <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> metody <xref:System.Windows.Interop.HwndHost>. V tomto příkladu jsou zpracovávány zprávy pro ovládací prvek <xref:System.Windows.Interop.HwndHost.MessageHook> obslužné rutiny, takže provádění <xref:System.Windows.Interop.HwndHost.WndProc%2A> a <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> je minimální. V případě třídy <xref:System.Windows.Interop.HwndHost.WndProc%2A>, nastavte `handled` k `false` do značí, že zpráva nebyla zpracována a vrátí 0. Pro <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>, jednoduše odstranit okno.  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroy](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroy)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroy](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroy)]  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroyHelper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroyhelper)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroyHelper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroyhelper)]  
  
<a name="host_the_control"></a>   
## <a name="host-the-control-on-the-page"></a>Hostování ovládacího prvku na stránce  
 K hostování ovládacího prvku na stránce, nejprve vytvoříte novou instanci třídy `ControlHost` třídy. Předejte výšku a šířku ohraničení prvku, který obsahuje ovládací prvek (`ControlHostElement`) k `ControlHost` konstruktoru. Tím se zajistí, že objekt ListBox správnou velikost. Potom hostovat ovládací prvek na stránce pomocí přiřazení `ControlHost` objektu <xref:System.Windows.Controls.Decorator.Child%2A> vlastnost hostitele <xref:System.Windows.Controls.Border>.  
  
 Ukázka připojí obslužnou rutinu pro <xref:System.Windows.Interop.HwndHost.MessageHook> událost `ControlHost` pro příjem zpráv z ovládacího prvku. Tato událost je aktivována pro všechny zprávy odeslané do okna prostředí. V tomto případě jsou tyto zprávy odeslané do okna, která obaluje skutečný ListBox – ovládací prvek, včetně oznámení z ovládacího prvku. Ukázka volá SendMessage k získání informací z ovládacího prvku a upravte jeho obsah. V další části jsou popsány podrobnosti o tom, jak na stránce komunikuje s ovládacím prvkem.  
  
> [!NOTE]
>  Všimněte si, že existují dvě Deklarace SendMessage PInvoke. To je nezbytné, protože jeden používá `wParam` předat řetězec a druhý parametr se používá k předání celé číslo. Budete potřebovat samostatné prohlášení pro každý podpis k zajištění, že je správně zařazovat data.  
  
 [!code-csharp[WPFHostingWin32Control#HostWindowClass](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#hostwindowclass)]
 [!code-vb[WPFHostingWin32Control#HostWindowClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#hostwindowclass)]  
  
 [!code-csharp[WPFHostingWin32Control#ControlMsgFilterSendMessage](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#controlmsgfiltersendmessage)]
 [!code-vb[WPFHostingWin32Control#ControlMsgFilterSendMessage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#controlmsgfiltersendmessage)]  
  
<a name="communication"></a>   
## <a name="implement-communication-between-the-control-and-the-page"></a>Implementace komunikace mezi ovládacím prvkem a na stránce  
 Manipulovat s prvkem odesíláním zpráv Windows. Ovládací prvek vás upozorní, když uživatel pracuje s jejich odesláním oznámení na jeho hostitelské okno. [Hostování ovládacího prvku ListBox Win32 v subsystému WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control) ukázka zahrnuje uživatelské rozhraní, které obsahuje několik příkladů toho, jak to funguje:  
  
-   Připojte položku do seznamu.  
  
-   Odstranit vybranou položku ze seznamu  
  
-   Zobrazte text vybrané položky.  
  
-   Zobrazte počet položek v seznamu.  
  
 Uživatele můžete také vybrat položku v seznamu kliknutím na ni, stejně jako běžné aplikace Win32. Zobrazená data se aktualizují pokaždé, když uživatel změní stav pole se seznamem vyberete, přidáte nebo přidávání položky.  
  
 Připojit položky odeslat pole se seznamem [ `LB_ADDSTRING` zpráva](/windows/desktop/Controls/lb-addstring). Odstranit položky odeslat [ `LB_GETCURSEL` ](/windows/desktop/Controls/lb-getcursel) získat index aktuálního výběru a potom [ `LB_DELETESTRING` ](/windows/desktop/Controls/lb-deletestring) odstranit položku. Ukázka rovněž odesílá [ `LB_GETCOUNT` ](/windows/desktop/Controls/lb-getcount)a aktualizovat zobrazení, který zobrazuje počet položek, které používá vrácené hodnoty. Obě tyto instance [ `SendMessage` ](/windows/desktop/api/winuser/nf-winuser-sendmessage) použijte jednu z deklarace PInvoke popsané v předchozí části.  
  
 [!code-csharp[WPFHostingWin32Control#AppendDeleteText](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#appenddeletetext)]
 [!code-vb[WPFHostingWin32Control#AppendDeleteText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#appenddeletetext)]  
  
 Když uživatel vybere položku nebo mění jejich výběr, ovládací prvek upozorní okno hostitele a odeslat ho [ `WM_COMMAND` zprávy](/windows/desktop/menurc/wm-command), která vyvolává <xref:System.Windows.Interop.HwndHost.MessageHook> událostí stránky. Obslužná rutina obdrží stejné informace jako hlavní okno procedury okna hostitele. Také předá odkazem na hodnotu typu Boolean `handled`. Nastavíte `handled` k `true` k označení, že mají zpracovat zprávu a je potřeba žádné další zpracování.  
  
 [`WM_COMMAND`](/windows/desktop/menurc/wm-command) pro celou řadu důvodů se odešle, tak, aby musí zkontrolovat ID oznámení k určení, zda je událost, kterou chcete zpracovat. ID je součástí vysokou slova `wParam` parametru. Ukázka používá bitové operátory k extrakci ID. Pokud uživatel provedené nebo změnit jejich výběr, ID bude [ `LBN_SELCHANGE` ](/windows/desktop/Controls/lbn-selchange).  
  
 Když [ `LBN_SELCHANGE` ](/windows/desktop/Controls/lbn-selchange) je přijata, ukázka získá index vybrané položky odesláním ovládacího prvku [ `LB_GETCURSEL` zpráva](/windows/desktop/Controls/lb-getcursel). Pokud chcete získat text, je třeba nejprve vytvořit <xref:System.Text.StringBuilder>. Poté pošlete ovládacího prvku [ `LB_GETTEXT` zpráva](/windows/desktop/Controls/lb-gettext). Předat prázdnou <xref:System.Text.StringBuilder> objektu jako `wParam` parametru. Když [ `SendMessage` ](/windows/desktop/api/winuser/nf-winuser-sendmessage) návratu <xref:System.Text.StringBuilder> bude obsahovat text vybrané položky. Toto použití [ `SendMessage` ](/windows/desktop/api/winuser/nf-winuser-sendmessage) vyžaduje další deklarace PInvoke.  
  
 Nakonec nastavte `handled` k `true` k označení, že zpráva byla zpracována.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Interop.HwndHost>
- [Vzájemná spolupráce grafického subsystému WPF a systému Win32](wpf-and-win32-interoperation.md)
- [Návod: Moje první desktopová aplikace WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
