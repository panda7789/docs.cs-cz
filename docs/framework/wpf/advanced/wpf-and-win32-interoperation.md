---
title: Vzájemná spolupráce grafického subsystému WPF a systému Win32
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- hosting WPF content in Win32 window [WPF]
- HWND interop [WPF]
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 0ffbde0d-701d-45a3-a6fa-dd71f4d9772e
caps.latest.revision: 26
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6388762815a621b37c2894cdb7f7966b2c36639c
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="wpf-and-win32-interoperation"></a>Vzájemná spolupráce grafického subsystému WPF a systému Win32
Toto téma obsahuje přehled o tom, jak zajistit vzájemnou funkční spolupráci [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kódu. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje bohaté prostředí pro vytváření aplikací. Pokud však máte významné investice [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] kódu, může být efektivnější opakovaně používat některé z tohoto kódu.  
  

  
<a name="basics"></a>   
## <a name="wpf-and-win32-interoperation-basics"></a>WPF a součinnosti základy Win32  
 Existují dva základní postupy pro spolupráci mezi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kódu.  
  
-   Hostitele [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno. S touto technikou, můžete použít grafické pokročilé možnosti [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v rámci standardní [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno a aplikace.  
  
-   Hostitele [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okno v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu. Tento postup můžete využít existující vlastní [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ovládací prvek v rámci jiné [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu a předávání dat mezi hranice.  
  
 Každý z těchto postupů je koncepčně představenými v tomto tématu. A ukázky kódu více orientovaných na hostování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)], najdete v části [návod: hostování obsahu WPF v Win32](../../../../docs/framework/wpf/advanced/walkthrough-hosting-wpf-content-in-win32.md). A ukázky kódu více orientovaných na hostování [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], najdete v části [návod: hostování ovládacího prvku Win32 v grafickém subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-win32-control-in-wpf.md).  
  
<a name="projects"></a>   
## <a name="wpf-interoperation-projects"></a>Projekty součinnosti WPF  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] spravovaný kód, ale většina existující [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programy jsou zapsány v nespravované [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)].  Nelze volat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] ze skutečného nespravované programu. Avšak pomocí `/clr` možnost s [!INCLUDE[TLA#tla_visualcpp](../../../../includes/tlasharptla-visualcpp-md.md)] kompilátoru, můžete vytvořit smíšené spravované nespravované program kde je možné bezproblémově kombinovat spravovaných a nespravovaných [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] volání.  
  
 Jeden komplikace úrovni projektu je, nelze zkompilovat [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] soubory do [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)] projektu.  Existuje několik postupů dělení projektu kompenzovat to.  
  
-   Vytvořit knihovnu DLL jazyka C# obsahující všechny vaše [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] stránky jako kompilované sestavení a tak vaše [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)] zahrnují spustitelný soubor, který [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] jako odkaz.  
  
-   Vytvořit C# pro spustitelný soubor [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu a mějte ho odkazovat [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)] [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] obsahující [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] obsah.  
  
-   Použití <xref:System.Windows.Markup.XamlReader.Load%2A> načíst všechny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] za běhu, místo kompilování vaší [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
-   Nepoužívejte [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] vůbec a zapisovat všechny vaše [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v kódu, vytváření nahoru k element z <xref:System.Windows.Application>.  
  
 Použijte libovolnou metodu vám nejvíce vyhovuje.  
  
> [!NOTE]
>  Pokud jste nepoužili [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] před, možná jste si všimli některé "new" klíčová slova, jako `gcnew` a `nullptr` v příkladech součinnosti kódu. Tato klíčová slova nahrazují starší syntaxe dvojité podtržítko (`__gc`) a poskytují více fyzických syntaxi pro spravovaný kód v [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)].  Další informace o [!INCLUDE[TLA#tla_cppcli](../../../../includes/tlasharptla-cppcli-md.md)] spravované funkce, najdete na [rozšíření komponent pro platformy běhového prostředí](/cpp/windows/component-extensions-for-runtime-platforms) a [Hello, C + +/ CLI](http://go.microsoft.com/fwlink/?LinkId=98739).  
  
<a name="hwnds"></a>   
## <a name="how-wpf-uses-hwnds"></a>Jak WPF používá hWnd  
 Aby nejvíc z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] "HWND zprostředkovatel komunikace s objekty", musíte pochopit, jak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá HWND. Pro všechny HWND není možné kombinovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vykreslování pomocí [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] vykreslování nebo [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)]  /  [!INCLUDE[TLA2#tla_gdiplus](../../../../includes/tla2sharptla-gdiplus-md.md)] vykreslování. To má číslo dopadů. Především se stává aby bylo možné kombinovat tyto modely vykreslování vůbec, musíte vytvořit součinnosti řešení a použít určené segmenty vzájemná spolupráce pro každý model vykreslování, který chcete použít. Chování vykreslování také vytvoří "vzdušného prostoru" omezení pro co můžete provádět součinnosti řešení. Koncept "vzdušného prostoru" je vysvětlené podrobněji v tématu [oblasti Přehled technologie](../../../../docs/framework/wpf/advanced/technology-regions-overview.md).  
  
 Všechny [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jsou elementy na obrazovce zajišťované HWND. Při vytváření [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window>, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vytvoří nejvyšší úrovně HWND a použije <xref:System.Windows.Interop.HwndSource> se umístí <xref:System.Windows.Window> a jeho [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu uvnitř HWND.  Zbytek vaší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] této singulární HWND sdílí obsahu v aplikaci. Výjimkou je nabídek, rozevírací nabídky pole se seznamem a dalších automaticky otevíraná okna. Tyto prvky vytvořit své vlastní nejvyšší úrovně okno, které je důvod, proč [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nabídky může potenciálně přejděte po okraji okna HWND, který jej obsahuje. Při použití <xref:System.Windows.Interop.HwndHost> uvést popisovačem HWND uvnitř [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] informuje [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] postup umístit do nové relativního HWND podřízené [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Window> HWND.  
  
 Související koncept jako HWND je průhlednost v rámci a mezi každou HWND. To je také popsané v tématu [oblasti Přehled technologie](../../../../docs/framework/wpf/advanced/technology-regions-overview.md).  
  
<a name="hosting_a_wpf_page"></a>   
## <a name="hosting-wpf-content-in-a-microsoft-win32-window"></a>Hostování obsahu subsystému WPF v okně Microsoft Win32  
 Klíč k hostování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] na [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] je okno <xref:System.Windows.Interop.HwndSource> třídy. Zabalí tuto třídu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu v [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okně tak, aby [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu lze začlenit do vaší [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] jako podřízeného okna. Následující metoda kombinuje [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v jedné aplikaci.  
  
1.  Implementace vaší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu (obsah kořenový element) jako spravované třídy. Obvykle třídy dědí z jednoho z třídy, které může obsahovat více podřízených elementů nebo použít jako kořenový element, jako například <xref:System.Windows.Controls.DockPanel> nebo <xref:System.Windows.Controls.Page>. V dalších krocích, tato třída se označuje jako [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu třídy a instance této třídy jsou označovány jako [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu objektů.  
  
2.  Implementace [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikace s [!INCLUDE[TLA2#tla_cppcli](../../../../includes/tla2sharptla-cppcli-md.md)]. Pokud začínáte s existujícím nespravované [!INCLUDE[TLA2#tla_cpp](../../../../includes/tla2sharptla-cpp-md.md)] aplikace, můžete obvykle ho povolit volání spravovaného kódu změnou nastavení projektu zahrnout `/clr` kompilátoru příznak (v plném rozsahu co může být nezbytné pro podporu `/clr`kompilace není popsaných v tomto tématu).  
  
3.  Nastavte modelu vláken pro Threaded Apartment STA (Single). [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používá tento model vláken.  
  
4.  Zpracování oznámení WM_CREATE v procedury okna.  
  
5.  V rámci obslužná rutina (nebo funkci, která volá obslužnou rutinu) postupujte takto:  
  
    1.  Vytvořte novou <xref:System.Windows.Interop.HwndSource> objekt s nadřazeného okna HWND jako jeho `parent` parametr.  
  
    2.  Vytvoření instance vaší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu třídy.  
  
    3.  Přiřaďte odkaz na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu objekt, který má <xref:System.Windows.Interop.HwndSource> objektu <xref:System.Windows.Interop.HwndSource.RootVisual%2A> vlastnost.  
  
    4.  <xref:System.Windows.Interop.HwndSource> Objektu <xref:System.Windows.Interop.HwndSource.Handle%2A> vlastnost obsahuje popisovač okna (HWND). Pokud chcete popisovačem HWND, který můžete použít v nespravované součástí aplikace, přetypujte `Handle.ToPointer()` k popisovačem HWND.  
  
6.  Implementace spravovaných třídu, která obsahuje statické pole, která obsahuje odkaz na vaši [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objekt obsahu. Tato třída umožňuje získat odkaz na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objekt obsahu z vašeho [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kód, ale informace je nejdůležitější zabrání vaší <xref:System.Windows.Interop.HwndSource> nebudou neúmyslně uvolnění z paměti.  
  
7.  Příjem oznámení z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objekt obsahu připojením obslužné rutiny na jeden nebo více [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu události objektu.  
  
8.  Komunikovat s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] objekt obsahu pomocí odkazu, který je uložený v statické pole, které chcete nastavit vlastnosti volání metody, atd.  
  
> [!NOTE]
>  Můžete provést některé nebo všechny [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu jeden krok v definici třídy [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pomocí výchozí třídu obsahu třídy, je-li vytvořit samostatné sestavení a potom na něj odkazovat. I když obvykle zahrnují <xref:System.Windows.Application> objekt v rámci kompilování [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] do sestavení, není skončili pomocí, který <xref:System.Windows.Application> jako součást vzájemná spolupráce, pouze použijete jeden nebo více tříd kořenové [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] označuje soubory pro aplikace a odkazovat na jejich částečné třídy. Zbytek procesu je v podstatě podobná uvedených výše.  
>   
>  Každý z těchto kroků je zobrazená prostřednictvím kódu v tomto tématu [návod: hostování obsahu WPF v Win32](../../../../docs/framework/wpf/advanced/walkthrough-hosting-wpf-content-in-win32.md).  
  
<a name="hosting_an_hwnd"></a>   
## <a name="hosting-a-microsoft-win32-window-in-wpf"></a>Hostování okno Microsoft Win32 v grafickém subsystému WPF  
 Klíč k hostování [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okně v rámci jiné [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah je <xref:System.Windows.Interop.HwndHost> třídy. Tato třída zabalí okno v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element, který lze přidat do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element stromu. <xref:System.Windows.Interop.HwndHost> podporuje také [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] , abyste mohli provádět úlohy, jako jsou zpracování zpráv pro hostované okno Povolit. Základní postup je:  
  
1.  Ve stromu element pro vytvoření [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace (může být prostřednictvím kódu nebo značek). Ve stromové struktuře element vyhledejte odpovídající a povolenou bod kde <xref:System.Windows.Interop.HwndHost> implementace se dá přidat jako podřízený element. Ve zbývající části tyto kroky tento element se označuje jako rezervace element.  
  
2.  Odvozena od <xref:System.Windows.Interop.HwndHost> vytvořit objekt, který obsahuje vaše [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] obsah.  
  
3.  V této třídě hostitele přepsat <xref:System.Windows.Interop.HwndHost> metoda <xref:System.Windows.Interop.HwndHost.BuildWindowCore%2A>. Vrátí HWND hostované okna. Můžete chtít zabalení skutečné požadovaný jako podřízeného okna okna vrácený; obtékání ovládacích prvků v okně hostitel poskytuje jednoduchý způsob pro váš [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu pro příjem oznámení z ovládacích prvků. Tato technika pomáhá opravte pro některé [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] problémy týkající se zpracování zpráv na hranici hostované řízení.  
  
4.  Přepsání <xref:System.Windows.Interop.HwndHost> metody <xref:System.Windows.Interop.HwndHost.DestroyWindowCore%2A> a <xref:System.Windows.Interop.HwndHost.WndProc%2A>. Zde záměrem je zpracovat čištění a odebrat odkazy na hostované obsahu, zejména v případě, že jste vytvořili odkazy na nespravované objekty.  
  
5.  V souboru kódu na pozadí vytvoření instance třídy hostování ovládacího prvku a nastavte jej podřízený element rezervace. Obvykle byste použili obslužné rutiny události, jako <xref:System.Windows.FrameworkElement.Loaded>, nebo použijte konstruktor třídu. Ale můžete také přidat součinnosti obsah prostřednictvím modul runtime chování.  
  
6.  Vybrané okno pro zpracování zprávy, jako je například oznámení ovládacího prvku. Existují dva přístupy. Obě poskytují identické přístup do datového proudu zpráv, vaše volba je z velké části řádu programování pohodlí.  
  
    -   Implementace zpracování pro všechny zprávy (ne jenom vypnutí zpráv) ve vašem přepsání zpráv <xref:System.Windows.Interop.HwndHost> metoda <xref:System.Windows.Interop.HwndHost.WndProc%2A>.  
  
    -   Máte, který je hostitelem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element zpracování zprávy zpracování <xref:System.Windows.Interop.HwndHost.MessageHook> událostí. Tato událost se vyvolá pro každou zprávu, která je odeslána hlavní okno procedury okna hostované.  
  
    -   Nelze zpracovat zprávy ze systému windows, které jsou mimo proces pomocí <xref:System.Windows.Interop.HwndHost.WndProc%2A>.  
  
7.  Komunikovat s okno hostované pomocí platformy vyvolat volání nespravovanou `SendMessage` funkce.  
  
 Následujícím postupem vytvoří aplikaci, která funguje s vstup z myši. Můžete přidat dají se procházet tabulátorem podporu pro hostované okno implementací <xref:System.Windows.Interop.IKeyboardInputSink> rozhraní.  
  
 Každý z těchto kroků je zobrazená prostřednictvím kódu v tomto tématu [návod: hostování ovládacího prvku Win32 v grafickém subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-win32-control-in-wpf.md).  
  
### <a name="hwnds-inside-wpf"></a>HWND uvnitř WPF  
 Si můžete představit <xref:System.Windows.Interop.HwndHost> jako speciální ovládací prvek. (Technicky <xref:System.Windows.Interop.HwndHost> je <xref:System.Windows.FrameworkElement> odvozené třídy, ne <xref:System.Windows.Controls.Control> odvozené třídy, ale lze považovat ovládací prvek pro účely vzájemná spolupráce.) <xref:System.Windows.Interop.HwndHost> abstrahuje základní [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] povaha hostované obsah tak, aby zbytek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zvažuje hostované obsah jako další ovládací prvek jako objektu, který by měl vykreslení a zpracovat vstup. <xref:System.Windows.Interop.HwndHost> Obecně se chová stejně jako jakýkoli jiný [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.FrameworkElement>, i když existuje několik důležitých rozdílů kolem výstup (Kreslení a grafiky) a vstup (myši a klávesnice) podle omezení jaké základní HWND může podporovat.  
  
#### <a name="notable-differences-in-output-behavior"></a>Významné rozdíly v chování výstup  
  
-   <xref:System.Windows.FrameworkElement>, který je <xref:System.Windows.Interop.HwndHost> základní třídu, má několik vlastností, které implikují změny uživatelského rozhraní. Patří mezi ně vlastnosti, jako <xref:System.Windows.FrameworkElement.FlowDirection%2A?displayProperty=nameWithType>, které změní rozložení elementů v rámci tohoto elementu jako nadřazený objekt. Ale většinu tyto vlastnosti nejsou namapované na možné [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ekvivalenty, i když může existovat takové ekvivalenty. Příliš mnoho z těchto vlastností a jejich významy jsou příliš vykreslování technologie specifické pro mapování praktické. Proto nastavení vlastností <xref:System.Windows.FrameworkElement.FlowDirection%2A> na <xref:System.Windows.Interop.HwndHost> nemá žádný vliv.  
  
-   <xref:System.Windows.Interop.HwndHost> nemůže být otočený, škálovat, zkreslilo nebo jinak vliv transformace.  
  
-   <xref:System.Windows.Interop.HwndHost> nepodporuje <xref:System.Windows.UIElement.Opacity%2A> vlastnost (prolnutí alfa). Pokud obsahu uvnitř <xref:System.Windows.Interop.HwndHost> provede <xref:System.Drawing> operace, které zahrnují alfa informace, které nejsou samotné narušení, ale <xref:System.Windows.Interop.HwndHost> jako celek podporuje pouze krytí = 1.0 (100 %).  
  
-   <xref:System.Windows.Interop.HwndHost> se zobrazí nad dalších [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementů v rámci stejného časového období nejvyšší úrovně. Ale <xref:System.Windows.Controls.ToolTip> nebo <xref:System.Windows.Controls.ContextMenu> generovaného nabídky je samostatném okně nejvyšší úrovně a proto bude se chovat správně s <xref:System.Windows.Interop.HwndHost>.  
  
-   <xref:System.Windows.Interop.HwndHost> nerespektuje oblast ořezu nadřazené <xref:System.Windows.UIElement>. Toto je možná problém, pokud se pokusíte převést <xref:System.Windows.Interop.HwndHost> třída uvnitř oblasti s možností posouvání nebo <xref:System.Windows.Controls.Canvas>.  
  
#### <a name="notable-differences-in-input-behavior"></a>Významné rozdíly v chování vstupní  
  
-   Obecně platí, že při vstupní zařízení jsou určené v rámci <xref:System.Windows.Interop.HwndHost> hostované [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] oblasti vstupních událostech přejít přímo na [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].  
  
-   Při přesunutí myši <xref:System.Windows.Interop.HwndHost>, vaše aplikace neobdrží [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] událostí myši a hodnota [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnost <xref:System.Windows.UIElement.IsMouseOver%2A> bude `false`.  
  
-   Při <xref:System.Windows.Interop.HwndHost> má fokus klávesnice aplikace neobdrží [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klávesové události a hodnota [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnost <xref:System.Windows.UIElement.IsKeyboardFocusWithin%2A> bude `false`.  
  
-   Pokud je fokus v rámci <xref:System.Windows.Interop.HwndHost> a změny na další ovládací prvek v rámci <xref:System.Windows.Interop.HwndHost>, aplikace neobdrží [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] události <xref:System.Windows.UIElement.GotFocus> nebo <xref:System.Windows.UIElement.LostFocus>.  
  
-   Související s pera vlastnosti a události se podobá a Neoznamovat informace při pera přes <xref:System.Windows.Interop.HwndHost>.  
  
<a name="tabbing_mnemonics_accelerators"></a>   
## <a name="tabbing-mnemonics-and-accelerators"></a>Procházení tabulátorem, klávesové zkratky a akcelerátorů  
 <xref:System.Windows.Interop.IKeyboardInputSink> a <xref:System.Windows.Interop.IKeyboardInputSite> rozhraní umožňují vytvořit prostředí bezproblémové klávesnice pro smíšený [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikace:  
  
-   Přecházení mezi pomocí tabulátoru [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] součásti  
  
-   Klávesové zkratky a zkratky, ke kterým fungovat, i když je aktivní v rámci komponenty Win32 a pokud je v rámci komponenty WPF.  
  
 <xref:System.Windows.Interop.HwndHost> a <xref:System.Windows.Interop.HwndSource> obě třídy poskytovat implementace <xref:System.Windows.Interop.IKeyboardInputSink>, ale nemusí se zpracovat vstupní zprávy, které chcete použít pro pokročilejší scénáře. Přepište příslušné metody klávesnice chování, které chcete.  
  
 Rozhraní pouze poskytují podporu pro co se stane, že na přechod mezi [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] oblasti. V rámci [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] oblasti použití tabulátoru chování je zcela řízené [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] implementovat logiku pro procházení tabulátorem, pokud existuje.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Interop.HwndHost>  
 <xref:System.Windows.Interop.HwndSource>  
 <xref:System.Windows.Interop>  
 [Návod: Hostování ovládacího prvku Win32 v subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-win32-control-in-wpf.md)  
 [Návod: Hostování obsahu WPF v systému Win32](../../../../docs/framework/wpf/advanced/walkthrough-hosting-wpf-content-in-win32.md)
