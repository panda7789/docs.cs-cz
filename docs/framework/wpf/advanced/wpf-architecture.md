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
ms.openlocfilehash: 2ec979240b8fead10522817b77eef23e29409411
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740688"
---
# <a name="wpf-architecture"></a>Architektura WPF
Toto téma poskytuje vodítko v hierarchii tříd Windows Presentation Foundation (WPF). Pokrývá většinu hlavních subsystémů [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]a popisuje, jak s nimi pracují. Popisuje také některé z možností provedených architekty [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  

<a name="System_Object"></a>   
## <a name="systemobject"></a>System.Object  
 Primární programovací model [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] se zveřejňuje prostřednictvím spravovaného kódu. V rané fázi návrhu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] existovalo několik jednání o tom, kde by měl být řádek vykreslen mezi spravovanými komponentami systému a nespravovanými systémy. CLR nabízí celou řadu funkcí, které zvýší produktivitu a robustní vývoj (včetně správy paměti, zpracování chyb, společného systému typů atd.), ale dostanou za cenu.  
  
 Hlavní součásti [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] jsou znázorněny na následujícím obrázku. Červené části diagramu (PresentationFramework, PresentationCore a milcore) jsou hlavní části kódu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Z těchto, pouze jedna je nespravovanou komponentou – milcore. Milcore je zapsán v nespravovaném kódu, aby bylo možné povolit úzkou integraci s rozhraním DirectX. Všechna zobrazení v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] se provádí prostřednictvím modulu DirectX, což umožňuje efektivní vykreslování hardwaru a softwaru. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] taky vyžadovala přesnější kontrolu paměti a provádění. Modul kompozice v milcore je extrémně citlivý na výkon a vyžaduje mnoho výhod CLR pro získání výkonu.  
  
 ![Pozice WPF v rámci .NET Framework.](./media/wpf-architect1.PNG "wpf_architect1")  
  
 Komunikace mezi spravovanými a nespravovanými částmi [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] je popsána dále v tomto tématu. Zbývající část spravovaného programovacího modelu je popsána níže.  
  
<a name="System_Threading_DispatcherObject"></a>   
## <a name="systemthreadingdispatcherobject"></a>System.Threading.DispatcherObject  
 Většina objektů v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] je odvozena z <xref:System.Windows.Threading.DispatcherObject>, která poskytuje základní konstrukce pro práci s souběžnou a vlákning. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] je založena na systému zasílání zpráv implementovaném dispečerem. To funguje podobně jako u známého [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)]ového pumpy zpráv; ve skutečnosti [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dispečer používá zprávy User32 pro provádění volání mezi vlákny.  
  
 Existují dva základní koncepty, které je potřeba pochopit při diskuzi o souběžnosti v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] – Spřažení dispečera a vlákna.  
  
 Během fáze návrhu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]byl cíl přesunut do jediného podprocesu provádění, ale nejedná se o nevlákenný model "spřažené". Spřažení vlákna se stane, když komponenta používá identitu vykonávajícího vlákna k uložení určitého typu stavu. Nejběžnějším formulářem je použití úložiště thread local Store (TLS) k uložení stavu. Spřažení vlákna vyžaduje, aby jednotlivé logické vlákno provádění bylo vlastněné pouze jedním fyzickým vláknem v operačním systému, což může být náročné na paměť. V tomto konci byl model vláken WPF udržován v synchronizaci s existujícím modelem vláken User32 s jedním vláknovým spuštěním s spřažením vlákna. Hlavním důvodem pro tuto spolupráci byla interoperabilita – systémy, jako je například technologie OLE 2,0, schránka a aplikace Internet Explorer, vyžadují spuštění s jedním vláknem (STA).  
  
 Vzhledem k tom, že máte objekty s vlákny STA, potřebujete způsob, jak komunikovat mezi vlákny a ověřit, zda jste ve správném vlákně. V této části je role dispečera. Dispečer je základní systém odesílání zpráv s více frontami s více prioritami. Příklady zpráv zahrnují nezpracovaná vstupní oznámení (přesunutí myši), funkce architektury (rozložení) nebo uživatelské příkazy (spustit tuto metodu). Odvozením z <xref:System.Windows.Threading.DispatcherObject>vytvoříte objekt CLR, který má chování STA, a bude předána ukazatel na dispečera v okamžiku vytvoření.  
  
<a name="System_Windows_DependencyObject"></a>   
## <a name="systemwindowsdependencyobject"></a>System.Windows.DependencyObject  
 Jedna z primárních filozofiemi architektury používaných při vytváření [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] byla preference pro vlastnosti přes metody nebo události. Vlastnosti jsou deklarativní a umožňují snadněji zadat záměr namísto akce. To také podporuje modelem řízený nebo datově řízený systém pro zobrazení obsahu uživatelského rozhraní. Tento filozofie měl zamýšlený účinek vytvoření dalších vlastností, které můžete vytvořit s cílem zajistit lepší kontrolu nad chováním aplikace.  
  
 Aby bylo možné mít více systémů řízených vlastnostmi, bohatší systém vlastností, než který je potřebný pro CLR. Jednoduchým příkladem této bohatosti je oznámení o změně. Aby bylo možné povolit oboustrannou vazbu, potřebujete obě strany vazby, aby podporovaly oznámení o změně. Aby bylo chování vázané na hodnoty vlastností, musíte být upozorněni, když se změní hodnota vlastnosti. Microsoft .NET Framework má rozhraní **INotifyPropertyChange**, které umožňuje objektu publikovat oznámení o změnách, ale je nepovinný.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] poskytuje bohatší systém vlastností odvozený z typu <xref:System.Windows.DependencyObject>. Systém vlastností je skutečně "systém vlastností" závislosti "v tom, že sleduje závislosti mezi výrazy vlastností a automaticky znovu ověřuje hodnoty vlastností při změně závislosti. Například pokud máte vlastnost, která dědí (například <xref:System.Windows.Controls.Control.FontSize%2A>), systém se automaticky aktualizuje, pokud se změní vlastnost u nadřazené položky prvku, který dědí hodnotu.  
  
 Základem [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]ho systému vlastností je pojem výrazu vlastnosti. V této první vydané verzi [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]je uzavřen systém výrazů vlastnosti a všechny výrazy jsou k dispozici jako součást architektury. Výrazy jsou důvody, proč systém vlastností nemá datovou vazbu, styl nebo dědění, které jsou pevně kódované, ale jsou k dispozici v rámci rozhraní později.  
  
 Systém vlastností také poskytuje pro zhuštěné úložiště hodnot vlastností. Vzhledem k tomu, že objekty mohou mít desítky (pokud nejsou stovky) vlastností a většina hodnot je ve výchozím stavu (Zděděno, nastaveno styly atd.), ne každá instance objektu musí mít úplnou váhu každé definované vlastnosti.  
  
 Poslední novou funkcí systému vlastností je pojem připojených vlastností. prvky [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] jsou postaveny na principu složení a opětovného použití komponenty. Často se jedná o případ, že některé obsahující prvky (například <xref:System.Windows.Controls.Grid> prvek rozložení) potřebují další data podřízených prvků pro řízení jeho chování (například informace o řádku nebo sloupci). Namísto přidružení všech těchto vlastností ke každému prvku může libovolný objekt poskytovat definice vlastností pro jakýkoliv jiný objekt. To se podobá funkcím "Expanded" jazyka JavaScript.  
  
<a name="System_Windows_Media_Visual"></a>   
## <a name="systemwindowsmediavisual"></a>System.Windows.Media.Visual  
 V dalším kroku, který je definovaný systémem, se na obrazovku nakreslí pixely. Třída <xref:System.Windows.Media.Visual> poskytuje pro vytváření stromové struktury vizuálních objektů, každou volitelně obsahující pokyny pro kreslení a metadata o způsobu vykreslování těchto instrukcí (oříznutí, transformace atd.). <xref:System.Windows.Media.Visual> je navržený tak, aby byl extrémně lehký a flexibilní, takže většina funkcí nemá žádnou veřejnou expozici rozhraní API a spoléhat na chráněné funkce zpětného volání.  
  
 <xref:System.Windows.Media.Visual> je skutečně vstupním bodem do systému [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] kompozice. <xref:System.Windows.Media.Visual> je bod připojení mezi těmito dvěma subsystémy, spravovaným rozhraním API a nespravovaným milcore.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zobrazuje data procházením nespravovaných datových struktur spravovaných pomocí milcore. Tyto struktury označované jako uzly kompozice reprezentují hierarchický strom zobrazení s pokyny pro vykreslování v jednotlivých uzlech. Tento strom, který je znázorněn na pravé straně obrázku níže, je přístupný pouze prostřednictvím protokolu zasílání zpráv.  
  
 Při programování [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]vytvoříte <xref:System.Windows.Media.Visual> prvky a odvozené typy, které interně komunikují do stromu kompozice prostřednictvím tohoto protokolu pro zasílání zpráv. Každý <xref:System.Windows.Media.Visual> v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] může vytvořit jeden, žádný nebo několik uzlů kompozice.  
  
 ![Windows Presentation Foundation vizuální strom.](./media/wpf-architecture2.PNG "wpf_architecture2")  
  
 Tady si můžete všimnout podrobných podrobností o architektuře – celý strom vizuálů a instrukcí pro kreslení se ukládá do mezipaměti. V případě grafických výrazů používá [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] zadržený vykreslovací systém. To umožňuje systému překreslit s vysokou mírou aktualizace bez blokování systému kompozice při zpětných voláních kódu uživatele. To pomáhá zabránit vzhledu nereagujících aplikací.  
  
 Další důležité podrobnosti, které v diagramu opravdu nevšimnete, je způsob, jakým systém skutečně provádí složení.  
  
 V User32 a GDI systém funguje v režimu ořezového systému přímo v režimu. V případě, že je nutné vykreslit komponentu, systém vytvoří ořezové meze mimo prvek, který není povolen k dotyku s pixely, a poté, co je komponenta požádána o Malování pixelů v tomto poli. Tento systém funguje velmi dobře v omezených systémech paměti, protože když se něco změní jenom na ovlivněnou součást – žádné dvě komponenty nepřispívají k barvě jednoho pixelu.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] používá model Malování "Algorithm 's". To znamená, že místo oříznutí jednotlivých komponent je každá komponenta požádána o vykreslení od zpátky po začátek zobrazení. Díky tomu mohou jednotlivé komponenty malovat přes zobrazení předchozí součásti. Výhodou tohoto modelu je, že můžete mít složité a částečně transparentní tvary. Díky dnešnímu modernímu grafickému hardwaru je tento model poměrně rychlý (což neplatí při vytvoření User32/GDI).  
  
 Jak již bylo uvedeno výše, základní filozofie [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] je přesunout na více deklarativní model "orientovaný na vlastnosti". V vizuálním systému se to zobrazuje na několika zajímavých místech.  
  
 Za prvé, pokud si myslíte o grafickém systému uchovávaného režimu, je to skutečně přesun z imperativního modelu typu DrawLine/DrawLine na model s daty orientovaný na nový řádek ()/New řádek (). Tato operace přejít na vykreslování řízené daty umožňuje, aby se v pokynech pro kreslení vyjádřily informace pomocí vlastností. Typy odvozené od <xref:System.Windows.Media.Drawing> jsou efektivně objektový model pro vykreslování.  
  
 Za druhé, pokud vyhodnocujete animační systém, uvidíte, že je skoro zcela deklarativní. Místo vyžadování vývojářů pro výpočet dalšího umístění nebo další barvy můžete vyjádřit animace jako sadu vlastností objektu animace. Tyto animace mohou následně vyjádřit záměr vývojáře nebo návrháře (přesunout toto tlačítko sem za 5 sekund) a systém může určit nejúčinnější způsob, jak to provést.  
  
<a name="System_Windows_UIElement"></a>   
## <a name="systemwindowsuielement"></a>System.Windows.UIElement  
 <xref:System.Windows.UIElement> definuje základní subsystémy, včetně rozložení, vstupu a událostí.  
  
 Rozložení je základní koncept v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. V mnoha systémech existuje buď pevná sada modelů rozložení (HTML podporuje tři modely pro rozložení, flow, absolutní a tabulky), nebo žádný model pro rozložení (User32 skutečně podporuje pouze absolutní umístění). [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] spuštěn s předpokladem, že vývojáři a návrháři chtěli flexibilní a rozšiřitelný model rozložení, který by mohl být založen na hodnotách vlastností, a ne na imperativní logice. Na úrovni <xref:System.Windows.UIElement> zavádíme základní kontrakt pro rozložení – dva fáze modelu s <xref:System.Windows.UIElement.Measure%2A> a <xref:System.Windows.UIElement.Arrange%2A> průchody.  
  
 <xref:System.Windows.UIElement.Measure%2A> umožňuje komponentě určit, jakou velikost by chtěli provést. Jedná se o samostatnou fázi od <xref:System.Windows.UIElement.Arrange%2A>, protože je k dispozici mnoho situací, kdy nadřazený prvek bude pokládat podřízeným elementem k měření jeho optimální polohy a velikosti. Skutečnost, že nadřazené prvky žádají podřízené prvky k měření ukazuje další klíčová filozofie [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] – velikost obsahu. Všechny ovládací prvky v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] podporují možnost velikosti podle přirozené velikosti jejich obsahu. Díky tomu je lokalizace mnohem jednodušší a umožňuje dynamické rozložení prvků pro změny velikosti. <xref:System.Windows.UIElement.Arrange%2A> fáze umožňuje nadřazenému umístění a určení konečné velikosti jednotlivých podřízených objektů.  
  
 Spousta času často stráví rozhovorem na straně výstupu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] – <xref:System.Windows.Media.Visual> a souvisejících objektů. Na straně vstupu je ale také obrovské množství inovací. Největší základní změnou modelu vstupu pro [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] je konzistentní model, podle kterého jsou vstupní události směrovány přes systém.  
  
 Vstup pochází jako signál pro ovladač zařízení režimu jádra a je směrován do správného procesu a vlákna prostřednictvím komplikovaného procesu zahrnujícího jádro Windows a User32. Jakmile je zpráva User32 odpovídající vstupu směrována na [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], je převedena na [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] nezpracovaná vstupní zpráva a odeslána do dispečera. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] umožňuje převod nezpracovaných vstupních událostí na více skutečných událostí a povolení funkcí, jako je "MouseEnter", bude implementováno na nízké úrovni systému se zaručeným doručením.  
  
 Každá vstupní událost se převede na alespoň dvě události – na událost Preview a na skutečnou událost. Všechny události v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] mají pojem směrování prostřednictvím stromu elementu. Události jsou označeny jako "bublina", pokud procházejí z cíle stromu stromu do kořenového adresáře a jsou označeny jako "tunel", pokud se spustí v kořenovém adresáři a přesměruje na cíl. Vstupní tunelové události ve verzi Preview umožňují všem prvkům ve stromu možnost filtrovat nebo provést akci s událostí. Běžné události (bez verze Preview) jsou pak z cíle až do kořenového adresáře.  
  
 Tento rozdělení mezi fází tunelového propojení a bublinový postup umožňuje implementaci funkcí, jako jsou klávesové zkratky, fungovat konzistentně způsobem ve složeném světě. V User32 byste implementovali klávesové zkratky s jednou globální tabulkou obsahující všechny akcelerátory, které chcete podporovat (CTRL + N mapování na "New"). V dispečeru vaší aplikace byste volali **TranslateAccelerator** , která by mohla sledovat vstupní zprávy v User32 a zjistit, jestli se nějaký odpovídající registrovaný akcelerátor. V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] to by nefungovalo, protože systém je plně "sestavitelný" – libovolný prvek může zpracovat a použít jakékoli klávesové zkratky. Má-li tento model dvou fází vstup, umožňuje komponentám implementovat vlastní "TranslateAccelerator".  
  
 Chcete-li provést tento krok dál, <xref:System.Windows.UIElement> také zavádí pojem CommandBindings. Systém [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] příkazů umožňuje vývojářům definovat funkce v souvislosti s koncovým bodem příkazu – něco, co implementuje <xref:System.Windows.Input.ICommand>. Vazby příkazů umožňují elementu definovat mapování mezi vstupním gestem (CTRL + N) a příkazem (New). Vstupní gesta i definice příkazů jsou rozšiřitelné a můžou být v čase použití kabelové. Díky tomu je to triviální, například umožňuje koncovému uživateli přizpůsobit klíčové vazby, které chtějí používat v rámci aplikace.  
  
 K tomuto bodu je v tématu "základní" funkce [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] – funkce implementované v sestavení PresentationCore byly soustředěny. Při sestavování [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]byl požadovaný výsledek čistým oddělením mezi základními částmi (jako je kontrakt pro rozložení s **měřením** a **uspořádáním**) a rámec částí (jako je implementace konkrétního rozložení, jako je například <xref:System.Windows.Controls.Grid>). Cílem bylo poskytnout v zásobníku nedostatek bodu rozšiřitelnosti, který by umožnil externím vývojářům vytvořit v případě potřeby vlastní rozhraní.  
  
<a name="System_Windows_FrameworkElement"></a>   
## <a name="systemwindowsframeworkelement"></a>System.Windows.FrameworkElement  
 <xref:System.Windows.FrameworkElement> lze prohledat dvěma různými způsoby. Zavádí sadu zásad a přizpůsobení v subsystémech představených v nižších vrstvách [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Zavádí také sadu nových subsystémů.  
  
 Primární zásada, kterou zavádí <xref:System.Windows.FrameworkElement>, je okolo rozložení aplikace. <xref:System.Windows.FrameworkElement> sestaví na základní smlouvě o rozložení, kterou zavádí <xref:System.Windows.UIElement> a přidává pojem rozložení "slot", který usnadňuje tvůrci rozložení, aby měli konzistentní sadu vlastností řízených rozložení. Vlastnosti jako <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>, <xref:System.Windows.FrameworkElement.MinWidth%2A>a <xref:System.Windows.FrameworkElement.Margin%2A> (pro pojmenování) poskytují všechny komponenty odvozené od <xref:System.Windows.FrameworkElement> konzistentního chování uvnitř kontejnerů rozložení.  
  
 <xref:System.Windows.FrameworkElement> také nabízí snadnější vystavení rozhraní API pro mnoho funkcí, které se nacházejí v základních vrstvách [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Například <xref:System.Windows.FrameworkElement> poskytuje přímý přístup k animaci prostřednictvím metody <xref:System.Windows.FrameworkElement.BeginStoryboard%2A>. <xref:System.Windows.Media.Animation.Storyboard> poskytuje způsob, jak skriptovat více animací proti sadě vlastností.  
  
 Dvě nejdůležitější věci, které <xref:System.Windows.FrameworkElement> zavádí, jsou datové vazby a styly.  
  
 Podsystém datových vazeb v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] by měl být poměrně obeznámen s kýmkoli, kdo používal [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] nebo ASP.NET k vytvoření [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]aplikace. V každém z těchto systémů existuje jednoduchý způsob, jak vyjádřit, že chcete, aby jedna nebo více vlastností z daného prvku bylo vázáno na určitou část dat. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] má úplnou podporu pro vazby vlastností, transformaci a vazbu seznamu.  
  
 Jednou z nejzajímavějších funkcí datové vazby v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] je zavedení šablon dat. Šablony dat umožňují deklarativní určení způsobu vizuálního zobrazení části dat. Místo vytvoření vlastního uživatelského rozhraní, které může být vázáno na data, můžete místo toho problém vyřešit a nechat data určit zobrazení, které bude vytvořeno.  
  
 Stylování je ve skutečnosti odlehčená forma datové vazby. Pomocí stylů můžete navazovat sadu vlastností ze sdílené definice na jednu nebo více instancí elementu. Styly se aplikují na element buď explicitním odkazem (nastavením vlastnosti <xref:System.Windows.FrameworkElement.Style%2A>), nebo implicitně přidružením stylu k typu CLR elementu.  
  
<a name="System_Windows_Controls_Control"></a>   
## <a name="systemwindowscontrolscontrol"></a>System.Windows.Controls.Control  
 Nejvýznamnější funkcí ovládacího prvku je šablonování. Pokud si myslíte o systému kompozice WPF jako systém vykreslování v zachované podobě, šablonování umožňuje ovládacímu prvku popsat jeho vykreslování v parametrizovaném, deklarativním způsobu. <xref:System.Windows.Controls.ControlTemplate> není nic více než skript pro vytvoření sady podřízených prvků s vazbami na vlastnosti nabízené ovládacím prvkem.  
  
 <xref:System.Windows.Controls.Control> poskytuje sadu základních vlastností, <xref:System.Windows.Controls.Control.Foreground%2A>, <xref:System.Windows.Controls.Control.Background%2A><xref:System.Windows.Controls.Control.Padding%2A>, pro pojmenování několika, které autoři šablon mohou použít k přizpůsobení zobrazení ovládacího prvku. Implementace ovládacího prvku poskytuje model datového modelu a interakce. Model interakce definuje sadu příkazů (například zavřít pro okno) a vazby na vstupní gesta (například kliknutím na červený symbol X v horním rohu okna). Datový model poskytuje sadu vlastností buď k přizpůsobení modelu interakce, nebo přizpůsobení zobrazení (určené šablonou).  
  
 Tento rozdělení mezi datovým modelem (vlastnosti), modelem interakce (příkazy a události) a modelem zobrazení (šablony) umožňuje kompletní přizpůsobení vzhledu a chování ovládacího prvku.  
  
 Běžný aspekt datového modelu ovládacího prvku je model obsahu. Pokud se podíváte na ovládací prvek, jako je <xref:System.Windows.Controls.Button>, uvidíte, že má vlastnost s názvem "obsah" typu <xref:System.Object>. V [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] a ASP.NET by tato vlastnost byla obvykle řetězec – ale omezuje typ obsahu, který lze vložit do tlačítka. Obsah pro tlačítko může být buď jednoduchý řetězec, komplexní datový objekt, nebo celý strom elementu. V případě datového objektu se k sestavení zobrazení použije šablona dat.  
  
<a name="Summary"></a>   
## <a name="summary"></a>Souhrn  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] je navržená tak, aby umožňovala vytvářet dynamické prezentační systémy založené na datech. Každá část systému je navržena tak, aby vytvářela objekty prostřednictvím sad vlastností, které řídí chování jednotky. Datová vazba je základní součástí systému a je integrovaná na všech vrstvách.  
  
 Tradiční aplikace vytvoří zobrazení a pak vytvoří vazby k některým datům. V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]vše o ovládacím prvku, každý aspekt zobrazení, vygeneruje nějaký typ datové vazby. Text, který se nachází uvnitř tlačítka, se zobrazí tak, že se vytvoří složený ovládací prvek uvnitř tlačítka a vazba jeho zobrazení na vlastnost obsahu tlačítka.  
  
 Když začnete vyvíjet aplikace založené na [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], mělo by se velmi seznámit. Můžete nastavit vlastnosti, použít objekty a vytvořit datovou vazby podobným způsobem, jakým můžete použít [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] nebo ASP.NET. Díky hlubšímu šetření architektury [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]zjistíte, že existuje možnost pro vytváření mnohem rozsáhlejších aplikací, které v podstatě považují data za základní ovladač aplikace.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.Visual>
- <xref:System.Windows.UIElement>
- <xref:System.Windows.Input.ICommand>
- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.Threading.DispatcherObject>
- <xref:System.Windows.Input.CommandBinding>
- <xref:System.Windows.Controls.Control>
- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Rozložení](layout.md)
- [Přehled animace](../graphics-multimedia/animation-overview.md)
