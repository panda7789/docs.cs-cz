---
title: 'Návod: Hostování obsahu WPF ve Win32'
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- hosting WPF content in Win32 window [WPF]
ms.assetid: 38ce284a-4303-46dd-b699-c9365b22a7dc
ms.openlocfilehash: 3a0a6d09fe34fed9f5b0d353252461fdffbeb5e1
ms.sourcegitcommit: 4b9c2d893b45d47048c6598b4182ba87759b1b59
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/25/2019
ms.locfileid: "68484622"
---
# <a name="walkthrough-hosting-wpf-content-in-win32"></a>Návod: Hostování obsahu WPF ve Win32
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]poskytuje bohatý prostředí pro vytváření aplikací. Nicméně pokud máte významnou investici do [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] kódu, může být efektivnější přidat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkce do aplikace namísto přepisu původního kódu. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje jednoduchý mechanismus pro hostování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] v okně.  
  
 Tento kurz popisuje, jak napsat ukázkovou aplikaci, [hostování obsahu WPF v okně ukázek Win32](https://go.microsoft.com/fwlink/?LinkID=160004), které hostuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah v [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okně. Tuto ukázku můžete roztáhnout na hostování libovolného [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna. Vzhledem k tomu, že zahrnuje kombinování spravovaného a nespravovaného C++kódu, aplikace je zapsána v/CLI.  

<a name="requirements"></a>   
## <a name="requirements"></a>Požadavky  
 V tomto kurzu se [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] předpokládá základní znalost i programování. Základní Úvod do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programování naleznete v tématu [Začínáme](../getting-started/index.md). Úvod do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programování byste měli odkazovat na některé z mnoha knih v předmětu, zejména v *oknech programování* pomocí Charles Petzold.  
  
 Vzhledem k tomu, že je ukázka, která doprovází C++tento kurz, implementována ve verzi/CLI, v tomto C++ kurzu se předpokládá znalost použití nástroje k programování rozhraní Windows API a porozumění programování spravovaného kódu. Znalost C++/CLI je užitečná, ale není nezbytná.  
  
> [!NOTE]
>  Tento kurz obsahuje několik příkladů kódu z přidruženého vzorku. Pro čitelnost ale nezahrnuje kompletní vzorový kód. Úplný vzorový kód naleznete v tématu [hostování obsahu WPF v ukázce okna Win32](https://go.microsoft.com/fwlink/?LinkID=160004).  
  
<a name="basic_procedure"></a>   
## <a name="the-basic-procedure"></a>Základní postup  
 Tato část popisuje základní postup, který používáte k hostování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] v okně. Zbývající části obsahují podrobné informace o jednotlivých krocích.  
  
 Klíč pro hostování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] v okně je <xref:System.Windows.Interop.HwndSource> třída. Tato třída zalomí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] v okně, což umožňuje jeho začlenění do vašeho [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] podřízeného okna. Následující postup kombinuje [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v jediné aplikaci.  
  
1. Implementujte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] svůj obsah jako spravovanou třídu.  
  
2. Implementace aplikace pro Windows pomocí C++/CLI. Pokud začínáte s existující aplikací a nespravovaným C++ kódem, můžete ji obvykle povolit pro volání spravovaného kódu změnou nastavení projektu tak, aby zahrnoval `/clr` příznak kompilátoru.  
  
3. Nastavte model dělení na vlákna (STA) s jedním vláknem.  
  
4. Zpracujte oznámení [WM_CREATE](/windows/desktop/winmsg/wm-create)v postupu okna a proveďte následující kroky:  
  
    1. Vytvoří nový <xref:System.Windows.Interop.HwndSource> objekt s nadřazeným oknem jako jeho `parent` parametr.  
  
    2. Vytvořte instanci vaší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] třídy obsahu.  
  
    3. Přiřaďte odkaz na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objekt Content <xref:System.Windows.Interop.HwndSource.RootVisual%2A> k vlastnosti <xref:System.Windows.Interop.HwndSource>objektu.  
  
    4. Získat HWND pro obsah <xref:System.Windows.Interop.HwndSource.Handle%2A> Vlastnost<xref:System.Windows.Interop.HwndSource> objektu obsahuje popisovač okna (HWND). Chcete-li získat HWND, který můžete použít v nespravované části aplikace, přetypování `Handle.ToPointer()` na HWND.  
  
5. Implementujte spravovanou třídu, která obsahuje statické pole pro uložení odkazu na váš [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah. Tato třída umožňuje získat odkaz na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah z vašeho [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kódu.  
  
6. Přiřaďte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah do statického pole.  
  
7. Příjem oznámení z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu připojením obslužné rutiny k jedné nebo více [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] událostem.  
  
8. Komunikujte s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahem pomocí odkazu, který jste uložili do statického pole pro nastavení vlastností a tak dále.  
  
> [!NOTE]
>  K implementaci vašeho [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] můžete použít také. Budete je však muset zkompilovat samostatně jako [!INCLUDE[TLA#tla_dll](../../../../includes/tlasharptla-dll-md.md)] a [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] odkazem z [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikace. Zbytek postupu je podobný jako uvedený výše.

<a name="implementing_the_application"></a>
## <a name="implementing-the-host-application"></a>Implementace hostitelské aplikace
 Tato část popisuje, jak hostovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah v základní [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikaci. Samotný obsah je implementován v C++/CLI jako spravovaná třída. Ve většině případů je to jednoduché [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programování. Klíčové aspekty implementace obsahu jsou popsány v tématu [implementace obsahu WPF](#implementing_the_wpf_page).

<a name="autoNestedSectionsOUTLINE1"></a>
- [Základní aplikace](#the_basic_application)

- [Hostování obsahu WPF](#hosting_the_wpf_page)

- [Držení odkazu na obsah WPF](#holding_a_reference)

- [Komunikace s obsahem WPF](#communicating_with_the_page)

<a name="the_basic_application"></a>
### <a name="the-basic-application"></a>Základní aplikace
 Výchozím bodem pro hostitelskou aplikaci bylo vytvoření šablony sady Visual Studio 2005.

1. Otevřete Visual Studio 2005 a v nabídce **soubor** vyberte **Nový projekt** .

2. V  seznamu [!INCLUDE[TLA2#tla_visualcpp](../../../../includes/tla2sharptla-visualcpp-md.md)] typů projektů vyberte Win32. Pokud váš výchozí jazyk není C++, najdete tyto typy projektů v části **jiné jazyky**.

3. Vyberte šablonu **projektu Win32** , přiřaďte k projektu název a kliknutím na tlačítko **OK** spusťte **Průvodce aplikací Win32**.

4. Přijměte výchozí nastavení průvodce a kliknutím na tlačítko **Dokončit** spusťte projekt.

 Šablona vytvoří základní [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikaci, včetně:

- Vstupní bod pro aplikaci.

- Okno s přiřazenou procedurou okna (WndProc).

- Nabídka se záhlavími **souborů** a **nápovědě** Nabídka **soubor** obsahuje položku **Exit** , která zavírá aplikaci. Nabídka **help** obsahuje **informace o** položce, která spustí jednoduché dialogové okno.

 Než začnete psát kód pro hostování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu, musíte provést dvě úpravy základní šablony.

 První je kompilovat projekt jako spravovaný kód. Ve výchozím nastavení se projekt zkompiluje jako nespravovaný kód. Protože [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je však implementován ve spravovaném kódu, projekt musí být zkompilován odpovídajícím způsobem.

1. Klikněte pravým tlačítkem myši na název projektu v **Průzkumník řešení** a v místní nabídce vyberte možnost **vlastnosti** . tím otevřete dialogové okno **stránky vlastností** .

2. Ve stromovém zobrazení v levém podokně vyberte **Vlastnosti konfigurace** .

3. V pravém podokně vyberte možnost Podpora **Common Language Runtime** ze seznamu **výchozích hodnot projektu** .

4. V rozevíracím seznamu vyberte možnost **Podpora Common Language Runtime (/CLR)** .

> [!NOTE]
>  Tento příznak kompilátoru umožňuje použít spravovaný kód v aplikaci, ale váš nespravovaný kód bude zkompilován jako dříve.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]používá model vláken s jedním vláknem (STA). Aby bylo možné správně pracovat s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kódem obsahu, je nutné nastavit model vláken aplikace na sta tím, že použijete atribut na vstupní bod.

 [!code-cpp[Win32HostingWPFPage#WinMain](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#winmain)]

<a name="hosting_the_wpf_page"></a>
### <a name="hosting-the-wpf-content"></a>Hostování obsahu WPF
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Obsah je jednoduchá aplikace zadávání adres. Obsahuje několik <xref:System.Windows.Controls.TextBox> ovládacích prvků pro uživatelské jméno, adresu a tak dále. K dispozici jsou <xref:System.Windows.Controls.Button> také dva ovládací prvky, **OK** a **Zrušit**. Když uživatel klikne na tlačítko **OK**, obslužná <xref:System.Windows.Controls.Primitives.ButtonBase.Click> rutina události tlačítka shromáždí data z <xref:System.Windows.Controls.TextBox> ovládacích prvků, přiřadí je k odpovídajícím vlastnostem a vyvolá vlastní `OnButtonClicked`událost. Když uživatel klikne na **Storno**, obslužná rutina `OnButtonClicked`jednoduše vyvolá. Objekt argumentu události pro `OnButtonClicked` obsahuje logické pole, které indikuje, na které tlačítko bylo kliknuto.

 Kód pro hostování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu je implementován v obslužné rutině pro oznámení [WM_CREATE](/windows/desktop/winmsg/wm-create) v okně hostitele.

 [!code-cpp[Win32HostingWPFPage#WMCreate](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcreate)]

 Metoda přebírá informace o velikosti a umístění spolu s popisovačem nadřazeného okna a vrací popisovač okna hostovaného [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu. `GetHwnd`

> [!NOTE]
>  Pro obor názvů nelze `#using`použít direktivu.`System::Windows::Interop` Tím se vytvoří kolize názvů mezi <xref:System.Windows.Interop.MSG> strukturou v tomto oboru názvů a strukturou MSG deklarovanou v Winuser. h. Místo toho je nutné použít plně kvalifikované názvy pro přístup k obsahu tohoto oboru názvů.

 [!code-cpp[Win32HostingWPFPage#GetHwnd](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#gethwnd)]

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Obsah nemůžete hostovat přímo v okně aplikace. Místo toho nejprve vytvoříte <xref:System.Windows.Interop.HwndSource> objekt pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zabalení obsahu. Tento objekt je v podstatě okno, které je navrženo pro hostování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu. <xref:System.Windows.Interop.HwndSource> Objekt můžete hostovat v nadřazeném okně jeho vytvořením jako podřízeného [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna, které je součástí vaší aplikace. Parametry konstruktoru obsahují mnohem stejné informace, které byste při [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] vytváření podřízeného okna předávali funkci CreateWindow. <xref:System.Windows.Interop.HwndSource>

 Dále vytvoříte instanci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objektu Content. V tomto případě [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je obsah implementován jako samostatná `WPFPage`třída, pomocí/CLI. C++ Můžete také implementovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. K tomu však potřebujete nastavit samostatný projekt a vytvořit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)]jako. Můžete přidat odkaz na [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] projekt a použít tento odkaz k vytvoření instance [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Obsah v podřízeném okně zobrazíte tak, že přiřadíte odkaz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] na obsah <xref:System.Windows.Interop.HwndSource>k <xref:System.Windows.Interop.HwndSource.RootVisual%2A> vlastnosti objektu.

 Další řádek kódu připojí obslužnou rutinu `WPFButtonClicked`události [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] k události obsahu `OnButtonClicked` . Tato obslužná rutina se volá, když uživatel klikne na tlačítko **OK** nebo **Storno** . Další diskuzi o této obslužné rutině události najdete v tématu [communicating_with_the_WPF Content](#communicating_with_the_page) .

 Poslední zobrazený řádek kódu vrátí popisovač okna (HWND), který je spojen s <xref:System.Windows.Interop.HwndSource> objektem. Pomocí tohoto popisovače z [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kódu můžete odesílat zprávy do hostovaného okna, i když ukázka to neudělá. <xref:System.Windows.Interop.HwndSource> Objekt vyvolá událost pokaždé, když obdrží zprávu. Chcete-li zpracovat zprávy, zavolejte <xref:System.Windows.Interop.HwndSource.AddHook%2A> metodu pro připojení obslužné rutiny zprávy a poté zpracování zpráv v této obslužné rutině.

<a name="holding_a_reference"></a>
### <a name="holding-a-reference-to-the-wpf-content"></a>Držení odkazu na obsah WPF
 U mnoha aplikací budete chtít s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahem později komunikovat. Můžete například chtít upravit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnosti obsahu nebo může <xref:System.Windows.Interop.HwndSource> mít objekt hostitele jiný [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah. K tomu potřebujete odkaz na <xref:System.Windows.Interop.HwndSource> objekt [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nebo obsah. Objekt a jeho přidružený [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah zůstanou v paměti, dokud nezničíte popisovač okna. <xref:System.Windows.Interop.HwndSource> Proměnná, kterou přiřadíte k <xref:System.Windows.Interop.HwndSource> objektu, však bude po návratu z postupu okna přecházet do rozsahu. Vlastní způsob, jak tento problém zpracovat u [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikací, je použít statickou nebo globální proměnnou. K těmto typům proměnných bohužel nelze přiřadit spravovaný objekt. Popisovač okna přidružený <xref:System.Windows.Interop.HwndSource> k objektu lze přiřadit globální nebo statické proměnné, ale tato operace Chvojková neposkytuje přístup k objektu samotnému.

 Nejjednodušší řešení tohoto problému je implementace spravované třídy, která obsahuje sadu statických polí pro blokování odkazů na jakékoli spravované objekty, ke kterým potřebujete přístup. Ukázka používá `WPFPageHost` třídu pro uchování odkazu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] na obsah a počáteční hodnoty počtu jeho vlastností, které může později změnit uživatel. Tato definice je definována v hlavičce.

 [!code-cpp[Win32HostingWPFPage#WPFPageHost](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.h#wpfpagehost)]

 Druhá část `GetHwnd` funkce přiřadí hodnoty do těchto polí pro pozdější použití, zatímco `myPage` je stále v oboru.

<a name="communicating_with_the_page"></a>
### <a name="communicating-with-the-wpf-content"></a>Komunikace s obsahem WPF
 Existují dva typy komunikace s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahem. Aplikace obdrží informace z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu, když uživatel klikne na tlačítko **OK** nebo **Storno** . Aplikace má [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] také možnost, která umožňuje uživateli měnit různé [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnosti obsahu, například barvu pozadí nebo výchozí velikost písma.

 Jak je uvedeno výše, když uživatel klikne buď na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tlačítko, obsah `OnButtonClicked` vyvolá událost. Aplikace k této události připojí obslužnou rutinu pro příjem těchto oznámení. Pokud bylo kliknuto na tlačítko **OK** , obslužná rutina získá informace o uživateli z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu a zobrazí ji v sadě statických ovládacích prvků.

 [!code-cpp[Win32HostingWPFPage#WPFButtonClicked](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wpfbuttonclicked)]

 Obslužná rutina obdrží z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] `MyPageEventArgs`obsahu objekt vlastního argumentu události. `IsOK` Vlastnost objektu je nastavena na `true` hodnotu, pokud bylo kliknuto na tlačítko **OK** a `false` bylo kliknuto na tlačítko **Storno** .

 Pokud bylo kliknuto na tlačítko **OK** , obslužná rutina získá odkaz na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah z třídy kontejneru. Poté shromáždí informace o uživateli, které jsou uchovávány prostřednictvím přidružených [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastností obsahu, a používá statické ovládací prvky k zobrazení informací v nadřazeném okně. Vzhledem k tomu, že data [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] obsahujsouveforměspravovanéhořetězce,jenutnéjizařaditpropoužitíovládacímprvkem.[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Pokud bylo kliknuto na tlačítko **Storno** , obslužná rutina vymaže data ze statických ovládacích prvků.

 Aplikace [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] poskytuje sadu přepínačů, které umožňují uživateli upravovat barvu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pozadí obsahu a několik vlastností souvisejících s písmy. Následující příklad je výpis z procedury okna aplikace (WndProc) a jeho zpracování zpráv, které nastavuje různé vlastnosti v různých zprávách, včetně barvy pozadí. Ostatní jsou podobné a nejsou zobrazeny. Podrobnosti a kontext najdete v kompletní ukázce.

 [!code-cpp[Win32HostingWPFPage#WMCommandToBG](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcommandtobg)]

 Chcete-li nastavit barvu pozadí, získejte odkaz na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah (`hostedPage`) z `WPFPageHost` a nastavte vlastnost barva pozadí na příslušnou barvu. Ukázka používá tři možnosti barev: původní barva, světle zelená nebo světle losos. Původní barva pozadí je uložena jako statické pole ve `WPFPageHost` třídě. Chcete-li nastavit druhé dva objekty, vytvořte nový <xref:System.Windows.Media.SolidColorBrush> objekt a předejte konstruktoru hodnotu statických barev <xref:System.Windows.Media.Colors> z objektu.

<a name="implementing_the_wpf_page"></a>
## <a name="implementing-the-wpf-page"></a>Implementace stránky WPF
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Obsah můžete hostovat a používat bez znalosti skutečné implementace. [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)]Pokud byl [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah zabalen samostatně, mohl by být sestaven v jakémkoli jazyce modulu CLR (Common Language Runtime). Následuje stručný návod k implementaci C++/CLI, která se používá v ukázce. Tato část obsahuje následující pododdíly.

<a name="autoNestedSectionsOUTLINE2"></a>
- [Rozložení](#page_layout)

- [Vrácení dat do hostitelského okna](#returning_data_to_window)

- [Nastavení vlastností WPF](#set_page_properties)

<a name="page_layout"></a>
### <a name="layout"></a>Rozložení
 Prvky v obsahu se skládají z pěti <xref:System.Windows.Controls.TextBox> ovládacích prvků s přidruženými <xref:System.Windows.Controls.Label> ovládacími prvky: [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Název, adresa, město, stát a PSČ. K dispozici jsou <xref:System.Windows.Controls.Button> také dva ovládací prvky, **OK** a **Zrušit** .

 Obsah je implementován `WPFPage` ve třídě. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Rozložení se zpracovává pomocí <xref:System.Windows.Controls.Grid> elementu layout. Třída dědí z <xref:System.Windows.Controls.Grid>, což efektivně zpřístupňuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kořenový prvek obsahu.

 Konstruktor obsahu má požadovanou šířku a výšku a <xref:System.Windows.Controls.Grid> podle toho velikost upraví. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Pak definuje základní <xref:System.Windows.Controls.ColumnDefinition> rozložení vytvořením sady objektů a <xref:System.Windows.Controls.RowDefinition> <xref:System.Windows.Controls.Grid> a jejich přidáním do základu <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> objektu a <xref:System.Windows.Controls.Grid.RowDefinitions%2A> kolekce v uvedeném pořadí. Tím se definuje mřížka s pěti řádky a sedmi sloupci s rozměry určenými obsahem buněk.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorToGridDef](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortogriddef)]

 Dále konstruktor přidá [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] prvky <xref:System.Windows.Controls.Grid>do. První prvek je text nadpisu, který je <xref:System.Windows.Controls.Label> ovládací prvek, který je zarovnán na střed prvního řádku mřížky.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorTitle](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortitle)]

 Další řádek obsahuje ovládací prvek název <xref:System.Windows.Controls.Label> a jeho přidružený <xref:System.Windows.Controls.TextBox> ovládací prvek. Vzhledem k tomu, že se stejný kód používá pro každou dvojici popisku nebo textového pole, je umístěn ve dvojici privátních metod a používá se pro všechna pět párů popisku nebo textového pole. Metody vytvoří příslušný ovládací prvek a zavolá <xref:System.Windows.Controls.Grid> statickou <xref:System.Windows.Controls.Grid.SetColumn%2A> třídu a <xref:System.Windows.Controls.Grid.SetRow%2A> metody k umístění ovládacích prvků do příslušné buňky. Po vytvoření ovládacího prvku ukázka volá <xref:System.Windows.Controls.UIElementCollection.Add%2A> metodu <xref:System.Windows.Controls.Panel.Children%2A> na vlastnost <xref:System.Windows.Controls.Grid> pro přidání ovládacího prvku do mřížky. Kód pro přidání zbývajících párů popisku nebo textového pole je podobný. Podrobnosti najdete v ukázkovém kódu.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorName](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorname)]

 Implementace těchto dvou metod je následující:

 [!code-cpp[Win32HostingWPFPage#WPFPageCreateHelpers](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagecreatehelpers)]

 Nakonec ukázka přidá tlačítka **OK** a **Storno** a připojí obslužnou rutinu události ke svým <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událostem.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorButtonsEvents](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorbuttonsevents)]

<a name="returning_data_to_window"></a>
### <a name="returning-the-data-to-the-host-window"></a>Vrácení dat do hostitelského okna
 Při kliknutí na tlačítko je vyvolána jeho <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událost. Hostitelské okno může jednoduše připojit obslužné rutiny k těmto událostem a získat data přímo z <xref:System.Windows.Controls.TextBox> ovládacích prvků. Ukázka používá poněkud méně přímý přístup. Zpracovává <xref:System.Windows.Controls.Primitives.ButtonBase.Click> ho `OnButtonClicked`v rámci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu a potom vyvolá vlastní událost pro oznamování obsahu. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Díky tomu může [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah provést několik ověření parametru před tím, než je hostitel upozorněn. Obslužná rutina získá text z <xref:System.Windows.Controls.TextBox> ovládacích prvků a přiřadí mu veřejné vlastnosti, ze kterých může hostitel získat informace.

 Deklarace události v WPFPage. h:

 [!code-cpp[Win32HostingWPFPage#WPFPageEventDecl](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpageeventdecl)]

 Obslužná <xref:System.Windows.Controls.Primitives.ButtonBase.Click> rutina události v WPFPage. cpp:

 [!code-cpp[Win32HostingWPFPage#WPFPageButtonClicked](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagebuttonclicked)]

<a name="set_page_properties"></a>
### <a name="setting-the-wpf-properties"></a>Nastavení vlastností WPF
 Hostitel umožní uživateli změnit několik [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastností obsahu. [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] Po straně je to prostě Změna vlastností. Implementace ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] třídě obsahu je trochu složitější, protože neexistuje žádná jediná globální vlastnost, která ovládá písma pro všechny ovládací prvky. Místo toho se v přístupových objektech set vlastností změní příslušná vlastnost pro každý ovládací prvek. Následující příklad ukazuje kód pro `DefaultFontFamily` vlastnost. Nastavení vlastnosti volá soukromou metodu, která zase nastaví <xref:System.Windows.Controls.Control.FontFamily%2A> vlastnosti pro různé ovládací prvky.

 Z WPFPage. h:

 [!code-cpp[Win32HostingWPFPage#WPFPageFontFamilyProperty](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpagefontfamilyproperty)]

 From WPFPage.cpp:

 [!code-cpp[Win32HostingWPFPage#WPFPageSetFontFamily](~/samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagesetfontfamily)]

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Interop.HwndSource>
- [Vzájemná spolupráce grafického subsystému WPF a systému Win32](wpf-and-win32-interoperation.md)
