---
title: Architektura vstupu interoperability Windows Forms a WPF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a246a3297d212eabc31bf2ac9d000aeb56329d09
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="windows-forms-and-wpf-interoperability-input-architecture"></a>Architektura vstupu interoperability Windows Forms a WPF
Součinnosti mezi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] vyžaduje, aby obě technologie bylo zpracování vstupních příslušné klávesnice. Toto téma popisuje, jak implementovat tyto technologie klávesnici a k povolení technologie smooth vzájemná spolupráce v hybridní aplikace zpracování zpráv.  
  
 Toto téma obsahuje následující témata:  
  
-   Nemodální formulářích a dialogových oknech  
  
-   WindowsFormsHost klávesnici a zpracování zpráv  
  
-   Elementhost – klávesnici a zpracování zpráv  
  
## <a name="modeless-forms-and-dialog-boxes"></a>Nemodální formulářích a dialogových oknech  
 Volání <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A> metoda na <xref:System.Windows.Forms.Integration.WindowsFormsHost> element pro otevření nemodální formulář nebo dialogové okno pole z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]– na základě aplikace.  
  
 Volání <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> metodu <xref:System.Windows.Forms.Integration.ElementHost> řízení otevřete nemodální [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stránky v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]– aplikace založené na.  
  
## <a name="windowsformshost-keyboard-and-message-processing"></a>WindowsFormsHost klávesnici a zpracování zpráv  
 Když hostované [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]– aplikace založené na [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] klávesnici a zpracování se skládá z následujících zpráv:  
  
-   <xref:System.Windows.Forms.Integration.WindowsFormsHost> Třída získá zprávy z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve smyčce zpráv, které je implementované <xref:System.Windows.Interop.ComponentDispatcher> – třída.  
  
-   <xref:System.Windows.Forms.Integration.WindowsFormsHost> Třída vytvoří náhradní [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] zpráva smyčky zajistit, že běžném provozu [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] neproběhne zpracování klávesnice.  
  
-   <xref:System.Windows.Forms.Integration.WindowsFormsHost> Třída implementuje <xref:System.Windows.Interop.IKeyboardInputSink> rozhraní pro koordinaci fokus správy s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
-   <xref:System.Windows.Forms.Integration.WindowsFormsHost> Ovládací prvky se registrují spustit jejich zpráva smyčky.  
  
 Následující části popisují tyto části procesu podrobněji.  
  
### <a name="acquiring-messages-from-the-wpf-message-loop"></a>Získávání zprávy z grafického subsystému WPF zpráva smyčky  
 <xref:System.Windows.Interop.ComponentDispatcher> Třída implementuje smyčky Správce zpráv pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. <xref:System.Windows.Interop.ComponentDispatcher> Třída poskytuje háky externí klientům filtrovat zprávy před povolit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je zpracuje.  
  
 Obslužné rutiny součinnosti implementace <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> událost, která umožňuje [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky ke zpracování zpráv před [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky.  
  
### <a name="surrogate-windows-forms-message-loop"></a>Náhradní Windows Forms zpráva smyčky  
 Ve výchozím nastavení <xref:System.Windows.Forms.Application?displayProperty=nameWithType> třída obsahuje primární zpráva smyčky pro [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] aplikace. Během vzájemná spolupráce [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] zpráva smyčky nezpracovává zprávy. Proto musí být reprodukovat tuto logiku. Obslužná rutina pro <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> událostí provede následující kroky:  
  
1.  Filtry zpráv pomocí <xref:System.Windows.Forms.IMessageFilter> rozhraní.  
  
2.  Volání <xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=nameWithType> metoda.  
  
3.  Odeslání zprávy, je-li vyžadován a překládá.  
  
4.  Předá zprávu do hostování ovládacího prvku, pokud zprávu zpracovat žádné další ovládací prvky.  
  
### <a name="ikeyboardinputsink-implementation"></a>Implementace IKeyboardInputSink  
 Zpráva smyčky náhradní zpracovává klávesnice správy. Proto <xref:System.Windows.Interop.IKeyboardInputSink.TabInto%2A?displayProperty=nameWithType> metoda je jedinou <xref:System.Windows.Interop.IKeyboardInputSink> člena, který vyžaduje implementace v <xref:System.Windows.Forms.Integration.WindowsFormsHost> – třída.  
  
 Ve výchozím nastavení <xref:System.Windows.Interop.HwndHost> vrací `false` pro jeho <xref:System.Windows.Interop.HwndHost.System%23Windows%23Interop%23IKeyboardInputSink%23TabInto%2A> implementace. To brání použití tabulátoru z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] řídit k [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacího prvku.  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> Implementace <xref:System.Windows.Interop.IKeyboardInputSink.TabInto%2A?displayProperty=nameWithType> metoda provede následující kroky:  
  
1.  Najde první nebo poslední [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek, který je obsažený v <xref:System.Windows.Forms.Integration.WindowsFormsHost> řízení a které mohou získat fokus. Výběr ovládacího prvku závisí na traversal informace.  
  
2.  Nastaví fokus na ovládací prvek a vrátí `true`.  
  
3.  Pokud žádnou kontrolu mohou získat fokus, vrátí `false`.  
  
### <a name="windowsformshost-registration"></a>WindowsFormsHost registrace  
 Když popisovač okna <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládací prvek je vytvořen, <xref:System.Windows.Forms.Integration.WindowsFormsHost> řízení volá interní statickou metodu, která registruje jeho přítomnosti zpráva smyčky.  
  
 Během registrace <xref:System.Windows.Forms.Integration.WindowsFormsHost> řízení prozkoumá smyčce zpráv. Pokud zpráva smyčky nebyla spuštěna, <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> vytvořena obslužná rutina události. Zpráva smyčky považuje, aby byl spuštěn, když <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> obslužné rutiny události je připojen.  
  
 Po zničení popisovač okna, <xref:System.Windows.Forms.Integration.WindowsFormsHost> řízení samotné odebere registrace.  
  
## <a name="elementhost-keyboard-and-message-processing"></a>Elementhost – klávesnici a zpracování zpráv  
 Když hostované [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] aplikace, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klávesnici a zpracování se skládá z následujících zpráv:  
  
-   <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.IKeyboardInputSink>, a <xref:System.Windows.Interop.IKeyboardInputSite> rozhraní implementace.  
  
-   Použití tabulátoru a šipku klíče.  
  
-   Příkaz klíčích a dialogové okno pole.  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]zpracování akcelerátoru.  
  
 Následující části popisují tyto části podrobněji.  
  
### <a name="interface-implementations"></a>Implementace rozhraní  
 V [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)], jsou směrovány popisovač okna Ovládací prvek, který má právě fokus klávesnice zprávy. V <xref:System.Windows.Forms.Integration.ElementHost> řízení, tyto zprávy jsou směrovány do hostované elementu. K tomu <xref:System.Windows.Forms.Integration.ElementHost> řízení <xref:System.Windows.Interop.HwndSource> instance. Pokud <xref:System.Windows.Forms.Integration.ElementHost> řízení má právě fokus, <xref:System.Windows.Interop.HwndSource> instance směruje většina klávesnice vstup, aby ji může zpracovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.InputManager> třídy.  
  
 <xref:System.Windows.Interop.HwndSource> Třída implementuje <xref:System.Windows.Interop.IKeyboardInputSink> a <xref:System.Windows.Interop.IKeyboardInputSite> rozhraní.  
  
 Vzájemná spolupráce klávesnice závisí na implementaci <xref:System.Windows.Interop.IKeyboardInputSite.OnNoMoreTabStops%2A> metoda popisovač tabulátor a šipku klíče vstup, který přesouvá fokus mimo hostované elementy.  
  
### <a name="tabbing-and-arrow-keys"></a>Tabbing a klávesy se šipkami  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] Logiku výběru je namapovaný na <xref:System.Windows.Interop.HwndSource.System%23Windows%23Interop%23IKeyboardInputSink%23TabInto%2A> a <xref:System.Windows.Interop.IKeyboardInputSite.OnNoMoreTabStops%2A> metody k implementaci KARTĚ a šipku klíče navigace. Přepsání <xref:System.Windows.Forms.Integration.ElementHost.Select%2A> metoda provede toto mapování.  
  
### <a name="command-keys-and-dialog-box-keys"></a>Příkaz klíčích a dialogové okno pole  
 Umožnit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] první příležitostí ke zpracování příkazu klíčích a dialogové okno, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] předběžného zpracování příkazu je připojený k <xref:System.Windows.Interop.IKeyboardInputSink.TranslateAccelerator%2A> metoda. Přepsání <xref:System.Windows.Forms.Control.ProcessCmdKey%2A?displayProperty=nameWithType> metoda připojení dvě technologie.  
  
 Pomocí <xref:System.Windows.Interop.IKeyboardInputSink.TranslateAccelerator%2A> metody hostované elementy dokáže zpracovat jakékoli klíče zprávy, jako je například WM_KEYDOWN WM_KEYUP, WM_SYSKEYDOWN nebo WM_SYSKEYUP, včetně příkaz klíčů, jako jsou karty, zadejte, ESC a šipku klíče. Pokud nejsou zpracovávány klíčová zpráva, bude odeslán [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] předchůdce hierarchie pro zpracování.  
  
### <a name="accelerator-processing"></a>Zpracování akcelerátoru  
 Při zpracování akcelerátorů správně, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] akcelerátoru zpracování musí být připojen k [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.AccessKeyManager> třídy. Kromě toho všechny zprávy WM_CHAR musejí správně směrovat na hostované elementy.  
  
 Protože výchozí <xref:System.Windows.Interop.HwndSource> implementace <xref:System.Windows.Interop.IKeyboardInputSink.TranslateChar%2A> metoda vrátí `false`, zpracování zpráv WM_CHAR pomocí následujícího postupu:  
  
-   <xref:System.Windows.Forms.Control.IsInputChar%2A?displayProperty=nameWithType> Je metoda potlačena za účelem Ujistěte se, že všechny zprávy WM_CHAR předávány na hostované elementy.  
  
-   Pokud není stisknuta klávesa ALT, zpráva je WM_SYSCHAR. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]není předběžné zpracování této zprávy prostřednictvím <xref:System.Windows.Forms.Control.IsInputChar%2A> metoda. Proto <xref:System.Windows.Forms.Control.ProcessMnemonic%2A> je metoda potlačena k dotazu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.AccessKeyManager> pro registrované akcelerátoru. Pokud se akcelerátor registrovaných nenajde, <xref:System.Windows.Input.AccessKeyManager> procesy.  
  
-   Pokud není stisknuta klávesa ALT, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.InputManager> třída zpracovává neošetřené vstup. Pokud vstup je akcelerátor, <xref:System.Windows.Input.AccessKeyManager> procesy. <xref:System.Windows.Input.InputManager.PostProcessInput> Událost je zpracovávána WM_CHAR zprávy, které nebyly zpracovány.  
  
 Po stisknutí klávesy ALT akcelerátoru vizuální upozornění se zobrazí na celý formulář. Pro podporu toto chování všech <xref:System.Windows.Forms.Integration.ElementHost> ovládacích prvků na formuláři active přijímat zprávy WM_SYSKEYDOWN, bez ohledu na to, které má ovládací prvek fokus.  
  
 Zprávy jsou odesílány pouze <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvky ve formuláři aktivní.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A>  
 <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Návod: Hostování složeného ovládacího prvku Windows Forms v subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [Vzájemná spolupráce grafického subsystému WPF a systému Win32](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)
