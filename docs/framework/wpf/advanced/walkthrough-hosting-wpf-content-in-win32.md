---
title: 'Návod: Hostování obsahu WPF v Win32'
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- hosting WPF content in Win32 window [WPF]
ms.assetid: 38ce284a-4303-46dd-b699-c9365b22a7dc
ms.openlocfilehash: 692105d464c005109cbf1ff704045efa7d1e9173
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48842798"
---
# <a name="walkthrough-hosting-wpf-content-in-win32"></a>Návod: Hostování obsahu WPF v Win32
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje bohaté prostředí pro vytváření aplikací. Pokud však máte značné investice [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] kódu, může být mnohem efektivnější přidat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkce, které vaše aplikace místo přepsání původní kód. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje jednoduchý mechanismus pro hostování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna.  
  
 Tento kurz popisuje, jak psát ukázkovou aplikaci, [hostování obsahu WPF v ukázce okně Win32](https://go.microsoft.com/fwlink/?LinkID=160004), že hostitelé [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu v [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna. Můžete rozšířit tuto ukázku pro hostování všech [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna. Protože se týká kombinace spravovaného a nespravovaného kódu, je aplikace napsaná v [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)].  
  
 
  
<a name="requirements"></a>   
## <a name="requirements"></a>Požadavky  
 V tomto kurzu se předpokládá základní znalost obou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programování. Pro základní informace o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programování, naleznete v tématu [Začínáme](../../../../docs/framework/wpf/getting-started/index.md). Úvod do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programování, můžete by měly odkazovat všechny mnoho knih, které k tomuto tématu, zejména *programování Windows* podle Charles Petzold.  
  
 Protože vzorku, který doprovází tento kurz je implementována v [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)], tento kurz předpokládá znalost použití [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] programu [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] plus znalost programování spravovaného kódu. Znalost [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] je užitečné, ale není nutná.  
  
> [!NOTE]
>  Tento kurz obsahuje některé příklady kódů z přidružené ukázkové. Ale pro lepší čitelnost, neobsahuje úplnou ukázku kódu. Úplný ukázkový kód, naleznete v tématu [hostování obsahu WPF v ukázce okně Win32](https://go.microsoft.com/fwlink/?LinkID=160004).  
  
<a name="basic_procedure"></a>   
## <a name="the-basic-procedure"></a>Základní postup  
 Tato část popisuje základní postup použijte k hostiteli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu v [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna. Zbývající části popisují podrobnosti jednotlivých kroků.  
  
 Klíčem k hostování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] je okno <xref:System.Windows.Interop.HwndSource> třídy. Zabalí tuto třídu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu v [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna, což umožňuje začlenit do vaší [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] jako podřízeného okna. Tento přístup spojuje [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v jedné aplikaci.  
  
1.  Implementovat vaše [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah jako spravovanou třídu.  
  
2.  Implementace [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikace s [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)]. Pokud jste začínající existující aplikaci a nespravovaných [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] kódu, můžete obvykle ji povolit pro volání spravovaného kódu tak, že změníte nastavení projektu chcete zahrnout `/clr` příznaku kompilátoru.  
  
3.  Nastavte model vláken na jednovláknový apartment (STA).  
  
4.  Zpracování [WM_CREATE](/windows/desktop/winmsg/wm-create)oznámení v proceduru okna a proveďte následující akce:  
  
    1.  Vytvořte nový <xref:System.Windows.Interop.HwndSource> objekt s nadřazené okno jako jeho `parent` parametru.  
  
    2.  Vytvoření instance vaší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu třídy.  
  
    3.  Odkaz na přiřazení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu objektu <xref:System.Windows.Interop.HwndSource.RootVisual%2A> vlastnost <xref:System.Windows.Interop.HwndSource>.  
  
    4.  Získejte HWND pro obsah. <xref:System.Windows.Interop.HwndSource.Handle%2A> Vlastnost <xref:System.Windows.Interop.HwndSource> objekt obsahuje popisovač okna (HWND). HWND, který vám pomůže v nespravované součástí vaší aplikace získáte přetypování `Handle.ToPointer()` k popisovačem HWND.  
  
5.  Implementace spravované třídy, která obsahuje statické pole k uložení odkazu na vaši [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah. Tato třída umožňuje získat odkaz na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu z vašeho [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kódu.  
  
6.  Přiřazení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu pro statické pole.  
  
7.  Příjem oznámení z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu připojením obslužnou rutinu na jeden nebo více [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] události.  
  
8.  Komunikovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu pomocí odkazu, která je uložená ve statickém poli. Chcete-li nastavit vlastnosti a tak dále.  
  
> [!NOTE]
>  Můžete také použít [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] implementovat vaše [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah. Ale budete muset zkompilovat jej samostatně jako [!INCLUDE[TLA#tla_dll](../../../../includes/tlasharptla-dll-md.md)] a odkázat [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] z vaší [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikace. Zbytek postupu je podobný tomu uvedených výše.

<a name="implementing_the_application"></a>
## <a name="implementing-the-host-application"></a>Implementace hostitele aplikace
 Tato část popisuje, jak hostitele [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu v základní [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikace. Samotný obsah je implementována v [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] jako spravovanou třídu. Ve většině případů je jednoduché [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programování. Klíčové aspekty implementace obsahu jsou popsány v [implementace obsahu WPF](#implementing_the_wpf_page).

<a name="autoNestedSectionsOUTLINE1"></a>
-   [Základní aplikace](#the_basic_application)

-   [Hostování obsahu WPF](#hosting_the_wpf_page)

-   [Uchovávající odkaz na obsahu WPF](#holding_a_reference)

-   [Komunikace s obsahu WPF](#communicating_with_the_page)

<a name="the_basic_application"></a>
### <a name="the-basic-application"></a>Základní aplikace
 Výchozí bod pro hostitelskou aplikaci došlo k vytvoření šablony sady Visual Studio 2005.

1.  Otevřete Visual Studio 2005 a vyberte **nový projekt** z **souboru** nabídky.

2.  Vyberte **Win32** ze seznamu [!INCLUDE[TLA2#tla_visualcpp](../../../../includes/tla2sharptla-visualcpp-md.md)] typů projektů. Pokud není výchozí jazyk [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)], najdete tyto typy projektů v rámci **jiné jazyky**.

3.  Vyberte **projekt Win32** šablony, přiřaďte název projektu a klikněte na tlačítko **OK** ke spuštění **Průvodce aplikací Win32**.

4.  Přijměte výchozí nastavení průvodce a klikněte na tlačítko **Dokončit** ke spuštění projektu.

 Šablona vytvoří základní [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikace, včetně:

-   Vstupní bod pro aplikaci.

-   Okno, s proceduru související okno (WndProc).

-   Nabídka s **souboru** a **pomáhají** záhlaví. **Souboru** nabídka **ukončovací** položku, která slouží k ukončení aplikace. **Pomáhají** nabídka **o** položku, která spustí jednoduchých dialogového okna.

 Než začnete psát kód pro hostitele [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu, je třeba provést dvě změny do základní šablony.

 První je ke kompilaci projektu jako spravovaný kód. Ve výchozím nastavení se projekt zkompiluje jako nespravovaný kód. Ale protože [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je implementovaná ve spravovaném kódu, musí být projekt kompilován odpovídajícím způsobem.

1.  Klikněte pravým tlačítkem na název projektu v **Průzkumníka řešení** a vyberte **vlastnosti** z místní nabídky ke spuštění **stránky vlastností** dialogové okno.

2.  Vyberte **vlastnosti konfigurace** ve stromovém zobrazení v levém podokně.

3.  Vyberte **Common Language Runtime** podporu **výchozí nastavení projektu** seznam v pravém podokně.

4.  Vyberte **Common Language Runtime Support (/ clr)** z rozevíracího seznamu.

> [!NOTE]
>  Tento příznak kompilátoru umožňuje používat spravovaný kód ve vaší aplikaci, ale nespravovaný kód bude stále kompilovat jako předtím.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá jednovláknový apartment (STA) model vláken. Aby bylo možné správně pracovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu kódu, je nutné nastavit model vláken aplikace na STA použitím atributu na vstupní bod.

 [!code-cpp[Win32HostingWPFPage#WinMain](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#winmain)]

<a name="hosting_the_wpf_page"></a>
### <a name="hosting-the-wpf-content"></a>Hostování obsahu WPF
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Obsah je jednoduché adresy vstupní aplikace. Skládá se z několika <xref:System.Windows.Controls.TextBox> ovládacích prvků pro uživatelské jméno, adresu a tak dále. Jsou zde také dva <xref:System.Windows.Controls.Button> ovládací prvky, **OK** a **zrušit**. Když uživatel klepne **OK**, tlačítka <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obslužná rutina události shromažďuje data z <xref:System.Windows.Controls.TextBox> ovládací prvky, přiřadí odpovídající vlastnosti a vyvolá vlastní událost `OnButtonClicked`. Když uživatel klepne **zrušit**, jednoduše vyvolá obslužnou rutinu `OnButtonClicked`. Objekt argumentu události pro `OnButtonClicked` obsahuje pole Boolean určující, které tlačítko došlo ke kliknutí na.

 Kód pro hostitele [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah je implementována v obslužné rutiny pro [WM_CREATE](/windows/desktop/winmsg/wm-create) oznámení v okně hostitele.

 [!code-cpp[Win32HostingWPFPage#WMCreate](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcreate)]

 `GetHwnd` Metoda přijímá informace velikost a umístění a nadřazeného popisovač okna a vrátí popisovač okna hostovanou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah.

> [!NOTE]
>  Nelze použít `#using` směrnice pro `System::Windows::Interop` oboru názvů. Tím se vytvoří kolize názvů mezi <xref:System.Windows.Interop.MSG> struktury v tomto oboru názvů a msg – struktura deklarována ve winuser. Místo toho musíte použít plně kvalifikované názvy pro přístup k obsahu daného oboru názvů.

 [!code-cpp[Win32HostingWPFPage#GetHwnd](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#gethwnd)]

 Nelze umístit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu přímo v okně aplikace. Místo toho byste nejprve vytvořit <xref:System.Windows.Interop.HwndSource> pro obtékání [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah. Tento objekt je v podstatě okno, které slouží k hostování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah. Můžete hostovat <xref:System.Windows.Interop.HwndSource> v nadřazené okno tak, že vytvoříte jako podřízený objekt [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno, které je součástí vaší aplikace. <xref:System.Windows.Interop.HwndSource> Parametry konstruktoru obsahují mnohem stejné informace, které by předat CreateWindow při vytváření [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] podřízené okno.

 Dále vytvoříte instanci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu objektu. V takovém případě [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah je implementovaný jako samostatné třídy `WPFPage`s použitím [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)]. Je možné implementovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu s [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Ale k tomu budete muset nastavit samostatný projekt a sestavení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jako obsahu [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)]. Můžete přidat odkaz na daný [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] k projektu a použití, které odkazují k vytvoření instance [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah.

 Můžete zobrazit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu ve vašich podřízeného okna tak, že přiřadíte odkaz na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah <xref:System.Windows.Interop.HwndSource.RootVisual%2A> vlastnost <xref:System.Windows.Interop.HwndSource>.

 Další řádek kódu připojí obslužnou rutinu události `WPFButtonClicked`, možnosti [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah `OnButtonClicked` událostí. Tato obslužná rutina se volá, když uživatel klikne **OK** nebo **zrušit** tlačítko. Zobrazit [communicating_with_the_WPF obsah](#communicating_with_the_page) Další informace o této obslužné rutiny události.

 Vrátí popisovač okna (HWND), který je spojen s poslední řádek kódu ukazuje <xref:System.Windows.Interop.HwndSource> objektu. Můžete použít tento ovladač z vaší [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kódu pro odesílání zpráv do okna prostředí, i když se ukázka tak neučiní. <xref:System.Windows.Interop.HwndSource> Objekt vyvolá událost pokaždé, když se přijme zprávu. Ke zpracování zpráv, zavolejte <xref:System.Windows.Interop.HwndSource.AddHook%2A> metoda připojte obslužné rutiny zpráv a následně zpracovat zprávy v této rutině.

<a name="holding_a_reference"></a>
### <a name="holding-a-reference-to-the-wpf-content"></a>Uchovávající odkaz na obsahu WPF
 Pro mnoho aplikací, můžete ke komunikaci s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu později. Například můžete chtít změnit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah vlastnosti nebo možná jste <xref:System.Windows.Interop.HwndSource> jiný objekt hostitele [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah. Chcete-li to provést, potřebujete odkaz na <xref:System.Windows.Interop.HwndSource> objektu nebo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah. <xref:System.Windows.Interop.HwndSource> Objektu a jeho přidruženého [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah zůstanou v paměti, dokud zničit popisovač okna. Ale proměnné můžete přiřadit <xref:System.Windows.Interop.HwndSource> objektu bude poté, co vrátí z procedury okna dostanou mimo rozsah. Obvyklé způsob, jak zpracovat tento problém s [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikací je použití statické nebo globální proměnné. Spravovaný objekt bohužel nelze přiřadit tyto typy proměnných. Můžete přiřadit přidružen nativní popisovač okna <xref:System.Windows.Interop.HwndSource> do globální nebo statická proměnná, ale, že doe poskytovat přístup k objektu samotného objektu.

 Nejjednodušším řešením tohoto problému je implementace spravovanou třídu, která obsahuje sadu statických polí pro odkazy pro všemi spravovanými objekty, které potřebují přístup k uložení. Ukázka používá `WPFPageHost` třídy pro uložení odkazu na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu včetně počáteční hodnoty počtu její vlastnosti, které může uživatel později změnit. Toto je definováno v záhlaví.

 [!code-cpp[Win32HostingWPFPage#WPFPageHost](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.h#wpfpagehost)]

 Druhá část `GetHwnd` funkce přiřazuje hodnoty těchto polí pro pozdější použití při `myPage` je stále v oboru.

<a name="communicating_with_the_page"></a>
### <a name="communicating-with-the-wpf-content"></a>Komunikace s obsahu WPF
 Existují dva typy komunikace se službou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah. Aplikace obdrží informace z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah, když uživatel klikne **OK** nebo **zrušit** tlačítka. Aplikace má také [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , který umožňuje uživateli změnit různými [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah vlastnosti, jako je například velikost písma barvy nebo výchozí pozadí.

 Jak je uvedeno výše, když uživatel klepne buď tlačítko [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu vyvolá `OnButtonClicked` událostí. Aplikace připojí obslužnou rutinu pro tuto událost, chcete-li dostávat tato oznámení. Pokud **OK** došlo ke kliknutí na tlačítko, obslužná rutina načte informace o uživateli z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu a zobrazí ho v sadě statické ovládací prvky.

 [!code-cpp[Win32HostingWPFPage#WPFButtonClicked](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wpfbuttonclicked)]

 Obslužná rutina přijímá argument objektu vlastní události z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah, `MyPageEventArgs`. Objektu `IsOK` je nastavena na `true` Pokud **OK** došlo ke kliknutí na tlačítko, a `false` Pokud **zrušit** došlo ke kliknutí na tlačítko.

 Pokud **OK** došlo ke kliknutí na tlačítko, získá odkaz na obslužnou rutinu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu ze třídy kontejneru. Následně shromažďuje informace o uživateli, který se nachází přiřazeným [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah vlastnosti a použití statické ovládací prvky pro zobrazení informací v nadřazeném okně. Protože [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu data jsou ve formě řetězce, bylo potřeba zařadit používají [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ovládacího prvku. Pokud **zrušit** došlo ke kliknutí na tlačítko, obslužná rutina vymaže data z statické ovládací prvky.

 Aplikace [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] poskytuje sadu přepínací tlačítka, které umožní uživateli změnit barvu pozadí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah a několik vlastností písma související. Následující příklad je výpisem z procedury okna aplikace (WndProc) a její zprávy zpracování, který nastaví různé vlastnosti na různé zprávy, včetně barvu pozadí. Ostatní jsou podobné a nejsou zobrazeny. Zobrazit úplnou ukázku podrobnosti a kontext.

 [!code-cpp[Win32HostingWPFPage#WMCommandToBG](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcommandtobg)]

 Pokud chcete nastavit barvu pozadí, získejte odkaz na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah (`hostedPage`) z `WPFPageHost` a nastavte vlastnost barvu pozadí na požadovanou barvu. Ukázka používá tři volby barev: původní barvu, světle zelená nebo světle lososová. Původní barva pozadí se ukládá jako statické pole v `WPFPageHost` třídy. Chcete-li nastavit další dva, vytvořte nový <xref:System.Windows.Media.SolidColorBrush> objektu a předejte hodnotu statické barvy z konstruktoru <xref:System.Windows.Media.Colors> objektu.

<a name="implementing_the_wpf_page"></a>
## <a name="implementing-the-wpf-page"></a>Implementace stránky WPF
 Můžete hostovat a používat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu bez znalosti jazyka se skutečná implementace. Pokud [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah měl byla zabalena v samostatném [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)], ho může sestavené v libovolném [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] jazyka. Tady je stručný návod [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] implementace, která se používá v ukázce. Tato část obsahuje následující témata.

<a name="autoNestedSectionsOUTLINE2"></a>
-   [Rozložení](#page_layout)

-   [Vrací Data do okna hostitele](#returning_data_to_window)

-   [Nastavení vlastností WPF](#set_page_properties)

<a name="page_layout"></a>
### <a name="layout"></a>Rozložení
 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Prvky [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu se skládá z pěti <xref:System.Windows.Controls.TextBox> ovládací prvky, s přidruženými <xref:System.Windows.Controls.Label> ovládacích prvků: název, adresu, Město, stát a Zip. Jsou zde také dva <xref:System.Windows.Controls.Button> ovládací prvky, **OK** a **zrušit**

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Obsah je implementována v `WPFPage` třídy. Zpracovává rozložení s <xref:System.Windows.Controls.Grid> element rozložení. Třída dědí z <xref:System.Windows.Controls.Grid>, což účinně vytvoří [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu kořenový element.

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Obsahu konstruktoru přijímá požadované šířku a výšku a velikosti <xref:System.Windows.Controls.Grid> odpovídajícím způsobem. Potom definuje základní rozložení tak, že vytvoříte sadu <xref:System.Windows.Controls.ColumnDefinition> a <xref:System.Windows.Controls.RowDefinition> objekty a jejich přidání na <xref:System.Windows.Controls.Grid> základní objekt <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> a <xref:System.Windows.Controls.Grid.RowDefinitions%2A> kolekcí, v uvedeném pořadí. Definuje mřížky pěti řádcích a sedmi sloupcích, s dimenzemi určené obsah buňky.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorToGridDef](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortogriddef)]

 V dalším kroku se přidá konstruktoru [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] prvků, které mají <xref:System.Windows.Controls.Grid>. Prvním prvkem je text nadpisu, který je <xref:System.Windows.Controls.Label> ovládacího prvku, které jsou zaměřeny na prvním řádku mřížky.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorTitle](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortitle)]

 Další řádek obsahuje název <xref:System.Windows.Controls.Label> ovládacího prvku a jeho přidruženého <xref:System.Windows.Controls.TextBox> ovládacího prvku. Stejný kód, protože se používají pro každý pár popisku nebo textového pole je umístěna společně s privátní metody a použít pro všechny pět párů popisku nebo textového pole. Metody vytvoření odpovídající ovládací prvek a volat <xref:System.Windows.Controls.Grid> statická třída <xref:System.Windows.Controls.Grid.SetColumn%2A> a <xref:System.Windows.Controls.Grid.SetRow%2A> metody umístit ovládací prvky v buňku. Po vytvoření ovládacího prvku, ukázka zavolá <xref:System.Windows.Controls.UIElementCollection.Add%2A> metodu <xref:System.Windows.Controls.Panel.Children%2A> vlastnost <xref:System.Windows.Controls.Grid> přidání ovládacího prvku do mřížky. Kód pro přidání zbývající páry popisku nebo textového pole je podobné. Zobrazit ukázkový kód pro podrobnosti.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorName](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorname)]

 Implementace ze dvou způsobů je následujícím způsobem:

 [!code-cpp[Win32HostingWPFPage#WPFPageCreateHelpers](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagecreatehelpers)]

 Nakonec ukázka přidá **OK** a **zrušit** tlačítka a připojí obslužnou rutinu události pro jejich <xref:System.Windows.Controls.Primitives.ButtonBase.Click> události.

 [!code-cpp[Win32HostingWPFPage#WPFPageCtorButtonsEvents](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorbuttonsevents)]

<a name="returning_data_to_window"></a>
### <a name="returning-the-data-to-the-host-window"></a>Vrací Data do okna hostitele
 Po kliknutí na tlačítko buď jeho <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událost se vyvolá. Okno hostitele může jednoduše připojte obslužné rutiny těmto událostem a získat data přímo z <xref:System.Windows.Controls.TextBox> ovládacích prvků. Ukázka používá méně přímý přístup. Zpracovává <xref:System.Windows.Controls.Primitives.ButtonBase.Click> v rámci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu a poté vyvolá vlastní událost `OnButtonClicked`, upozornit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah. Díky tomu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu provedete nějaké parametr ověření, než oznámí hostitele. Získá text z obslužné rutiny <xref:System.Windows.Controls.TextBox> ovládací prvky a přiřadí ji k veřejné vlastnosti, ze kterých můžete načíst hostiteli informace.

 Deklarace událostí v WPFPage.h:

 [!code-cpp[Win32HostingWPFPage#WPFPageEventDecl](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpageeventdecl)]

 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> Obslužné rutiny události v WPFPage.cpp:

 [!code-cpp[Win32HostingWPFPage#WPFPageButtonClicked](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagebuttonclicked)]

<a name="set_page_properties"></a>
### <a name="setting-the-wpf-properties"></a>Nastavení vlastností WPF
 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] Hostitele umožňuje uživateli změnit několik [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah vlastnosti. Z [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] straně, je jednoduše pár změn vlastností. Implementace ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu třída je o něco složitější, protože neexistuje žádný jedinou globální vlastnost písma pro všechny ovládací prvky pro ovládací prvky. Místo toho příslušné vlastnosti pro každý ovládací prvek se změnilo v přístupových objektů vlastností sady. Následující příklad ukazuje kód `DefaultFontFamily` vlastnost. Nastavení vlastnosti volá soukromou metodu, která zase sad <xref:System.Windows.Controls.Control.FontFamily%2A> vlastnosti pro různé ovládací prvky.

 Z WPFPage.h:

 [!code-cpp[Win32HostingWPFPage#WPFPageFontFamilyProperty](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpagefontfamilyproperty)]

 Z WPFPage.cpp:

 [!code-cpp[Win32HostingWPFPage#WPFPageSetFontFamily](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagesetfontfamily)]

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Interop.HwndSource>
- [Vzájemná spolupráce grafického subsystému WPF a systému Win32](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)