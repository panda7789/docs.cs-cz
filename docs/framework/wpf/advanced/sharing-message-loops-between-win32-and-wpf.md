---
title: Sdílení smyčky zpráv mezi systémem Win32 a platformou WPF
ms.date: 03/30/2017
helpviewer_keywords:
- Win32 code [WPF], sharing message loops
- message loops [WPF]
- sharing message loops [WPF]
- interoperability [WPF], Win32
ms.assetid: 39ee888c-e5ec-41c8-b11f-7b851a554442
ms.openlocfilehash: d2fe63ed4bdefc91e4847af799747219bd7b4a76
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64611729"
---
# <a name="sharing-message-loops-between-win32-and-wpf"></a>Sdílení smyčky zpráv mezi systémem Win32 a platformou WPF
Toto téma popisuje, jak implementovat smyčky zpráv pro součinnost s produktem [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], buď pomocí existující zprávu vystavení smyčky v <xref:System.Windows.Threading.Dispatcher> nebo vytvořením smyčku samostatné na [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] součinnosti kódu vedle sebe.  
  
## <a name="componentdispatcher-and-the-message-loop"></a>ComponentDispatcher a smyčky zpráv  
 Běžné scénáře pro podporu události vzájemná spolupráce grafického subsystému a klávesnice je implementace <xref:System.Windows.Interop.IKeyboardInputSink>, nebo jsou podtřídami tříd, které již implementují <xref:System.Windows.Interop.IKeyboardInputSink>, jako například <xref:System.Windows.Interop.HwndSource> nebo <xref:System.Windows.Interop.HwndHost>. Podpora klávesnice jímky nezabývá všechny možné zpráva smyčky potřeby, může být při odesílání a příjem zprávy přes součinnosti hranice. Abychom formalizujte architektura smyčky zpráv aplikace [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje <xref:System.Windows.Interop.ComponentDispatcher> třídu, která definuje jednoduchý protokol pro smyčku zpráv dodržovat.  
  
 <xref:System.Windows.Interop.ComponentDispatcher> je statická třída, která zveřejňuje několik členů. Oboru každé metody je implicitně svázána do volajícího vlákna. Smyčky zpráv musí volat některé z nich [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] v kritické dobu (jak jsou definovány v další části).  
  
 <xref:System.Windows.Interop.ComponentDispatcher> poskytuje události, které může naslouchat další součásti (například prvek klávesnice). <xref:System.Windows.Threading.Dispatcher> Třídy volání všechny příslušné <xref:System.Windows.Interop.ComponentDispatcher> metody v příslušné pořadí. Pokud implementujete vlastní smyčky zpráv, váš kód je zodpovědná za volání <xref:System.Windows.Interop.ComponentDispatcher> metody podobným způsobem.  
  
 Volání <xref:System.Windows.Interop.ComponentDispatcher> metody ve vlákně pouze vyvolá obslužné rutiny událostí, které jste zaregistrovali v daném vláknu.  
  
## <a name="writing-message-loops"></a>Zápis smyčky zpráv  
 Tady je kontrolní seznam <xref:System.Windows.Interop.ComponentDispatcher> členy, které budete používat při zápisu smyčku zpráv:  
  
- <xref:System.Windows.Interop.ComponentDispatcher.PushModal%2A>: vaše smyčky zpráv by měly volat tím, že je vlákno modální okno.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.PopModal%2A>: vaše smyčky zpráv by měly volat to znamenat, že vlákno se vrátil na nonmodal.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.RaiseIdle%2A>: vaše smyčky zpráv by měly volat to označuje, že <xref:System.Windows.Interop.ComponentDispatcher> by měla vyvolat <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle> událostí. <xref:System.Windows.Interop.ComponentDispatcher> nastavení nevydá <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle> Pokud <xref:System.Windows.Interop.ComponentDispatcher.IsThreadModal%2A> je `true`, ale smyčky zpráv můžete volat <xref:System.Windows.Interop.ComponentDispatcher.RaiseIdle%2A> i v případě <xref:System.Windows.Interop.ComponentDispatcher> nemůže reagovat na něj ve modálního stavu.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.RaiseThreadMessage%2A>: vaše smyčky zpráv by měly volat tím, že je k dispozici nová zpráva. Návratová hodnota označuje, zda naslouchací proces pro <xref:System.Windows.Interop.ComponentDispatcher> událost zpracovává zprávy. Pokud <xref:System.Windows.Interop.ComponentDispatcher.RaiseThreadMessage%2A> vrátí `true` (zpracovat), dispečer by provést žádnou akci dále se zprávou. Pokud je návratová hodnota `false`, dispečer je očekává volání [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] funkce `TranslateMessage`, poté zavolejte `DispatchMessage`.  
  
## <a name="using-componentdispatcher-and-existing-message-handling"></a>Pomocí ComponentDispatcher a existující zpracování zpráv  
 Tady je kontrolní seznam <xref:System.Windows.Interop.ComponentDispatcher> členy, které použijete, pokud se spoléháte na vnořeným [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] smyčku zpráv.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.IsThreadModal%2A>: vrátí, zda aplikace náramků RFID modální (například zpracování zpráv modální smyčky bylo vloženo). <xref:System.Windows.Interop.ComponentDispatcher> Tento stav můžete sledovat, protože třída udržuje počet <xref:System.Windows.Interop.ComponentDispatcher.PushModal%2A> a <xref:System.Windows.Interop.ComponentDispatcher.PopModal%2A> volání ze smyčky zpráv.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage> a <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> události dodržovat standardní pravidla pro vyvolání delegáta. Delegáti jsou vyvolány v nespecifikovaném pořadí a všichni Delegáti jsou vyvolány i v případě, že první z nich, označí zprávu jako zpracování.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle>: označuje odpovídající a efektivní čas nečinnosti zpracování (neexistují žádné čekající zprávy pro vlákno). <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle> nebude vyvolána, pokud je vlákno modální okno.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage>: vyvoláno pro všechny zprávy, které zpracovává pumpu zpráv.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage>: vyvoláno pro všechny zprávy, které nebyly zpracovány během <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage>.  
  
 Zpráva se považuje za zpracovaný if po <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage> události nebo <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> událostí, `handled` parametr předaný odkazem v datech událostí je `true`. Obslužné rutiny události by měl ignorovat Pokud `handled` je `true`, protože to znamená, že různé obslužná rutina zpracovává zprávy nejprve. Obslužné rutiny událostí do obou událostí může upravit zprávu. Dispečer by měl odeslání upravené zprávy a nejsou původní zprávu beze změny. <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> je určena pro všechny posluchače, ale architektury záměrem je, že pouze okno nejvyšší úrovně obsahující HWND, ve kterém by měla vyvolat zprávy cílové kódu v reakci na zprávu.  
  
## <a name="how-hwndsource-treats-componentdispatcher-events"></a>Způsob, jakým zpracovává HwndSource ComponentDispatcher události  
 Pokud <xref:System.Windows.Interop.HwndSource> je okno nejvyšší úrovně (žádný nadřazený prvek HWND), k registraci do <xref:System.Windows.Interop.ComponentDispatcher>. Pokud <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> se vyvolá, a pokud jsou určené pro <xref:System.Windows.Interop.HwndSource> nebo podřízená okna <xref:System.Windows.Interop.HwndSource> volání jeho <xref:System.Windows.Interop.HwndSource.System%23Windows%23Interop%23IKeyboardInputSink%23TranslateAccelerator%2A>, <xref:System.Windows.Interop.IKeyboardInputSink.TranslateChar%2A>, <xref:System.Windows.Interop.IKeyboardInputSink.OnMnemonic%2A> klávesnice pořadí jímky.  
  
 Pokud <xref:System.Windows.Interop.HwndSource> není okno nejvyšší úrovně (má nadřazený objekt HWND), nedojde k žádné zpracování. Pouze okna nejvyšší úrovně má provést zpracování a existuje má být okno nejvyšší úrovně s podporou jímky klávesnice jako součást scénářích vzájemné spolupráce.  
  
 Pokud <xref:System.Windows.Interop.HwndHost.WndProc%2A> na <xref:System.Windows.Interop.HwndSource> nazývá aniž se nejprve volat metodu jímky příslušné klávesové vaší aplikace přijímat události vyšší úrovně klávesnice, jako <xref:System.Windows.UIElement.KeyDown>. Ale žádný klávesnice jímky bude volat metody, který obchází žádoucí klávesnice vstupním modelu funkce, jako je přístup k podpoře klíčů. Příčinou může být smyčky zpráv není oznamovat správně odpovídající vlákno <xref:System.Windows.Interop.ComponentDispatcher>, nebo proto, že nadřazený HWND nevyvolal odpovědi správné klávesnice jímky.  
  
 Zpráva, která přejde na prvek klávesnice nemusí být odeslána do HWND, pokud jste přidali háky pro tuto zprávu s použitím <xref:System.Windows.Interop.HwndSource.AddHook%2A> metody. Zpráva může byla zpracována na úrovni čerpadlo zprávy přímo a není odeslána `DispatchMessage` funkce.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Interop.ComponentDispatcher>
- <xref:System.Windows.Interop.IKeyboardInputSink>
- [Vzájemná spolupráce grafického subsystému WPF a systému Win32](wpf-and-win32-interoperation.md)
- [Model vláken](threading-model.md)
- [Přehled vstupu](input-overview.md)
