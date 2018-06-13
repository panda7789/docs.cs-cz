---
title: Sdílení smyčky zpráv mezi systémem Win32 a platformou WPF
ms.date: 03/30/2017
helpviewer_keywords:
- Win32 code [WPF], sharing message loops
- message loops [WPF]
- sharing message loops [WPF]
- interoperability [WPF], Win32
ms.assetid: 39ee888c-e5ec-41c8-b11f-7b851a554442
ms.openlocfilehash: 35a908cc26e6b70c9acd8732521837f2b20eaf5b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548812"
---
# <a name="sharing-message-loops-between-win32-and-wpf"></a>Sdílení smyčky zpráv mezi systémem Win32 a platformou WPF
Toto téma popisuje, jak implementovat smyčku zpráv pro spolupráci s [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], buď pomocí stávající zpráva smyčky ohrožení v <xref:System.Windows.Threading.Dispatcher> nebo vytvořením smyčku samostatnou zprávu na [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] postranní součinnosti kódu.  
  
## <a name="componentdispatcher-and-the-message-loop"></a>ComponentDispatcher a zpráva smyčky  
 Normální scénář pro podporu událostí vzájemná spolupráce a klávesnice je implementace <xref:System.Windows.Interop.IKeyboardInputSink>, nebo podtřídou ze třídy, které již implementovat <xref:System.Windows.Interop.IKeyboardInputSink>, jako například <xref:System.Windows.Interop.HwndSource> nebo <xref:System.Windows.Interop.HwndHost>. Podpora klávesnice jímka ale neřeší všechny možné zpráva smyčky potřeb, které může mít při odesílání a přijímání zpráv mezi součinnosti hranice. Abyste formalizovat architektura smyčky zpráv aplikace [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje <xref:System.Windows.Interop.ComponentDispatcher> třídy, která definuje protokolu pro zpráva smyčky podle.  
  
 <xref:System.Windows.Interop.ComponentDispatcher> je statická třída, která zveřejňuje několik členů. Volající vlákno je implicitně svázaný oboru jednotlivých metod. Zpráva smyčky musí volat některým z nich [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] v kritické dobu (jak je definována v další části).  
  
 <xref:System.Windows.Interop.ComponentDispatcher> poskytuje události, které můžete naslouchat ostatní součásti (například klávesnice jímky). <xref:System.Windows.Threading.Dispatcher> Třídy volání všechny příslušné <xref:System.Windows.Interop.ComponentDispatcher> metody v příslušné pořadí. Pokud implementujete vlastní zpráva smyčky, váš kód je zodpovědná za volání <xref:System.Windows.Interop.ComponentDispatcher> metody podobným způsobem.  
  
 Volání metody <xref:System.Windows.Interop.ComponentDispatcher> metody na vlákno bude volat pouze obslužné rutiny událostí, které byly zaregistrovány v daném vláknu.  
  
## <a name="writing-message-loops"></a>Zápis zpráva smyčky  
 Toto je kontrolní seznam <xref:System.Windows.Interop.ComponentDispatcher> členy použijete můžete psát vlastní smyčce zpráv:  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.PushModal%2A>: vaše zpráva smyčky by měly volat to znamenat, že vlákno modální.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.PopModal%2A>: vaše zpráva smyčky by měly volat to znamenat, že vlákno je vrácen do nonmodal.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.RaiseIdle%2A>: vaše zpráva smyčky to označuje, zda by měly volat <xref:System.Windows.Interop.ComponentDispatcher> by měla vyvolat <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle> událostí. <xref:System.Windows.Interop.ComponentDispatcher> nevydá <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle> Pokud <xref:System.Windows.Interop.ComponentDispatcher.IsThreadModal%2A> je `true`, ale zpráva smyčky rozhodnout volání <xref:System.Windows.Interop.ComponentDispatcher.RaiseIdle%2A> i v případě <xref:System.Windows.Interop.ComponentDispatcher> nemůže reagovat na ni ve modální stavu.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.RaiseThreadMessage%2A>: vaše zpráva smyčky by měly volat k označení, že je k dispozici novou zprávu. Návratová hodnota určuje, zda naslouchací proces a <xref:System.Windows.Interop.ComponentDispatcher> události zpracovává zprávy. Pokud <xref:System.Windows.Interop.ComponentDispatcher.RaiseThreadMessage%2A> vrátí `true` (zpracovává), měli dispečera udělat nic dalšího se zprávou. Pokud je vrácenou hodnotou `false`, dispečera očekává se volání [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] funkce `TranslateMessage`, pak zavolají `DispatchMessage`.  
  
## <a name="using-componentdispatcher-and-existing-message-handling"></a>Pomocí ComponentDispatcher a existující zpracování zpráv  
 Toto je kontrolní seznam <xref:System.Windows.Interop.ComponentDispatcher> členy použijete, pokud byste tedy spoléhat na vnořeným [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zpráva smyčky.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.IsThreadModal%2A>: vrátí, zda aplikace přešel modální (například smyčku modální zpráva bylo posunuto). <xref:System.Windows.Interop.ComponentDispatcher> Tento stav můžete sledovat, protože třída spravuje počet <xref:System.Windows.Interop.ComponentDispatcher.PushModal%2A> a <xref:System.Windows.Interop.ComponentDispatcher.PopModal%2A> volání zpráva smyčky.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage> a <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> události podle standardní pravidla pro vyvolání delegáta. Delegáti jsou vyvolány v neurčené pořadí a všechny Delegáti jsou vyvolány i v případě, že první označí zprávu jako zpracování.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle>: Určuje příslušnou a efektivní dobu nečinnosti zpracování (nejsou žádné čekající zprávy pro vlákno). <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle> nebude-li vyvolána vlákno se modální.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage>: vyvolané pro všechny zprávy, které message pump zpracuje.  
  
-   <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage>: vyvolané pro všechny zprávy, které nebyly zpracovány během <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage>.  
  
 Zprávu se považuje zpracovávaný Pokud po <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage> události nebo <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> událostí, `handled` parametr předaný odkazem v datech události je `true`. Obslužné rutiny událostí by měl zprávu ignorovat, pokud `handled` je `true`, protože to znamená, že jiný obslužná rutina zpracovává zprávy nejprve. Obslužné rutiny událostí na obou události mohou upravit zprávu. Dispečer by měl odeslání upravené zprávy a není původní zprávy beze změny. <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> se doručí na všechny moduly pro naslouchání, ale architektury záměrem je, že pouze nejvyšší úrovně okno obsahující HWND, kdy by měla vyvolat zprávy cílové kódu v odpovědi na zprávy.  
  
## <a name="how-hwndsource-treats-componentdispatcher-events"></a>Jak HwndSource zpracovává ComponentDispatcher události  
 Pokud <xref:System.Windows.Interop.HwndSource> nejvyšší úrovně okno (nadřazený HWND), se registrují s <xref:System.Windows.Interop.ComponentDispatcher>. Pokud <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> se vyvolá, a pokud zpráva je určený pro <xref:System.Windows.Interop.HwndSource> nebo podřízená okna <xref:System.Windows.Interop.HwndSource> volání jeho <xref:System.Windows.Interop.HwndSource.System%23Windows%23Interop%23IKeyboardInputSink%23TranslateAccelerator%2A>, <xref:System.Windows.Interop.IKeyboardInputSink.TranslateChar%2A>, <xref:System.Windows.Interop.IKeyboardInputSink.OnMnemonic%2A> klávesové podřízený pořadí.  
  
 Pokud <xref:System.Windows.Interop.HwndSource> není nejvyšší úrovně okno (má nadřazený HWND), budou existovat žádné zpracování. Očekává se jenom okno nejvyšší úrovně uděláte zpracování a existuje se očekává okno nejvyšší úrovně s podporou podřízený klávesnice v rámci všech součinnosti scénáře.  
  
 Pokud <xref:System.Windows.Interop.HwndHost.WndProc%2A> na <xref:System.Windows.Interop.HwndSource> je volána bez nejprve zavolat metodu podřízený příslušné klávesnice aplikace se zobrazí události vyšší úrovně klávesnice, jako <xref:System.Windows.UIElement.KeyDown>. Však žádné klávesnice podřízený bude volat metody, které by se obešla žádoucí klávesnice vstupní modelu funkce jako je podpora klíče přístup. K tomu může dojít, protože zpráva smyčky v správně neupozornila relevantní vlákno <xref:System.Windows.Interop.ComponentDispatcher>, nebo protože nadřazené HWND není vyvolání odpovědi podřízený správné klávesnice.  
  
 Zprávu, která přejde na klávesnici jímky nemusí být odeslána do HWND, pokud jste přidali háky pro tuto zprávu pomocí <xref:System.Windows.Interop.HwndSource.AddHook%2A> metoda. Zpráva může být manipulováno na úrovni čerpadlo zprávy přímo a nebyla odeslána `DispatchMessage` funkce.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Interop.ComponentDispatcher>  
 <xref:System.Windows.Interop.IKeyboardInputSink>  
 [Vzájemná spolupráce grafického subsystému WPF a systému Win32](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)  
 [Model vláken](../../../../docs/framework/wpf/advanced/threading-model.md)  
 [Přehled vstupu](../../../../docs/framework/wpf/advanced/input-overview.md)
