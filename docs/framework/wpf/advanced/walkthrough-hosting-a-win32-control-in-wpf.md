---
title: 'Návod: Hostování ovládacího prvku Win32 ve WPF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Win32 control in WPF [WPF]
- Win32 code [WPF], WPF interoperation
ms.assetid: a676b1eb-fc55-4355-93ab-df840c41cea0
ms.openlocfilehash: cc27189afd2185d5f0a1eeacccf4c537dd3d9c2e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917542"
---
# <a name="walkthrough-hosting-a-win32-control-in-wpf"></a>Návod: Hostování ovládacího prvku Win32 ve WPF
Windows Presentation Foundation (WPF) poskytuje bohatou prostředí pro vytváření aplikací. Nicméně pokud máte významnou investici do kódu Win32, může být efektivnější znovu použít alespoň část kódu v aplikaci WPF, nikoli úplně přepsat. WPF poskytuje jednoduchý mechanismus pro hostování okna Win32 na stránce WPF.  
  
 Toto téma vás provede aplikací a [hostitelem ovládacího prvku seznamu Win32 v UKÁZCE WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control), který je hostitelem ovládacího prvku seznam Win32. Tento obecný postup lze rozšířit na hostování jakéhokoli okna systému Win32.  

<a name="requirements"></a>   
## <a name="requirements"></a>Požadavky  
 V tomto tématu se předpokládá základní znalost pro programování WPF i Windows API. Základní informace o programování WPF naleznete v tématu [Začínáme](../getting-started/index.md). Úvod do programování rozhraní API systému Windows najdete v libovolné řadě knih v předmětu, zejména v *oknech programování* podle Charles Petzold.  
  
 Vzhledem k tomu, že je ukázka, která provází toto C#téma, implementována v systému, používá pro přístup k rozhraní Windows API služby vyvolání platformy (PInvoke). Některé zkušenosti s PInvoke jsou užitečné, ale nejsou nezbytné.  
  
> [!NOTE]
> Toto téma obsahuje několik příkladů kódu z přidruženého vzorku. Pro čitelnost ale nezahrnuje kompletní vzorový kód. Můžete získat nebo zobrazit úplný kód z [hostování ovládacího prvku seznamu Win32 v UKÁZCE WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control).  
  
<a name="basic_procedure"></a>   
## <a name="the-basic-procedure"></a>Základní postup  
 Tato část popisuje základní postup pro hostování okna Win32 na stránce WPF. Zbývající části si Projděte podrobnosti o jednotlivých krocích.  
  
 Základní hostující procedura je:  
  
1. Implementujte stránku WPF pro hostování okna. Jednou z technik je vytvořit <xref:System.Windows.Controls.Border> prvek, který vyhradí část stránky pro hostované okno.  
  
2. Implementujte třídu pro hostování ovládacího prvku, který dědí <xref:System.Windows.Interop.HwndHost>z.  
  
3. V této třídě přepište <xref:System.Windows.Interop.HwndHost> člen <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>třídy.  
  
4. Vytvoření hostovaného okna jako podřízeného okna, které obsahuje stránku WPF. I když konvenční programování WPF nemusí explicitně používat, hostující stránka je okno s popisovačem (HWND). Zobrazí se HWND stránky přes `hwndParent` parametr <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A> metody. Hostované okno by se mělo vytvořit jako podřízený prvek tohoto HWND.  
  
5. Po vytvoření hostitelského okna vraťte HWND hostovaného okna. Chcete-li hostovat jeden nebo více ovládacích prvků Win32, obvykle vytvoříte hostitelské okno jako podřízený prvek HWND a nastavíte podřízené prvky tohoto hostitelského okna. Zabalení ovládacích prvků v hostitelském okně poskytuje jednoduchý způsob, jak může vaše stránka WPF přijímat oznámení z ovládacích prvků, což se zabývá konkrétními problémy Win32 s oznámeními v rámci hranice HWND.  
  
6. Zpracuje vybrané zprávy odeslané do hostitelského okna, například oznámení z podřízených ovládacích prvků. To můžete provést dvěma způsoby.  
  
    - Pokud dáváte přednost zpracování zpráv ve vaší hostující třídě, přepište <xref:System.Windows.Interop.HwndHost.WndProc%2A> metodu <xref:System.Windows.Interop.HwndHost> třídy.  
  
    - Pokud dáváte přednost tomu, aby WPF zpracoval zprávy, zpracujte <xref:System.Windows.Interop.HwndHost> událost třídy <xref:System.Windows.Interop.HwndHost.MessageHook> v kódu na pozadí. K této události dochází u každé zprávy, která je přijata hostovaným oknem. Pokud zvolíte tuto možnost, musíte stále přepsat <xref:System.Windows.Interop.HwndHost.WndProc%2A>, ale budete potřebovat jenom minimální implementaci.  
  
7. Přepište metody <xref:System.Windows.Interop.HwndHost.WndProc%2A> <xref:System.Windows.Interop.HwndHost>a pro <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> . Tyto metody musíte přepsat tak, aby splňovaly <xref:System.Windows.Interop.HwndHost> kontrakt, ale je možné, že budete muset jenom zadat minimální implementaci.  
  
8. V souboru kódu na pozadí vytvořte instanci třídy hostování ovládacího prvku a nastavte ji jako podřízený <xref:System.Windows.Controls.Border> elementu, který je určen pro hostování okna.  
  
9. Komunikujte s hostovaným oknem tím, [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] že posíláte zprávy IT a zpracováváte zprávy ze svých podřízených oken, jako jsou například oznámení odesílaná ovládacími prvky.  
  
<a name="page_layout"></a>   
## <a name="implement-the-page-layout"></a>Implementace rozložení stránky  
 Rozložení stránky WPF, která je hostitelem ovládacího prvku ListBox, se skládá ze dvou oblastí. Levá strana stránky je hostitelem několika ovládacích prvků WPF, které poskytují [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] ovládací prvky, které umožňují manipulaci s ovládacím prvkem Win32. V pravém horním rohu stránky je čtvercová oblast pro hostovaný ovládací prvek seznamu.  
  
 Kód pro implementaci tohoto rozložení je poměrně jednoduchý. Kořenový element je <xref:System.Windows.Controls.DockPanel> , který má dva podřízené elementy. První je <xref:System.Windows.Controls.Border> prvek, který je hostitelem ovládacího prvku ListBox. Zabírá v pravém horním rohu stránky 200x200 čtverec. Druhým je <xref:System.Windows.Controls.StackPanel> prvek, který obsahuje sadu ovládacích prvků WPF, které zobrazují informace a umožňují manipulovat ovládací prvek ListBox nastavením vlastností zpřístupněných operací. Pro každý element, který je podřízených <xref:System.Windows.Controls.StackPanel>prvků, viz Referenční materiál pro různé prvky, které jsou použity pro podrobnosti o tom, co jsou tyto prvky nebo co dělají, jsou uvedeny v následujícím ukázkovém kódu, ale nebude vysvětlen (Basic Model interakce nevyžaduje žádné z nich, je k dispozici pro přidání některé interaktivity k ukázce.  
  
 [!code-xaml[WPFHostingWin32Control#WPFUI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml#wpfui)]  
  
<a name="host_class"></a>   
## <a name="implement-a-class-to-host-the-microsoft-win32-control"></a>Implementace třídy pro hostování ovládacího prvku Microsoft Win32  
 Jádrem této ukázky je třída, která je ve skutečnosti hostitelem ovládacího prvku, ControlHost.cs. Dědí z <xref:System.Windows.Interop.HwndHost>. Konstruktor přijímá dva parametry, výšku a šířku, které odpovídají výšce a šířce <xref:System.Windows.Controls.Border> prvku, který je hostitelem ovládacího prvku ListBox. Tyto hodnoty se používají později, aby se zajistilo, že velikost ovládacího prvku <xref:System.Windows.Controls.Border> odpovídá prvku.  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostClass](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostclass)]
 [!code-vb[WPFHostingWin32Control#ControlHostClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostclass)]  
  
 K dispozici je také sada konstant. Tyto konstanty jsou z velké části z Winuser. h a umožňují při volání funkcí Win32 použít konvenční názvy.  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostConstants](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostconstants)]
 [!code-vb[WPFHostingWin32Control#ControlHostConstants](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostconstants)]  
  
<a name="buildwindowcore"></a>   
### <a name="override-buildwindowcore-to-create-the-microsoft-win32-window"></a>Přepsat BuildWindowCore a vytvořit okno Microsoft Win32  
 Tuto metodu přepíšete, chcete-li vytvořit okno Win32, které bude hostováno stránkou, a vytvořit propojení mezi oknem a stránkou. Vzhledem k tomu, že tato ukázka zahrnuje hostování ovládacího prvku seznamu, vytvoří se dvě okna. První je okno, které je skutečně hostováno stránkou WPF. Ovládací prvek ListBox je vytvořen jako podřízený objekt tohoto okna.  
  
 Důvodem tohoto přístupu je zjednodušení procesu přijímání oznámení z ovládacího prvku. <xref:System.Windows.Interop.HwndHost> Třída umožňuje zpracovat zprávy odesílané do okna, které je hostitelem. Pokud je přímo hostitelem ovládacího prvku Win32, obdržíte zprávy odeslané do interní smyčky zpráv ovládacího prvku. Můžete zobrazit ovládací prvek a odeslat zprávy, ale neobdržíte oznámení, která ovládací prvek odešle do svého nadřazeného okna. To mimo jiné znamená, že nemáte žádný způsob, jak zjistit, kdy uživatel komunikuje s ovládacím prvkem. Místo toho vytvořte okno hostitele a nastavte ho jako podřízenou položku tohoto okna. To vám umožní zpracovat zprávy pro hostitelské okno, včetně oznámení, která mu ovládací prvek odesílají. Pro usnadnění, protože hostitelské okno je o něco větší než jednoduchá obálka pro ovládací prvek, bude balíček označován jako ovládací prvek seznamu.  
  
<a name="create_the_window_and_listbox"></a>   
#### <a name="create-the-host-window-and-listbox-control"></a>Vytvoření hostitelského okna a ovládacího prvku seznamu  
 Můžete použít PInvoke k vytvoření hostitelského okna pro ovládací prvek vytvořením a registrací třídy okna a tak dále. Mnohem jednodušší přístup je však vytvořit okno s předdefinovanou "" statickou "třídou" Window ". To vám poskytne postup v okně, který potřebujete pro příjem oznámení z ovládacího prvku a vyžaduje minimální kódování.  
  
 Vlastnost HWND ovládacího prvku je vystavena prostřednictvím vlastnosti jen pro čtení, aby ji hostitelská stránka mohla použít k posílání zpráv do ovládacího prvku.  
  
 [!code-csharp[WPFHostingWin32Control#IntPtrProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#intptrproperty)]
 [!code-vb[WPFHostingWin32Control#IntPtrProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#intptrproperty)]  
  
 Ovládací prvek ListBox je vytvořen jako podřízený uzel hostitelského okna. Výška a šířka obou oken je nastavena na hodnoty předané do konstruktoru, popsané výše. Tím se zajistí, že velikost hostitelského okna a ovládacího prvku je stejná jako vyhrazená oblast na stránce.  Po vytvoření okna ukázka vrátí <xref:System.Runtime.InteropServices.HandleRef> objekt, který obsahuje HWND okna hostitele.  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCore](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcore)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCore](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcore)]  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCoreHelper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcorehelper)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCoreHelper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcorehelper)]  
  
<a name="destroywindow_wndproc"></a>   
### <a name="implement-destroywindow-and-wndproc"></a>Implementace DestroyWindow a WndProc  
 Kromě <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>toho je nutné také <xref:System.Windows.Interop.HwndHost.WndProc%2A> přepsat metody a <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> v <xref:System.Windows.Interop.HwndHost>. V tomto příkladu jsou zprávy pro ovládací prvek zpracovávány <xref:System.Windows.Interop.HwndHost.MessageHook> obslužnou rutinou, takže <xref:System.Windows.Interop.HwndHost.WndProc%2A> implementace a <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> je minimální. V případě <xref:System.Windows.Interop.HwndHost.WndProc%2A> `handled` nastavte ,abyoznačoval,žezprávanebylazpracovánaavrátíhodnotu0.`false` Pro <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>můžete jednoduše zničit okno.  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroy](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroy)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroy](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroy)]  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroyHelper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroyhelper)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroyHelper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroyhelper)]  
  
<a name="host_the_control"></a>   
## <a name="host-the-control-on-the-page"></a>Hostování ovládacího prvku na stránce  
 Chcete-li hostovat ovládací prvek na stránce, nejprve vytvořte novou instanci `ControlHost` třídy. Předejte výšku a šířku prvku ohraničení, který obsahuje ovládací prvek (`ControlHostElement`) `ControlHost` do konstruktoru. Tím se zajistí, že se seznam bude správně měnit. Potom můžete ovládací prvek hostovat na stránce přiřazením `ControlHost` objektu <xref:System.Windows.Controls.Decorator.Child%2A> k vlastnosti hostitele <xref:System.Windows.Controls.Border>.  
  
 Ukázka připojí obslužnou rutinu k <xref:System.Windows.Interop.HwndHost.MessageHook> události `ControlHost` pro příjem zpráv z ovládacího prvku. Tato událost je vyvolána pro každou zprávu odeslanou do hostovaného okna. V tomto případě se jedná o zprávy odesílané do okna, které zabalí skutečný ovládací prvek seznamu, včetně oznámení z ovládacího prvku. Ukázka volá metodu SendMessage pro získání informací z ovládacího prvku a pro úpravu jeho obsahu. Podrobnosti o tom, jak stránka komunikuje s ovládacím prvkem, jsou popsány v následující části.  
  
> [!NOTE]
> Všimněte si, že existují dvě deklarace PInvoke pro SendMessage. To je nezbytné, protože jeden používá `wParam` parametr k předání řetězce a druhý používá k předání celého čísla. Pro každý podpis potřebujete samostatnou deklaraci, abyste zajistili správné zařazení dat.  
  
 [!code-csharp[WPFHostingWin32Control#HostWindowClass](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#hostwindowclass)]
 [!code-vb[WPFHostingWin32Control#HostWindowClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#hostwindowclass)]  
  
 [!code-csharp[WPFHostingWin32Control#ControlMsgFilterSendMessage](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#controlmsgfiltersendmessage)]
 [!code-vb[WPFHostingWin32Control#ControlMsgFilterSendMessage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#controlmsgfiltersendmessage)]  
  
<a name="communication"></a>   
## <a name="implement-communication-between-the-control-and-the-page"></a>Implementace komunikace mezi ovládacím prvkem a stránkou  
 Řízení se řídí odesláním zpráv systému Windows. Ovládací prvek vás upozorní, když s ním uživatel komunikuje odesláním oznámení do hostitelského okna. [Hostování ovládacího prvku seznamu Win32 v UKÁZCE WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFHostingWin32Control) obsahuje uživatelské rozhraní, které poskytuje několik příkladů toho, jak to funguje:  
  
- Připojí položku k seznamu.  
  
- Odstranit vybranou položku ze seznamu  
  
- Zobrazí text aktuálně vybrané položky.  
  
- Zobrazí počet položek v seznamu.  
  
 Uživatel může také vybrat položku v seznamu kliknutím na ni, stejně jako v případě konvenční aplikace Win32. Zobrazená data se aktualizují pokaždé, když uživatel změní stav pole seznam tak, že vybere, přidá nebo připojí položku.  
  
 Chcete-li připojit položky, odešlete seznam do pole [ `LB_ADDSTRING` zpráva](/windows/desktop/Controls/lb-addstring). Chcete-li odstranit položky [`LB_GETCURSEL`](/windows/desktop/Controls/lb-getcursel) , odešlete, aby se získal index aktuálního výběru [`LB_DELETESTRING`](/windows/desktop/Controls/lb-deletestring) a pak se položka odstranila. Ukázka také pošle [`LB_GETCOUNT`](/windows/desktop/Controls/lb-getcount)a pomocí vrácené hodnoty aktualizuje zobrazení, které zobrazuje počet položek. Obě tyto instance [`SendMessage`](/windows/desktop/api/winuser/nf-winuser-sendmessage) používají jednu z deklarací PInvoke popsaných v předchozí části.  
  
 [!code-csharp[WPFHostingWin32Control#AppendDeleteText](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#appenddeletetext)]
 [!code-vb[WPFHostingWin32Control#AppendDeleteText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#appenddeletetext)]  
  
 Když uživatel vybere položku nebo změní jejich výběr, ovládací prvek upozorní okno hostitele odesláním [ `WM_COMMAND` zprávy](/windows/desktop/menurc/wm-command) <xref:System.Windows.Interop.HwndHost.MessageHook> , která vyvolá událost pro stránku. Obslužná rutina obdrží stejné informace jako hlavní okno v rámci okna hostitele. Také předává odkaz na logickou hodnotu, `handled`. `handled` Nastavíte`true` , abyste označili, že jste zprávu zpracovali a není potřeba žádné další zpracování.  
  
 [`WM_COMMAND`](/windows/desktop/menurc/wm-command)je odesílán z nejrůznějších důvodů, takže je nutné prostudovat ID oznámení, abyste zjistili, zda se jedná o událost, kterou chcete zpracovat. ID je obsaženo v horním slově `wParam` parametru. Ukázka používá k extrakci IDENTIFIKÁTORu bitové operátory. Pokud uživatel provedl nebo změnil výběr, bude ID [`LBN_SELCHANGE`](/windows/desktop/Controls/lbn-selchange).  
  
 Když [`LBN_SELCHANGE`](/windows/desktop/Controls/lbn-selchange) je přijato, ukázka Získá index vybrané položky odesláním [ `LB_GETCURSEL` ](/windows/desktop/Controls/lb-getcursel)ovládacího prvku zprávy. Chcete-li získat text, je třeba nejprve <xref:System.Text.StringBuilder>vytvořit. Pak odešlete ovládací prvek [ `LB_GETTEXT` zprávu](/windows/desktop/Controls/lb-gettext). Předat prázdný <xref:System.Text.StringBuilder> objekt `wParam` jako parametr. Když [`SendMessage`](/windows/desktop/api/winuser/nf-winuser-sendmessage) se vrátí <xref:System.Text.StringBuilder> , bude obsahovat text vybrané položky. Toto použití [`SendMessage`](/windows/desktop/api/winuser/nf-winuser-sendmessage) vyžaduje ještě jinou deklaraci PInvoke.  
  
 Nakonec nastavte `handled` `true` , aby označoval, že zpráva byla zpracována.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Interop.HwndHost>
- [Vzájemná spolupráce grafického subsystému WPF a systému Win32](wpf-and-win32-interoperation.md)
- [Návod: Moje první desktopová aplikace WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
