---
title: Vzájemná spolupráce grafického subsystému WPF a systému Win32
ms.date: 03/30/2017
helpviewer_keywords:
- hosting WPF content in Win32 window [WPF]
- HWND interop [WPF]
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 0ffbde0d-701d-45a3-a6fa-dd71f4d9772e
ms.openlocfilehash: 71c454edc6a124f732f1e6b56e25c28671fa11b6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59314409"
---
# <a name="wpf-and-win32-interoperation"></a>Vzájemná spolupráce grafického subsystému WPF a systému Win32
Toto téma obsahuje přehled o tom, jak zajistit vzájemnou funkční spolupráci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kódu. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje bohaté prostředí pro vytváření aplikací. Pokud však máte značné investice [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] kódu, může být efektivnější opakovaně používat některé z kódu.  

<a name="basics"></a>   
## <a name="wpf-and-win32-interoperation-basics"></a>WPF a vzájemné spolupráce základy Win32  
 Existují dva základní postupy pro interoperabilitu mezi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kódu.  
  
-   Hostitel [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna. S touto technikou, můžete použít grafické pokročilé možnosti [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v rámci standardní [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno a aplikace.  
  
-   Hostitel [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah. S touto technikou, můžete použít existující vlastní [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ovládacího prvku v kontextu jiných [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu a předání dat přes hranice.  
  
 Každá z těchto postupů je koncepčně představenými v tomto tématu. Hostování více kódu objektově orientovaný ukázky [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], naleznete v tématu [názorný postup: Hostování obsahu WPF v Win32](walkthrough-hosting-wpf-content-in-win32.md). Hostování více kódu objektově orientovaný ukázky [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], naleznete v tématu [názorný postup: Hostování ovládacího prvku Win32 v subsystému WPF](walkthrough-hosting-a-win32-control-in-wpf.md).  
  
<a name="projects"></a>   
## <a name="wpf-interoperation-projects"></a>Součinnost projekty WPF  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] spravovaný kód, ale většina existující [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programy jsou napsané v nespravované [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)].  Nejde volat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] ze skutečného nespravované aplikace. Nicméně s použitím `/clr` spolu s možností [!INCLUDE[TLA#tla_visualcpp](../../../../includes/tlasharptla-visualcpp-md.md)] kompilátor, můžete vytvořit smíšené spravovaného nespravovaného programu ve kterém můžete bez problémů používat spravované a nespravované [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] volání.  
  
 Jeden komplikací na úrovni projektu je, že nejde zkompilovat [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] soubory do [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)] projektu.  Existuje několik postupů dělení projektu jako kompenzaci za to.  
  
-   Vytvořit knihovnu DLL jazyka C#, která obsahuje všechny vaše [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky jako zkompilovaném sestavení a pak je mít vaše [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)] spustitelný soubor, který patří [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] jako odkaz.  
  
-   Vytvořit C# pro spustitelný soubor [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu a jeho odkazovat [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)] [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] obsahující [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] obsah.  
  
-   Použití <xref:System.Windows.Markup.XamlReader.Load%2A> načíst žádné [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] v době běhu, namísto kompilaci vašeho [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
-   Nepoužívejte [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] vůbec a zapisovat všechny vaše [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v kódu, vytváření nahoru stromem prvků z <xref:System.Windows.Application>.  
  
 Použijte jakýkoli přístup vám nejvíce vyhovuje.  
  
> [!NOTE]
>  Pokud jste ještě nepoužívali [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] dříve, můžete si všimnout některých "nové" klíčová slova, jako `gcnew` a `nullptr` v příkladech kódu vzájemné spolupráce. Tato klíčová slova, mají přednost před starší syntaxe dvojité podtržítko (`__gc`) a poskytují přirozenější syntaxi pro spravovaný kód v [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)].  Další informace o [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] spravované funkce, najdete v článku [přípony komponent pro platformy běhového prostředí](/cpp/windows/component-extensions-for-runtime-platforms) a [Hello, C++vyhodnocovací](https://go.microsoft.com/fwlink/?LinkId=98739).  
  
<a name="hwnds"></a>   
## <a name="how-wpf-uses-hwnds"></a>Použití HWND WPF  
 Chcete-li maximálně využít [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] "Interoperabilita HWND", je potřeba pochopit, jak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá HWND. Pro všechny HWND, nejde kombinovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vykreslování pomocí [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] vykreslování nebo [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)]  /  [!INCLUDE[TLA2#tla_gdiplus](../../../../includes/tla2sharptla-gdiplus-md.md)] vykreslování. To má několik důsledky. Především aby bylo možné kombinovat tyto modely vykreslování vůbec, musíte vytvořit součinnosti řešení a pomocí určené segmentů vzájemná spolupráce grafického subsystému pro každý model vykreslování, který chcete použít. Také chování vykreslování vytvoří "vzdušného prostoru" omezení pro co lze provádět součinnosti řešení. Pojem "vzdušného prostoru" je vysvětleno podrobněji v tématu [přehled technologických oblastí](technology-regions-overview.md).  
  
 Všechny [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jsou prvky na obrazovce opírá HWND. Při vytváření [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window>, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vytvoří nejvyšší úrovně HWND a použije <xref:System.Windows.Interop.HwndSource> umístit <xref:System.Windows.Window> a jeho [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu uvnitř HWND.  Zbývající část vaší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tomto jednotném HWND sdílí obsah v aplikaci. Výjimka je nabídek, pole se seznamem pole rozevírací nabídky a jiné automaticky otevíraná okna. Tyto prvky vytvořit své vlastní okno nejvyšší úrovně, což je důvod, proč [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nabídky potenciálně přejít po okraji okna HWND, který jej obsahuje. Při použití <xref:System.Windows.Interop.HwndHost> umístit popisovačem HWND uvnitř [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] informuje [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] tom, jak umístit nové podřízené HWND relativní vzhledem k [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window> HWND.  
  
 Pojmem k HWND je průhlednosti v rámci a mezi každou HWND. To je také popsáno v tématu [přehled technologických oblastí](technology-regions-overview.md).  
  
<a name="hosting_a_wpf_page"></a>   
## <a name="hosting-wpf-content-in-a-microsoft-win32-window"></a>Hostování obsahu WPF v okně Microsoft Win32  
 Klíčem k hostování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] na [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] je okno <xref:System.Windows.Interop.HwndSource> třídy. Zabalí tuto třídu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu v [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okně tak, aby [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu může být zahrnut do vaší [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] jako podřízeného okna. Tento přístup spojuje [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v jedné aplikaci.  
  
1. Implementovat vaše [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu (obsah kořenový element) jako spravované třídy. Obvykle třída dědí z jedné ze tříd, které může obsahovat více podřízenými prvky a/nebo použít jako kořenový element, jako například <xref:System.Windows.Controls.DockPanel> nebo <xref:System.Windows.Controls.Page>. V dalších krocích, tato třída se označuje jako [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu třídy a instance třídy jsou označovány jako [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah objektů.  
  
2. Implementace [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikace s [!INCLUDE[TLA2#tla_cppcli](../../../../includes/tla2sharptla-cppcli-md.md)]. Pokud začínáte s existujícím nespravované [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)] aplikace, můžete obvykle ji povolit pro volání spravovaného kódu tak, že změníte nastavení projektu zahrnout `/clr` kompilátoru příznak (úplného oboru toho, co může být potřeba podporovat `/clr`kompilace není popsané v tomto tématu).  
  
3. Nastavte model vláken na jeden Threaded Apartment (STA). [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá tento model vláken.  
  
4. Zpracuje WM_CREATE oznámení ve vaší proceduru okna.  
  
5. V rámci obslužné rutiny (nebo funkci, která volá obslužná rutina) postupujte takto:  
  
    1.  Vytvořte nový <xref:System.Windows.Interop.HwndSource> objekt s nadřazené okno HWND jako jeho `parent` parametru.  
  
    2.  Vytvoření instance vaší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu třídy.  
  
    3.  Přiřadit odkaz na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu objektu <xref:System.Windows.Interop.HwndSource> objekt <xref:System.Windows.Interop.HwndSource.RootVisual%2A> vlastnost.  
  
    4.  <xref:System.Windows.Interop.HwndSource> Objekt <xref:System.Windows.Interop.HwndSource.Handle%2A> vlastnost obsahuje popisovač okna (HWND). HWND, který vám pomůže v nespravované součástí vaší aplikace získáte přetypování `Handle.ToPointer()` k popisovačem HWND.  
  
6. Implementace spravované třídy, která obsahuje statické pole, která obsahuje odkaz na vaši [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu objektu. Tato třída umožňuje získat odkaz na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objekt obsahu z vašeho [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kód, ale další důležité je brání vaše <xref:System.Windows.Interop.HwndSource> nebudou neúmyslně uvolněna z paměti.  
  
7. Příjem oznámení z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu objektu připojením obslužnou rutinu na jeden nebo více [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah události objektu.  
  
8. Komunikovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu objektu pomocí odkazu, která je uložená ve statickém poli. k nastavení vlastností, volání metody, atd.  
  
> [!NOTE]
>  Můžete provést některé nebo všechny [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah definice třídy pro jeden krok v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] horizontálních oddílů pomocí třídy výchozí částečné třídy obsahu, je-li vytvořit samostatné sestavení a pak na něj odkazovat. I když obvykle zahrnují <xref:System.Windows.Application> objektu jako část kompilace [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] do sestavení, nikoli skončíte, který pomocí <xref:System.Windows.Application> jako součást spolupráci, stačí použijete jeden nebo více kořenové třídy pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souborů uvedených do aplikace a odkazovat na jejich částečné třídy. Zbytek postupu je v podstatě podobný tomu uvedených výše.  
>   
>  Každý z těchto kroků je znázorněn prostřednictvím kódu v tomto tématu [názorný postup: Hostování obsahu WPF v Win32](walkthrough-hosting-wpf-content-in-win32.md).  
  
<a name="hosting_an_hwnd"></a>   
## <a name="hosting-a-microsoft-win32-window-in-wpf"></a>Hostující okno Microsoft Win32 v subsystému WPF  
 Klíčem k hostování [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna do jiných [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah je <xref:System.Windows.Interop.HwndHost> třídy. Tato třída zabalí okna [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element, který lze přidat do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stromem prvků. <xref:System.Windows.Interop.HwndHost> podporuje také [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] , které umožňují provádět úkoly, jako je zpracování zpráv pro okno prostředí. Je základní postup:  
  
1. Vytvoření stromu pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace (může být prostřednictvím kódu nebo značky). Najít odpovídající a přípustné bodu ve stromu elementů kde <xref:System.Windows.Interop.HwndHost> implementace se dá přidat jako podřízený element. Ve zbývající části Postup tento element se nazývá elementu rezervace.  
  
2. Jsou odvozeny z <xref:System.Windows.Interop.HwndHost> pro vytvoření objektu, který obsahuje vaše [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] obsah.  
  
3. V této třídě hostitele přepsat <xref:System.Windows.Interop.HwndHost> metoda <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>. Vrací HWND okno prostředí. Může být potřeba zalomit skutečný ovládací prvky jako podřízeného okna vrácené okna. obtékání ovládacích prvků v okně hostitel poskytuje jednoduchý způsob pro váš [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dostávala oznámení z ovládacích prvků obsahu. Tento postup pomáhá opravit některé [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] problémy týkající se zpracování zpráv na hranici hostovaného ovládacího prvku.  
  
4. Přepsat <xref:System.Windows.Interop.HwndHost> metody <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> a <xref:System.Windows.Interop.HwndHost.WndProc%2A>. Záměr tady je pro zpracování vyčištění a odeberte odkazy na hostovaný obsah, zejména v případě, že jste vytvořili odkazy na nespravované objekty.  
  
5. V souboru kódu na pozadí vytvořte instanci hostující třídy ovládacího prvku a nastavte ji podřízeným prvkem prvku rezervace. Obvykle použijete obslužné rutiny události, jako <xref:System.Windows.FrameworkElement.Loaded>, nebo použijte konstruktor částečné třídy. Ale můžete také přidat součinnosti obsah prostřednictvím chování za běhu.  
  
6. Proces vybrané okno zpráv, jako je například oznámení ovládacího prvku. Existují dva přístupy. Oba poskytují stejné přístup k datové proudy zpráv tedy do značné míry na danou programovací pohodlí podle vašeho výběru.  
  
    -   Implementace zpracování pro všechny zprávy (nikoli pouze zprávy vypnutí) v přepsání metody zpráv <xref:System.Windows.Interop.HwndHost> metoda <xref:System.Windows.Interop.HwndHost.WndProc%2A>.  
  
    -   Mít hostování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element zpracování zpráv pomocí manipulace <xref:System.Windows.Interop.HwndHost.MessageHook> událostí. Tato událost je aktivována pro každou zprávu, která je odeslána do hlavního okna procedury okna prostředí.  
  
    -   Nelze zpracovat zprávy ze systému windows, které jsou mimo proces <xref:System.Windows.Interop.HwndHost.WndProc%2A>.  
  
7. Komunikovat s hostovanou okna s použitím platformy vyvolat volat nespravovanou `SendMessage` funkce.  
  
 Tímto postupem se vytvoří aplikaci, která funguje s vstup z myši. Můžete přidat nezávislým podporu pro vaše prostředí okno implementací <xref:System.Windows.Interop.IKeyboardInputSink> rozhraní.  
  
 Každý z těchto kroků je znázorněn prostřednictvím kódu v tomto tématu [názorný postup: Hostování ovládacího prvku Win32 v subsystému WPF](walkthrough-hosting-a-win32-control-in-wpf.md).  
  
### <a name="hwnds-inside-wpf"></a>Hwnds Inside WPF  
 Můžete si představit <xref:System.Windows.Interop.HwndHost> jako speciální ovládací prvek. (Technicky vzato <xref:System.Windows.Interop.HwndHost> je <xref:System.Windows.FrameworkElement> odvozené třídy, ne <xref:System.Windows.Controls.Control> odvozené třídy, ale jeho vzít v úvahu ovládací prvek pro účely vzájemná spolupráce grafického subsystému.) <xref:System.Windows.Interop.HwndHost> abstrahuje základní [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] povaze hostovaný obsah tak, aby zbývající část [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bere v úvahu hostovaný obsah bude jiný ovládací prvek jako objekt, který by měl vykreslení a zpracování vstupu. <xref:System.Windows.Interop.HwndHost> Obecně se chová stejně jako jakýkoli jiný [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement>, i když jsou některé důležité rozdíly kolem výstup (pro vykreslování a grafiku) a vstup (myš a klávesnici) podle omezení jaké základní HWND může podporovat.  
  
#### <a name="notable-differences-in-output-behavior"></a>Významné rozdíly v chování výstupu  
  
-   <xref:System.Windows.FrameworkElement>, což je <xref:System.Windows.Interop.HwndHost> základní třídu, má poměrně málo vlastností, které znamenají změny v uživatelském rozhraní. Tyto vlastnosti patří například <xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=nameWithType>, které změní rozložení elementů v rámci tohoto elementu jako nadřazený. Ale většina těchto vlastností nejsou namapované na možné [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ekvivalenty, i když možná existuje takový ekvivalenty. Příliš mnoho z těchto vlastností a jejich význam jsou příliš vykreslování technologie specifické pro mapování praktické. Proto se nastavení vlastností <xref:System.Windows.FrameworkElement.FlowDirection%2A> na <xref:System.Windows.Interop.HwndHost> nemá žádný vliv.  
  
-   <xref:System.Windows.Interop.HwndHost> nemůže být otočený, škálovaná, výrazně nerovnoměrnou distribucí nebo jinak ovlivněny transformace.  
  
-   <xref:System.Windows.Interop.HwndHost> nepodporuje <xref:System.Windows.UIElement.Opacity%2A> vlastnosti (alfa míchání). Pokud je obsah uvnitř <xref:System.Windows.Interop.HwndHost> provádí <xref:System.Drawing> operace, které zahrnují alfa informace, které není samotného porušení, ale <xref:System.Windows.Interop.HwndHost> jako celek podporuje pouze krytí = 1.0 (100 %).  
  
-   <xref:System.Windows.Interop.HwndHost> se zobrazí nad jiné [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementy ve stejném okně nejvyšší úrovně. Nicméně <xref:System.Windows.Controls.ToolTip> nebo <xref:System.Windows.Controls.ContextMenu> generované nabídky je okno nejvyšší úrovně samostatnou a proto se bude chovat správně s <xref:System.Windows.Interop.HwndHost>.  
  
-   <xref:System.Windows.Interop.HwndHost> nerespektuje oblast ořezu svého nadřazeného objektu <xref:System.Windows.UIElement>. Toto je možná problém, pokud se pokusíte vložit <xref:System.Windows.Interop.HwndHost> třídy v posuvné oblasti nebo <xref:System.Windows.Controls.Canvas>.  
  
#### <a name="notable-differences-in-input-behavior"></a>Významné rozdíly v chování vstupu  
  
-   Obecně platí, že zatímco vstupní zařízení jsou v rámci oboru <xref:System.Windows.Interop.HwndHost> hostované [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] oblast, přejít přímo na vstupní události [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].  
  
-   Zatímco je ukazatel myši nad <xref:System.Windows.Interop.HwndHost>, aplikace nepřijímá [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] událostí myši a hodnota [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnost <xref:System.Windows.UIElement.IsMouseOver%2A> bude `false`.  
  
-   Při <xref:System.Windows.Interop.HwndHost> má fokus klávesnice, vaše aplikace nebude dostávat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klávesnice události a hodnota [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnost <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> bude `false`.  
  
-   Když je fokus v rámci <xref:System.Windows.Interop.HwndHost> a změny v jiném ovládacím prvku uvnitř <xref:System.Windows.Interop.HwndHost>, vaše aplikace nebude dostávat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] události <xref:System.Windows.UIElement.GotFocus> nebo <xref:System.Windows.UIElement.LostFocus>.  
  
-   Související stylus vlastnosti a události jsou podobná a nehlásí informace, zatímco se stylus nachází nad <xref:System.Windows.Interop.HwndHost>.  
  
<a name="tabbing_mnemonics_accelerators"></a>   
## <a name="tabbing-mnemonics-and-accelerators"></a>Přecházení pomocí tabulátoru, klávesových zkratek a akcelerátorů  
 <xref:System.Windows.Interop.IKeyboardInputSink> a <xref:System.Windows.Interop.IKeyboardInputSite> rozhraní vám umožňují vytvářet klávesnice bezproblémové prostředí pro smíšené [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikace:  
  
-   Přecházení mezi pomocí tabulátoru [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] komponenty  
  
-   Klávesových zkratek a akcelerátory, které fungují, i když je aktivní v rámci komponenty Win32 a kdy je v rámci součásti WPF.  
  
 <xref:System.Windows.Interop.HwndHost> a <xref:System.Windows.Interop.HwndSource> obě třídy poskytují implementace <xref:System.Windows.Interop.IKeyboardInputSink>, ale nemusí zpracovávají všechny vstupní zprávy, které chcete použít pro pokročilejší scénáře. Patřičné metody k získání chování klávesnice, které chcete přepište.  
  
 Rozhraní pouze poskytovat podporu pro co se stane při přechodu mezi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] oblastech. V rámci [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] oblast, tabulátor chování je zcela řídí [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] implementovat logiku pro procházení tabulátorem, pokud existuje.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Interop.HwndHost>
- <xref:System.Windows.Interop.HwndSource>
- <xref:System.Windows.Interop>
- [Návod: Hostování ovládacího prvku Win32 v subsystému WPF](walkthrough-hosting-a-win32-control-in-wpf.md)
- [Návod: Hostování obsahu WPF v Win32](walkthrough-hosting-wpf-content-in-win32.md)
