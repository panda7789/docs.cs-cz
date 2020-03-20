---
title: Obsah WPF hostitele ve win32
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- hosting WPF content in Win32 window [WPF]
ms.assetid: 38ce284a-4303-46dd-b699-c9365b22a7dc
ms.openlocfilehash: 8a5d556abf49c9c1f49e7853e752ebc5248d1101
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186072"
---
# <a name="walkthrough-hosting-wpf-content-in-win32"></a>Návod: Hostování obsahu WPF v Win32
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]poskytuje bohaté prostředí pro vytváření aplikací. Pokud však máte značné investice do kódu Win32, může [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] být efektivnější přidat funkce do aplikace, spíše než přepisovat původní kód. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje jednoduchý mechanismus [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pro hostování obsahu v okně Win32.  
  
 Tento kurz popisuje, jak napsat ukázkovou aplikaci [Hostování wpf obsahu v ukázce okna Win32](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/Win32HostingWPFPage), který hostuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah v okně Win32. Tuto ukázku můžete rozšířit tak, aby hostovala libovolné okno Win32. Protože zahrnuje míchání spravovaného a nespravovaného kódu, je aplikace zapsána v jazyce C++/CLI.  

<a name="requirements"></a>
## <a name="requirements"></a>Požadavky  
 Tento kurz předpokládá základní znalost obou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a Win32 programování. Základní úvod k [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programování najdete v tématu [Začínáme](../getting-started/index.md). Pro úvod do Win32 programování, měli byste odkazovat na některou z mnoha knih na toto téma, zejména *programování Windows* Charles Petzold.  
  
 Vzhledem k tomu, že ukázka, která doprovází tento kurz je implementována v Jazyce C++/CLI, tento kurz předpokládá znalost s použitím Jazyka C++ k programování rozhraní API systému Windows plus pochopení programování spravovaného kódu. Znalost C++/CLI je užitečná, ale není nezbytná.  
  
> [!NOTE]
> Tento kurz obsahuje řadu příkladů kódu z přidružené ukázky. Pro čitelnost však neobsahuje úplný ukázkový kód. Úplný ukázkový kód naleznete [v tématu Hostování obsahu WPF v ukázce okna Win32](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/Win32HostingWPFPage).  
  
<a name="basic_procedure"></a>
## <a name="the-basic-procedure"></a>Základní postup  
 Tato část popisuje základní postup, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] který slouží k hostování obsahu v okně Win32. Zbývající části vysvětlují podrobnosti každého kroku.  
  
 Klíčem k [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hostování obsahu v okně Win32 je <xref:System.Windows.Interop.HwndSource> třída. Tato třída zalomí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah v okně Win32, což umožňuje, aby byly začleněny do okna [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] jako podřízené. Následující přístup kombinuje Win32 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a v jedné aplikaci.  
  
1. Implementujte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah jako spravovanou třídu.  
  
2. Implementujte aplikaci systému Windows s c++/CLI. Pokud začínáte s existující aplikací a nespravovaným kódem c++, můžete obvykle povolit volání spravovaného kódu změnou nastavení projektu tak, aby zahrnovalpříznak kompilátoru. `/clr`  
  
3. Nastavte model závitování na jednovláknový byt (STA).  
  
4. Zpracovat [oznámení WM_CREATE](/windows/desktop/winmsg/wm-create)v okně postup a postupujte takto:  
  
    1. Vytvořte <xref:System.Windows.Interop.HwndSource> nový objekt s nadřazeným oknem jako parametrem. `parent`  
  
    2. Vytvořte instanci třídy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu.  
  
    3. Přiřaďte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] odkaz na <xref:System.Windows.Interop.HwndSource.RootVisual%2A> objekt obsahu <xref:System.Windows.Interop.HwndSource>vlastnosti .  
  
    4. Získejte HWND pro obsah. Vlastnost <xref:System.Windows.Interop.HwndSource.Handle%2A> objektu <xref:System.Windows.Interop.HwndSource> obsahuje popisovač okna (HWND). Chcete-li získat HWND, který můžete použít v nespravované části aplikace, přetypované `Handle.ToPointer()` do HWND.  
  
5. Implementujte spravovanou třídu, která obsahuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] statické pole pro uložení odkazu na váš obsah. Tato třída umožňuje získat odkaz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] na obsah z kódu Win32.  
  
6. Přiřaďte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah ke statickému poli.  
  
7. Přijímat oznámení z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu připojením obslužné [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rutiny k jedné nebo více událostí.  
  
8. Komunikujte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] s obsahem pomocí odkazu, který jste uložili do statického pole, nastavte vlastnosti a tak dále.  
  
> [!NOTE]
> Můžete také [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] použít k [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementaci obsahu. Budete ji však muset zkompilovat samostatně jako dynamickou knihovnu (DLL) a odkazovat na tuto knihovnu DLL z aplikace Win32. Zbývající část postupu je podobná výše uvedenému postupu.

<a name="implementing_the_application"></a>
## <a name="implementing-the-host-application"></a>Implementace hostitelské aplikace
 Tato část popisuje, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jak hostovat obsah v základní aplikaci Win32. Samotný obsah je implementován v jazyce C++/CLI jako spravovaná třída. Z větší části je [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] to jednoduché programování. Klíčové aspekty implementace obsahu jsou popsány v [implementaci obsahu WPF](#implementing_the_wpf_page).

- [Základní aplikace](#the_basic_application)

- [Hostování obsahu WPF](#hosting_the_wpf_page)

- [Držení odkazu na obsah WPF](#holding_a_reference)

- [Komunikace s obsahem WPF](#communicating_with_the_page)

<a name="the_basic_application"></a>
### <a name="the-basic-application"></a>Základní aplikace
 Výchozím bodem pro hostitelskou aplikaci bylo vytvoření šablony sady Visual Studio 2005.

1. Otevřete Visual Studio 2005 a v nabídce **Soubor** vyberte **Nový projekt.**

2. Vyberte **Win32** ze seznamu typů projektů Visual C++. Pokud výchozí jazyk není C++, najdete tyto typy projektů v části **Jiné jazyky**.

3. Vyberte šablonu **projektu Win32,** přiřaďte projektu název a klepnutím na **tlačítko OK** spusťte Průvodce **aplikací win32**.

4. Přijměte výchozí nastavení průvodce a klepnutím na **tlačítko Dokončit** spusťte projekt.

 Šablona vytvoří základní aplikaci Win32, včetně:

- Vstupní bod pro aplikaci.

- Okno s přidruženou procedurou okna (WndProc).

- Nabídka s nadpisy **Soubor** a **Nápověda.** Nabídka **Soubor** obsahuje položku **Exit,** která uzavírá aplikaci. Nabídka **Nápověda** obsahuje položku **O** aplikaci, která spouští jednoduché dialogové okno.

 Než začnete psát kód [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pro hostování obsahu, musíte provést dvě změny základní šablony.

 První je zkompilovat projekt jako spravovaný kód. Ve výchozím nastavení se projekt zkompiluje jako nespravovaný kód. Protože [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je však implementována ve spravovaném kódu, musí být projekt zkompilován odpovídajícím způsobem.

1. Klikněte pravým tlačítkem myši na název projektu v **Průzkumníku řešení** a v místní nabídce vyberte **Vlastnosti** a spusťte dialogové okno **Stránky vlastností.**

2. Ve stromovém zobrazení v levém podokně vyberte **Vlastnosti konfigurace.**

3. V pravém podokně vyberte podporu **běžného zaběhu jazyka** ze seznamu **Výchozí nastavení projektu.**

4. V rozevíracím seznamu vyberte podpora **běžného jazykového běhu (/clr).**

> [!NOTE]
> Tento příznak kompilátoru umožňuje používat spravovaný kód ve vaší aplikaci, ale váš nespravovaný kód bude stále kompilovat jako dříve.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]používá model podprocesu s jedním závitem (STA). Aby bylo možné pracovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] správně s kódem obsahu, musíte nastavit model zřetězení aplikace na STA použitím atributu na vstupní bod.

 [!code-cpp[Win32HostingWPFPage#WinMain](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#winmain)]

<a name="hosting_the_wpf_page"></a>
### <a name="hosting-the-wpf-content"></a>Hostování obsahu WPF
 Obsah [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je jednoduchá aplikace pro zadávání adres. Skládá se z <xref:System.Windows.Controls.TextBox> několika ovládacích prvků, které mají uživatelské jméno, adresu a tak dále. K dispozici <xref:System.Windows.Controls.Button> jsou také dva ovládací prvky, **OK** a **Zrušit**. Když uživatel klepne na **tlačítko** <xref:System.Windows.Controls.Primitives.ButtonBase.Click> OK , obslužná rutina události tlačítka shromažďuje data z <xref:System.Windows.Controls.TextBox> `OnButtonClicked`ovládacích prvků, přiřazuje je k odpovídajícím vlastnostem a vyvolá vlastní událost . Když uživatel klepne na tlačítko `OnButtonClicked` **Storno**, obslužná rutina jednoduše vyvolá . Objekt argumentu `OnButtonClicked` události obsahuje logické pole, které označuje, na které tlačítko bylo kliknuto.

 Kód pro hostování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu je implementován v obslužné rutině pro [oznámení WM_CREATE](/windows/desktop/winmsg/wm-create) v okně hostitele.

 [!code-cpp[Win32HostingWPFPage#WMCreate](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcreate)]

 Metoda `GetHwnd` přebírá informace o velikosti a umístění plus popisovač nadřazeného okna a vrátí popisovač okna hostovaného [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu.

> [!NOTE]
> Pro obor `#using` názvů nelze `System::Windows::Interop` použít direktivu. Tím se vytvoří kolize <xref:System.Windows.Interop.MSG> názvů mezi strukturou v tomto oboru názvů a strukturou MSG deklarovanou v souboru winuser.h. Místo toho je nutné použít plně kvalifikované názvy pro přístup k obsahu tohoto oboru názvů.

 [!code-cpp[Win32HostingWPFPage#GetHwnd](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#gethwnd)]

 Obsah nelze [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hostovat přímo v okně aplikace. Místo toho nejprve <xref:System.Windows.Interop.HwndSource> vytvoříte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objekt pro obtékání obsahu. Tento objekt je v podstatě okno, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] které je určeno k hostování obsahu. Objekt hostujete <xref:System.Windows.Interop.HwndSource> v nadřazeném okně jeho vytvořením jako podřízenéokno win32, které je součástí vaší aplikace. Parametry <xref:System.Windows.Interop.HwndSource> konstruktoru obsahují téměř stejné informace, které byste předat CreateWindow při vytváření podřízené okno Win32.

 Dále vytvoříte instanci objektu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu. V tomto případě [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je obsah implementován `WPFPage`jako samostatná třída , pomocí C++/CLI. Můžete také implementovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]obsah s . Chcete-li tak však provést, musíte nastavit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] samostatný projekt a vytvořit obsah jako knihovnu DLL. Do projektu můžete přidat odkaz na tuto knihovnu DLL a použít [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tento odkaz k vytvoření instance obsahu.

 Obsah se [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zobrazí v podřízeném okně přiřazením odkazu <xref:System.Windows.Interop.HwndSource.RootVisual%2A> na <xref:System.Windows.Interop.HwndSource> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah ve vlastnosti .

 Další řádek kódu připojí obslužnou rutinu události , `WPFButtonClicked`k události [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu. `OnButtonClicked` Tato obslužná rutina je volána, když uživatel klepne na tlačítko **OK** nebo **Zrušit.** Další diskusi o této obslužné rutině události naleznete v [communicating_with_the_WPF obsahu.](#communicating_with_the_page)

 Poslední zobrazený řádek kódu vrátí popisovač okna (HWND), který je přidružen k objektu. <xref:System.Windows.Interop.HwndSource> Tento popisovač můžete použít z kódu Win32 k odeslání zpráv do hostovaného okna, i když ukázka tak nečiní. Objekt <xref:System.Windows.Interop.HwndSource> vyvolá událost pokaždé, když obdrží zprávu. Chcete-li zprávy zpracovat, zavolejte metodu <xref:System.Windows.Interop.HwndSource.AddHook%2A> k připojení obslužné rutiny zprávy a potom zpracujte zprávy v této obslužné rutině.

<a name="holding_a_reference"></a>
### <a name="holding-a-reference-to-the-wpf-content"></a>Držení odkazu na obsah WPF
 U mnoha aplikací budete chtít s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahem později komunikovat. Můžete například chtít upravit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnosti obsahu nebo <xref:System.Windows.Interop.HwndSource> mít objekt [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hostitele mj. Chcete-li to provést, potřebujete <xref:System.Windows.Interop.HwndSource> odkaz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] na objekt nebo obsah. Objekt <xref:System.Windows.Interop.HwndSource> a jeho [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] přidružený obsah zůstanou v paměti, dokud nezničíte popisovač okna. Proměnná, kterou přiřadíte objektu, <xref:System.Windows.Interop.HwndSource> však přejde mimo rozsah, jakmile se vrátíte z procedury okna. Obvyklý způsob, jak tento problém zpracovat s aplikacemi Win32 je použití statické nebo globální proměnné. Bohužel nelze přiřadit spravovaný objekt těmto typům proměnných. Popisovač okna přidružený k <xref:System.Windows.Interop.HwndSource> objektu můžete přiřadit globální nebo statické proměnné, ale které doe neposkytují přístup k samotnému objektu.

 Nejjednodušším řešením tohoto problému je implementace spravované třídy, která obsahuje sadu statických polí pro uložení odkazů na všechny spravované objekty, ke kterým potřebujete přístup. Ukázka používá `WPFPageHost` třídu k uložení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] odkazu na obsah a počáteční hodnoty několika jeho vlastností, které může uživatel později změnit. To je definováno v záhlaví.

 [!code-cpp[Win32HostingWPFPage#WPFPageHost](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.h#wpfpagehost)]

 Druhá část funkce `GetHwnd` přiřazuje hodnoty těmto `myPage` polím pro pozdější použití, zatímco je stále v oboru.

<a name="communicating_with_the_page"></a>
### <a name="communicating-with-the-wpf-content"></a>Komunikace s obsahem WPF
 Existují dva typy komunikace [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] s obsahem. Aplikace obdrží informace z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu, když uživatel klepne na tlačítko **OK** nebo **Storno.** Aplikace má [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] také, který umožňuje uživateli změnit různé [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnosti obsahu, jako je například barva pozadí nebo výchozí velikost písma.

 Jak bylo uvedeno výše, když uživatel [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klikne `OnButtonClicked` na jedno tlačítko, obsah vyvolá událost. Aplikace připojí obslužnou rutinu k této události přijímat tato oznámení. Pokud bylo kliknuto na tlačítko **OK,** obslužná rutina získá informace o uživateli z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu a zobrazí je v sadě statických ovládacích prvků.

 [!code-cpp[Win32HostingWPFPage#WPFButtonClicked](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wpfbuttonclicked)]

 Obslužná rutina obdrží [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objekt `MyPageEventArgs`argumentu vlastní události z obsahu . `IsOK` Vlastnost objektu je nastavena `true` na pokud bylo kliknuto na tlačítko **OK** a `false` pokud bylo klepnuto na tlačítko **Storno.**

 Pokud bylo kliknuto na tlačítko **OK,** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obslužná rutina získá odkaz na obsah z třídy kontejneru. Poté shromažďuje informace o uživateli, které [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jsou v držení přidružené vlastnosti obsahu a používá statické ovládací prvky k zobrazení informací v nadřazeném okně. Vzhledem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] k tomu, že data obsahu je ve formě spravovaného řetězce, musí být zařazenpro použití ovládacího prvku Win32. Pokud bylo kliknuto na tlačítko **Storno,** obslužná rutina vymaže data ze statických ovládacích prvků.

 Aplikace [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] poskytuje sadu přepínacích tlačítek, které umožňují uživateli upravit barvu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pozadí obsahu a několik vlastností souvisejících s písmem. Následující příklad je výňatek z procedury okna aplikace (WndProc) a jeho zpracování zpráv, které nastaví různé vlastnosti na různé zprávy, včetně barvy pozadí. Ostatní jsou podobné a nejsou zobrazeny. Podrobnosti a kontext najdete v celé ukázce.

 [!code-cpp[Win32HostingWPFPage#WMCommandToBG](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcommandtobg)]

 Chcete-li nastavit barvu pozadí, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] získejte`hostedPage`odkaz `WPFPageHost` na obsah ( ) z a nastavte vlastnost barvy pozadí na příslušnou barvu. Ukázka používá tři barevné možnosti: původní barvu, světle zelenou nebo světlého lososa. Původní barva pozadí je uložena jako `WPFPageHost` statické pole ve třídě. Chcete-li nastavit další dva, <xref:System.Windows.Media.SolidColorBrush> vytvořte nový objekt a předat <xref:System.Windows.Media.Colors> konstruktoru statickou hodnotu barev z objektu.

<a name="implementing_the_wpf_page"></a>
## <a name="implementing-the-wpf-page"></a>Implementace stránky WPF
 Obsah můžete hostovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a používat bez znalosti skutečné implementace. Pokud [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] byl obsah zabalen do samostatné knihovny DLL, mohl být vytvořen v libovolném jazyce CLR (COMMON Language runtime). Následuje stručný návod implementace C++/CLI, který se používá v ukázce. Tato část obsahuje následující pododdíly.

- [Rozložení](#page_layout)

- [Vrácení dat do okna hostitele](#returning_data_to_window)

- [Nastavení vlastností WPF](#set_page_properties)

<a name="page_layout"></a>
### <a name="layout"></a>Rozložení
 Prvky [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu se <xref:System.Windows.Controls.TextBox> skládají <xref:System.Windows.Controls.Label> z pěti ovládacích prvků s přidruženými ovládacími prvky: Název, Adresa, Město, Stát a Zip. K dispozici <xref:System.Windows.Controls.Button> jsou také dva ovládací prvky, **OK** a **Zrušit**

 Obsah [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je implementován ve `WPFPage` třídě. Rozložení je zpracováno <xref:System.Windows.Controls.Grid> s prvkem rozložení. Třída dědí <xref:System.Windows.Controls.Grid>z , což efektivně [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] umožňuje kořenový prvek obsahu.

 Konstruktor [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu má požadovanou šířku a <xref:System.Windows.Controls.Grid> výšku a odpovídajícím způsobem zvětší velikost. Potom definuje základní rozložení vytvořením sady <xref:System.Windows.Controls.ColumnDefinition> <xref:System.Windows.Controls.RowDefinition> a objektů a <xref:System.Windows.Controls.Grid> jejich <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> přidáním do základny objektu a <xref:System.Windows.Controls.Grid.RowDefinitions%2A> kolekcí. Definuje mřížku pěti řádků a sedmi sloupců s rozměry určenými obsahem buněk.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorToGridDef](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortogriddef)]

 Dále konstruktor přidá [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] prvky <xref:System.Windows.Controls.Grid>do . Prvním prvkem je text nadpisu, <xref:System.Windows.Controls.Label> což je ovládací prvek, který je vycentrován v prvním řádku mřížky.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorTitle](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortitle)]

 Následující řádek obsahuje <xref:System.Windows.Controls.Label> name ovládací <xref:System.Windows.Controls.TextBox> prvek a jeho přidružený ovládací prvek. Vzhledem k tomu, že stejný kód se používá pro každý pár popisek/textové pole, je umístěn v páru soukromých metod a používá se pro všech pět párů popisek/textové pole. Metody vytvořit příslušný ovládací prvek <xref:System.Windows.Controls.Grid> a <xref:System.Windows.Controls.Grid.SetColumn%2A> volání <xref:System.Windows.Controls.Grid.SetRow%2A> třídy statické a metody umístit ovládací prvky v příslušné buňce. Po vytvoření ovládacího prvku ukázka volá <xref:System.Windows.Controls.Panel.Children%2A> metodu <xref:System.Windows.Controls.Grid> <xref:System.Windows.Controls.UIElementCollection.Add%2A> na vlastnost přidat ovládací prvek do mřížky. Kód pro přidání zbývajících párů popisek/textového pole je podobný. Podrobnosti naleznete v ukázkovém kódu.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorName](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorname)]

 Provádění těchto dvou metod je následující:

 [!code-cpp[Win32HostingWPFPage#WPFPageCreateHelpers](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagecreatehelpers)]

 Nakonec ukázka přidá **tlačítka OK** a **Cancel** a připojí <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obslužnou rutinu události k jejich událostem.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorButtonsEvents](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorbuttonsevents)]

<a name="returning_data_to_window"></a>
### <a name="returning-the-data-to-the-host-window"></a>Vrácení dat do okna hostitele
 Po klepnutí na jedno <xref:System.Windows.Controls.Primitives.ButtonBase.Click> tlačítko je vyvolána jeho událost. Okno hostitele může jednoduše připojit obslužné rutiny <xref:System.Windows.Controls.TextBox> k těmto událostem a získat data přímo z ovládacích prvků. Vzorek používá poněkud méně přímý přístup. Zpracovává <xref:System.Windows.Controls.Primitives.ButtonBase.Click> v rámci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu a potom vyvolá `OnButtonClicked`vlastní událost [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , aby ho upozornil na obsah. To umožňuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu provést ověření některých parametrů před oznámením hostitele. Obslužná rutina získá text z <xref:System.Windows.Controls.TextBox> ovládacích prvků a přiřadí jej k veřejným vlastnostem, ze kterých může hostitel načíst informace.

 Deklarace události v souboru WPFPage.h:

 [!code-cpp[Win32HostingWPFPage#WPFPageEventDecl](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpageeventdecl)]

 Obslužná rutina <xref:System.Windows.Controls.Primitives.ButtonBase.Click> události v souboru WPFPage.cpp:

 [!code-cpp[Win32HostingWPFPage#WPFPageButtonClicked](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagebuttonclicked)]

<a name="set_page_properties"></a>
### <a name="setting-the-wpf-properties"></a>Nastavení vlastností WPF
 Hostitel Win32 umožňuje uživateli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] změnit několik vlastností obsahu. Ze strany Win32 je to prostě otázka změny vlastností. Implementace ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] třídě content je poněkud složitější, protože neexistuje žádná jediná globální vlastnost, která řídí písma pro všechny ovládací prvky. Místo toho příslušná vlastnost pro každý ovládací prvek se změní v přístupové objekty sady vlastností. Následující příklad ukazuje kód `DefaultFontFamily` vlastnosti. Nastavení vlastnosti volá soukromou metodu, která zase nastaví vlastnosti <xref:System.Windows.Controls.Control.FontFamily%2A> pro různé ovládací prvky.

 Z souboru WPFPage.h:

 [!code-cpp[Win32HostingWPFPage#WPFPageFontFamilyProperty](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpagefontfamilyproperty)]

 Z wpfpage.cpp:

 [!code-cpp[Win32HostingWPFPage#WPFPageSetFontFamily](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagesetfontfamily)]

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Interop.HwndSource>
- [Vzájemná spolupráce grafického subsystému WPF a systému Win32](wpf-and-win32-interoperation.md)
