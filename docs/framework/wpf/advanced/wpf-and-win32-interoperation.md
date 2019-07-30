---
title: Vzájemná spolupráce grafického subsystému WPF a systému Win32
ms.date: 03/30/2017
helpviewer_keywords:
- hosting WPF content in Win32 window [WPF]
- HWND interop [WPF]
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 0ffbde0d-701d-45a3-a6fa-dd71f4d9772e
ms.openlocfilehash: 860e8f11859bfbd85d6a5f0e4420fda3047bb236
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629830"
---
# <a name="wpf-and-win32-interoperation"></a>Vzájemná spolupráce grafického subsystému WPF a systému Win32
Toto téma poskytuje přehled o tom, jak pracovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] s kódem. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]poskytuje bohatý prostředí pro vytváření aplikací. Nicméně pokud máte významnou investici do [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] kódu, může být efektivnější použít některý z těchto kódů.  

<a name="basics"></a>   
## <a name="wpf-and-win32-interoperation-basics"></a>Základní informace o meziprovozu WPF a Win32  
 Existují dva základní techniky pro vzájemné [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] provozování a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kódování.  
  
- Obsah [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hostitele[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] v okně. Pomocí této techniky můžete využít pokročilé možnosti [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] grafiky v rámci rozhraní standardního [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna a aplikace.  
  
- Hostování okna v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]obsahu. [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] Pomocí této techniky můžete použít stávající vlastní [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ovládací prvek v kontextu jiného [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu a předávat data přes hranice.  
  
 Každý z těchto postupů je koncepčně představený v tomto tématu. Další ilustraci hostování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]nástroji naleznete v tématu [Návod: Hostování obsahu WPF v systému](walkthrough-hosting-wpf-content-in-win32.md)Win32. Další ilustraci hostování [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]nástroji naleznete v tématu [Návod: Hostování ovládacího prvku Win32 v subsystému WPF](walkthrough-hosting-a-win32-control-in-wpf.md).  
  
<a name="projects"></a>   
## <a name="wpf-interoperation-projects"></a>Projekty spolupráce WPF  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Rozhraní API jsou spravovaného kódu, ale [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] většina existujících programů je zapsána v nespravovaném C++jazyce.  Nemůžete [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] volat rozhraní API z skutečného nespravovaného programu. Nicméně pomocí [!INCLUDE[TLA#tla_visualcpp](../../../../includes/tlasharptla-visualcpp-md.md)] možnosti s kompilátorem můžete vytvořit smíšený spravovaný a nespravovaný program, kde můžete hladce kombinovat spravovaná a Nespravovaná volání rozhraní API. `/clr`  
  
 Jedna komplikace na úrovni projektu je taková, že nemůžete [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kompilovat C++ soubory do projektu.  K dispozici je několik technik dělení projektu.  
  
- Vytvořte C# knihovnu DLL, která obsahuje všechny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] vaše stránky, jako zkompilované sestavení a pak svůj C++ spustitelný soubor zahrne tuto knihovnu DLL jako referenci.  
  
- Vytvořte C# spustitelný soubor pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah a pokažte na C++ něj knihovnu DLL, která obsahuje [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] obsah.  
  
- Použijte <xref:System.Windows.Markup.XamlReader.Load%2A> k [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]načtení v době běhu, namísto kompilování. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
- Nepoužívejte [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] vůbec a zapište všechny své [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v kódu a sestavte strom elementů z <xref:System.Windows.Application>.  
  
 Použijte libovolný přístup, který vám vyhovuje.  
  
> [!NOTE]
>  Pokud jste ještě nepoužili C++/CLI, můžete si všimnout některých klíčových slov `gcnew` "New", jako jsou například a `nullptr` v příkladech kódu mezioperace. Tato klíčová slova nahrazují starší syntaxi s dvojitým podtržítkem (`__gc`) a poskytují přirozenější syntaxi pro spravovaný kód v. C++  Další informace o spravovaných C++funkcích/CLI najdete v tématu [rozšíření komponent pro běhové platformy](/cpp/windows/component-extensions-for-runtime-platforms) a [Hello C++,/CLI](https://go.microsoft.com/fwlink/?LinkId=98739).  
  
<a name="hwnds"></a>   
## <a name="how-wpf-uses-hwnds"></a>Jak WPF používá HWND  
 Pro zajištění většiny [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] "interoperability s funkcí HWND" potřebujete pochopit, jak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá HWND. Pro libovolný HWND nelze [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kombinovat vykreslování s vykreslováním nebo [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)]  /  [!INCLUDE[TLA2#tla_gdiplus](../../../../includes/tla2sharptla-gdiplus-md.md)] vykreslováním rozhraní DirectX. To má řadu dopadů. Primárně, aby bylo možné tyto vykreslovací modely vzájemně kombinovat, musíte vytvořit řešení vzájemného provozu a použít určené segmenty vzájemného provozu pro každý model vykreslování, který se rozhodnete použít. Také chování vykreslování vytvoří omezení vzdušného prostoru pro to, co vaše řešení pro vzájemnou práci může dosáhnout. Koncept "vzdušného prostoru" je podrobněji vysvětlen v tématu [Přehled technologických oblastí](technology-regions-overview.md).  
  
 Všechny [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementy na obrazovce jsou nakonec zazálohovány HWND. Při [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vytváření <xref:System.Windows.Window> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vytvoří nástroj NástrojHWND<xref:System.Windows.Interop.HwndSource> nejvyšší úrovně a použije objekt k vložení a jeho obsahu do HWND. <xref:System.Windows.Window> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]  Zbytek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu ve sdílených složkách aplikace v jednotném HWND. Výjimkou jsou nabídky, rozevírací seznamy pole se seznamem a další automaticky otevíraná okna. Tyto prvky vytvoří vlastní okno nejvyšší úrovně, což je důvod, proč [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] by nabídka mohla jít po okraji HWND okna, který ho obsahuje. Když použijete <xref:System.Windows.Interop.HwndHost> k vložení HWND dovnitř [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] informuje [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] o tom, jak umístit nový podřízený HWND relativní k [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window> HWND.  
  
 Související koncept pro HWND je transparentnost uvnitř a mezi jednotlivými HWND. To je také popsáno v tématu [Přehled technologických oblastí](technology-regions-overview.md).  
  
<a name="hosting_a_wpf_page"></a>   
## <a name="hosting-wpf-content-in-a-microsoft-win32-window"></a>Hostování obsahu WPF v okně Microsoft Win32  
 Klíč pro hostování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] v okně je <xref:System.Windows.Interop.HwndSource> třída. Tato třída zalomí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] okně, aby bylo možné obsah vložit do svého [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] podřízeného okna. Následující postup kombinuje [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v jediné aplikaci.  
  
1. Implementujte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] svůj obsah (kořenový element obsahu) jako spravovanou třídu. Třída obvykle dědí z jedné třídy, která může obsahovat více podřízených elementů nebo slouží jako kořenový prvek, například <xref:System.Windows.Controls.DockPanel> nebo. <xref:System.Windows.Controls.Page> V následujících krocích je tato třída označována jako [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Třída obsahu a instance třídy jsou označovány jako [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objekty obsahu.  
  
2. Implementace aplikace pro Windows pomocí C++/CLI. Pokud začínáte s existující nespravovanou C++ aplikací, můžete ji obvykle povolit pro volání spravovaného kódu změnou nastavení projektu tak, aby zahrnovala `/clr` příznak kompilátoru (plný rozsah toho, co může být nutné pro podporu `/clr` kompilace není popsána v tomto tématu).  
  
3. Nastavte model dělení na vlákna (STA) na jeden podproces. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]používá tento model vláken.  
  
4. V postupu okna zpracujte oznámení WM_CREATE.  
  
5. V obslužné rutině (nebo funkci, kterou volá obslužná rutina), udělejte toto:  
  
    1. Vytvoří nový <xref:System.Windows.Interop.HwndSource> objekt s nadřazeným oknem HWND jako jeho `parent` parametr.  
  
    2. Vytvořte instanci vaší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] třídy obsahu.  
  
    3. Přiřaďte odkaz na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objekt Content <xref:System.Windows.Interop.HwndSource> k vlastnosti objektu <xref:System.Windows.Interop.HwndSource.RootVisual%2A> .  
  
    4. Vlastnost <xref:System.Windows.Interop.HwndSource> Object<xref:System.Windows.Interop.HwndSource.Handle%2A> obsahuje popisovač okna (HWND). Chcete-li získat HWND, který můžete použít v nespravované části aplikace, přetypování `Handle.ToPointer()` na HWND.  
  
6. Implementujte spravovanou třídu obsahující statické pole, které obsahuje odkaz na váš [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objekt Content. Tato třída umožňuje získat odkaz na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objekt obsahu z vašeho [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kódu, ale důležitější je, že brání <xref:System.Windows.Interop.HwndSource> neúmyslnému uvolňování paměti.  
  
7. Příjem oznámení z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objektu obsahu připojením obslužné rutiny k jedné nebo více [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] událostem objektu obsahu.  
  
8. Komunikujte s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objektem Content pomocí odkazu, který jste uložili do statického pole pro nastavení vlastností, metod volání atd.  
  
> [!NOTE]
>  Můžete provést některé nebo všechny [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] definice třídy obsahu pro krok 1 v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] použití výchozí částečné třídy třídy obsahu, pokud vytváříte samostatné sestavení a pak na něj odkazuje. I když obvykle zahrnete <xref:System.Windows.Application> objekt jako součást [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] kompilace do sestavení, neukončíte ho jako součást spolupráce, stačí použít <xref:System.Windows.Application> jednu nebo více kořenových tříd pro soubory, na [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] které odkazuje. do aplikace a odkazují na jejich dílčí třídy. Zbytek postupu je v podstatě podobný jako uvedený výše.  
>   
>  Každý z těchto kroků je znázorněn prostřednictvím kódu v tématu [Návod: Hostování obsahu WPF v systému](walkthrough-hosting-wpf-content-in-win32.md)Win32.  
  
<a name="hosting_an_hwnd"></a>   
## <a name="hosting-a-microsoft-win32-window-in-wpf"></a>Hostování okna Microsoft Win32 v subsystému WPF  
 Klíč pro hostování [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna v rámci jiného [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu je <xref:System.Windows.Interop.HwndHost> třída. Tato třída zalomí okno do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prvku, který lze přidat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do stromu elementu. <xref:System.Windows.Interop.HwndHost>podporuje také rozhraní API, která umožňují provádět takové úkoly jako zprávy procesu pro hostované okno. Základní postup je následující:  
  
1. Vytvoří strom elementu pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikaci (může být prostřednictvím kódu nebo kódu). Ve stromové struktuře elementu Najděte příslušný a přípustný bod, kde <xref:System.Windows.Interop.HwndHost> lze implementovat implementaci jako podřízený element. Ve zbývající části tohoto postupu je tento element označován jako reobsluhující element.  
  
2. Odvodit <xref:System.Windows.Interop.HwndHost> z k vytvoření objektu, který obsahuje [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] váš obsah.  
  
3. V této třídě hostitele přepište <xref:System.Windows.Interop.HwndHost> metodu. <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A> Vrátí HWND hostovaného okna. Můžete chtít zabalit vlastní ovládací prvky jako podřízené okno vráceného okna. zabalení ovládacích prvků v hostitelském okně poskytuje jednoduché zobrazení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu pro příjem oznámení z ovládacích prvků. Tento postup pomáhá opravit některé [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] problémy týkající se zpracování zpráv na hranici hostovaného ovládacího prvku.  
  
4. <xref:System.Windows.Interop.HwndHost> Přepsat metody <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> a. <xref:System.Windows.Interop.HwndHost.WndProc%2A> Cílem je, aby bylo možné zpracovat vyčištění a odebrat odkazy na hostovaný obsah, zejména pokud jste vytvořili odkazy na nespravované objekty.  
  
5. V souboru kódu na pozadí vytvořte instanci třídy hostování ovládacího prvku a nastavte ji jako podřízenou pro rezervaci elementu. Obvykle byste použili obslužnou rutinu <xref:System.Windows.FrameworkElement.Loaded>události, jako je, nebo použijte konstruktor částečné třídy. Obsah mezioperace ale můžete také přidat pomocí chování za běhu.  
  
6. Zpracuje vybrané zprávy okna, například oznámení o řízení. Existují dva přístupy. Oba poskytují stejný přístup ke streamu zpráv, takže výběr je převážně věcí pro programování.  
  
    - Implementujte zpracování zpráv pro všechny zprávy (nikoli jenom zprávy o vypnutí) v přepsání <xref:System.Windows.Interop.HwndHost> metody. <xref:System.Windows.Interop.HwndHost.WndProc%2A>  
  
    - Má hostující [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prvek zpracovat zprávy <xref:System.Windows.Interop.HwndHost.MessageHook> zpracováním události. Tato událost je vyvolána pro každou zprávu, která je odeslána do hlavního okna procedury hostovaného okna.  
  
    - Nemůžete zpracovat zprávy ze systému Windows, které se nezpracovávají pomocí <xref:System.Windows.Interop.HwndHost.WndProc%2A>.  
  
7. Komunikujte s hostovaným oknem pomocí vyvolání platformy pro volání nespravované `SendMessage` funkce.  
  
 Pomocí těchto kroků vytvoříte aplikaci, která funguje se vstupem myši. Můžete přidat podporu tabulátoru pro hostované okno implementací <xref:System.Windows.Interop.IKeyboardInputSink> rozhraní.  
  
 Každý z těchto kroků je znázorněn prostřednictvím kódu v tématu [Návod: Hostování ovládacího prvku Win32 v subsystému WPF](walkthrough-hosting-a-win32-control-in-wpf.md).  
  
### <a name="hwnds-inside-wpf"></a>HWND v rámci WPF  
 Můžete si představit <xref:System.Windows.Interop.HwndHost> jako speciální ovládací prvek. (Technicky, <xref:System.Windows.Interop.HwndHost> <xref:System.Windows.FrameworkElement> je<xref:System.Windows.Controls.Control> odvozenou třídou, nikoli odvozenou třídou, ale může být považována za ovládací prvek pro účely meziprovozu.) vyhodnotí základní [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] charakter hostovaného obsahu tak, že zbytek vychází [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] z předpokladu, že hostovaný obsah bude jiný objekt podobný ovládacímu prvku, který by měl vykreslovat a zpracovat vstup. <xref:System.Windows.Interop.HwndHost> <xref:System.Windows.Interop.HwndHost>Obecně se chová jako jiné [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement>, i když jsou důležité rozdíly ve výstupu (kreslení a grafika) a vstup (myš a klávesnice) na základě omezení, co mohou základní HWND podporovat.  
  
#### <a name="notable-differences-in-output-behavior"></a>Významné rozdíly v chování výstupu  
  
- <xref:System.Windows.FrameworkElement>, což je <xref:System.Windows.Interop.HwndHost> základní třída, má poměrně několik vlastností, které implikují změny uživatelského rozhraní. Mezi ně patří vlastnosti <xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=nameWithType>, které mění rozložení prvků v rámci daného prvku jako nadřazené. Většina těchto vlastností ale není namapovaná na možné [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ekvivalenty, a to i v případě, že tyto ekvivalenty existují. Příliš mnoho těchto vlastností a jejich význam jsou příliš vykreslení – specifické pro technologii pro mapování, aby byly praktické. Proto nastavení vlastností, <xref:System.Windows.FrameworkElement.FlowDirection%2A> <xref:System.Windows.Interop.HwndHost> jako je například, nemá žádný vliv.  
  
- <xref:System.Windows.Interop.HwndHost>nedá se otočit, škálovat, zkosit nebo jinak ovlivněné transformací.  
  
- <xref:System.Windows.Interop.HwndHost><xref:System.Windows.UIElement.Opacity%2A> nepodporuje vlastnost (prolnutí alfa). Pokud obsah uvnitř <xref:System.Windows.Interop.HwndHost> provádí <xref:System.Drawing> operace, které zahrnují informace o alfa, což sám o sobě není porušení, ale <xref:System.Windows.Interop.HwndHost> jako celek podporuje pouze krytí = 1,0 (100%).  
  
- <xref:System.Windows.Interop.HwndHost>zobrazí se nad ostatními [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prvky v jednom okně nejvyšší úrovně. <xref:System.Windows.Controls.ToolTip> Nabídka nebo <xref:System.Windows.Controls.ContextMenu> vygenerovaná nabídka je ale samostatné okno nejvyšší úrovně, které se tak bude chovat správně pomocí <xref:System.Windows.Interop.HwndHost>.  
  
- <xref:System.Windows.Interop.HwndHost>nerespektuje oblast oříznutí svého nadřazeného prvku <xref:System.Windows.UIElement>. To může být problém, pokud se pokusíte vložit <xref:System.Windows.Interop.HwndHost> třídu do oblasti pro posouvání nebo. <xref:System.Windows.Controls.Canvas>  
  
#### <a name="notable-differences-in-input-behavior"></a>Významné rozdíly v chování vstupu  
  
- Obecně platí, že když jsou vstupní zařízení vymezená v <xref:System.Windows.Interop.HwndHost> hostované [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] oblasti, vstupní události se přecházejí [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]přímo na.  
  
- Když je ukazatel myši nad <xref:System.Windows.Interop.HwndHost>, vaše aplikace nepřijímá [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] události myši [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a hodnota vlastnosti <xref:System.Windows.UIElement.IsMouseOver%2A> bude `false`.  
  
- `false` <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] I když máfokusklávesnice,aplikacenebudepřijímatudálostiklávesniceahodnotavlastnostibude.<xref:System.Windows.Interop.HwndHost>  
  
- Pokud je fokus v rámci <xref:System.Windows.Interop.HwndHost> a se změní na jiný ovládací prvek <xref:System.Windows.Interop.HwndHost>uvnitř, vaše [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace nebude přijímat události <xref:System.Windows.UIElement.GotFocus> nebo <xref:System.Windows.UIElement.LostFocus>.  
  
- Související vlastnosti a události stylusu jsou analogické a neoznamují informace, když je Stylus nad <xref:System.Windows.Interop.HwndHost>ním.  
  
<a name="tabbing_mnemonics_accelerators"></a>   
## <a name="tabbing-mnemonics-and-accelerators"></a>Tabulátory, klávesové zkratky a akcelerátory  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] Rozhraní <xref:System.Windows.Interop.IKeyboardInputSink> a <xref:System.Windows.Interop.IKeyboardInputSite> umožňují vytvořit bezproblémové prostředí klávesnice pro smíšené aplikace a aplikace:  
  
- Procházení tabulátorem [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] mezi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] komponentami a  
  
- Klávesové zkratky a akcelerátory, které fungují v případě, že se fokus nachází v rámci součásti systému Win32 a je v rámci komponenty WPF.  
  
 Třídy a poskytují<xref:System.Windows.Interop.HwndSource> implementace ,alenemusízpracovávatvšechnyvstupnízprávy,kteréchcetemítvpokročilejších<xref:System.Windows.Interop.IKeyboardInputSink>scénářích. <xref:System.Windows.Interop.HwndHost> Přepište vhodné metody, abyste získali chování klávesnice, které chcete.  
  
 Rozhraní poskytují podporu pouze pro to, co se stane s přechodem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mezi [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] oblastmi a. V rámci [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] oblasti je chování pomocí tabulátoru zcela řízeno implementovanou logikou pro procházení tabulátorem, pokud existují. [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Interop.HwndHost>
- <xref:System.Windows.Interop.HwndSource>
- <xref:System.Windows.Interop>
- [Návod: Hostování ovládacího prvku Win32 v subsystému WPF](walkthrough-hosting-a-win32-control-in-wpf.md)
- [Návod: Hostování obsahu WPF v systému Win32](walkthrough-hosting-wpf-content-in-win32.md)
