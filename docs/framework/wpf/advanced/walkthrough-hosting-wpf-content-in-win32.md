---
title: 'Návod: Hostování obsahu WPF v Win32'
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- hosting WPF content in Win32 window [WPF]
ms.assetid: 38ce284a-4303-46dd-b699-c9365b22a7dc
ms.openlocfilehash: 429acf6e3b37f5532e031fdef999d252a3aae3cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549448"
---
# <a name="walkthrough-hosting-wpf-content-in-win32"></a>Návod: Hostování obsahu WPF v Win32
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje bohaté prostředí pro vytváření aplikací. Pokud však máte významné investice [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] kódu, může být efektivnější přidat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkce do vaší aplikace a nikoli přepisování původní kód. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Poskytuje přehledné mechanismus pro hostování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno.  
  
 Tento kurz popisuje, jak psát ukázkové aplikace, [hostování obsahu subsystému WPF v ukázku okno Win32](http://go.microsoft.com/fwlink/?LinkID=160004), že hostitelé [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno. Tato ukázka hostování všech můžete rozšířit [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno. Protože se týká kombinování spravovanými a nespravovanými kódu, aplikace je napsána v [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)].  
  
 
  
<a name="requirements"></a>   
## <a name="requirements"></a>Požadavky  
 Tento kurz předpokládá základní znalost obou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programování. Pro základní informace o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programování, najdete v části [Začínáme](../../../../docs/framework/wpf/getting-started/index.md). Úvod do [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programování, by měl odkazujete některé z mnoha knih na subjektu, zejména *programování Windows* podle Charlese Petzold.  
  
 Protože vzorku, který doprovází tento kurz je implementována ve [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)], tento kurz předpokládá znalost použití [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] programu [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] plus představu o programování spravovaného kódu. Znalost [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] je užitečné, ale není nezbytné.  
  
> [!NOTE]
>  Tento kurz zahrnuje několik příklady kódu z přidružených ukázky. Ale čitelnější neobsahuje úplný ukázkový kód. Úplný ukázkový kód, najdete v části [hostování obsahu WPF ve vzorku okno Win32](http://go.microsoft.com/fwlink/?LinkID=160004).  
  
<a name="basic_procedure"></a>   
## <a name="the-basic-procedure"></a>Základní postup  
 Tato část popisuje základní postup použijete k hostiteli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno. Zbývající části popisují podrobnosti o jednotlivých kroků.  
  
 Klíč k hostování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu na [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] je okno <xref:System.Windows.Interop.HwndSource> třídy. Zabalí tuto třídu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno, díky kterému jej začlenit do vaší [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] jako podřízeného okna. Následující metoda kombinuje [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v jedné aplikaci.  
  
1.  Implementace vaší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah jako spravovanou třídou.  
  
2.  Implementace [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikace s [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)]. Pokud jste od verze existující aplikaci a nespravované [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] kódu, můžete obvykle ho povolit volání spravovaného kódu změnou nastavení projektu zahrnout `/clr` příznak kompilátoru.  
  
3.  Nastavte model vláken single-threaded apartment (STA).  
  
4.  Zpracování [WM_CREATE](http://msdn.microsoft.com/library/ms632619.aspx)oznámení v postupu okno a proveďte následující akce:  
  
    1.  Vytvořte novou <xref:System.Windows.Interop.HwndSource> objekt s nadřazeného okna jako jeho `parent` parametr.  
  
    2.  Vytvoření instance vaší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu třídy.  
  
    3.  Přiřaďte odkaz na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu objekt, který má <xref:System.Windows.Interop.HwndSource.RootVisual%2A> vlastnost <xref:System.Windows.Interop.HwndSource>.  
  
    4.  Získáte HWND pro obsah. <xref:System.Windows.Interop.HwndSource.Handle%2A> Vlastnost <xref:System.Windows.Interop.HwndSource> objekt obsahuje popisovač okna (HWND). Pokud chcete popisovačem HWND, který můžete použít v nespravované součástí aplikace, přetypujte `Handle.ToPointer()` k popisovačem HWND.  
  
5.  Implementace spravovaných třídu, která obsahuje statické pole pro uložení odkaz na vaši [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah. Tato třída umožňuje získat odkaz na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu z vašeho [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kódu.  
  
6.  Přiřazení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu do statického pole.  
  
7.  Příjem oznámení z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu připojením obslužné rutiny na jeden nebo více [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] události.  
  
8.  Komunikovat s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu pomocí odkazu, který je uložený v statické pole a nastavte vlastnosti a tak dále.  
  
> [!NOTE]
>  Můžete také použít [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] implementovat vaše [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah. Ale je nutné jej zkompilovat samostatně jako [!INCLUDE[TLA#tla_dll](../../../../includes/tlasharptla-dll-md.md)] a odkaz, který [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] z vaší [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikace. Zbytek postupu je podobná uvedených výše.  
  
<a name="implementing_the_application"></a>   
## <a name="implementing-the-host-application"></a>Implementace aplikace pro hostitele  
 Tato část popisuje, jak hostitele [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu v základní [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikace. Samotný obsah je implementována ve [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] jako spravovanou třídou. Ve většině případů je jednoduchá [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] programování. Klíčových aspektů obsahu implementace, které jsou popsané v [implementace obsahu WPF](#implementing_the_wpf_page).  
  
<a name="autoNestedSectionsOUTLINE1"></a>   
-   [Základní aplikační](#the_basic_application)  
  
-   [Hostování obsahu subsystému WPF](#hosting_the_wpf_page)  
  
-   [Podržíte odkaz na obsah WPF](#holding_a_reference)  
  
-   [Komunikuje s obsahu WPF](#communicating_with_the_page)  
  
<a name="the_basic_application"></a>   
### <a name="the-basic-application"></a>Základní aplikační  
 Výchozím bodem pro hostitelskou aplikaci byl k vytvoření [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] šablony.  
  
1.  Otevřete [!INCLUDE[TLA2#tla_visualstu2005](../../../../includes/tla2sharptla-visualstu2005-md.md)]a vyberte **nový projekt** z **souboru** nabídky.  
  
2.  Vyberte **Win32** ze seznamu [!INCLUDE[TLA2#tla_visualcpp](../../../../includes/tla2sharptla-visualcpp-md.md)] typy projektů. Pokud není výchozí jazyk [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)], zjistíte, tyto typy projektů v části **jiné jazyky**.  
  
3.  Vyberte **projektu Win32** šablony, přiřadit název projektu a klikněte na tlačítko **OK** ke spuštění **Win32 – Průvodce aplikací**.  
  
4.  Přijměte výchozí nastavení v průvodci a klikněte na **Dokončit** a spusťte projekt.  
  
 Šablona vytvoří základní [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikace, včetně:  
  
-   Vstupní bod pro aplikaci.  
  
-   Okno, pomocí procedury okna přidružené (WndProc –).  
  
-   Nabídku s **soubor** a **pomoci** záhlaví. **Soubor** má nabídky **ukončení** položku, která ukončí aplikaci. **Pomoci** má nabídky **o** položku, která spustí jednoduché dialogové okno.  
  
 Než začnete psát kód pro hostitele [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu, budete muset udělat dvě úpravy základní šablony.  
  
 První je kompilace projektu jako spravovaného kódu. Ve výchozím projektu zkompiluje jako nespravovaný kód. Ale protože [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je implementována ve spravovaném kódu, musí být projektu zkompilovány odpovídajícím způsobem.  
  
1.  Klikněte pravým tlačítkem myši na název projektu v **Průzkumníku řešení** a vyberte **vlastnosti** z místní nabídky ke spuštění **stránky vlastností** dialogové okno.  
  
2.  Vyberte **vlastnosti konfigurace** z stromové zobrazení v levém podokně.  
  
3.  Vyberte **modul Common Language Runtime** podporují z **výchozí projekt** seznamu v pravém podokně.  
  
4.  Vyberte **Common Language Runtime Support (/ clr)** z rozevíracího seznamu.  
  
> [!NOTE]
>  Tento příznak kompilátoru umožňuje používat spravovaného kódu v aplikaci, ale nespravovaného kódu stále zkompilovat jako předtím.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá jednovláknový (STA) model vláken typu apartment. Aby bylo možné správně pracovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu kód, je nutné nastavit model vláken aplikace na STA použitím atribut vstupní bod.  
  
 [!code-cpp[Win32HostingWPFPage#WinMain](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#winmain)]  
  
<a name="hosting_the_wpf_page"></a>   
### <a name="hosting-the-wpf-content"></a>Hostování obsahu subsystému WPF  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Obsah je jednoduché adresy vstupní aplikace. Se skládá z několika <xref:System.Windows.Controls.TextBox> ovládací prvky uživatelské jméno, adresu a tak dále. Jsou zde také dva <xref:System.Windows.Controls.Button> ovládací prvky, **OK** a **zrušit**. Když uživatel klikne na **OK**, na tlačítko <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obslužné rutiny události shromažďuje data z <xref:System.Windows.Controls.TextBox> ovládací prvky, přiřadí ji k odpovídající vlastnosti a vyvolá vlastní události `OnButtonClicked`. Když uživatel klikne na **zrušit**, jednoduše vyvolá obslužnou rutinu `OnButtonClicked`. Objekt argument události pro `OnButtonClicked` obsahuje logické pole, která určuje, které tlačítko bylo kliknuto.  
  
 Kód pro hostitele [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah je implementována ve obslužnou rutinu pro [WM_CREATE](http://msdn.microsoft.com/library/ms632619.aspx) oznámení v okně hostitele.  
  
 [!code-cpp[Win32HostingWPFPage#WMCreate](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcreate)]  
  
 `GetHwnd` Metoda přijímá informace o velikosti a pozice plus nadřazený popisovač okna a vrátí popisovač okna hostované [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah.  
  
> [!NOTE]
>  Nelze použít `#using` direktivy pro `System::Windows::Interop` oboru názvů. Kolize názvů mezi vytvoříte tak <xref:System.Windows.Interop.MSG> struktury v daném oboru názvů a struktura MSG deklarované v winuser. Místo toho musíte použít názvy úplný přístup k obsahu daného oboru názvů.  
  
 [!code-cpp[Win32HostingWPFPage#GetHwnd](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#gethwnd)]  
  
 Nelze hostovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu přímo v okně vaší aplikace. Místo toho je nejprve vytvořit <xref:System.Windows.Interop.HwndSource> objekt zabalit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah. Tento objekt je v podstatě okno, které slouží k hostování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah. Hostujete <xref:System.Windows.Interop.HwndSource> objektu v okně nadřazené vytvořením jako podřízenou [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna, které je součástí vaší aplikace. <xref:System.Windows.Interop.HwndSource> Konstruktor parametry obsahovat mnohem stejné informace, které by předat CreateWindow při vytváření [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] podřízeného okna.  
  
 Vytvoříte další instanci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objekt obsahu. V takovém případě [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah je implementovaný jako samostatné třídy, `WPFPage`pomocí [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)]. Může také implementovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu s [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Ale k tomu budete muset nastavit samostatného projektu a sestavení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah jako [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)]. Můžete přidat odkaz na daný [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] k projektu a které odkaz na vytvoření instance [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah.  
  
 Můžete zobrazit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu v okně podřízené přiřazením odkaz na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah <xref:System.Windows.Interop.HwndSource.RootVisual%2A> vlastnost <xref:System.Windows.Interop.HwndSource>.  
  
 Dalším řádku kódu připojí obslužnou rutinu události `WPFButtonClicked`do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah `OnButtonClicked` událostí. Tato obslužná rutina je volána, když uživatel klikne **OK** nebo **zrušit** tlačítko. V tématu [communicating_with_the_WPF obsah](#communicating_with_the_page) Další informace o této obslužné rutiny události.  
  
 Vrátí popisovač okna (HWND), který je spojen s poslední řádek kódu ukazuje <xref:System.Windows.Interop.HwndSource> objektu. Můžete použít tento popisovač z vaší [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kódu pro odeslání zprávy do okna hostované, i když vzorku tak neprovádí. <xref:System.Windows.Interop.HwndSource> Objekt vyvolá událost pokaždé, když obdrží zprávu. Ke zpracování zpráv, volání <xref:System.Windows.Interop.HwndSource.AddHook%2A> metoda připojení obslužné rutiny zpráv a potom zpracování zpráv v této obslužné rutiny.  
  
<a name="holding_a_reference"></a>   
### <a name="holding-a-reference-to-the-wpf-content"></a>Podržíte odkaz na obsah WPF  
 Pro mnoho aplikací, můžete ke komunikaci s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu později. Například můžete chtít změnit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu vlastnosti, nebo třeba mít <xref:System.Windows.Interop.HwndSource> objekt hostitele jiný [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah. K tomu potřebujete odkaz na <xref:System.Windows.Interop.HwndSource> objekt nebo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah. <xref:System.Windows.Interop.HwndSource> Objekt a jeho přidružený [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah zůstat v paměti, dokud destroy popisovač okna. Ale proměnné můžete přiřadit <xref:System.Windows.Interop.HwndSource> objektu se dostala mimo rozsah při návratu z procedury okna. Obvyklým způsobem, jak zpracovávat tento problém s [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikace je použití statické nebo globální proměnné. Bohužel nelze přiřadit spravovaného objektu na tyto typy proměnných. Můžete přiřadit popisovač okna přidružené <xref:System.Windows.Interop.HwndSource> objektu globální nebo statické proměnné, ale, že doe neposkytuje přístup odkaz sám na sebe.  
  
 Nejjednodušší řešení tohoto problému je implementace spravovaných třídu, která obsahuje sadu statických polí k udržení odkazů na spravované objekty, které potřebují přístup k. Ukázce se používá `WPFPageHost` třída pro uložení odkaz na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah plus počáteční hodnoty počtu jeho vlastnosti, které může uživatel později změnit. To je definováno v hlavičce.  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageHost](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.h#wpfpagehost)]  
  
 Druhé části `GetHwnd` funkce přiřazuje hodnoty těchto polí pro pozdější použití při `myPage` je stále v oboru.  
  
<a name="communicating_with_the_page"></a>   
### <a name="communicating-with-the-wpf-content"></a>Komunikuje s obsahu WPF  
 Existují dva typy komunikace s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah. Aplikace obdrží informace z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu, když uživatel klikne **OK** nebo **zrušit** tlačítka. Aplikace má také [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , který umožňuje uživatelům změnit různé [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu vlastnosti, jako je například velikost písma barvu nebo výchozí pozadí.  
  
 Jak je uvedeno nahoře, když uživatel klikne buď tlačítko [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu vyvolá `OnButtonClicked` událostí. Aplikace připojí k této události pro příjem těchto oznámení obslužnou rutinu. Pokud **OK** bylo stisknuto tlačítko, obslužná rutina získá informace o uživateli z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu a zobrazí se v sadě statické ovládací prvky.  
  
 [!code-cpp[Win32HostingWPFPage#WPFButtonClicked](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wpfbuttonclicked)]  
  
 Obslužná rutina přijímá objekt argument vlastní události z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu, `MyPageEventArgs`. Objektu `IsOK` je nastavena na `true` Pokud **OK** bylo stisknuto tlačítko, a `false` Pokud **zrušit** bylo stisknuto tlačítko.  
  
 Pokud **OK** bylo stisknuto tlačítko, obslužná rutina získá odkaz na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu ze třídy kontejneru. Pak shromáždí informace o uživateli, která se nachází přiřazeným [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu vlastnosti a používá statické ovládací prvky pro zobrazení informací v nadřazeném okně. Protože [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu data jsou ve formě řetězce, má být zařazena pro použití [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ovládacího prvku. Pokud **zrušit** bylo stisknuto tlačítko, obslužná rutina vymaže data z statické ovládací prvky.  
  
 Aplikace [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] poskytuje sadu přepínačů, který umožní uživatelům změnit barvu pozadí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah a několik vlastností souvisejících s písma. Následující příklad je výňatek z procedury okna aplikace (WndProc) a jeho zpracování, který zpráv na jiné zprávy, včetně barvu pozadí nastaví různé vlastnosti. Ostatní jsou podobné a nejsou zobrazeny. Najdete je kompletní ukázka podrobnosti a kontext.  
  
 [!code-cpp[Win32HostingWPFPage#WMCommandToBG](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/Win32HostingWPFPage.cpp#wmcommandtobg)]  
  
 Pokud chcete nastavit barvu pozadí, získat odkaz na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah (`hostedPage`) z `WPFPageHost` a nastavte vlastnost Barva pozadí na požadovanou barvu. Ukázka používá tři možnosti barev: původní barvu, světle zelená nebo světla losos. Původní barva pozadí se ukládají jako statické pole v `WPFPageHost` třídy. Pro nastavení dalších dvou, vytvořte novou <xref:System.Windows.Media.SolidColorBrush> objektu a předat hodnotu statických barvy z konstruktoru <xref:System.Windows.Media.Colors> objektu.  
  
<a name="implementing_the_wpf_page"></a>   
## <a name="implementing-the-wpf-page"></a>Implementace stránce WPF  
 Můžete hostovat a používat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu bez znalostí skutečné implementace. Pokud [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu byl vytvořen balíček v samostatném [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)], se může jsou součástí žádné [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] jazyk. Následuje stručný návod [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] implementace, která se používá v ukázce. Tato část obsahuje následující témata.  
  
<a name="autoNestedSectionsOUTLINE2"></a>   
-   [Rozložení](#page_layout)  
  
-   [Vrací Data do okna hostitele](#returning_data_to_window)  
  
-   [Nastavení vlastností WPF](#set_page_properties)  
  
<a name="page_layout"></a>   
### <a name="layout"></a>Rozložení  
 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Elementů v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu se skládá z pěti <xref:System.Windows.Controls.TextBox> řídí, k přiřazen <xref:System.Windows.Controls.Label> ovládacích prvků: jméno, adresu, Město, stavu a Zip. Jsou zde také dva <xref:System.Windows.Controls.Button> ovládací prvky, **OK** a **zrušit**  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Obsah je implementována ve `WPFPage` třídy. Rozložení je zpracována s <xref:System.Windows.Controls.Grid> element rozložení. Třídy dědí z <xref:System.Windows.Controls.Grid>, takže efektivní [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu kořenový element.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Obsahu konstruktor přijímá požadované šířku a výšku a velikosti <xref:System.Windows.Controls.Grid> odpovídajícím způsobem. Pak definuje základní rozložení tak, že vytvoříte sadu <xref:System.Windows.Controls.ColumnDefinition> a <xref:System.Windows.Controls.RowDefinition> objekty a jejich přidání <xref:System.Windows.Controls.Grid> základní objekt <xref:System.Windows.Controls.Grid.ColumnDefinitions%2A> a <xref:System.Windows.Controls.Grid.RowDefinitions%2A> kolekcí, v uvedeném pořadí. Definuje mřížku pět řádků a sloupců sedm s dimenzemi dáno obsah buněk.  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageCtorToGridDef](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortogriddef)]  
  
 V dalším kroku konstruktoru přidá [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elementů <xref:System.Windows.Controls.Grid>. První prvek je text nadpisu, který je <xref:System.Windows.Controls.Label> ovládací prvek, který je umístěn na střed v prvním řádku mřížky.  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageCtorTitle](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectortitle)]  
  
 Na další řádek obsahuje název <xref:System.Windows.Controls.Label> ovládací prvek a jeho přidružených <xref:System.Windows.Controls.TextBox> ovládacího prvku. Protože má stejný kód se používá pro každý pár popisek nebo textové pole, je umístěn v pár soukromých metod a použít pro všechny pět párů popisek nebo textové pole. Vytvořit odpovídající metody řízení a volání <xref:System.Windows.Controls.Grid> statická třída <xref:System.Windows.Controls.Grid.SetColumn%2A> a <xref:System.Windows.Controls.Grid.SetRow%2A> metody umístění ovládacích prvků do příslušné buňky. Po vytvoření ovládacího prvku ukázka volá <xref:System.Windows.Controls.UIElementCollection.Add%2A> metodu <xref:System.Windows.Controls.Panel.Children%2A> vlastnost <xref:System.Windows.Controls.Grid> přidání ovládacího prvku do mřížky. Je podobný kódu k přidání zbývající páry popisek nebo textové pole. Najdete ukázkový kód podrobnosti.  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageCtorName](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorname)]  
  
 Implementace tyto dvě metody vypadá takto:  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageCreateHelpers](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagecreatehelpers)]  
  
 Nakonec ukázka přidá **OK** a **zrušit** tlačítka a připojí obslužné rutiny události pro jejich <xref:System.Windows.Controls.Primitives.ButtonBase.Click> události.  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageCtorButtonsEvents](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagectorbuttonsevents)]  
  
<a name="returning_data_to_window"></a>   
### <a name="returning-the-data-to-the-host-window"></a>Vrací Data do okna hostitele  
 Při kliknutí na tlačítko buď jeho <xref:System.Windows.Controls.Primitives.ButtonBase.Click> událost se vyvolá. Okno hostitele může jednoduše připojit obslužné rutiny na tyto události a získat data přímo z <xref:System.Windows.Controls.TextBox> ovládací prvky. Ukázka používá méně přímý přístup. Zpracovává <xref:System.Windows.Controls.Primitives.ButtonBase.Click> v rámci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu a potom vydá vlastní události `OnButtonClicked`, upozornit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah. To umožňuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu udělat některé ověření parametru než oznámí hostitele. Obslužná rutina načte text z <xref:System.Windows.Controls.TextBox> ovládací prvky a přiřadí ji k veřejné vlastnosti, ze kterých můžete načíst hostitele informace.  
  
 Deklarace událostí v WPFPage.h:  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageEventDecl](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpageeventdecl)]  
  
 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> Obslužné rutiny událostí v WPFPage.cpp:  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageButtonClicked](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagebuttonclicked)]  
  
<a name="set_page_properties"></a>   
### <a name="setting-the-wpf-properties"></a>Nastavení vlastností WPF  
 [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] Hostitele umožňuje uživatelům změnit několik [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu vlastnosti. Z [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] straně je pouze záležitost změna vlastností. Implementace ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu třída je trochu složitější, protože není žádná jednoho globální vlastnost písma pro všechny ovládací prvky pro ovládací prvky. Místo toho odpovídající vlastnost pro každý ovládací prvek se změní v průvodcem sady vlastností. Následující příklad ukazuje kód pro `DefaultFontFamily` vlastnost. Nastavení vlastnosti volá soukromá metoda který naopak nastaví <xref:System.Windows.Controls.Control.FontFamily%2A> vlastnosti pro různé ovládací prvky.  
  
 Z WPFPage.h:  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageFontFamilyProperty](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.h#wpfpagefontfamilyproperty)]  
  
 Z WPFPage.cpp:  
  
 [!code-cpp[Win32HostingWPFPage#WPFPageSetFontFamily](../../../../samples/snippets/cpp/VS_Snippets_Wpf/Win32HostingWPFPage/CPP/WPFPage.cpp#wpfpagesetfontfamily)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Interop.HwndSource>  
 [Vzájemná spolupráce grafického subsystému WPF a systému Win32](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)
