---
title: 'Návod: Hostování obsahu WPF v Win32'
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- hosting WPF content in Win32 window [WPF]
ms.assetid: 38ce284a-4303-46dd-b699-c9365b22a7dc
ms.openlocfilehash: 5bc6e6d805d74bcf01044a16d94d6b3fc0ccf881
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846855"
---
# <a name="walkthrough-hosting-wpf-content-in-win32"></a>Návod: Hostování obsahu WPF v Win32
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje bohatou prostředí pro vytváření aplikací. Nicméně pokud máte významnou investici do [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] kódu, může být efektivnější přidat do aplikace [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkce místo přepisu původního kódu. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje jednoduchý mechanismus pro hostování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu v [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okně.  
  
 V tomto kurzu se dozvíte, jak napsat ukázkovou aplikaci, která [hostuje obsah WPF v okně ukázek Win32](https://go.microsoft.com/fwlink/?LinkID=160004), který hostuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu v [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okně. Tuto ukázku můžete v případě, že chcete hostovat libovolné [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno, roztáhnout. Vzhledem k tomu, že zahrnuje kombinování spravovaného a nespravovaného C++kódu, aplikace je zapsána v/CLI.  

<a name="requirements"></a>   
## <a name="requirements"></a>Požadavky  
 V tomto kurzu se předpokládá základní znalost [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programování. Základní Úvod do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programování naleznete v tématu [Začínáme](../getting-started/index.md). Úvodní informace o [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programování by se měly odkázat na některé z mnoha knih v předmětu, zejména v *oknech programování* podle Charles Petzold.  
  
 Vzhledem k tomu, že je ukázka, která doprovází C++tento kurz, implementována ve verzi/CLI, v tomto C++ kurzu se předpokládá znalost použití nástroje k programování rozhraní Windows API a porozumění programování spravovaného kódu. Znalost C++/CLI je užitečná, ale není nezbytná.  
  
> [!NOTE]
> Tento kurz obsahuje několik příkladů kódu z přidruženého vzorku. Pro čitelnost ale nezahrnuje kompletní vzorový kód. Úplný vzorový kód naleznete v tématu [hostování obsahu WPF v ukázce okna Win32](https://go.microsoft.com/fwlink/?LinkID=160004).  
  
<a name="basic_procedure"></a>   
## <a name="the-basic-procedure"></a>Základní postup  
 Tato část popisuje základní postup, který slouží k hostování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu v [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okně. Zbývající části obsahují podrobné informace o jednotlivých krocích.  
  
 Klíč pro hostování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu v [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okně je třída <xref:System.Windows.Interop.HwndSource>. Tato třída zalomí obsah [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v okně [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] a umožňuje jeho začlenění do [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] jako podřízené okno. Následující postup kombinuje [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v jediné aplikaci.  
  
1. Implementujte svůj [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah jako spravovanou třídu.  
  
2. Implementace aplikace pro Windows pomocí C++/CLI. Pokud začínáte s existující aplikací a nespravovaným C++ kódem, můžete ji obvykle povolit pro volání spravovaného kódu změnou nastavení projektu tak, aby obsahovala příznak kompilátoru`/clr`.  
  
3. Nastavte model dělení na vlákna (STA) s jedním vláknem.  
  
4. Zpracujte oznámení [WM_CREATE](/windows/desktop/winmsg/wm-create)v postupu okna a proveďte následující kroky:  
  
    1. Vytvořte nový objekt <xref:System.Windows.Interop.HwndSource> s nadřazeným oknem jako jeho parametr `parent`.  
  
    2. Vytvořte instanci třídy obsahu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
    3. Přiřaďte odkaz na objekt [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu na vlastnost <xref:System.Windows.Interop.HwndSource.RootVisual%2A> <xref:System.Windows.Interop.HwndSource>.  
  
    4. Získat HWND pro obsah Vlastnost <xref:System.Windows.Interop.HwndSource.Handle%2A> objektu <xref:System.Windows.Interop.HwndSource> obsahuje popisovač okna (HWND). Chcete-li získat HWND, který můžete použít v nespravované části aplikace, přetypování `Handle.ToPointer()` na HWND.  
  
5. Implementujte spravovanou třídu, která obsahuje statické pole pro uložení odkazu na váš [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah. Tato třída umožňuje získat odkaz na obsah [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] z kódu [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].  
  
6. Přiřaďte obsah [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] statickému poli.  
  
7. Příjem oznámení z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu připojením obslužné rutiny k jedné nebo více událostem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
8. Komunikujte s obsahem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pomocí odkazu, který jste uložili do statického pole pro nastavení vlastností a tak dále.  
  
> [!NOTE]
> K implementaci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu můžete použít taky [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Bude však nutné jej zkompilovat samostatně jako dynamickou knihovnu (DLL) a odkazovat na tuto knihovnu DLL z aplikace [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]. Zbytek postupu je podobný jako uvedený výše.

<a name="implementing_the_application"></a>
## <a name="implementing-the-host-application"></a>Implementace hostitelské aplikace
 Tato část popisuje, jak hostovat obsah [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v základní aplikaci [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]. Samotný obsah je implementován v C++/CLI jako spravovaná třída. Ve většině případů je [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programování jednoduché. Klíčové aspekty implementace obsahu jsou popsány v tématu [implementace obsahu WPF](#implementing_the_wpf_page).

- [Základní aplikace](#the_basic_application)

- [Hostování obsahu WPF](#hosting_the_wpf_page)

- [Držení odkazu na obsah WPF](#holding_a_reference)

- [Komunikace s obsahem WPF](#communicating_with_the_page)

<a name="the_basic_application"></a>
### <a name="the-basic-application"></a>Základní aplikace
 Výchozím bodem pro hostitelskou aplikaci bylo vytvoření šablony sady Visual Studio 2005.

1. Otevřete Visual Studio 2005 a v nabídce **soubor** vyberte **Nový projekt** .

2. V seznamu typů vizuálních C++ projektů vyberte Win32. Pokud váš výchozí jazyk není C++, najdete tyto typy projektů v části **jiné jazyky**.

3. Vyberte šablonu **projektu Win32** , přiřaďte k projektu název a kliknutím na tlačítko **OK** spusťte **Průvodce aplikací Win32**.

4. Přijměte výchozí nastavení průvodce a kliknutím na tlačítko **Dokončit** spusťte projekt.

 Šablona vytvoří základní aplikaci [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], včetně:

- Vstupní bod pro aplikaci.

- Okno s přiřazenou procedurou okna (WndProc).

- Nabídka se záhlavími **souborů** a **nápovědě** Nabídka **soubor** obsahuje položku **Exit** , která zavírá aplikaci. Nabídka **help** obsahuje **informace o** položce, která spustí jednoduché dialogové okno.

 Než začnete psát kód pro hostování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu, je třeba provést dvě úpravy základní šablony.

 První je kompilovat projekt jako spravovaný kód. Ve výchozím nastavení se projekt zkompiluje jako nespravovaný kód. Avšak protože [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je implementováno ve spravovaném kódu, projekt musí být zkompilován odpovídajícím způsobem.

1. Klikněte pravým tlačítkem myši na název projektu v **Průzkumník řešení** a v místní nabídce vyberte možnost **vlastnosti** . tím otevřete dialogové okno **stránky vlastností** .

2. Ve stromovém zobrazení v levém podokně vyberte **Vlastnosti konfigurace** .

3. V pravém podokně vyberte možnost Podpora **Common Language Runtime** ze seznamu **výchozích hodnot projektu** .

4. V rozevíracím seznamu vyberte možnost **Podpora Common Language Runtime (/CLR)** .

> [!NOTE]
> Tento příznak kompilátoru umožňuje použít spravovaný kód v aplikaci, ale váš nespravovaný kód bude zkompilován jako dříve.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá model vláken typu apartment (STA) s jedním vláknem. Aby bylo možné správně pracovat s kódem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu, je nutné nastavit model vláken aplikace na STA použitím atributu na vstupní bod.

 [!code-cpp[Win32HostingWPFPage#WinMain](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#winmain)]

<a name="hosting_the_wpf_page"></a>
### <a name="hosting-the-wpf-content"></a>Hostování obsahu WPF
 Obsah [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je jednoduchá aplikace zadávání adres. Skládá se z několika ovládacích prvků <xref:System.Windows.Controls.TextBox> k převzetí uživatelského jména, adresy a tak dále. Existují také dva ovládací prvky <xref:System.Windows.Controls.Button>, **OK** a **Zrušit**. Když uživatel klikne na tlačítko **OK**, obslužná rutina události <xref:System.Windows.Controls.Primitives.ButtonBase.Click> tlačítka shromáždí data z ovládacích prvků <xref:System.Windows.Controls.TextBox>, přiřadí je k odpovídajícím vlastnostem a vyvolá vlastní událost, `OnButtonClicked`. Když uživatel klikne na **Storno**, obslužná rutina jednoduše vyvolá `OnButtonClicked`. Objekt argumentu události pro `OnButtonClicked` obsahuje pole Boolean, které indikuje, na které tlačítko bylo kliknuto.

 Kód pro hostování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ho obsahu je implementován v obslužné rutině pro oznámení [WM_CREATE](/windows/desktop/winmsg/wm-create) v okně hostitele.

 [!code-cpp[Win32HostingWPFPage#WMCreate](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcreate)]

 Metoda `GetHwnd` přebírá informace o velikosti a umístění a také popisovači nadřazeného okna a vrací popisovač okna hostovaného [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ho obsahu.

> [!NOTE]
> Pro obor názvů `System::Windows::Interop` nelze použít direktivu `#using`. Tím se vytvoří kolize názvů mezi <xref:System.Windows.Interop.MSG> strukturou v tomto oboru názvů a strukturou MSG deklarovanou v Winuser. h. Místo toho je nutné použít plně kvalifikované názvy pro přístup k obsahu tohoto oboru názvů.

 [!code-cpp[Win32HostingWPFPage#GetHwnd](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#gethwnd)]

 Obsah [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nelze hostovat přímo v okně aplikace. Místo toho vytvořte nejprve objekt <xref:System.Windows.Interop.HwndSource> pro zabalení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu. Tento objekt je v podstatě okno, které je navrženo pro hostování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ho obsahu. Objekt <xref:System.Windows.Interop.HwndSource> hostovat v nadřazeném okně tak, že ho vytvoříte jako podřízenou položku [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ho okna, které je součástí vaší aplikace. Parametry konstruktoru <xref:System.Windows.Interop.HwndSource> obsahují mnohem stejné informace, které byste při vytváření [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] podřízeného okna předávali do CreateWindow.

 Dále vytvoříte instanci objektu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu. V tomto případě se [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah implementuje jako samostatná třída, `WPFPage`pomocí C++/CLI. Můžete také implementovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. K tomu však potřebujete nastavit samostatný projekt a sestavit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah jako knihovnu DLL. Můžete přidat odkaz na tuto knihovnu DLL do projektu a použít tento odkaz k vytvoření instance [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ho obsahu.

 Obsah [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v podřízeném okně zobrazíte tak, že do vlastnosti <xref:System.Windows.Interop.HwndSource.RootVisual%2A> <xref:System.Windows.Interop.HwndSource>přiřadíte odkaz na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah.

 Další řádek kódu připojí obslužnou rutinu události `WPFButtonClicked`k události [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu `OnButtonClicked`. Tato obslužná rutina se volá, když uživatel klikne na tlačítko **OK** nebo **Storno** . Další diskuzi o této obslužné rutině události najdete v tématu [communicating_with_the_WPF Content](#communicating_with_the_page) .

 Poslední zobrazený řádek kódu vrátí popisovač okna (HWND), který je spojen s objektem <xref:System.Windows.Interop.HwndSource>. Pomocí tohoto popisovače z kódu [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] můžete odesílat zprávy do hostovaného okna, i když ukázka to neudělá. Objekt <xref:System.Windows.Interop.HwndSource> vyvolá událost pokaždé, když obdrží zprávu. Chcete-li zpracovat zprávy, zavolejte metodu <xref:System.Windows.Interop.HwndSource.AddHook%2A> pro připojení obslužné rutiny zpráv a poté zpracování zpráv v této obslužné rutině.

<a name="holding_a_reference"></a>
### <a name="holding-a-reference-to-the-wpf-content"></a>Držení odkazu na obsah WPF
 U mnoha aplikací budete chtít později komunikovat s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahem. Můžete například chtít upravit vlastnosti obsahu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nebo může mít <xref:System.Windows.Interop.HwndSource> hostitel objektu jiný [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah. K tomu potřebujete odkaz na objekt <xref:System.Windows.Interop.HwndSource> nebo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah. Objekt <xref:System.Windows.Interop.HwndSource> a jeho přidružený [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah zůstanou v paměti, dokud nezničíte popisovač okna. Nicméně proměnná, kterou přiřadíte objektu <xref:System.Windows.Interop.HwndSource>, se po návratu z postupu okna přejdou do rozsahu. Vlastní způsob, jak tento problém vyřešit s aplikacemi [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], je použití statické nebo globální proměnné. K těmto typům proměnných bohužel nelze přiřadit spravovaný objekt. Popisovač okna přidružený k objektu <xref:System.Windows.Interop.HwndSource> lze přiřadit globální nebo statické proměnné, ale tato operace Chvojková neposkytuje přístup k objektu samotnému.

 Nejjednodušší řešení tohoto problému je implementace spravované třídy, která obsahuje sadu statických polí pro blokování odkazů na jakékoli spravované objekty, ke kterým potřebujete přístup. Ukázka používá třídu `WPFPageHost` k uložení odkazu na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu a počáteční hodnoty počtu jeho vlastností, které může uživatel později změnit. Tato definice je definována v hlavičce.

 [!code-cpp[Win32HostingWPFPage#WPFPageHost](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.h#wpfpagehost)]

 Druhá část funkce `GetHwnd` přiřadí hodnoty do těchto polí pro pozdější použití, zatímco `myPage` stále ještě v oboru.

<a name="communicating_with_the_page"></a>
### <a name="communicating-with-the-wpf-content"></a>Komunikace s obsahem WPF
 Existují dva typy komunikace s obsahem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Aplikace obdrží informace z obsahu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], když uživatel klikne na tlačítko **OK** nebo **Storno** . Aplikace má také [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], která umožňuje uživateli měnit různé vlastnosti obsahu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], například barvu pozadí nebo výchozí velikost písma.

 Jak je uvedeno výše, když uživatel klikne buď na tlačítko, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah vyvolá událost `OnButtonClicked`. Aplikace k této události připojí obslužnou rutinu pro příjem těchto oznámení. Pokud bylo kliknuto na tlačítko **OK** , obslužná rutina získá informace o uživateli z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu a zobrazí ji v sadě statických ovládacích prvků.

 [!code-cpp[Win32HostingWPFPage#WPFButtonClicked](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wpfbuttonclicked)]

 Obslužná rutina přijme objekt vlastní argument události z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu `MyPageEventArgs`. Vlastnost `IsOK` objektu je nastavena na hodnotu `true`, pokud bylo tlačítko **OK** kliknuto a `false`, pokud bylo kliknuto na tlačítko **Storno** .

 Pokud bylo kliknuto na tlačítko **OK** , obslužná rutina získá odkaz na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah z třídy kontejneru. Poté shromáždí informace o uživateli, které jsou uchovávány v rámci přidružených vlastností obsahu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a používá statické ovládací prvky k zobrazení informací v nadřazeném okně. Vzhledem k tomu, že data obsahu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jsou ve formě spravovaného řetězce, je nutné ji zařadit pro použití ovládacím prvkem [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]. Pokud bylo kliknuto na tlačítko **Storno** , obslužná rutina vymaže data ze statických ovládacích prvků.

 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] aplikace poskytuje sadu přepínačů, které umožňují uživateli upravovat barvu pozadí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu a několik vlastností souvisejících s písmem. Následující příklad je výpis z procedury okna aplikace (WndProc) a jeho zpracování zpráv, které nastavuje různé vlastnosti v různých zprávách, včetně barvy pozadí. Ostatní jsou podobné a nejsou zobrazeny. Podrobnosti a kontext najdete v kompletní ukázce.

 [!code-cpp[Win32HostingWPFPage#WMCommandToBG](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcommandtobg)]

 Chcete-li nastavit barvu pozadí, získáte odkaz na obsah [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (`hostedPage`) z `WPFPageHost` a nastavte vlastnost barva pozadí na odpovídající barvu. Ukázka používá tři možnosti barev: původní barva, světle zelená nebo světle losos. Původní barva pozadí je uložena jako statické pole ve třídě `WPFPageHost`. Chcete-li nastavit druhé dva, vytvořte nový objekt <xref:System.Windows.Media.SolidColorBrush> a předejte konstruktoru hodnotu statické barvy z objektu <xref:System.Windows.Media.Colors>.

<a name="implementing_the_wpf_page"></a>
## <a name="implementing-the-wpf-page"></a>Implementace stránky WPF
 Obsah [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] můžete hostovat a používat bez znalosti skutečné implementace. Pokud byl obsah [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zabalen v samostatné knihovně DLL, mohl by být sestaven v jakémkoli jazyce modulu CLR (Common Language Runtime). Následuje stručný návod k implementaci C++/CLI, která se používá v ukázce. Tato část obsahuje následující pododdíly.

- [Rozložení](#page_layout)

- [Vrácení dat do hostitelského okna](#returning_data_to_window)

- [Nastavení vlastností WPF](#set_page_properties)

<a name="page_layout"></a>
### <a name="layout"></a>Rozložení
 Prvky [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] v obsahu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] se skládají z pěti ovládacích prvků <xref:System.Windows.Controls.TextBox> s přidruženými ovládacími prvky <xref:System.Windows.Controls.Label>: název, adresa, město, stát a PSČ. Existují také dva ovládací prvky <xref:System.Windows.Controls.Button>, **OK** a **Storno** .

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah je implementován ve třídě `WPFPage`. Rozložení se zpracovává pomocí elementu <xref:System.Windows.Controls.Grid> rozložení. Třída dědí z <xref:System.Windows.Controls.Grid>, což efektivně zpřístupňuje kořenový prvek obsahu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] konstruktor obsahu přebírá požadovanou šířku a výšku a <xref:System.Windows.Controls.Grid> odpovídajícím způsobem velikost. Pak definuje základní rozložení vytvořením sady <xref:System.Windows.Controls.ColumnDefinition> a <xref:System.Windows.Controls.RowDefinition> objektů a jejich přidáním do základních <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> a <xref:System.Windows.Controls.Grid.RowDefinitions%2A> kolekcí objektů <xref:System.Windows.Controls.Grid>. Tím se definuje mřížka s pěti řádky a sedmi sloupci s rozměry určenými obsahem buněk.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorToGridDef](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortogriddef)]

 Dále konstruktor přidá prvky [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] do <xref:System.Windows.Controls.Grid>. První prvek je text nadpisu, což je <xref:System.Windows.Controls.Label> ovládací prvek, který je zarovnán na střed prvního řádku mřížky.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorTitle](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortitle)]

 Další řádek obsahuje název <xref:System.Windows.Controls.Label> ovládací prvek a jeho přidružený ovládací prvek <xref:System.Windows.Controls.TextBox>. Vzhledem k tomu, že se stejný kód používá pro každou dvojici popisku nebo textového pole, je umístěn ve dvojici privátních metod a používá se pro všechna pět párů popisku nebo textového pole. Metody vytvoří příslušný ovládací prvek a zavolá metodu <xref:System.Windows.Controls.Grid> static <xref:System.Windows.Controls.Grid.SetColumn%2A> a <xref:System.Windows.Controls.Grid.SetRow%2A>, aby ovládací prvky umístily do příslušné buňky. Po vytvoření ovládacího prvku ukázka zavolá metodu <xref:System.Windows.Controls.UIElementCollection.Add%2A> pro vlastnost <xref:System.Windows.Controls.Panel.Children%2A> <xref:System.Windows.Controls.Grid> pro přidání ovládacího prvku do mřížky. Kód pro přidání zbývajících párů popisku nebo textového pole je podobný. Podrobnosti najdete v ukázkovém kódu.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorName](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorname)]

 Implementace těchto dvou metod je následující:

 [!code-cpp[Win32HostingWPFPage#WPFPageCreateHelpers](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagecreatehelpers)]

 Nakonec ukázka přidá tlačítka **OK** a **Storno** a připojí obslužnou rutinu události ke svým <xref:System.Windows.Controls.Primitives.ButtonBase.Click>m událostem.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorButtonsEvents](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorbuttonsevents)]

<a name="returning_data_to_window"></a>
### <a name="returning-the-data-to-the-host-window"></a>Vrácení dat do hostitelského okna
 Po kliknutí na tlačítko je vyvolána jeho událost <xref:System.Windows.Controls.Primitives.ButtonBase.Click>. Hostitelské okno může jednoduše připojit obslužné rutiny k těmto událostem a získat data přímo z ovládacích prvků <xref:System.Windows.Controls.TextBox>. Ukázka používá poněkud méně přímý přístup. Zpracovává <xref:System.Windows.Controls.Primitives.ButtonBase.Click> v rámci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu a potom vyvolá vlastní událost `OnButtonClicked`, aby upozornila [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah. Díky tomu může [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu provést několik ověření parametru před tím, než bude hostiteli upozorněni. Obslužná rutina získá text z ovládacích prvků <xref:System.Windows.Controls.TextBox> a přiřadí ho k veřejným vlastnostem, ze kterých může hostitel získat informace.

 Deklarace události v WPFPage. h:

 [!code-cpp[Win32HostingWPFPage#WPFPageEventDecl](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpageeventdecl)]

 Obslužná rutina události <xref:System.Windows.Controls.Primitives.ButtonBase.Click> v WPFPage. cpp:

 [!code-cpp[Win32HostingWPFPage#WPFPageButtonClicked](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagebuttonclicked)]

<a name="set_page_properties"></a>
### <a name="setting-the-wpf-properties"></a>Nastavení vlastností WPF
 Hostitel [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] umožňuje uživateli změnit několik [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ch vlastností obsahu. Na straně [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] je prostě Změna vlastností. Implementace ve třídě obsahu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je trochu složitější, protože neexistuje žádná jediná globální vlastnost, která ovládá písma pro všechny ovládací prvky. Místo toho se v přístupových objektech set vlastností změní příslušná vlastnost pro každý ovládací prvek. Následující příklad ukazuje kód pro vlastnost `DefaultFontFamily`. Nastavení vlastnosti volá soukromou metodu, která zase nastaví vlastnosti <xref:System.Windows.Controls.Control.FontFamily%2A> pro různé ovládací prvky.

 Z WPFPage. h:

 [!code-cpp[Win32HostingWPFPage#WPFPageFontFamilyProperty](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpagefontfamilyproperty)]

 Z WPFPage. cpp:

 [!code-cpp[Win32HostingWPFPage#WPFPageSetFontFamily](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagesetfontfamily)]

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Interop.HwndSource>
- [Vzájemná spolupráce grafického subsystému WPF a systému Win32](wpf-and-win32-interoperation.md)
