---
title: Architektura vstupu interoperability Windows Forms a WPF
ms.date: 03/30/2017
helpviewer_keywords:
- input architecture [WPF interoperability]
- messages [WPF]
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- modeless forms [WPF]
- ElementHost keyboard and messages [WPF]
- keyboard interoperation [WPF]
- WindowsFormsHost keyboard and messages [WPF]
- modeless dialog boxes [WPF]
ms.assetid: 0eb6f137-f088-4c5e-9e37-f96afd28f235
ms.openlocfilehash: f9fb5a0d2a23d2ad23aa3886ce25edb999b50678
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59160976"
---
# <a name="windows-forms-and-wpf-interoperability-input-architecture"></a>Architektura vstupu interoperability Windows Forms a WPF
Vzájemné spolupráce mezi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] vyžaduje vstupní zpracování příslušné klávesové obou technologií. Toto téma popisuje, jak implementovat tyto technologie klávesnice a umožňuje hladký vzájemná spolupráce grafického subsystému v hybridních aplikacích zpracování zpráv.  
  
 Toto téma obsahuje následující témata:  
  
-   Nemodální formuláře a dialogová okna  
  
-   Windowsformshost – klávesnice a zpracování zpráv  
  
-   Elementhost – klávesnice a zpracování zpráv  
  
## <a name="modeless-forms-and-dialog-boxes"></a>Nemodální formuláře a dialogová okna  
 Volání <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A> metodu <xref:System.Windows.Forms.Integration.WindowsFormsHost> element pro otevření nemodální formuláře nebo dialogového okna pole z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]– aplikace založené na.  
  
 Volání <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> metodu <xref:System.Windows.Forms.Integration.ElementHost> CTRL otevřete položku nemodální [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stránku [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]– aplikace založené na.  
  
## <a name="windowsformshost-keyboard-and-message-processing"></a>Windowsformshost – klávesnice a zpracování zpráv  
 Když jsou hostované ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]– aplikace založené na [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] klávesnice a zprávy zpracování se skládá z následujících akcí:  
  
-   <xref:System.Windows.Forms.Integration.WindowsFormsHost> Třídy získá zprávy z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] smyčky zpráv, které je implementované <xref:System.Windows.Interop.ComponentDispatcher> třídy.  
  
-   <xref:System.Windows.Forms.Integration.WindowsFormsHost> Třída vytvoří náhradní [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] smyčky zpráv zajistit, že běžný [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] neproběhne zpracování klávesnice.  
  
-   <xref:System.Windows.Forms.Integration.WindowsFormsHost> Implementuje třída <xref:System.Windows.Interop.IKeyboardInputSink> rozhraní ke koordinaci fokus správy s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
-   <xref:System.Windows.Forms.Integration.WindowsFormsHost> Ovládací prvky zaregistrovat se a začněte jejich smyčky zpráv.  
  
 Následující části popisují tyto části procesu podrobněji.  
  
### <a name="acquiring-messages-from-the-wpf-message-loop"></a>Získání zprávy ze smyčky zpráv WPF  
 <xref:System.Windows.Interop.ComponentDispatcher> Třída implementuje správce smyčky zpráv pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. <xref:System.Windows.Interop.ComponentDispatcher> Třída poskytuje zachytávání externí klientům, aby se zprávy před povolit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zpracovává je.  
  
 Součinnost implementace obslužné rutiny <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> událost, která umožňuje [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacích prvků pro zpracování zpráv před [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládacích prvků.  
  
### <a name="surrogate-windows-forms-message-loop"></a>Náhradní Windows Forms zpráva smyčky  
 Ve výchozím nastavení <xref:System.Windows.Forms.Application?displayProperty=nameWithType> třída obsahuje primární zpráva smyčky pro [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] aplikací. Během vzájemná spolupráce grafického subsystému [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] zprávu, smyčka nezpracovává zprávy. Proto musí být reprodukovat tuto logiku. Obslužná rutina pro <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> události provede následující kroky:  
  
1.  Filtry zpráv pomocí <xref:System.Windows.Forms.IMessageFilter> rozhraní.  
  
2.  Volání <xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=nameWithType> metody.  
  
3.  Přeloží a odešle zprávu, pokud se vyžaduje.  
  
4.  Předá zprávu do hostitelského ovládacího prvku, pokud zprávu zpracovat žádné další ovládací prvky.  
  
### <a name="ikeyboardinputsink-implementation"></a>Implementace IKeyboardInputSink  
 Smyčky zpráv náhradní zpracovává správu klávesnice. Proto <xref:System.Windows.Interop.IKeyboardInputSink.TabInto%2A?displayProperty=nameWithType> je jediná metoda <xref:System.Windows.Interop.IKeyboardInputSink> člena, který vyžaduje implementaci v <xref:System.Windows.Forms.Integration.WindowsFormsHost> třídy.  
  
 Ve výchozím nastavení <xref:System.Windows.Interop.HwndHost> třídy vrátí `false` pro jeho <xref:System.Windows.Interop.HwndHost.System%23Windows%23Interop%23IKeyboardInputSink%23TabInto%2A> implementace. To zabraňuje tabulátor z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mít pod kontrolou [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacího prvku.  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Provádění <xref:System.Windows.Interop.IKeyboardInputSink.TabInto%2A?displayProperty=nameWithType> metoda provede následující kroky:  
  
1.  Najde první nebo poslední [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek, který je obsažen <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládacího prvku a, která může získat fokus. Ovládací prvek Výběr závisí na informace o procházení.  
  
2.  Nastaví fokus na ovládací prvek a vrátí `true`.  
  
3.  Pokud žádný ovládací prvek může získat fokus, vrátí `false`.  
  
### <a name="windowsformshost-registration"></a>WindowsFormsHost Registration  
 Když v okně popisovače <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládací prvek je vytvořen, <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontrolní volání interní statická metoda, která se registruje jeho přítomnost smyčky zpráv.  
  
 Během registrace <xref:System.Windows.Forms.Integration.WindowsFormsHost> prozkoumá ovládacího prvku smyčky zpráv. Pokud se nespustil smyčky zpráv <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> se vytvoří obslužnou rutinu události. Smyčky zpráv se považuje za běžet, když <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> obslužná rutina události je připojen.  
  
 Při zničení popisovač okna <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládací prvek samotné zruší registraci.  
  
## <a name="elementhost-keyboard-and-message-processing"></a>Elementhost – klávesnice a zpracování zpráv  
 Když jsou hostované ve [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] aplikace, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klávesnice a zprávy zpracování se skládá z následujících akcí:  
  
-   <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.IKeyboardInputSink>, a <xref:System.Windows.Interop.IKeyboardInputSite> implementace rozhraní.  
  
-   Přecházení pomocí tabulátoru a šipku klíče.  
  
-   Příkaz a dialogové okno pole klíče.  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] zpracování akcelerátoru.  
  
 Následující části podrobněji v následujících částech.  
  
### <a name="interface-implementations"></a>Implementace rozhraní  
 V [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], zprávy týkající se klávesnice jsou směrovány na popisovač okna ovládacího prvku, který má právě fokus. V <xref:System.Windows.Forms.Integration.ElementHost> ovládacího prvku, tyto zprávy jsou směrovány na hostovaný prvek. Jak toho dosáhnout, <xref:System.Windows.Forms.Integration.ElementHost> poskytuje ovládací prvek <xref:System.Windows.Interop.HwndSource> instance. Pokud <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek má fokus, <xref:System.Windows.Interop.HwndSource> instance směruje většina klávesnice tak, aby ji mohou být zpracovány [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.InputManager> třídy.  
  
 <xref:System.Windows.Interop.HwndSource> Implementuje třída <xref:System.Windows.Interop.IKeyboardInputSink> a <xref:System.Windows.Interop.IKeyboardInputSite> rozhraní.  
  
 Vzájemná spolupráce grafického subsystému klávesnice závisí na implementaci <xref:System.Windows.Interop.IKeyboardInputSite.OnNoMoreTabStops%2A> metodu pro popisovač klávesu TAB a šipku klíče vstup, který přesouvá fokus z hostované elementy.  
  
### <a name="tabbing-and-arrow-keys"></a>Tabbing a klávesy se šipkami  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Logiku výběru je namapována na <xref:System.Windows.Interop.HwndSource.System%23Windows%23Interop%23IKeyboardInputSink%23TabInto%2A> a <xref:System.Windows.Interop.IKeyboardInputSite.OnNoMoreTabStops%2A> klíče metody k implementaci kartu a šipku navigace. Přepsání <xref:System.Windows.Forms.Integration.ElementHost.Select%2A> metoda provede toto mapování.  
  
### <a name="command-keys-and-dialog-box-keys"></a>Příkaz pole klíčů a dialogové okno  
 Poskytnout [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] první příležitosti ke zpracování příkazu a dialogové okno klíče [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] předběžného zpracování příkazu je připojen k <xref:System.Windows.Interop.IKeyboardInputSink.TranslateAccelerator%2A> metody. Přepsání <xref:System.Windows.Forms.Control.ProcessCmdKey%2A?displayProperty=nameWithType> metoda připojí tyto technologie.  
  
 S <xref:System.Windows.Interop.IKeyboardInputSink.TranslateAccelerator%2A> metody hostované prvky dokáže zpracovat všechny klíčová zpráva WM_KEYDOWN, WM_KEYUP, WM_SYSKEYDOWN nebo WM_SYSKEYUP, včetně příkaz klíčů, jako je karta, ENTER, ESC a šipka. Pokud klíčová zpráva není zpracována, je odeslána [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] předchůdce hierarchie pro zpracování.  
  
### <a name="accelerator-processing"></a>Zpracování akcelerátoru  
 Ke zpracování akcelerátory správně, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] akcelerátoru zpracování musí být připojené k [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.AccessKeyManager> třídy. Kromě toho všechny zprávy WM_CHAR musí správně směrovat na hostované elementy.  
  
 Protože výchozí <xref:System.Windows.Interop.HwndSource> provádění <xref:System.Windows.Interop.IKeyboardInputSink.TranslateChar%2A> vrátí metoda `false`, WM_CHAR zprávy jsou zpracovány pomocí následujícího postupu:  
  
-   <xref:System.Windows.Forms.Control.IsInputChar%2A?displayProperty=nameWithType> Je metoda potlačena za účelem zajištění, že všechny zprávy WM_CHAR jsou předávány na hostované elementy.  
  
-   Pokud se stiskne klávesu ALT, je zpráva WM_SYSCHAR. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] není předběžně zpracovat tuto zprávu přes <xref:System.Windows.Forms.Control.IsInputChar%2A> metody. Proto <xref:System.Windows.Forms.Control.ProcessMnemonic%2A> je přepsána metoda k dotazu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.AccessKeyManager> pro registrované akcelerátoru. Pokud se najde registrované akcelerátoru <xref:System.Windows.Input.AccessKeyManager> zpracovává je.  
  
-   Pokud se stiskne klávesu ALT, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.InputManager> třída zpracovává neošetřené vstup. Pokud je vstup akcelerátoru, <xref:System.Windows.Input.AccessKeyManager> zpracovává je. <xref:System.Windows.Input.InputManager.PostProcessInput> Události se postará služba za WM_CHAR zprávy, které nebyly zpracovány.  
  
 Když uživatel stiskne klávesu ALT, akcelerátoru vizuální prvky jsou zobrazeny na celý formulář. Pro podporu tohoto chování všech <xref:System.Windows.Forms.Integration.ElementHost> ovládacích prvků na aktivního formuláře příjem zpráv WM_SYSKEYDOWN, bez ohledu na to, které ovládací prvek má fokus.  
  
 Zprávy jsou odesílány pouze <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvky ve formuláři aktivní.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A>
- <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A>
- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Návod: Hostování složeného ovládacího prvku Windows Forms ve WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Vzájemná spolupráce grafického subsystému WPF a systému Win32](wpf-and-win32-interoperation.md)
