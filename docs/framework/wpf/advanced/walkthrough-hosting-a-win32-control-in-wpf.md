---
title: Hostování ovládacího prvku Win32 v subsystému WPF
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Win32 control in WPF [WPF]
- Win32 code [WPF], WPF interoperation
ms.assetid: a676b1eb-fc55-4355-93ab-df840c41cea0
ms.openlocfilehash: eb497a88c119dece85d61d6a32e7b86fb03b44b5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744929"
---
# <a name="walkthrough-host-a-win32-control-in-wpf"></a>Návod: hostování ovládacího prvku Win32 v subsystému WPF
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
  
1. Implementujte stránku WPF pro hostování okna. Jednou z postupů je vytvoření prvku <xref:System.Windows.Controls.Border>, který vyhradí část stránky pro hostované okno.  
  
2. Implementujte třídu pro hostování ovládacího prvku, který dědí z <xref:System.Windows.Interop.HwndHost>.  
  
3. V této třídě přepište <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>člena třídy <xref:System.Windows.Interop.HwndHost>.  
  
4. Vytvoření hostovaného okna jako podřízeného okna, které obsahuje stránku WPF. I když konvenční programování WPF nemusí explicitně používat, hostující stránka je okno s popisovačem (HWND). Zobrazí se HWND stránky pomocí parametru `hwndParent` metody <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>. Hostované okno by se mělo vytvořit jako podřízený prvek tohoto HWND.  
  
5. Po vytvoření hostitelského okna vraťte HWND hostovaného okna. Chcete-li hostovat jeden nebo více ovládacích prvků Win32, obvykle vytvoříte hostitelské okno jako podřízený prvek HWND a nastavíte podřízené prvky tohoto hostitelského okna. Zabalení ovládacích prvků v hostitelském okně poskytuje jednoduchý způsob, jak může vaše stránka WPF přijímat oznámení z ovládacích prvků, což se zabývá konkrétními problémy Win32 s oznámeními v rámci hranice HWND.  
  
6. Zpracuje vybrané zprávy odeslané do hostitelského okna, například oznámení z podřízených ovládacích prvků. Můžete to provést dvěma způsoby.  
  
    - Pokud dáváte přednost zpracování zpráv ve vaší hostující třídě, přepište metodu <xref:System.Windows.Interop.HwndHost.WndProc%2A> třídy <xref:System.Windows.Interop.HwndHost>.  
  
    - Pokud dáváte přednost tomu, aby WPF zpracoval zprávy, zpracujte v kódu na pozadí událost <xref:System.Windows.Interop.HwndHost> třídy <xref:System.Windows.Interop.HwndHost.MessageHook>. K této události dochází u každé zprávy, která je přijata hostovaným oknem. Pokud zvolíte tuto možnost, musíte přesto přepsat <xref:System.Windows.Interop.HwndHost.WndProc%2A>, ale budete potřebovat jenom minimální implementaci.  
  
7. Přepsat <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> a <xref:System.Windows.Interop.HwndHost.WndProc%2A> metody <xref:System.Windows.Interop.HwndHost>. Tyto metody je nutné přepsat, aby splňovaly <xref:System.Windows.Interop.HwndHost> kontraktu, ale je možné, že budete muset pouze zadat minimální implementaci.  
  
8. V souboru kódu na pozadí vytvořte instanci třídy hostování ovládacího prvku a nastavte ji jako podřízenou prvku <xref:System.Windows.Controls.Border>, který je určen pro hostování okna.  
  
9. Komunikujte s hostovaným oknem odesláním zpráv Microsoft Windows a zpracováním zpráv ze svých podřízených oken, jako jsou oznámení odesílaná ovládacími prvky.  
  
<a name="page_layout"></a>   
## <a name="implement-the-page-layout"></a>Implementace rozložení stránky  
 Rozložení stránky WPF, která je hostitelem ovládacího prvku ListBox, se skládá ze dvou oblastí. Levá strana stránky je hostitelem několika ovládacích prvků WPF, které poskytují [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], které umožňují manipulaci s ovládacím prvkem Win32. V pravém horním rohu stránky je čtvercová oblast pro hostovaný ovládací prvek seznamu.  
  
 Kód pro implementaci tohoto rozložení je poměrně jednoduchý. Kořenový prvek je <xref:System.Windows.Controls.DockPanel>, který má dva podřízené elementy. První je <xref:System.Windows.Controls.Border> prvek, který je hostitelem ovládacího prvku ListBox. Zabírá v pravém horním rohu stránky 200x200 čtverec. Druhým je <xref:System.Windows.Controls.StackPanel> prvek, který obsahuje sadu ovládacích prvků WPF, které zobrazují informace a umožňují manipulaci s ovládacím prvkem seznamu nastavením vlastností zpřístupněných operací. Pro každý element, který je podřízených prvků <xref:System.Windows.Controls.StackPanel>, přečtěte si referenční materiál pro různé prvky, které se používají k podrobnostem o tom, jaké jsou tyto prvky nebo co dělají, jsou uvedeny v níže uvedeném příkladu kódu, ale nebudete je vysvětlit (základní model vzájemné operace nevyžaduje žádný z nich, je k dispozici pro přidání některé interaktivity k ukázce).  
  
 [!code-xaml[WPFHostingWin32Control#WPFUI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml#wpfui)]  
  
<a name="host_class"></a>   
## <a name="implement-a-class-to-host-the-microsoft-win32-control"></a>Implementace třídy pro hostování ovládacího prvku Microsoft Win32  
 Jádrem této ukázky je třída, která je ve skutečnosti hostitelem ovládacího prvku, ControlHost.cs. Dědí z <xref:System.Windows.Interop.HwndHost>. Konstruktor přijímá dva parametry, výšku a šířku, které odpovídají výšce a šířce <xref:System.Windows.Controls.Border> prvku, který je hostitelem ovládacího prvku ListBox. Tyto hodnoty se používají později, aby se zajistilo, že velikost ovládacího prvku odpovídá prvku <xref:System.Windows.Controls.Border>.  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostClass](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostclass)]
 [!code-vb[WPFHostingWin32Control#ControlHostClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostclass)]  
  
 K dispozici je také sada konstant. Tyto konstanty jsou z velké části z Winuser. h a umožňují při volání funkcí Win32 použít konvenční názvy.  
  
 [!code-csharp[WPFHostingWin32Control#ControlHostConstants](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#controlhostconstants)]
 [!code-vb[WPFHostingWin32Control#ControlHostConstants](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#controlhostconstants)]  
  
<a name="buildwindowcore"></a>   
### <a name="override-buildwindowcore-to-create-the-microsoft-win32-window"></a>Přepsat BuildWindowCore a vytvořit okno Microsoft Win32  
 Tuto metodu přepíšete, chcete-li vytvořit okno Win32, které bude hostováno stránkou, a vytvořit propojení mezi oknem a stránkou. Vzhledem k tomu, že tato ukázka zahrnuje hostování ovládacího prvku seznamu, vytvoří se dvě okna. První je okno, které je skutečně hostováno stránkou WPF. Ovládací prvek ListBox je vytvořen jako podřízený objekt tohoto okna.  
  
 Důvodem tohoto přístupu je zjednodušení procesu přijímání oznámení z ovládacího prvku. Třída <xref:System.Windows.Interop.HwndHost> umožňuje zpracovat zprávy odesílané do okna, které je hostitelem. Pokud je přímo hostitelem ovládacího prvku Win32, obdržíte zprávy odeslané do interní smyčky zpráv ovládacího prvku. Můžete zobrazit ovládací prvek a odeslat zprávy, ale neobdržíte oznámení, která ovládací prvek odešle do svého nadřazeného okna. To mimo jiné znamená, že nemáte žádný způsob, jak zjistit, kdy uživatel komunikuje s ovládacím prvkem. Místo toho vytvořte okno hostitele a nastavte ho jako podřízenou položku tohoto okna. To vám umožní zpracovat zprávy pro hostitelské okno, včetně oznámení, která mu ovládací prvek odesílají. Pro usnadnění, protože hostitelské okno je o něco větší než jednoduchá obálka pro ovládací prvek, bude balíček označován jako ovládací prvek seznamu.  
  
<a name="create_the_window_and_listbox"></a>   
#### <a name="create-the-host-window-and-listbox-control"></a>Vytvoření hostitelského okna a ovládacího prvku seznamu  
 Můžete použít PInvoke k vytvoření hostitelského okna pro ovládací prvek vytvořením a registrací třídy okna a tak dále. Mnohem jednodušší přístup je však vytvořit okno s předdefinovanou "" statickou "třídou" Window ". To vám poskytne postup v okně, který potřebujete pro příjem oznámení z ovládacího prvku a vyžaduje minimální kódování.  
  
 Vlastnost HWND ovládacího prvku je vystavena prostřednictvím vlastnosti jen pro čtení, aby ji hostitelská stránka mohla použít k posílání zpráv do ovládacího prvku.  
  
 [!code-csharp[WPFHostingWin32Control#IntPtrProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#intptrproperty)]
 [!code-vb[WPFHostingWin32Control#IntPtrProperty](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#intptrproperty)]  
  
 Ovládací prvek ListBox je vytvořen jako podřízený uzel hostitelského okna. Výška a šířka obou oken je nastavena na hodnoty předané do konstruktoru, popsané výše. Tím se zajistí, že velikost hostitelského okna a ovládacího prvku je stejná jako vyhrazená oblast na stránce.  Po vytvoření okna ukázka vrátí objekt <xref:System.Runtime.InteropServices.HandleRef>, který obsahuje HWND okna hostitele.  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCore](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcore)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCore](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcore)]  
  
 [!code-csharp[WPFHostingWin32Control#BuildWindowCoreHelper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#buildwindowcorehelper)]
 [!code-vb[WPFHostingWin32Control#BuildWindowCoreHelper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#buildwindowcorehelper)]  
  
<a name="destroywindow_wndproc"></a>   
### <a name="implement-destroywindow-and-wndproc"></a>Implementace DestroyWindow a WndProc  
 Kromě <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>musíte také přepsat metody <xref:System.Windows.Interop.HwndHost.WndProc%2A> a <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> <xref:System.Windows.Interop.HwndHost>. V tomto příkladu jsou zprávy pro ovládací prvek zpracovávány obslužnou rutinou <xref:System.Windows.Interop.HwndHost.MessageHook>, takže implementace <xref:System.Windows.Interop.HwndHost.WndProc%2A> a <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> je minimální. V případě <xref:System.Windows.Interop.HwndHost.WndProc%2A>nastavte `handled` na `false` pro indikaci, že zpráva nebyla zpracována a vrátí hodnotu 0. V případě <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A>jednoduše zničí okno.  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroy](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroy)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroy](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroy)]  
  
 [!code-csharp[WPFHostingWin32Control#WndProcDestroyHelper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/ControlHost.cs#wndprocdestroyhelper)]
 [!code-vb[WPFHostingWin32Control#WndProcDestroyHelper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/ControlHost.vb#wndprocdestroyhelper)]  
  
<a name="host_the_control"></a>   
## <a name="host-the-control-on-the-page"></a>Hostování ovládacího prvku na stránce  
 Chcete-li hostovat ovládací prvek na stránce, nejprve vytvořte novou instanci třídy `ControlHost`. Předejte výšku a šířku prvku ohraničení, který obsahuje ovládací prvek (`ControlHostElement`) do konstruktoru `ControlHost`. Tím se zajistí, že se seznam bude správně měnit. Potom můžete ovládací prvek hostovat na stránce přiřazením objektu `ControlHost` k vlastnosti <xref:System.Windows.Controls.Decorator.Child%2A> <xref:System.Windows.Controls.Border>hostitele.  
  
 Ukázka připojí obslužnou rutinu k události <xref:System.Windows.Interop.HwndHost.MessageHook> `ControlHost` pro příjem zpráv z ovládacího prvku. Tato událost je vyvolána pro každou zprávu odeslanou do hostovaného okna. V tomto případě se jedná o zprávy odesílané do okna, které zabalí skutečný ovládací prvek seznamu, včetně oznámení z ovládacího prvku. Ukázka volá metodu SendMessage pro získání informací z ovládacího prvku a pro úpravu jeho obsahu. Podrobnosti o tom, jak stránka komunikuje s ovládacím prvkem, jsou popsány v následující části.  
  
> [!NOTE]
> Všimněte si, že existují dvě deklarace PInvoke pro SendMessage. To je nezbytné, protože jeden používá parametr `wParam` k předání řetězce a druhý ho používá k předání celého čísla. Pro každý podpis potřebujete samostatnou deklaraci, abyste zajistili správné zařazení dat.  
  
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
  
 Chcete-li připojit položky, odešlete seznam [`LB_ADDSTRING` zprávu](/windows/desktop/Controls/lb-addstring). Chcete-li odstranit položky, odešlete [`LB_GETCURSEL`](/windows/desktop/Controls/lb-getcursel) , abyste získali index aktuálního výběru a pak [`LB_DELETESTRING`](/windows/desktop/Controls/lb-deletestring) položku odstranili. Ukázka také odesílá [`LB_GETCOUNT`](/windows/desktop/Controls/lb-getcount)a pomocí vrácené hodnoty aktualizuje zobrazení, které zobrazuje počet položek. Obě tyto instance [`SendMessage`](/windows/desktop/api/winuser/nf-winuser-sendmessage) používají jeden z deklarací PInvoke popsaných v předchozí části.  
  
 [!code-csharp[WPFHostingWin32Control#AppendDeleteText](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFHostingWin32Control/CSharp/Page1.xaml.cs#appenddeletetext)]
 [!code-vb[WPFHostingWin32Control#AppendDeleteText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFHostingWin32Control/VisualBasic/Page1.xaml.vb#appenddeletetext)]  
  
 Když uživatel vybere položku nebo změní jejich výběr, ovládací prvek upozorní okno hostitele tím, že pošle [`WM_COMMAND` zprávu](/windows/desktop/menurc/wm-command), která vyvolává událost <xref:System.Windows.Interop.HwndHost.MessageHook> stránky. Obslužná rutina obdrží stejné informace jako hlavní okno v rámci okna hostitele. Také předává odkaz na logickou hodnotu, `handled`. Nastavením `handled` `true` označíte, že jste zprávu zpracovali a ještě není potřeba žádné další zpracování.  
  
 [`WM_COMMAND`](/windows/desktop/menurc/wm-command) se odesílá z nejrůznějších důvodů, takže je nutné prostudovat ID oznámení, abyste zjistili, jestli se jedná o událost, kterou chcete zpracovat. ID je obsaženo v horním slově parametru `wParam`. Ukázka používá k extrakci IDENTIFIKÁTORu bitové operátory. Pokud uživatel provedl nebo změnil výběr, bude ID [`LBN_SELCHANGE`](/windows/desktop/Controls/lbn-selchange).  
  
 Při přijetí [`LBN_SELCHANGE`](/windows/desktop/Controls/lbn-selchange) získá ukázka index vybrané položky odesláním ovládacího prvku [`LB_GETCURSEL` zprávu](/windows/desktop/Controls/lb-getcursel). Chcete-li získat text, je třeba nejprve vytvořit <xref:System.Text.StringBuilder>. Pak ovládacímu prvku odešlete [`LB_GETTEXT`ovou zprávu](/windows/desktop/Controls/lb-gettext). Předejte prázdný <xref:System.Text.StringBuilder> objekt jako parametr `wParam`. Když [`SendMessage`](/windows/desktop/api/winuser/nf-winuser-sendmessage) vrátí, <xref:System.Text.StringBuilder> bude obsahovat text vybrané položky. Toto použití [`SendMessage`](/windows/desktop/api/winuser/nf-winuser-sendmessage) vyžaduje ještě jinou deklaraci PInvoke.  
  
 Nakonec nastavte `handled` na `true`, aby označovala, že zpráva byla zpracována.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Interop.HwndHost>
- [Vzájemná spolupráce grafického subsystému WPF a systému Win32](wpf-and-win32-interoperation.md)
- [Návod: Moje první desktopová aplikace WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
