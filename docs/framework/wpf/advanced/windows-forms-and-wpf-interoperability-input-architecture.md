---
title: Vstupní architektura spolupráce model Windows Forms a WPF
titleSuffix: ''
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
ms.openlocfilehash: f79971ba13691ccc36420e39696b7b8a46e5ce0e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745050"
---
# <a name="windows-forms-and-wpf-interoperability-input-architecture"></a>Architektura vstupu interoperability Windows Forms a WPF
Vzájemná spolupráce mezi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] vyžaduje, aby obě technologie měly odpovídající zpracování vstupu z klávesnice. Toto téma popisuje, jak tyto technologie implementují klávesnice a zpracování zpráv, aby umožňovaly hladké fungování v hybridních aplikacích.  
  
 Toto téma obsahuje následující pododdíly:  
  
- Nemodální formuláře a dialogová okna  
  
- WindowsFormsHost klávesnice a zpracování zpráv  
  
- ElementHost klávesnice a zpracování zpráv  
  
## <a name="modeless-forms-and-dialog-boxes"></a>Nemodální formuláře a dialogová okna  
 Voláním metody <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A> u elementu <xref:System.Windows.Forms.Integration.WindowsFormsHost> otevřete nemodální formulář nebo dialogové okno z aplikace založené na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Voláním metody <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A> v ovládacím prvku <xref:System.Windows.Forms.Integration.ElementHost> otevřete nemodální [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stránky v aplikaci založené na [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
## <a name="windowsformshost-keyboard-and-message-processing"></a>WindowsFormsHost klávesnice a zpracování zpráv  
 Při hostování aplikace založené na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]se [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] zpracování klávesnice a zpráv skládá z těchto možností:  
  
- Třída <xref:System.Windows.Forms.Integration.WindowsFormsHost> získává zprávy ze smyčky zpráv [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], která je implementována třídou <xref:System.Windows.Interop.ComponentDispatcher>.  
  
- Třída <xref:System.Windows.Forms.Integration.WindowsFormsHost> vytvoří náhradní smyčku [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] zprávy, která zajistí, že dojde k běžnému zpracování [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] klávesnice.  
  
- Třída <xref:System.Windows.Forms.Integration.WindowsFormsHost> implementuje rozhraní <xref:System.Windows.Interop.IKeyboardInputSink> pro koordinaci správy fokusu pomocí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
- Ovládací prvky <xref:System.Windows.Forms.Integration.WindowsFormsHost> samy zaregistrovat a zahájí smyčky zpráv.  
  
 V následujících částech jsou podrobněji popsány tyto části procesu.  
  
### <a name="acquiring-messages-from-the-wpf-message-loop"></a>Získávání zpráv ze smyčky zpráv WPF  
 Třída <xref:System.Windows.Interop.ComponentDispatcher> implementuje správce smyčky zpráv pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Třída <xref:System.Windows.Interop.ComponentDispatcher> poskytuje připojení, aby externí klienti mohli filtrovat zprávy předtím, než je [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zpracuje.  
  
 Implementace mezi operacemi zpracovává událost <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType>, která umožňuje [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky zpracovávat zprávy před ovládacími prvky [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
### <a name="surrogate-windows-forms-message-loop"></a>Náhradní smyčka zpráv model Windows Forms  
 Ve výchozím nastavení třída <xref:System.Windows.Forms.Application?displayProperty=nameWithType> obsahuje primární smyčku zpráv pro [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] aplikace. Během spolupráce nezpracovává smyčka zpráv [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] zprávy. Proto musí být tato logika reprodukována. Obslužná rutina události <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType> provádí následující kroky:  
  
1. Filtruje zprávu pomocí rozhraní <xref:System.Windows.Forms.IMessageFilter>.  
  
2. Volá metodu <xref:System.Windows.Forms.Control.PreProcessMessage%2A?displayProperty=nameWithType>.  
  
3. Přeloží a odešle zprávu, pokud je to nutné.  
  
4. Předá zprávu ovládacímu prvku hostování, pokud žádné jiné ovládací prvky nezpracovávají zprávu.  
  
### <a name="ikeyboardinputsink-implementation"></a>Implementace IKeyboardInputSink  
 Náhradní smyčka zpráv zpracovává správu klávesnice. Proto je metoda <xref:System.Windows.Interop.IKeyboardInputSink.TabInto%2A?displayProperty=nameWithType> jediným členem <xref:System.Windows.Interop.IKeyboardInputSink>, který vyžaduje implementaci ve třídě <xref:System.Windows.Forms.Integration.WindowsFormsHost>.  
  
 Ve výchozím nastavení třída <xref:System.Windows.Interop.HwndHost> vrátí `false` pro jeho implementaci <xref:System.Windows.Interop.HwndHost.System%23Windows%23Interop%23IKeyboardInputSink%23TabInto%2A>. To brání tomu, aby se na ovládacím prvku [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvek [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost> implementace metody <xref:System.Windows.Interop.IKeyboardInputSink.TabInto%2A?displayProperty=nameWithType> provádí následující kroky:  
  
1. Najde první nebo poslední [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek, který je obsažený v ovládacím prvku <xref:System.Windows.Forms.Integration.WindowsFormsHost> a který může získat fokus. Volba ovládacího prvku závisí na propřenosných informacích.  
  
2. Nastaví fokus na ovládací prvek a vrátí `true`.  
  
3. Pokud žádný ovládací prvek nemůže získat fokus, vrátí `false`.  
  
### <a name="windowsformshost-registration"></a>WindowsFormsHost Registration  
 Když je vytvořena obslužná rutina okna <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládacímu prvku, ovládací prvek <xref:System.Windows.Forms.Integration.WindowsFormsHost> volá interní statickou metodu, která zaregistruje přítomnost pro smyčku zpráv.  
  
 Během registrace kontroluje <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládací prvek smyčka zpráv. Pokud nebyla smyčka zpráv spuštěna, je vytvořena obslužná rutina události <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType>. Smyčka zpráv je považována za spuštěnou, když je připojena obslužná rutina události <xref:System.Windows.Interop.ComponentDispatcher.ThreadFilterMessage?displayProperty=nameWithType>.  
  
 Při zničení popisovače okna se ovládací prvek <xref:System.Windows.Forms.Integration.WindowsFormsHost> sám odeberou od registrace.  
  
## <a name="elementhost-keyboard-and-message-processing"></a>ElementHost klávesnice a zpracování zpráv  
 Při hostování aplikace [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] se [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zpracování klávesnice a zpráv skládá z těchto možností:  
  
- implementace rozhraní <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.IKeyboardInputSink>a <xref:System.Windows.Interop.IKeyboardInputSite>.  
  
- Klávesy s kartami a šipkami.  
  
- Klíče příkazů a klávesy dialogových oken.  
  
- zpracování akcelerátoru [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)].  
  
 V následujících částech jsou podrobněji popsány tyto části.  
  
### <a name="interface-implementations"></a>Implementace rozhraní  
 V [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]jsou zprávy klávesnice směrovány na popisovač okna ovládacího prvku, který má fokus. V ovládacím prvku <xref:System.Windows.Forms.Integration.ElementHost> jsou tyto zprávy směrovány do hostovaného elementu. K tomuto účelu <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek poskytuje instanci <xref:System.Windows.Interop.HwndSource>. Pokud má ovládací prvek <xref:System.Windows.Forms.Integration.ElementHost> fokus, instance <xref:System.Windows.Interop.HwndSource> směruje většinu vstupu z klávesnice, aby je bylo možné zpracovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.InputManager>ou třídou.  
  
 Třída <xref:System.Windows.Interop.HwndSource> implementuje rozhraní <xref:System.Windows.Interop.IKeyboardInputSink> a <xref:System.Windows.Interop.IKeyboardInputSite>.  
  
 Operace s klávesnicí spoléhá na implementaci <xref:System.Windows.Interop.IKeyboardInputSite.OnNoMoreTabStops%2A> metody pro zpracování kláves TAB a klávesových zkratek, které přesouvají fokus mimo hostované prvky.  
  
### <a name="tabbing-and-arrow-keys"></a>Klávesy s kartami a šipkami  
 [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]ová logika výběru je namapována na metody <xref:System.Windows.Interop.HwndSource.System%23Windows%23Interop%23IKeyboardInputSink%23TabInto%2A> a <xref:System.Windows.Interop.IKeyboardInputSite.OnNoMoreTabStops%2A> pro implementaci karty a navigačních kláves šipky. Přepsání metody <xref:System.Windows.Forms.Integration.ElementHost.Select%2A> provede toto mapování.  
  
### <a name="command-keys-and-dialog-box-keys"></a>Příkazy a klíče dialogových oken  
 Chcete-li dát [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] první příležitost ke zpracování klávesových zkratek a klíčů dialogů, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] předzpracování příkazu je připojeno k metodě <xref:System.Windows.Interop.IKeyboardInputSink.TranslateAccelerator%2A>. Přepsání metody <xref:System.Windows.Forms.Control.ProcessCmdKey%2A?displayProperty=nameWithType> spojuje tyto dvě technologie.  
  
 Pomocí metody <xref:System.Windows.Interop.IKeyboardInputSink.TranslateAccelerator%2A> mohou hostované prvky zpracovat jakoukoli klíčovou zprávu, například WM_KEYDOWN, WM_KEYUP, WM_SYSKEYDOWN nebo WM_SYSKEYUP, včetně klávesových zkratek, jako je tabulátor, ENTER, ESC a klávesy se šipkami. Pokud se klíčová zpráva nezpracovává, pošle se [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] nadřazená hierarchie pro zpracování.  
  
### <a name="accelerator-processing"></a>Zpracování akcelerátoru  
 Aby bylo možné správně zpracovat akcelerátory, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] zpracování akcelerátoru musí být připojeno ke třídě <xref:System.Windows.Input.AccessKeyManager> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Kromě toho musí být všechny WM_CHAR zprávy správně směrovány na hostované prvky.  
  
 Vzhledem k tomu, že výchozí <xref:System.Windows.Interop.HwndSource> implementace metody <xref:System.Windows.Interop.IKeyboardInputSink.TranslateChar%2A> vrací `false`, jsou WM_CHAR zprávy zpracovávány pomocí následující logiky:  
  
- Metoda <xref:System.Windows.Forms.Control.IsInputChar%2A?displayProperty=nameWithType> je přepsána, aby se zajistilo, že všechny zprávy WM_CHAR budou předávány hostovaným elementům.  
  
- Při stisknutí klávesy ALT se zobrazí zpráva WM_SYSCHAR. [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] nezpracovává tuto zprávu prostřednictvím metody <xref:System.Windows.Forms.Control.IsInputChar%2A>. Proto je metoda <xref:System.Windows.Forms.Control.ProcessMnemonic%2A> přepsána k dotazování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.AccessKeyManager> pro registrovaný akcelerátor. Pokud se najde registrovaný akcelerátor, <xref:System.Windows.Input.AccessKeyManager> ho zpracuje.  
  
- Pokud klávesa ALT není stisknuta, třída [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Input.InputManager> zpracuje neošetřený vstup. Pokud vstup je akcelerátor, <xref:System.Windows.Input.AccessKeyManager> ho zpracuje. Událost <xref:System.Windows.Input.InputManager.PostProcessInput> se zpracovává pro WM_CHAR zprávy, které nebyly zpracovány.  
  
 Když uživatel stiskne klávesu ALT, vizuální pomůcky akcelerátoru se zobrazí v celém formuláři. Pro podporu tohoto chování všechny <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvky v aktivním formuláři přijímají WM_SYSKEYDOWN zprávy bez ohledu na to, který ovládací prvek má fokus.  
  
 Zprávy jsou odesílány pouze ovládacím prvkům <xref:System.Windows.Forms.Integration.ElementHost> v aktivním formuláři.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Integration.WindowsFormsHost.EnableWindowsFormsInterop%2A>
- <xref:System.Windows.Forms.Integration.ElementHost.EnableModelessKeyboardInterop%2A>
- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Návod: Hostování složeného ovládacího prvku Windows Forms v subsystému WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Vzájemná spolupráce grafického subsystému WPF a systému Win32](wpf-and-win32-interoperation.md)
