---
title: Sdílení smyčky zpráv mezi systémem Win32 a platformou WPF
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- Win32 code [WPF], sharing message loops
- message loops [WPF]
- sharing message loops [WPF]
- interoperability [WPF], Win32
ms.assetid: 39ee888c-e5ec-41c8-b11f-7b851a554442
ms.openlocfilehash: e1b96284d69645876d3e383beb03a2cc540d8b7b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731720"
---
# <a name="sharing-message-loops-between-win32-and-wpf"></a>Sdílení smyčky zpráv mezi systémem Win32 a platformou WPF
Toto téma popisuje, jak implementovat smyčku zpráv pro spoluprovozování s [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], a to buď pomocí existující expozice smyčky zpráv v <xref:System.Windows.Threading.Dispatcher> nebo vytvořením samostatné smyčky zpráv na straně Win32 kódu pro svůj kód.  
  
## <a name="componentdispatcher-and-the-message-loop"></a>ComponentDispatcher a smyčka zpráv  
 Běžným scénářem pro meziprovozu a podporu událostí klávesnice je implementace <xref:System.Windows.Interop.IKeyboardInputSink>nebo podtříd z tříd, které již implementují <xref:System.Windows.Interop.IKeyboardInputSink>, jako je například <xref:System.Windows.Interop.HwndSource> nebo <xref:System.Windows.Interop.HwndHost>. Podpora jímky klávesnice ale neřeší všechny možné potřeby smyčky zpráv, které byste mohli mít při posílání a přijímání zpráv napříč hranicemi mezi operacemi. Pro usnadnění formalizovat architektury smyčky zpráv aplikace [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje <xref:System.Windows.Interop.ComponentDispatcher> třídu, která definuje jednoduchý protokol, který má smyčka zpráv sledovat.  
  
 <xref:System.Windows.Interop.ComponentDispatcher> je statická třída, která zveřejňuje několik členů. Rozsah každé metody je implicitně svázán s volajícím vláknem. Smyčka zpráv musí volat některá z těchto rozhraní API v kritických časech (jak je definováno v další části).  
  
 <xref:System.Windows.Interop.ComponentDispatcher> poskytuje události, na které můžou naslouchat jiné součásti (například jímka klávesnice). Třída <xref:System.Windows.Threading.Dispatcher> volá všechny příslušné <xref:System.Windows.Interop.ComponentDispatcher> metody v příslušné sekvenci. Pokud implementujete vlastní smyčku zpráv, váš kód je zodpovědný za volání metod <xref:System.Windows.Interop.ComponentDispatcher> podobným způsobem.  
  
 Volání metod <xref:System.Windows.Interop.ComponentDispatcher> ve vlákně bude volat pouze obslužné rutiny událostí, které byly registrovány v tomto vlákně.  
  
## <a name="writing-message-loops"></a>Zápis smyček zpráv  
 Toto je kontrolní seznam <xref:System.Windows.Interop.ComponentDispatcher>ch členů, které budete používat, pokud píšete vlastní smyčku zpráv:  
  
- <xref:System.Windows.Interop.ComponentDispatcher.PushModal%2A>: vaše smyčka zprávy by měla zavolat to, aby označovala, že vlákno je modální.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.PopModal%2A>: vaše smyčka zprávy by měla zavolat to, aby označovala, že se vlákno vrátilo na nemodální.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.RaiseIdle%2A>: vaše smyčka zprávy by měla zavolat tuto metodu, aby označovala, že <xref:System.Windows.Interop.ComponentDispatcher> by měla vyvolat událost <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle>. <xref:System.Windows.Interop.ComponentDispatcher> nevyvolá <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle>, pokud <xref:System.Windows.Interop.ComponentDispatcher.IsThreadModal%2A> `true`, ale smyčky zpráv mohou zvolit volání <xref:System.Windows.Interop.ComponentDispatcher.RaiseIdle%2A> i v případě, že <xref:System.Windows.Interop.ComponentDispatcher> nemůže na něj reagovat v modálním stavu.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.RaiseThreadMessage%2A>: vaše smyčka zprávy by měla zavolat tuto zprávu, aby označovala, že je k dispozici nová zpráva. Vrácená hodnota označuje, zda naslouchací proces pro událost <xref:System.Windows.Interop.ComponentDispatcher> zpracoval zprávu. Pokud <xref:System.Windows.Interop.ComponentDispatcher.RaiseThreadMessage%2A> vrátí `true` (zpracovává), dispečer by neměl dělat nic dalšího s touto zprávou. Pokud je vrácená hodnota `false`, očekává se, že dispečer zavolá funkci Win32 `TranslateMessage`a pak zavolá `DispatchMessage`.  
  
## <a name="using-componentdispatcher-and-existing-message-handling"></a>Použití ComponentDispatcher a existující zpracování zpráv  
 Toto je kontrolní seznam <xref:System.Windows.Interop.ComponentDispatcher>ch členů, které budete používat, pokud se spoléháte na podstatu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zpráv.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.IsThreadModal%2A>: vrátí, zda aplikace opustí modální (např. byla vložena modální smyčka zpráv). <xref:System.Windows.Interop.ComponentDispatcher> může tento stav sledovat, protože Třída udržuje počet <xref:System.Windows.Interop.ComponentDispatcher.PushModal%2A> a <xref:System.Windows.Interop.ComponentDispatcher.PopModal%2A> volání ze smyčky zpráv.  
  
- události <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage> a <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> se řídí standardními pravidly pro volání delegátů. Delegáti jsou vyvoláni v nespecifikovaném pořadí a všichni Delegáti jsou vyvoláni i v případě, že první zpráva označí zprávu jako zpracovanou.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle>: označuje vhodnou a efektivní dobu nečinného zpracování (pro vlákno neexistují žádné další nevyřízené zprávy). <xref:System.Windows.Interop.ComponentDispatcher.ThreadIdle> nebude vyvolána, pokud je vlákno modální.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage>: Vyvolá se pro všechny zprávy, které čerpadlo zpráv zpracovává.  
  
- <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage>: Vyvolá se pro všechny zprávy, které nebyly během <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage>ošetřeny.  
  
 Zpráva se považuje za zpracovanou, pokud po události <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage> nebo <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> událost `handled` parametr předaný odkazem v datech události `true`. Obslužné rutiny události by měly ignorovat zprávu, pokud je `handled` `true`, protože to znamená, že se tato zpráva zpracovává jako první. Obslužné rutiny událostí do obou událostí mohou zprávu upravit. Dispečer by měl odeslat upravenou zprávu, nikoli původní nezměněnou zprávu. <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> se doručuje všem posluchačům, ale záměr architektury je to, že pouze okno nejvyšší úrovně obsahující HWND, na kterém mají cílové zprávy vyvolat kód jako odpověď na zprávu.  
  
## <a name="how-hwndsource-treats-componentdispatcher-events"></a>Jak HwndSource zpracovává události ComponentDispatcher  
 Pokud <xref:System.Windows.Interop.HwndSource> je okno nejvyšší úrovně (bez nadřazeného HWND), bude se registrovat v <xref:System.Windows.Interop.ComponentDispatcher>. Pokud je vyvolána <xref:System.Windows.Interop.ComponentDispatcher.ThreadPreprocessMessage> a je-li zpráva určena pro <xref:System.Windows.Interop.HwndSource> nebo podřízená okna, <xref:System.Windows.Interop.HwndSource> volá její <xref:System.Windows.Interop.HwndSource.System%23Windows%23Interop%23IKeyboardInputSink%23TranslateAccelerator%2A>, <xref:System.Windows.Interop.IKeyboardInputSink.TranslateChar%2A><xref:System.Windows.Interop.IKeyboardInputSink.OnMnemonic%2A>, sekvence jímky klávesnice.  
  
 Pokud <xref:System.Windows.Interop.HwndSource> není okno nejvyšší úrovně (má nadřazený HWND), nebude žádné zpracování. Je očekáváno pouze okno nejvyšší úrovně, které provádí zpracování, přičemž jako součást scénáře jakékoli spolupráce se očekává okno nejvyšší úrovně s podporou jímky na klávesnici.  
  
 Pokud je zavolána <xref:System.Windows.Interop.HwndHost.WndProc%2A> v <xref:System.Windows.Interop.HwndSource>, aniž by byla nejprve volána odpovídající metoda jímky klávesnice, bude aplikace přijímat události klávesnice vyšší úrovně, například <xref:System.Windows.UIElement.KeyDown>. Nebudete však volat žádné metody jímky klávesnice, což obchází žádoucí funkce modelu vstupu z klávesnice, jako je například podpora přístupových klíčů. K tomu může dojít, protože smyčka zpráv nesprávně upozornila na příslušné vlákno na <xref:System.Windows.Interop.ComponentDispatcher>nebo protože nadřazené HWND nevolalo správné odezvy na jímky.  
  
 Zpráva, která se dostane do jímky klávesnice, nemusí být odeslána do HWND, pokud jste přidali háky pro tuto zprávu pomocí metody <xref:System.Windows.Interop.HwndSource.AddHook%2A>. Zpráva mohla být zpracována přímo na úrovni čerpadla zpráv a nebyla odeslána do funkce `DispatchMessage`.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Interop.ComponentDispatcher>
- <xref:System.Windows.Interop.IKeyboardInputSink>
- [Vzájemná spolupráce grafického subsystému WPF a systému Win32](wpf-and-win32-interoperation.md)
- [Model vláken](threading-model.md)
- [Přehled vstupu](input-overview.md)
