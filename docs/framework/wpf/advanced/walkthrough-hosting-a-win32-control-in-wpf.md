---
title: Hostování ovládacího prvku Win32 ve WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Win32 control in WPF [WPF]
- Win32 code [WPF], WPF interoperation
ms.assetid: a676b1eb-fc55-4355-93ab-df840c41cea0
ms.openlocfilehash: 5185e60640c652b79bd105db54830ac3acc57129
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186742"
---
# <a name="walkthrough-host-a-win32-control-in-wpf"></a>Návod: Hostování ovládacího prvku Win32 ve WPF
Windows Presentation Foundation (WPF) poskytuje bohaté prostředí pro vytváření aplikací. Však pokud máte značné investice do kódu Win32, může být efektivnější znovu použít alespoň některé z tohoto kódu v aplikaci WPF, spíše než přepsat úplně. WPF poskytuje jednoduchý mechanismus pro hostování win32 okna, na stránce WPF.  
  
 Toto téma vás provede aplikací [Hosting Win32 ListBox control v WPF vzorku](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control), který je hostitelem win32 seznam ovládacíprvek. Tento obecný postup lze rozšířit na hostování libovolného okna Win32.  

<a name="requirements"></a>
## <a name="requirements"></a>Požadavky  
 Toto téma předpokládá základní znalost programování wpf a rozhraní API systému Windows. Základní úvod do programování WPF naleznete v [tématu Začínáme](../getting-started/index.md). Pro úvod do programování rozhraní API systému Windows, viz některý z mnoha knih na toto téma, zejména *programování Windows* Charles Petzold.  
  
 Vzhledem k tomu, že ukázka, která doprovází toto téma je implementována v C#, využívá služby vyvolání platformy (PInvoke) pro přístup k rozhraní API systému Windows. Některé obeznámenost s PInvoke je užitečné, ale není nezbytné.  
  
> [!NOTE]
> Toto téma obsahuje řadu příkladů kódu z přidružené ukázky. Pro čitelnost však neobsahuje úplný ukázkový kód. Můžete získat nebo zobrazit kompletní kód z [hostování Win32 ListBox control v WPF vzorku](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control).  
  
<a name="basic_procedure"></a>
## <a name="the-basic-procedure"></a>Základní postup  
 Tato část popisuje základní postup pro hostování win32 okno na stránce WPF. Zbývající části procházejí podrobnostmi o každém kroku.  
  
 Základním hostingovým postupem je:  
  
1. Implementujte stránku WPF pro hostování okna. Jednou z technik <xref:System.Windows.Controls.Border> je vytvořit prvek rezervovat část stránky pro hostované okno.  
  
2. Implementujte třídu pro hostování ovládacího prvku, který dědí z <xref:System.Windows.Interop.HwndHost>.  
  
3. V této třídě přepsat <xref:System.Windows.Interop.HwndHost> člen <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>třídy .  
  
4. Vytvořte hostované okno jako podřízený okno, které obsahuje stránku WPF. Ačkoli konvenční WPF programování nemusí explicitně využít, hosting stránka je okno s popisovač (HWND). Obdržíte stránku HWND `hwndParent` prostřednictvím <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A> parametru metody. Hostované okno by měla být vytvořena jako podřízený tento HWND.  
  
5. Po vytvoření okna hostitele vraťte HWND hostovaného okna. Pokud chcete hostit jeden nebo více ovládacích prvků Win32, obvykle vytvoříte okno hostitele jako podřízený HWND a ovládací prvky podřízené okno hostitele. Obtékání ovládacích prvků v okně hostitele poskytuje jednoduchý způsob, jak pro stránku WPF přijímat oznámení z ovládacích prvků, který se zabývá některé konkrétní Win32 problémy s oznámeními přes hranice HWND.  
  
6. Zpracování vybraných zpráv odeslaných do okna hostitele, například oznámení z podřízených ovládacích prvků. Můžete to provést dvěma způsoby.  
  
    - Pokud dáváte přednost zpracování zpráv ve vaší <xref:System.Windows.Interop.HwndHost.WndProc%2A> hostitelské <xref:System.Windows.Interop.HwndHost> třídy, přepsat metodu třídy.  
  
    - Pokud dáváte přednost wpf zpracování zprávy, <xref:System.Windows.Interop.HwndHost> <xref:System.Windows.Interop.HwndHost.MessageHook> zpracování události třídy v kódu na pozadí. K této události dochází pro každou zprávu, která je přijata v hostované okno. Pokud zvolíte tuto možnost, je <xref:System.Windows.Interop.HwndHost.WndProc%2A>nutné stále přepsat , ale potřebujete pouze minimální implementaci.  
  
7. Přepsat <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> a <xref:System.Windows.Interop.HwndHost.WndProc%2A> metody <xref:System.Windows.Interop.HwndHost>. Tyto metody je nutné přepsat, aby byla splněna <xref:System.Windows.Interop.HwndHost> smlouva, ale může být nutné zadat pouze minimální implementaci.  
  
8. V souboru s kódem na pozadí vytvořte instanci třídy hostování ovládacího prvku a udělejte z ní podřízený <xref:System.Windows.Controls.Border> prvek, který je určen k hostování okna.  
  
9. Komunikujte s hostovaným oknem tak, že mu odešlete zprávy systému Microsoft Windows a zpracováváte zprávy z podřízených oken, například oznámení odeslaná ovládacími prvky.  
  
<a name="page_layout"></a>
## <a name="implement-the-page-layout"></a>Implementace rozložení stránky  
 Rozložení pro stránku WPF, která je hostitelem Ovládací prvek ListBox, se skládá ze dvou oblastí. Na levé straně stránky je hostitelem několik [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] ovládacích prvků WPF, které poskytují, který umožňuje manipulovat s ovládacím prvkem Win32. V pravém horním rohu stránky má čtvercovou oblast pro hostované ListBox Control.  
  
 Kód k implementaci tohoto rozložení je poměrně jednoduchý. Kořenový prvek <xref:System.Windows.Controls.DockPanel> je, který má dva podřízené prvky. První je <xref:System.Windows.Controls.Border> prvek, který je hostitelem Ovládací prvek ListBox. Zabírá 200x200 náměstí v pravém horním rohu stránky. Druhý je <xref:System.Windows.Controls.StackPanel> prvek, který obsahuje sadu WPF ovládací prvky, které zobrazují informace a umožňují manipulovat listbox ovládací prvek nastavením vystavené interoperation vlastnosti. Pro každý z prvků, které <xref:System.Windows.Controls.StackPanel>jsou podřízené , viz referenční materiál pro různé prvky používané podrobnosti o tom, co tyto prvky jsou nebo co dělají, tyto jsou uvedeny v příkladu kódu níže, ale nebudou vysvětleny zde (základní interoperation model nevyžaduje žádné z nich, jsou k dispozici přidat některé interaktivity do vzorku).  
  
 [!code-xaml[WPFHostingWin32Control#WPFUI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml#wpfui)]  
  
<a name="host_class"></a>
## <a name="implement-a-class-to-host-the-microsoft-win32-control"></a>Implementace třídy pro hostování ovládacího prvku Microsoft Win32  
 Jádro této ukázky je třída, která skutečně hostuje ovládací prvek, ControlHost.cs. Dědí z <xref:System.Windows.Interop.HwndHost>. Konstruktor má dva parametry, výška a šířka, které <xref:System.Windows.Controls.Border> odpovídají výšce a šířce prvku, který je hostitelem ovládacího prvku ListBox. Tyto hodnoty se později používají k zajištění, <xref:System.Windows.Controls.Border> že velikost ovládacího prvku odpovídá prvku.  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostClass](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostclass)]
 [!code-vb[WPFHostingWin32Control#ControlHostClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostclass)]  
  
 K dispozici je také sada konstant. Tyto konstanty jsou z velké části převzaty z Winuser.h a umožňují používat konvenční názvy při volání win32 funkce.  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostConstants](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostconstants)]
 [!code-vb[WPFHostingWin32Control#ControlHostConstants](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostconstants)]  
  
<a name="buildwindowcore"></a>
### <a name="override-buildwindowcore-to-create-the-microsoft-win32-window"></a>Přepsat buildwindowcore pro vytvoření okna Microsoft Win32  
 Přepsat tuto metodu vytvořit okno Win32, který bude hostitelem stránky a vytvořit připojení mezi oknem a stránkou. Vzhledem k tomu, že tato ukázka zahrnuje hostování ovládacího prvku ListBox, jsou vytvořena dvě okna. První je okno, které je ve skutečnosti hostované na stránce WPF. Ovládací prvek ListBox je vytvořen jako podřízený prvek tohoto okna.  
  
 Důvodem tohoto přístupu je zjednodušit proces přijímání oznámení z ovládacího prvku. Třída <xref:System.Windows.Interop.HwndHost> umožňuje zpracovávat zprávy odeslané do okna, které je hostitelem. Pokud hostujete ovládací prvek Win32 přímo, obdržíte zprávy odeslané do smyčky interní zprávy ovládacího prvku. Ovládací prvek můžete zobrazit a odeslat zprávy, ale neobdržíte oznámení, která ovládací prvek odešle do nadřazeného okna. To mimo jiné znamená, že nemáte žádný způsob, jak zjistit, kdy uživatel pracuje s ovládacím prvkem. Místo toho vytvořte okno hostitele a vytvořte ovládací prvek podřízeným prvkem tohoto okna. To umožňuje zpracovat zprávy pro okno hostitele, včetně oznámení odeslaných ovládacím prvkem. Pro větší pohodlí, protože okno hostitele je o něco více než jednoduchý obálku pro ovládací prvek, balíček bude označován jako ovládací prvek ListBox.  
  
<a name="create_the_window_and_listbox"></a>
#### <a name="create-the-host-window-and-listbox-control"></a>Vytvoření okna hostitele a ovládacího prvku ListBox  
 PInvoke můžete použít k vytvoření okna hostitele pro ovládací prvek vytvořením a registrací třídy okna a tak dále. Mnohem jednodušší přístup je však vytvořit okno s předdefinovanou "statickou" třídou okna. To poskytuje postup okna, které potřebujete k přijímání oznámení z ovládacího prvku a vyžaduje minimální kódování.  
  
 HWND ovládacího prvku je vystavena prostřednictvím vlastnosti jen pro čtení, tak, aby stránka hostitele můžete použít k odesílání zpráv do ovládacího prvku.  
  
 [!code-csharp[WPFHostingWin32Control#IntPtrProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#intptrproperty)]
 [!code-vb[WPFHostingWin32Control#IntPtrProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#intptrproperty)]  
  
 Ovládací prvek ListBox je vytvořen jako podřízený okno hostitele. Výška a šířka obou oken jsou nastaveny na hodnoty předané konstruktoru, popsané výše. Tím je zajištěno, že velikost okna hostitele a ovládacího prvku je shodná s vyhrazenou oblastí na stránce.  Po vytvoření oken ukázka vrátí <xref:System.Runtime.InteropServices.HandleRef> objekt, který obsahuje HWND okna hostitele.  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCore](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcore)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCore](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcore)]  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCoreHelper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcorehelper)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCoreHelper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcorehelper)]  
  
<a name="destroywindow_wndproc"></a>
### <a name="implement-destroywindow-and-wndproc"></a>Implementovat DestroyWindow a WndProc  
 Kromě <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>, je nutné také <xref:System.Windows.Interop.HwndHost.WndProc%2A> přepsat <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> a <xref:System.Windows.Interop.HwndHost>metody . V tomto příkladu zprávy pro ovládací <xref:System.Windows.Interop.HwndHost.MessageHook> prvek jsou zpracovány <xref:System.Windows.Interop.HwndHost.WndProc%2A> <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> obslužnou rutinou, tedy implementace a je minimální. V případě <xref:System.Windows.Interop.HwndHost.WndProc%2A>, `handled` nastavte `false` na označuje, že zpráva nebyla zpracována a vrátit 0. Pro <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>, jednoduše zničit okno.  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroy](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroy)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroy](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroy)]  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroyHelper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroyhelper)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroyHelper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroyhelper)]  
  
<a name="host_the_control"></a>
## <a name="host-the-control-on-the-page"></a>Hostování ovládacího prvku na stránce  
 Chcete-li hostovat ovládací prvek na stránce, `ControlHost` nejprve vytvořte novou instanci třídy. Předejte výšku a šířku elementu ohraničení, který obsahuje ovládací prvek (`ControlHostElement`) konstruktoru. `ControlHost` Tím je zajištěno, že listbox je velikost správně. Potom hostitelem ovládacího prvku na `ControlHost` stránce přiřazením <xref:System.Windows.Controls.Decorator.Child%2A> objektu <xref:System.Windows.Controls.Border>vlastnost hostitele .  
  
 Ukázka připojí obslužnou <xref:System.Windows.Interop.HwndHost.MessageHook> `ControlHost` rutinu k události přijímat zprávy z ovládacího prvku. Tato událost je vyvolána pro každou zprávu odeslanou do hostovaného okna. V tomto případě se jedná o zprávy odeslané do okna, které zalomí skutečný ovládací prvek ListBox, včetně oznámení z ovládacího prvku. Ukázka volá SendMessage získat informace z ovládacího prvku a upravit jeho obsah. Podrobnosti o tom, jak stránka komunikuje s ovládacím prvkem jsou popsány v další části.  
  
> [!NOTE]
> Všimněte si, že existují dvě deklarace PInvoke pro SendMessage. To je nezbytné, `wParam` protože jeden používá parametr předat řetězec a druhý používá k předání celé číslo. Potřebujete samostatné prohlášení pro každý podpis, abyste zajistili, že data jsou správně zařazena.  
  
 [!code-csharp[WPFHostingWin32Control#HostWindowClass](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#hostwindowclass)]
 [!code-vb[WPFHostingWin32Control#HostWindowClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#hostwindowclass)]  
  
 [!code-csharp[WPFHostingWin32Control#ControlMsgFilterSendMessage](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#controlmsgfiltersendmessage)]
 [!code-vb[WPFHostingWin32Control#ControlMsgFilterSendMessage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#controlmsgfiltersendmessage)]  
  
<a name="communication"></a>
## <a name="implement-communication-between-the-control-and-the-page"></a>Implementace komunikace mezi ovládacím prvkem a stránkou  
 Ovládací prvek můžete zmanipulovat tak, že jej odešlete zprávy systému Windows. Ovládací prvek vás upozorní, když s ním uživatel interaguje odesláním oznámení do okna hostitele. [Hosting Win32 ListBox control v WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control) vzorku obsahuje ui, který poskytuje několik příkladů, jak to funguje:  
  
- Připojte položku do seznamu.  
  
- Odstranění vybrané položky ze seznamu  
  
- Zobrazí text aktuálně vybrané položky.  
  
- Zobrazí počet položek v seznamu.  
  
 Uživatel může také vybrat položku v seznamu kliknutím na něj, stejně jako by pro konvenční Win32 aplikace. Zobrazená data se aktualizují pokaždé, když uživatel změní stav seznamu výběrem, přidáním nebo připojením položky.  
  
 Chcete-li připojit položky, odešlete do seznamu [ `LB_ADDSTRING` zprávu](/windows/desktop/Controls/lb-addstring). Chcete-li odstranit [`LB_GETCURSEL`](/windows/desktop/Controls/lb-getcursel) položky, odešlete, [`LB_DELETESTRING`](/windows/desktop/Controls/lb-deletestring) abyste získali index aktuálního výběru a poté položku odstranili. Ukázka také [`LB_GETCOUNT`](/windows/desktop/Controls/lb-getcount)odešle a použije vrácenou hodnotu k aktualizaci zobrazení, které zobrazuje počet položek. Obě tyto instance [`SendMessage`](/windows/desktop/api/winuser/nf-winuser-sendmessage) použití jedné z Deklarací PInvoke popsaných v předchozí části.  
  
 [!code-csharp[WPFHostingWin32Control#AppendDeleteText](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#appenddeletetext)]
 [!code-vb[WPFHostingWin32Control#AppendDeleteText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#appenddeletetext)]  
  
 Když uživatel vybere položku nebo změní svůj výběr, ovládací prvek upozorní okno hostitele odesláním [ `WM_COMMAND` zprávy](/windows/desktop/menurc/wm-command), která vyvolá <xref:System.Windows.Interop.HwndHost.MessageHook> událost pro stránku. Obslužná rutina obdrží stejné informace jako procedura hlavního okna okna hostitele. Také předá odkaz na logickou `handled`hodnotu . `handled` Nastavíte `true` na označení, že jste zpracovali zprávu a žádné další zpracování je potřeba.  
  
 [`WM_COMMAND`](/windows/desktop/menurc/wm-command)je odeslána z různých důvodů, takže je nutné zkontrolovat ID oznámení k určení, zda se jedná o událost, kterou chcete zpracovat. ID je obsaženo ve vysokém `wParam` slově parametru. Ukázka používá bitové operátory k extrahování ID. Pokud uživatel provedl nebo změnil svůj výběr, [`LBN_SELCHANGE`](/windows/desktop/Controls/lbn-selchange)bude id .  
  
 Po [`LBN_SELCHANGE`](/windows/desktop/Controls/lbn-selchange) přijetí ukázka získá index vybrané položky odesláním [ `LB_GETCURSEL` ](/windows/desktop/Controls/lb-getcursel)ovládacího prvku zprávu . Chcete-li získat text, <xref:System.Text.StringBuilder>nejprve vytvořte . Potom odeslat ovládací prvek [ `LB_GETTEXT` zprávu](/windows/desktop/Controls/lb-gettext). Předaj <xref:System.Text.StringBuilder> te `wParam` prázdný objekt jako parametr. Když [`SendMessage`](/windows/desktop/api/winuser/nf-winuser-sendmessage) se <xref:System.Text.StringBuilder> vrátí, bude obsahovat text vybrané položky. Toto [`SendMessage`](/windows/desktop/api/winuser/nf-winuser-sendmessage) použití vyžaduje další PInvoke deklarace.  
  
 Nakonec nastavte `handled` `true` na označení, že zpráva byla zpracována.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Interop.HwndHost>
- [Vzájemná spolupráce grafického subsystému WPF a systému Win32](wpf-and-win32-interoperation.md)
- [Návod: Moje první desktopová aplikace WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
