---
title: Architektura WPF
ms.date: 03/30/2017
helpviewer_keywords:
- properties [WPF], attached
- attached properties [WPF]
- architecture [WPF]
- unmanaged components [WPF]
- affinity thread [WPF]
- Storyboards [WPF]
- milcore [WPF]
- components [WPF], unmanaged
- painter's algorithm
- interfaces [WPF], INotifyPropertyChange
- CommandBindings [WPF]
- data templates [WPF]
- thread [WPF], affinity
ms.assetid: 8579c10b-76ab-4c52-9691-195ce02333c8
ms.openlocfilehash: c214cb39bf51dad2aafe4ec0c9050f355db5b2c5
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331679"
---
# <a name="wpf-architecture"></a>Architektura WPF
Toto téma poskytuje vodítko v hierarchii tříd Windows Presentation Foundation (WPF). Pokrývá většinu hlavních subsystémů [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]a popisuje jejich interakci. Také podrobně popisuje některé z možností provedených architekty [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  

<a name="System_Object"></a>   
## <a name="systemobject"></a>System.Object  
 Primární [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] programovací model je zveřejněn prostřednictvím spravovaného kódu. Brzy ve fázi [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] návrhu existovalo několik informací o tom, kde by měl být řádek vykreslen mezi spravovanými komponentami systému a nespravovanými systémy. [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] Poskytuje celou řadu funkcí, které usnadňují vývoj a robustní zvýšení produktivity (včetně správy paměti, zpracování chyb, společného systému typů atd.), ale docházejí na náklady.  
  
 Hlavní součásti [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] nástroje jsou znázorněny na následujícím obrázku. Červené části diagramu (PresentationFramework, PresentationCore a milcore) jsou hlavní části kódu v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Z těchto, pouze jedna je nespravovanou komponentou – milcore. Milcore je zapsána v nespravovaném kódu, aby bylo [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]možné povolit úzkou integraci s. Veškeré zobrazení v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] nástroji se provádí [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] prostřednictvím modulu, což umožňuje efektivní vykreslování hardwaru a softwaru. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]také je vyžadována přesnější kontrola nad pamětí a prováděním. Modul kompozice v milcore je extrémně citlivý na výkon a vyžaduje mnoho výhod [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] pro získání výkonu.  
  
 ![Pozice WPF v rámci .NET Framework.](./media/wpf-architect1.PNG "wpf_architect1")  
  
 Komunikace mezi spravovanými a nespravovanými [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] částmi je popsána dále v tomto tématu. Zbývající část spravovaného programovacího modelu je popsána níže.  
  
<a name="System_Threading_DispatcherObject"></a>   
## <a name="systemthreadingdispatcherobject"></a>System.Threading.DispatcherObject  
 Většina objektů [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] , které jsou <xref:System.Windows.Threading.DispatcherObject>odvozeny z, která poskytuje základní konstrukce pro práci s souběžnou a vlákning. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]vychází ze systému zasílání zpráv implementovaného dispečerem. To funguje podobně jako u známého [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] pumpy [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zpráv. dispečer používá zprávy User32 pro provádění volání mezi vlákny.  
  
 Existují dva základní koncepty, které je potřeba pochopit při diskuzi o souběžnosti v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] nástroji – Spřažení dispečera a vlákna.  
  
 Během fáze [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]návrhu nástroje byl cíl přesunut do jediného podprocesu provádění, ale nejedná se o nevlákenný model "spřažené". Spřažení vlákna se stane, když komponenta používá identitu vykonávajícího vlákna k uložení určitého typu stavu. Nejběžnějším formulářem je použití úložiště thread local Store (TLS) k uložení stavu. Spřažení vlákna vyžaduje, aby jednotlivé logické vlákno provádění bylo vlastněné pouze jedním fyzickým vláknem v operačním systému, což může být náročné na paměť. V tomto konci byl model vláken WPF udržován v synchronizaci s existujícím modelem vláken User32 s jedním vláknovým spuštěním s spřažením vlákna. Hlavním důvodem pro tuto spolupráci byla interoperabilita – systémy [!INCLUDE[TLA2#tla_ole2.0](../../../../includes/tla2sharptla-ole2-0-md.md)], jako je, schránka a Internet Explorer, vyžadují spuštění s jedním vláknem (STA).  
  
 Vzhledem k tom, že máte objekty s vlákny STA, potřebujete způsob, jak komunikovat mezi vlákny a ověřit, zda jste ve správném vlákně. V této části je role dispečera. Dispečer je základní systém odesílání zpráv s více frontami s více prioritami. Příklady zpráv zahrnují nezpracovaná vstupní oznámení (přesunutí myši), funkce architektury (rozložení) nebo uživatelské příkazy (spustit tuto metodu). Odvozením z <xref:System.Windows.Threading.DispatcherObject>je [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] vytvoření objektu, který má chování sta, a při vytvoření bude mít ukazatel na dispečera.  
  
<a name="System_Windows_DependencyObject"></a>   
## <a name="systemwindowsdependencyobject"></a>System.Windows.DependencyObject  
 Jedna z primárních filozofiemi architektury používaných v sestavách [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] byla preference pro vlastnosti přes metody nebo události. Vlastnosti jsou deklarativní a umožňují snadněji zadat záměr namísto akce. To také podporuje modelem řízený nebo datově řízený systém pro zobrazení obsahu uživatelského rozhraní. Tento filozofie měl zamýšlený účinek vytvoření dalších vlastností, které můžete vytvořit s cílem zajistit lepší kontrolu nad chováním aplikace.  
  
 Aby bylo možné mít více systémů řízených vlastnostmi, bohatší systém vlastností, než kolik je [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] potřeba. Jednoduchým příkladem této bohatosti je oznámení o změně. Aby bylo možné povolit oboustrannou vazbu, potřebujete obě strany vazby, aby podporovaly oznámení o změně. Aby bylo chování vázané na hodnoty vlastností, musíte být upozorněni, když se změní hodnota vlastnosti. Microsoft .NET Framework má rozhraní **INotifyPropertyChange**, které umožňuje objektu publikovat oznámení o změnách, ale je nepovinný.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]poskytuje bohatší systém vlastností odvozený z <xref:System.Windows.DependencyObject> typu. Systém vlastností je skutečně "systém vlastností" závislosti "v tom, že sleduje závislosti mezi výrazy vlastností a automaticky znovu ověřuje hodnoty vlastností při změně závislosti. Například pokud máte vlastnost, která dědí (jako <xref:System.Windows.Controls.Control.FontSize%2A>), systém je automaticky aktualizován, pokud se změní vlastnost u nadřazené položky elementu, který dědí hodnotu.  
  
 Základem [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] systému vlastností je pojem výrazu vlastnosti. V této první verzi [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]nástroje je uzavřen systém výrazů vlastností a všechny výrazy jsou k dispozici jako součást architektury. Výrazy jsou důvody, proč systém vlastností nemá datovou vazbu, styl nebo dědění, které jsou pevně kódované, ale jsou k dispozici v rámci rozhraní později.  
  
 Systém vlastností také poskytuje pro zhuštěné úložiště hodnot vlastností. Vzhledem k tomu, že objekty mohou mít desítky (pokud nejsou stovky) vlastností a většina hodnot je ve výchozím stavu (Zděděno, nastaveno styly atd.), ne každá instance objektu musí mít úplnou váhu každé definované vlastnosti.  
  
 Poslední novou funkcí systému vlastností je pojem připojených vlastností. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]prvky jsou postaveny na principu složení a opětovného použití komponenty. Často se jedná o případ, kdy některé obsahující prvky (například <xref:System.Windows.Controls.Grid> prvek rozložení) potřebují další data podřízených prvků pro řízení jeho chování (například informace o řádku nebo sloupci). Namísto přidružení všech těchto vlastností ke každému prvku může libovolný objekt poskytovat definice vlastností pro jakýkoliv jiný objekt. To se podobá funkcím "Expanded" jazyka JavaScript.  
  
<a name="System_Windows_Media_Visual"></a>   
## <a name="systemwindowsmediavisual"></a>System.Windows.Media.Visual  
 V dalším kroku, který je definovaný systémem, se na obrazovku nakreslí pixely. <xref:System.Windows.Media.Visual> Třída poskytuje pro vytváření stromové struktury vizuálních objektů, každou volitelně obsahující pokyny pro kreslení a metadata o tom, jak tyto pokyny vykreslit (oříznutí, transformace atd.). <xref:System.Windows.Media.Visual>je navržený tak, aby byl extrémně lehký a flexibilní, takže většina funkcí nemá žádnou veřejnou expozici rozhraní API a spoléhat na chráněné funkce zpětného volání.  
  
 <xref:System.Windows.Media.Visual>je skutečně vstupním bodem [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] systému kompozice. <xref:System.Windows.Media.Visual>je bod připojení mezi těmito dvěma subsystémy, spravovaným rozhraním API a nespravovaným milcore.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]zobrazuje data přecházením do nespravovaných datových struktur spravovaných pomocí milcore. Tyto struktury označované jako uzly kompozice reprezentují hierarchický strom zobrazení s pokyny pro vykreslování v jednotlivých uzlech. Tento strom, který je znázorněn na pravé straně obrázku níže, je přístupný pouze prostřednictvím protokolu zasílání zpráv.  
  
 Při programování [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]vytvoříte <xref:System.Windows.Media.Visual> prvky a odvozené typy, které interně komunikují do stromu kompozice prostřednictvím tohoto protokolu pro zasílání zpráv. Každý <xref:System.Windows.Media.Visual> v[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] nástroji může vytvořit jeden, žádný nebo několik uzlů kompozice.  
  
 ![Windows Presentation Foundation vizuální strom.](./media/wpf-architecture2.PNG "wpf_architecture2")  
  
 Tady si můžete všimnout podrobných podrobností o architektuře – celý strom vizuálů a instrukcí pro kreslení se ukládá do mezipaměti. V případě [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] grafických výrazů používá systém uchovávaného vykreslování. To umožňuje systému překreslit s vysokou mírou aktualizace bez blokování systému kompozice při zpětných voláních kódu uživatele. To pomáhá zabránit vzhledu nereagujících aplikací.  
  
 Další důležité podrobnosti, které v diagramu opravdu nevšimnete, je způsob, jakým systém skutečně provádí složení.  
  
 V User32 a [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)]systém funguje v režimu ořezového systému přímo v režimu. V případě, že je nutné vykreslit komponentu, systém vytvoří ořezové meze mimo prvek, který není povolen k dotyku s pixely, a poté, co je komponenta požádána o Malování pixelů v tomto poli. Tento systém funguje velmi dobře v omezených systémech paměti, protože když se něco změní jenom na ovlivněnou součást – žádné dvě komponenty nepřispívají k barvě jednoho pixelu.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]používá model Malování "Algorithm 's". To znamená, že místo oříznutí jednotlivých komponent je každá komponenta požádána o vykreslení od zpátky po začátek zobrazení. Díky tomu mohou jednotlivé komponenty malovat přes zobrazení předchozí součásti. Výhodou tohoto modelu je, že můžete mít složité a částečně transparentní tvary. Díky dnešnímu modernímu grafickému hardwaru je tento model poměrně rychlý (což nevedlo v případě [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] vytvoření user32/).  
  
 Jak již [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] bylo zmíněno dříve, základní filozofie je třeba přesunout na více deklarativní model programování "vlastností" orientovaný na "vlastnosti". V vizuálním systému se to zobrazuje na několika zajímavých místech.  
  
 Za prvé, pokud si myslíte o grafickém systému uchovávaného režimu, je to skutečně přesun z imperativního modelu typu DrawLine/DrawLine na model s daty orientovaný na nový řádek ()/New řádek (). Tato operace přejít na vykreslování řízené daty umožňuje, aby se v pokynech pro kreslení vyjádřily informace pomocí vlastností. Typy odvozené z <xref:System.Windows.Media.Drawing> jsou efektivně objektovým modelem pro vykreslování.  
  
 Za druhé, pokud vyhodnocujete animační systém, uvidíte, že je skoro zcela deklarativní. Místo vyžadování vývojářů pro výpočet dalšího umístění nebo další barvy můžete vyjádřit animace jako sadu vlastností objektu animace. Tyto animace mohou následně vyjádřit záměr vývojáře nebo návrháře (přesunout toto tlačítko sem za 5 sekund) a systém může určit nejúčinnější způsob, jak to provést.  
  
<a name="System_Windows_UIElement"></a>   
## <a name="systemwindowsuielement"></a>System.Windows.UIElement  
 <xref:System.Windows.UIElement>definuje základní subsystémy, včetně rozložení, vstupu a událostí.  
  
 Rozložení je základní koncept v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]nástroji. V mnoha systémech existuje buď pevná sada modelů rozložení (HTML podporuje tři modely pro rozložení, flow, absolutní a tabulky), nebo žádný model pro rozložení (User32 skutečně podporuje pouze absolutní umístění). [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]zahájeno s předpokladem, že vývojáři a návrháři chtěli flexibilní a rozšiřitelný model rozložení, který by mohl být založen na hodnotách vlastností, a ne na imperativní logice. Na úrovni se zavádí základní kontrakt pro rozložení – dva fáze modelu s <xref:System.Windows.UIElement.Measure%2A> a <xref:System.Windows.UIElement.Arrange%2A> projde. <xref:System.Windows.UIElement>  
  
 <xref:System.Windows.UIElement.Measure%2A>umožňuje komponentě určit, jakou velikost by chtěla provést. Jedná se o samostatnou fázi <xref:System.Windows.UIElement.Arrange%2A> od, protože existuje mnoho situací, kdy nadřazený prvek bude pokládat podřízeným elementem k měření, aby bylo možné určit jeho optimální polohu a velikost. Skutečnost, že nadřazené prvky žádají podřízené prvky k měření ukazuje další klíč filozofie o [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] velikosti obsahu. Všechny ovládací prvky [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] v podporují možnost velikosti až do přirozené velikosti jejich obsahu. Díky tomu je lokalizace mnohem jednodušší a umožňuje dynamické rozložení prvků pro změny velikosti. <xref:System.Windows.UIElement.Arrange%2A> Fáze umožňuje nadřazenému umístění a určení konečné velikosti jednotlivých podřízených objektů.  
  
 Spousta času často stráví rozhovorem o výstupní straně [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] – <xref:System.Windows.Media.Visual> a souvisejících objektech. Na straně vstupu je ale také obrovské množství inovací. Nejvýznamnější změnou modelu vstupu pro [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] je pravděpodobně konzistentní model, podle kterého jsou vstupní události směrovány přes systém.  
  
 Vstup pochází jako signál pro ovladač zařízení režimu jádra a je směrován do správného procesu a vlákna prostřednictvím komplikovaného procesu zahrnujícího jádro Windows a User32. Jakmile je zpráva User32 odpovídající vstupu směrována na [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], je převedena [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] na nezpracované vstupní zprávy a odeslána na dispečera. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]umožňuje, aby se nezpracované vstupní události převedly na několik skutečných událostí, což umožňuje implementaci funkcí jako "MouseEnter" na nízké úrovni systému se zaručeným doručením.  
  
 Každá vstupní událost se převede na alespoň dvě události – na událost Preview a na skutečnou událost. Všechny události v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] nástroji mají pojem směrování prostřednictvím stromu elementu. Události jsou označeny jako "bublina", pokud procházejí z cíle stromu stromu do kořenového adresáře a jsou označeny jako "tunel", pokud se spustí v kořenovém adresáři a přesměruje na cíl. Vstupní tunelové události ve verzi Preview umožňují všem prvkům ve stromu možnost filtrovat nebo provést akci s událostí. Běžné události (bez verze Preview) jsou pak z cíle až do kořenového adresáře.  
  
 Tento rozdělení mezi fází tunelového propojení a bublinový postup umožňuje implementaci funkcí, jako jsou klávesové zkratky, fungovat konzistentně způsobem ve složeném světě. V User32 byste implementovali klávesové zkratky s jednou globální tabulkou obsahující všechny akcelerátory, které chcete podporovat (CTRL + N mapování na "New"). V dispečeru vaší aplikace byste volali **TranslateAccelerator** , která by mohla sledovat vstupní zprávy v User32 a zjistit, jestli se nějaký odpovídající registrovaný akcelerátor. V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] takovém případě to nefunguje, protože systém je plně "sestavitelný" – libovolný prvek může zpracovat a použít jakékoli klávesové zkratky. Má-li tento model dvou fází vstup, umožňuje komponentám implementovat vlastní "TranslateAccelerator".  
  
 Pokud chcete tento krok provést podrobněji, <xref:System.Windows.UIElement> zavádíme také pojem CommandBindings. Systém příkazů umožňuje vývojářům definovat funkce v souvislosti s koncovým bodem příkazu – něco, co implementuje <xref:System.Windows.Input.ICommand>. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Vazby příkazů umožňují elementu definovat mapování mezi vstupním gestem (CTRL + N) a příkazem (New). Vstupní gesta i definice příkazů jsou rozšiřitelné a můžou být v čase použití kabelové. Díky tomu je to triviální, například umožňuje koncovému uživateli přizpůsobit klíčové vazby, které chtějí používat v rámci aplikace.  
  
 K tomuto bodu v tématu, jsou základní funkce funkcí [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] – funkcí implementovaných v sestavení PresentationCore. Při sestavování [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]je požadováno čisté oddělení mezi základními částmi (jako je kontrakt pro rozložení s **měřením** a **uspořádáním**) a rámec částí (jako je <xref:System.Windows.Controls.Grid>implementace konkrétního rozložení). zaznamenaný. Cílem bylo poskytnout v zásobníku nedostatek bodu rozšiřitelnosti, který by umožnil externím vývojářům vytvořit v případě potřeby vlastní rozhraní.  
  
<a name="System_Windows_FrameworkElement"></a>   
## <a name="systemwindowsframeworkelement"></a>System.Windows.FrameworkElement  
 <xref:System.Windows.FrameworkElement>lze si prohledat dvěma různými způsoby. Zavádí sadu zásad a přizpůsobení v subsystémech představených v nižších vrstvách [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Zavádí také sadu nových subsystémů.  
  
 Primární zásada, kterou <xref:System.Windows.FrameworkElement> zavádí, je kolem rozložení aplikace. <xref:System.Windows.FrameworkElement>sestaví se na základě základní smlouvy <xref:System.Windows.UIElement> o rozložení, kterou zavádí a přidává pojem rozložení "slot", který usnadňuje tvůrci rozložení, aby měl konzistentní sadu vlastností řízených sémantikou rozložení. Vlastnosti jako <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>, <xref:System.Windows.FrameworkElement.MinWidth%2A> <xref:System.Windows.FrameworkElement> a (propojmenování)poskytujívšechnykomponentyodvozenézkonzistentníhochováníuvnitřkontejnerůrozložení.<xref:System.Windows.FrameworkElement.Margin%2A>  
  
 <xref:System.Windows.FrameworkElement>poskytuje také snadnější vystavení rozhraní API pro mnoho funkcí, které se [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]nacházejí v základních vrstvách. Například <xref:System.Windows.FrameworkElement> poskytuje přímý přístup k animaci <xref:System.Windows.FrameworkElement.BeginStoryboard%2A> prostřednictvím metody. <xref:System.Windows.Media.Animation.Storyboard> Poskytuje způsob, jak skriptovat více animací proti sadě vlastností.  
  
 Dvě nejdůležitější věci, které zavádí <xref:System.Windows.FrameworkElement> , jsou datové vazby a styly.  
  
 Podsystém datových vazeb v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] nástroji by měl být poměrně obeznámen s kýmkoli, kdo pro vytvoření aplikace [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]použil [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] nebo ASP.NET. V každém z těchto systémů existuje jednoduchý způsob, jak vyjádřit, že chcete, aby jedna nebo více vlastností z daného prvku bylo vázáno na určitou část dat. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]má úplnou podporu pro vazby vlastností, transformaci a vazby seznamu.  
  
 Jedním z nejzajímavějších funkcí datové vazby v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] nástroji je zavedení šablon dat. Šablony dat umožňují deklarativní určení způsobu vizuálního zobrazení části dat. Místo vytvoření vlastního uživatelského rozhraní, které může být vázáno na data, můžete místo toho problém vyřešit a nechat data určit zobrazení, které bude vytvořeno.  
  
 Stylování je ve skutečnosti odlehčená forma datové vazby. Pomocí stylů můžete navazovat sadu vlastností ze sdílené definice na jednu nebo více instancí elementu. <xref:System.Windows.FrameworkElement.Style%2A> Styly[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] se aplikují na element buď explicitním odkazem (nastavením vlastnosti), nebo implicitně přidružením stylu k typu elementu.  
  
<a name="System_Windows_Controls_Control"></a>   
## <a name="systemwindowscontrolscontrol"></a>System.Windows.Controls.Control  
 Nejvýznamnější funkcí ovládacího prvku je šablonování. Pokud si myslíte o systému kompozice WPF jako systém vykreslování v zachované podobě, šablonování umožňuje ovládacímu prvku popsat jeho vykreslování v parametrizovaném, deklarativním způsobu. Není <xref:System.Windows.Controls.ControlTemplate> ve skutečnosti nic více než skript pro vytvoření sady podřízených prvků s vazbami na vlastnosti nabízené ovládacím prvkem.  
  
 <xref:System.Windows.Controls.Control>poskytuje sadu burzovních vlastností, <xref:System.Windows.Controls.Control.Foreground%2A> <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Control.Padding%2A>,, pro pojmenování, které autoři šablon mohou použít k přizpůsobení zobrazení ovládacího prvku. Implementace ovládacího prvku poskytuje model datového modelu a interakce. Model interakce definuje sadu příkazů (například zavřít pro okno) a vazby na vstupní gesta (například kliknutím na červený symbol X v horním rohu okna). Datový model poskytuje sadu vlastností buď k přizpůsobení modelu interakce, nebo přizpůsobení zobrazení (určené šablonou).  
  
 Tento rozdělení mezi datovým modelem (vlastnosti), modelem interakce (příkazy a události) a modelem zobrazení (šablony) umožňuje kompletní přizpůsobení vzhledu a chování ovládacího prvku.  
  
 Běžný aspekt datového modelu ovládacího prvku je model obsahu. Pokud se podíváte na ovládací <xref:System.Windows.Controls.Button>prvek, například, uvidíte, že obsahuje vlastnost s názvem Content (obsah) <xref:System.Object>typu. V [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] a ASP.NET by tato vlastnost byla obvykle řetězec – ale omezuje typ obsahu, který lze vložit do tlačítka. Obsah pro tlačítko může být buď jednoduchý řetězec, komplexní datový objekt, nebo celý strom elementu. V případě datového objektu se k sestavení zobrazení použije šablona dat.  
  
<a name="Summary"></a>   
## <a name="summary"></a>Souhrn  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]je navržený tak, aby vám umožnil vytvářet dynamické prezentační systémy založené na datech. Každá část systému je navržena tak, aby vytvářela objekty prostřednictvím sad vlastností, které řídí chování jednotky. Datová vazba je základní součástí systému a je integrovaná na všech vrstvách.  
  
 Tradiční aplikace vytvoří zobrazení a pak vytvoří vazby k některým datům. V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]je vše o ovládacím prvku, každý aspekt zobrazení, vygenerováno nějakým typem datové vazby. Text, který se nachází uvnitř tlačítka, se zobrazí tak, že se vytvoří složený ovládací prvek uvnitř tlačítka a vazba jeho zobrazení na vlastnost obsahu tlačítka.  
  
 Když začnete vyvíjet [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] aplikace založené na systému, je vhodné se velmi seznámit. Můžete nastavit vlastnosti, použít objekty a vytvořit datovou vazby podobným způsobem, jakým můžete použít [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] nebo ASP.NET. Díky hlubšímu zkoumání architektury [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]nástroje zjistíte, že existuje možnost pro vytváření mnohem rozsáhlejších aplikací, které v podstatě považují data za základní ovladač aplikace.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.Visual>
- <xref:System.Windows.UIElement>
- <xref:System.Windows.Input.ICommand>
- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.Threading.DispatcherObject>
- <xref:System.Windows.Input.CommandBinding>
- <xref:System.Windows.Controls.Control>
- [Přehled datových vazeb](../data/data-binding-overview.md)
- [Rozložení](layout.md)
- [Přehled animace](../graphics-multimedia/animation-overview.md)
