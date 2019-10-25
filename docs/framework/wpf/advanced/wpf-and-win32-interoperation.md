---
title: Vzájemná spolupráce grafického subsystému WPF a systému Win32
ms.date: 03/30/2017
helpviewer_keywords:
- hosting WPF content in Win32 window [WPF]
- HWND interop [WPF]
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 0ffbde0d-701d-45a3-a6fa-dd71f4d9772e
ms.openlocfilehash: 7248b0e5abcf2c6357dc7ce7c708eaa85358061a
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846798"
---
# <a name="wpf-and-win32-interoperation"></a>Vzájemná spolupráce grafického subsystému WPF a systému Win32

Toto téma poskytuje přehled o tom, jak pracovat s kódem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje bohatou prostředí pro vytváření aplikací. Nicméně pokud máte významnou investici do [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] kódu, může být efektivnější použít některý z těchto kódů.

<a name="basics"></a>

## <a name="wpf-and-win32-interoperation-basics"></a>Základní informace o meziprovozu WPF a Win32

Existují dvě základní techniky pro spolupráci mezi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a kódem [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].

- Hostování obsahu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v okně [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]. Pomocí této techniky můžete použít pokročilé grafické funkce [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v rámci rozhraní Standard [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ho okna a aplikace.

- Hostování okna [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] v obsahu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Pomocí této techniky můžete použít stávající vlastní ovládací prvek [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] v kontextu jiného obsahu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a předávat data napříč hranicemi.

Každý z těchto postupů je koncepčně představený v tomto tématu. Další ilustraci hostování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]naleznete v tématu [Návod: Hostování obsahu WPF v systému Win32](walkthrough-hosting-wpf-content-in-win32.md). Další ilustraci hostování [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]naleznete v tématu [Návod: hostování ovládacího prvku Win32 v subsystému WPF](walkthrough-hosting-a-win32-control-in-wpf.md).

<a name="projects"></a>

## <a name="wpf-interoperation-projects"></a>Projekty spolupráce WPF

Rozhraní [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API jsou spravovaného kódu, ale většina stávajících [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ch programů je C++zapsána v nespravovaném jazyce.  Rozhraní API pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nemůžete volat z skutečného nespravovaného programu. Nicméně pomocí možnosti `/clr` s kompilátorem Microsoft Visual C++ Compiler můžete vytvořit smíšený spravovaný a nespravovaný program, kde můžete hladce kombinovat spravovaná a Nespravovaná volání rozhraní API.

Jedna komplikace na úrovni projektu je, že nemůžete kompilovat [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] soubory C++ do projektu.  K dispozici je několik technik dělení projektu.

- Vytvořte C# knihovnu DLL, která obsahuje všechny vaše [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]stránky jako zkompilované sestavení a pak svůj C++ spustitelný soubor zahrne tuto knihovnu DLL jako referenci.

- Vytvořte C# spustitelný soubor pro[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]obsah a přikažte na něj C++ knihovnu DLL, která obsahuje obsah[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].

- Použijte <xref:System.Windows.Markup.XamlReader.Load%2A> k načtení [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] v době běhu, namísto kompilování [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].

- Nepoužívejte [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] vůbec a zapište všechny [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v kódu a sestavte strom elementů z <xref:System.Windows.Application>.

Použijte libovolný přístup, který vám vyhovuje.

> [!NOTE]
> Pokud jste ještě nepoužili C++/CLI, můžete si všimnout některých klíčových slov "New", jako jsou například`gcnew`a`nullptr`v příkladech kódu mezioperace. Tato klíčová slova nahrazují starší syntaxi s dvojitým podtržítkem (`__gc`) a poskytují přirozenější syntaxi pro spravovaný kód C++v.  Další informace o spravovaných C++funkcích/CLI najdete v tématu [rozšíření komponent pro platformy běhového prostředí](/cpp/windows/component-extensions-for-runtime-platforms).

<a name="hwnds"></a>

## <a name="how-wpf-uses-hwnds"></a>Jak WPF používá HWND

Aby bylo možné [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] "HWND Interop", potřebujete pochopit, jak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá HWND. Pro libovolný HWND nemůžete kombinovat vykreslování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] s vykreslováním pomocí rozhraní DirectX nebo vykreslováním GDI/GDI+. To má řadu dopadů. Primárně, aby bylo možné tyto vykreslovací modely vzájemně kombinovat, musíte vytvořit řešení vzájemného provozu a použít určené segmenty vzájemného provozu pro každý model vykreslování, který se rozhodnete použít. Také chování vykreslování vytvoří omezení vzdušného prostoru pro to, co vaše řešení pro vzájemnou práci může dosáhnout. Koncept "vzdušného prostoru" je podrobněji vysvětlen v tématu [Přehled technologických oblastí](technology-regions-overview.md).

Všechny [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prvky na obrazovce jsou nakonec zazálohovány HWND. Když vytvoříte <xref:System.Windows.Window>[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vytvoří HWND nejvyšší úrovně a použije <xref:System.Windows.Interop.HwndSource> k vložení <xref:System.Windows.Window> a jeho [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ho obsahu do HWND.  Zbytek obsahu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ve sdílených složkách aplikace v jednotném HWND. Výjimkou jsou nabídky, rozevírací seznamy pole se seznamem a další automaticky otevíraná okna. Tyto prvky vytvoří vlastní okno nejvyšší úrovně, což je důvod, proč by nabídka [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mohla jít po okraji HWND okna, který ho obsahuje. Když použijete <xref:System.Windows.Interop.HwndHost> k umístění prvku HWND do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] informují [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], jak umístit nový podřízený HWND relativní ke [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window> HWND.

Související koncept pro HWND je transparentnost uvnitř a mezi jednotlivými HWND. To je také popsáno v tématu [Přehled technologických oblastí](technology-regions-overview.md).

<a name="hosting_a_wpf_page"></a>

## <a name="hosting-wpf-content-in-a-microsoft-win32-window"></a>Hostování obsahu WPF v okně Microsoft Win32

Klíč pro hostování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v okně [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] je třída <xref:System.Windows.Interop.HwndSource>. Tato třída zalomí obsah [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v okně [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], aby mohl být obsah [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] začleněn do [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] jako podřízené okno. Následující postup kombinuje [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v jediné aplikaci.

1. Implementujte svůj obsah [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (kořenový element obsahu) jako spravovanou třídu. Třída obvykle dědí z jedné třídy, která může obsahovat více podřízených prvků nebo slouží jako kořenový prvek, například <xref:System.Windows.Controls.DockPanel> nebo <xref:System.Windows.Controls.Page>. V následujících krocích je tato třída označována jako [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Třída obsahu a instance třídy jsou označovány jako [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objekty obsahu.

2. Implementace aplikace pro Windows pomocí C++/CLI. Pokud začínáte s existující nespravovanou C++ aplikací, můžete ji obvykle povolit pro volání spravovaného kódu změnou nastavení projektu tak, aby zahrnovala příznak kompilátoru`/clr`(plný rozsah toho, co může být nutné pro podporu kompilace`/clr`není popsán v tomto tématu).

3. Nastavte model dělení na vlákna (STA) na jeden podproces. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá tento model vláken.

4. V postupu okna zpracujte oznámení WM_CREATE.

5. V obslužné rutině (nebo funkci, kterou volá obslužná rutina), udělejte toto:

    1. Vytvoří nový objekt <xref:System.Windows.Interop.HwndSource> s nadřazeným oknem s HWND jako jeho parametrem `parent`.

    2. Vytvořte instanci třídy obsahu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

    3. Přiřaďte odkaz na objekt [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu k vlastnosti <xref:System.Windows.Interop.HwndSource.RootVisual%2A> objektu <xref:System.Windows.Interop.HwndSource>.

    4. Vlastnost <xref:System.Windows.Interop.HwndSource> objektů <xref:System.Windows.Interop.HwndSource.Handle%2A> obsahuje popisovač okna (HWND). Chcete-li získat HWND, který můžete použít v nespravované části aplikace, přetypování `Handle.ToPointer()` na HWND.

6. Implementujte spravovanou třídu obsahující statické pole, které obsahuje odkaz na objekt obsahu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Tato třída umožňuje získat odkaz na objekt [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu z vašeho [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kódu, ale důležitější je, že se <xref:System.Windows.Interop.HwndSource> neúmyslně shromáždí do paměti.

7. Příjem oznámení z objektu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu připojením obslužné rutiny k jedné nebo více událostem objektu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu.

8. Komunikujte s objektem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu pomocí odkazu, který jste uložili do statického pole pro nastavení vlastností, metod volání atd.

> [!NOTE]
> V případě, že vytvoříte samostatné sestavení a následně na něj odkazujete, můžete použít některou z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] definice třídy obsahu pro krok One v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] použití výchozí částečné třídy třídy obsahu. I když obvykle zahrnete <xref:System.Windows.Application> objekt jako součást kompilace [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] do sestavení, neukončíte ho pomocí tohoto <xref:System.Windows.Application> jako součást spolupráce, stačí použít jednu nebo více kořenových tříd pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubory, na které odkazuje aplikace. a odkazují na jejich dílčí třídy. Zbytek postupu je v podstatě podobný jako uvedený výše.
>
> Každý z těchto kroků je znázorněn prostřednictvím kódu v tématu [Návod: Hostování obsahu WPF v systému Win32](walkthrough-hosting-wpf-content-in-win32.md).

<a name="hosting_an_hwnd"></a>

## <a name="hosting-a-microsoft-win32-window-in-wpf"></a>Hostování okna Microsoft Win32 v subsystému WPF

Klíč pro hostování [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ho okna v rámci jiného obsahu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je třída <xref:System.Windows.Interop.HwndHost>. Tato třída zalomí okno do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ho prvku, který lze přidat do stromu elementu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. <xref:System.Windows.Interop.HwndHost> podporuje také rozhraní API, která umožňují provádět takové úkoly jako zprávy procesu pro hostované okno. Základní postup je následující:

1. Vytvořte strom elementu pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikaci (může být prostřednictvím kódu nebo kódu). Ve stromové struktuře elementu Najděte příslušný a přípustný bod, kde <xref:System.Windows.Interop.HwndHost> implementaci lze přidat jako podřízený element. Ve zbývající části tohoto postupu je tento element označován jako reobsluhující element.

2. Odvodit z <xref:System.Windows.Interop.HwndHost> k vytvoření objektu, který obsahuje obsah [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].

3. V této třídě hostitele přepište <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>metody <xref:System.Windows.Interop.HwndHost>. Vrátí HWND hostovaného okna. Můžete chtít zabalit vlastní ovládací prvky jako podřízené okno vráceného okna. zabalení ovládacích prvků v hostitelském okně poskytuje jednoduchý způsob, jak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah přijímat oznámení z ovládacích prvků. Tento postup pomáhá opravovat některé [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] problémy týkající se zpracování zpráv na hranici hostovaného ovládacího prvku.

4. Přepište metody <xref:System.Windows.Interop.HwndHost> <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> a <xref:System.Windows.Interop.HwndHost.WndProc%2A>. Cílem je, aby bylo možné zpracovat vyčištění a odebrat odkazy na hostovaný obsah, zejména pokud jste vytvořili odkazy na nespravované objekty.

5. V souboru kódu na pozadí vytvořte instanci třídy hostování ovládacího prvku a nastavte ji jako podřízenou pro rezervaci elementu. Obvykle byste použili obslužnou rutinu události, jako je například <xref:System.Windows.FrameworkElement.Loaded>, nebo použít konstruktor částečné třídy. Obsah mezioperace ale můžete také přidat pomocí chování za běhu.

6. Zpracuje vybrané zprávy okna, například oznámení o řízení. Existují dva přístupy. Oba poskytují stejný přístup ke streamu zpráv, takže výběr je převážně věcí pro programování.

    - Implementujte zpracování zpráv pro všechny zprávy (nikoli jenom zprávy pro vypnutí) ve vašem přepsání <xref:System.Windows.Interop.HwndHost.WndProc%2A>metody <xref:System.Windows.Interop.HwndHost>.

    - Musí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hostování elementu zpracovávat zprávy zpracováním události <xref:System.Windows.Interop.HwndHost.MessageHook>. Tato událost je vyvolána pro každou zprávu, která je odeslána do hlavního okna procedury hostovaného okna.

    - Nemůžete zpracovávat zprávy ze systému Windows, které se nezpracovávají pomocí <xref:System.Windows.Interop.HwndHost.WndProc%2A>.

7. Komunikujte s hostovaným oknem pomocí vyvolání platformy pro volání nespravované funkce `SendMessage`.

Pomocí těchto kroků vytvoříte aplikaci, která funguje se vstupem myši. Můžete přidat podporu tabulátoru pro hostované okno implementací rozhraní <xref:System.Windows.Interop.IKeyboardInputSink>.

Každý z těchto kroků je znázorněn prostřednictvím kódu v tématu [Návod: hostování ovládacího prvku Win32 v subsystému WPF](walkthrough-hosting-a-win32-control-in-wpf.md).

### <a name="hwnds-inside-wpf"></a>HWND v rámci WPF

<xref:System.Windows.Interop.HwndHost> můžete představit jako speciální ovládací prvek. (Technicky, <xref:System.Windows.Interop.HwndHost> je <xref:System.Windows.FrameworkElement> odvozená třída, ne <xref:System.Windows.Controls.Control> odvozená třída, ale může být považována za ovládací prvek pro účely meziprovozu.) <xref:System.Windows.Interop.HwndHost> vyabstrakce základní [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] charakter hostovaného obsahu tak, aby zbytek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] považovat hostovaný obsah za jiný objekt podobný ovládacímu prvku, který by měl vykreslovat a zpracovat vstup. <xref:System.Windows.Interop.HwndHost> se obecně chová jako jiné <xref:System.Windows.FrameworkElement>[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], i když jsou důležité rozdíly ve výstupu (kreslení a grafika) a vstup (myš a klávesnice) na základě omezení, co mohou základní HWND podporovat.

#### <a name="notable-differences-in-output-behavior"></a>Významné rozdíly v chování výstupu

- <xref:System.Windows.FrameworkElement>, která je základní třídou <xref:System.Windows.Interop.HwndHost>, má poměrně několik vlastností, které implikují změny uživatelského rozhraní. Mezi tyto vlastnosti patří například <xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=nameWithType>, které mění rozložení prvků v rámci daného prvku jako nadřazené. Většina těchto vlastností ale není namapovaná na možné [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ekvivalenty, a to i v případě, že tyto ekvivalenty existují. Příliš mnoho těchto vlastností a jejich význam jsou příliš vykreslení – specifické pro technologii pro mapování, aby byly praktické. Proto nastavení vlastností, například <xref:System.Windows.FrameworkElement.FlowDirection%2A> v <xref:System.Windows.Interop.HwndHost> nemá žádný vliv.

- <xref:System.Windows.Interop.HwndHost> nelze otočit, škálovat, zkosit nebo jinak ovlivněné transformací.

- <xref:System.Windows.Interop.HwndHost> nepodporuje vlastnost <xref:System.Windows.UIElement.Opacity%2A> (alfa míchání). Pokud obsah uvnitř <xref:System.Windows.Interop.HwndHost> provádí <xref:System.Drawing> operace, které zahrnují informace o alfa, což není porušení, ale <xref:System.Windows.Interop.HwndHost> jako celek podporuje pouze krytí = 1,0 (100%).

- <xref:System.Windows.Interop.HwndHost> se zobrazí nad ostatními prvky [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v jednom okně nejvyšší úrovně. Nabídka <xref:System.Windows.Controls.ToolTip> nebo <xref:System.Windows.Controls.ContextMenu> vygenerovala jako samostatné okno nejvyšší úrovně, takže se v <xref:System.Windows.Interop.HwndHost>správně chová.

- <xref:System.Windows.Interop.HwndHost> nerespektuje oblast oříznutí svého nadřazeného <xref:System.Windows.UIElement>. To může být problém, pokud se pokusíte vložit třídu <xref:System.Windows.Interop.HwndHost> do oblasti pro posouvání nebo <xref:System.Windows.Controls.Canvas>.

#### <a name="notable-differences-in-input-behavior"></a>Významné rozdíly v chování vstupu

- Obecně platí, že když jsou vstupní zařízení vymezená v <xref:System.Windows.Interop.HwndHost> hostované [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] oblasti, vstupní události se přejdou přímo na [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].

- Když je ukazatel myši nad <xref:System.Windows.Interop.HwndHost>, aplikace nepřijímá [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] události myši a hodnota vlastnosti [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.IsMouseOver%2A> bude `false`.

- I když má <xref:System.Windows.Interop.HwndHost> fokus klávesnice, aplikace nebude přijímat události [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klávesnice a hodnota vlastnosti [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> bude `false`.

- Pokud je fokus v rámci <xref:System.Windows.Interop.HwndHost> a změny jiného ovládacího prvku v rámci <xref:System.Windows.Interop.HwndHost>, aplikace nebude přijímat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]é události <xref:System.Windows.UIElement.GotFocus> nebo <xref:System.Windows.UIElement.LostFocus>.

- Související vlastnosti a události stylusu jsou analogické a neoznamují informace, když je Stylus nad <xref:System.Windows.Interop.HwndHost>.

<a name="tabbing_mnemonics_accelerators"></a>

## <a name="tabbing-mnemonics-and-accelerators"></a>Tabulátory, klávesové zkratky a akcelerátory

Rozhraní <xref:System.Windows.Interop.IKeyboardInputSink> a <xref:System.Windows.Interop.IKeyboardInputSite> umožňují vytvořit bezproblémové prostředí klávesnice pro smíšené [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikace:

- Procházení tabulátorů mezi [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] komponentami

- Klávesové zkratky a akcelerátory, které fungují v případě, že se fokus nachází v rámci součásti systému Win32 a je v rámci komponenty WPF.

Třídy <xref:System.Windows.Interop.HwndHost> a <xref:System.Windows.Interop.HwndSource> poskytují implementace <xref:System.Windows.Interop.IKeyboardInputSink>, ale nemusí zpracovávat všechny vstupní zprávy, které chcete mít v pokročilejších scénářích. Přepište vhodné metody, abyste získali chování klávesnice, které chcete.

Rozhraní poskytují podporu pouze pro to, co se stane s přechodem mezi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] oblasti. V rámci [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] oblasti je chování s kartami zcela řízeno [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] implementací logiky pro procházení tabulátory, pokud existují.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Interop.HwndHost>
- <xref:System.Windows.Interop.HwndSource>
- <xref:System.Windows.Interop>
- [Návod: Hostování ovládacího prvku Win32 v subsystému WPF](walkthrough-hosting-a-win32-control-in-wpf.md)
- [Návod: Hostování obsahu WPF v systému Win32](walkthrough-hosting-wpf-content-in-win32.md)
