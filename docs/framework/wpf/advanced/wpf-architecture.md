---
title: Architektura
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
ms.openlocfilehash: b16be8470a47f3e8e362feb0b13e10aa901baacb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187123"
---
# <a name="wpf-architecture"></a>Architektura WPF
Toto téma obsahuje prohlídku hierarchie tříd YPF (Windows Presentation Foundation). Pokrývá většinu hlavních subsystémů WPF a popisuje, jak interagují. Rovněž podrobně popisuje některá rozhodnutí učiněná architekty WPF.  

<a name="System_Object"></a>
## <a name="systemobject"></a>System.Object  
 Primární wpf programovací model je vystaven prostřednictvím spravovaného kódu. V rané fázi návrhu WPF se diskutovalo o tom, kde by měla být čára mezi spravovanými součástmi systému a neřízenými součástmi. CLR poskytuje řadu funkcí, které činí vývoj produktivnější a robustnější (včetně správy paměti, zpracování chyb, systému běžného typu atd.), ale jejich náklady.  
  
 Hlavní složky WPF jsou znázorněny na obrázku níže. Červené části diagramu (PresentationFramework, PresentationCore a milcore) jsou hlavní části kódu WPF. Z nich pouze jedna je neřízená součást - milcore. Milcore je napsán v nespravovaném kódu, aby bylo možné úzce integrace s DirectX. Všechny displeje ve WPF se provádějí pomocí modulu DirectX, což umožňuje efektivní vykreslování hardwaru a softwaru. WPF také vyžaduje jemnou kontrolu nad pamětí a spuštění. Kompozice motoru v milcore je velmi citlivý na výkon, a vyžaduje vzdát se mnoha výhod CLR získat výkon.  
  
 ![Pozice WPF v rámci .NET Framework.](./media/wpf-architect1.PNG "wpf_architect1")  
  
 Komunikace mezi spravované a nespravované části WPF je popsána dále v tomto tématu. Zbývající část spravovaného programovacího modelu je popsána níže.  
  
<a name="System_Threading_DispatcherObject"></a>
## <a name="systemthreadingdispatcherobject"></a>System.Threading.DispatcherObject  
 Většina objektů v <xref:System.Windows.Threading.DispatcherObject>WPF odvozuje od , který poskytuje základní konstrukce pro práci s souběžnosti a zřetězení. WPF je založen na systému zasílání zpráv implementovaném dispečerem. To funguje podobně jako známé Win32 zpráva čerpadlo; ve skutečnosti WPF dispečer používá User32 zprávy pro provádění volání mezi vlákny.  
  
 Existují opravdu dva základní koncepty pochopit při diskusi souběžnosti v WPF – dispečer a vlákno spřažení.  
  
 Během fáze návrhu WPF bylo cílem přesunout se do jednoho vlákna provádění, ale model bez podprocesu "spřažené". Spřažení vláken se stane, když komponenta používá identitu vykonávajícího vlákna k uložení určitého typu stavu. Nejběžnější formou je použití místního úložiště vlákna (TLS) k uložení stavu. Spřažení vláken vyžaduje, aby každé logické vlákno spuštění bylo vlastněno pouze jedním fyzickým vláknem v operačním systému, které může být náročné na paměť. Nakonec wpf model zřetězení byl udržován v synchronizaci s existující montovny User32 modelu s jedním podprocesem spuštění s spřažení vláken. Hlavním důvodem byla interoperabilita – systémy jako OLE 2.0, schránka a aplikace Internet Explorer vyžadují spuštění spřažení jednoho vlákna (STA).  
  
 Vzhledem k tomu, že máte objekty s STA zřetězení, potřebujete způsob, jak komunikovat mezi vlákny a ověřit, že jste ve správném vlákně. V tom spočívá role dispečera. Dispečer je základní systém dispečinku zpráv s více prioritními frontami. Příklady zpráv zahrnují nezpracovaná vstupní oznámení (přesunutí myši), rámcové funkce (rozložení) nebo uživatelské příkazy (spusťte tuto metodu). Odvozením z <xref:System.Windows.Threading.DispatcherObject>, vytvoříte objekt CLR, který má chování STA a bude mít ukazatel na dispečera v době vytvoření.  
  
<a name="System_Windows_DependencyObject"></a>
## <a name="systemwindowsdependencyobject"></a>System.Windows.DependencyObject  
 Jednou z primárních architektonických filozofií používaných při vytváření WPF bylo upřednostňování vlastností před metodami nebo událostmi. Vlastnosti jsou deklarativní a umožňují snadněji určit záměr namísto akce. To také podporovalo modelřízený nebo řízený data, systém pro zobrazení obsahu uživatelského rozhraní. Tato filozofie měla zamýšlený účinek vytváření více vlastností, které můžete vázat, aby bylo možné lépe řídit chování aplikace.  
  
 Aby bylo možné mít více systému řízenévlastnosti, bohatší vlastnost systému, než co poskytuje CLR bylo zapotřebí. Jednoduchým příkladem tohoto bohatství je změna oznámení. Chcete-li povolit obousměrnou vazbu, potřebujete obě strany vazby pro podporu oznámení o změně. Chcete-li mít chování vázané na hodnoty vlastností, musíte být upozorněni, když se změní hodnota vlastnosti. Rozhraní Microsoft .NET Framework má rozhraní **INotifyPropertyChange**, které umožňuje objektu publikovat oznámení o změnách, ale je volitelné.  
  
 WPF poskytuje bohatší vlastnostsystém, odvozený od <xref:System.Windows.DependencyObject> typu. Systém vlastností je skutečně systém vlastností "závislostí" v tom, že sleduje závislosti mezi výrazy vlastností a automaticky znovu ověří hodnoty vlastností při změně závislostí. Například pokud máte vlastnost, která dědí (jako <xref:System.Windows.Controls.Control.FontSize%2A>) systém se automaticky aktualizuje, pokud se změní vlastnost na nadřazený prvek, který dědí hodnotu.  
  
 Základem systému vlastností WPF je koncept výrazu vlastnosti. V této první verzi WPF je uzavřen systém výrazu vlastností a všechny výrazy jsou k dispozici jako součást rámce. Výrazy jsou důvod, proč systém vlastností nemá pevně zakódované datové vazby, styly nebo dědičnost, ale spíše je poskytuje novější vrstvy v rámci.  
  
 Systém vlastností také zajišťuje řídké ukládání hodnot vlastností. Vzhledem k tomu, že objekty mohou mít desítky (ne-li stovky) vlastností a většina hodnot je ve výchozím stavu (zděděné, nastavené styly atd.), nemusí mít každá instance objektu plnou váhu každé vlastnosti definované na něm.  
  
 Poslední novinkou systému vlastností je pojem připojených vlastností. WPF prvky jsou postaveny na principu složení a opětovné použití komponent. Často se stává, že některé obsahující <xref:System.Windows.Controls.Grid> prvek (jako prvek rozložení) potřebuje další data na podřízené prvky řídit jeho chování (jako řádek/ sloupec informace). Namísto připojování všech těchto vlastností s každým elementem je každému objektu povoleno poskytovat definice vlastností pro jakýkoli jiný objekt. To je podobné "expando" funkce JavaScriptu.  
  
<a name="System_Windows_Media_Visual"></a>
## <a name="systemwindowsmediavisual"></a>System.Windows.Media.Visual  
 S definovaným systémem je dalším krokem získání pixelů nakreslených na obrazovku. Třída <xref:System.Windows.Media.Visual> poskytuje vytváření stromu vizuálních objektů, z nichž každý volitelně obsahuje pokyny k výkresu a metadata o tom, jak tyto pokyny (oříznutí, transformace atd.). <xref:System.Windows.Media.Visual>je navržen tak, aby byl extrémně lehký a flexibilní, takže většina funkcí nemá žádnou public API a silně se spoléhá na chráněné funkce zpětného volání.  
  
 <xref:System.Windows.Media.Visual>je skutečně vstupním bodem do systému složení WPF. <xref:System.Windows.Media.Visual>je bod připojení mezi těmito dvěma subsystémy, spravované rozhraní API a nespravované milcore.  
  
 WPF zobrazuje data procházením nespravovaných datových struktur spravovaných milcore. Tyto struktury, nazývané uzly kompozice, představují hierarchický strom zobrazení s pokyny k vykreslování v každém uzlu. Tento strom, ilustrovaný na pravé straně obrázku níže, je přístupný pouze prostřednictvím protokolu zasílání zpráv.  
  
 Při programování WPF <xref:System.Windows.Media.Visual> vytvoříte prvky a odvozené typy, které interně komunikují se stromem kompozice prostřednictvím tohoto protokolu zasílání zpráv. Každý <xref:System.Windows.Media.Visual> v WPF může vytvořit jeden, žádný nebo několik uzlů složení.  
  
 ![Vizuální strom Windows Presentation Foundation.](./media/wpf-architecture2.PNG "wpf_architecture2")  
  
 Tam je velmi důležitý architektonický detail si všimnout zde - celý strom vizuálů a kreslení pokyny je uložen do mezipaměti. Z grafického hlediska WPF používá zachovaný vykreslovací systém. To umožňuje systému překreslit při vysokých obnovovacích frekvencích bez blokování kompozičního systému na zpětná volání uživatelského kódu. To pomáhá zabránit výskytu nereagující aplikace.  
  
 Dalším důležitým detailem, který není v diagramu skutečně patrný, je, jak systém skutečně provádí složení.  
  
 V User32 a GDI, systém pracuje na okamžitém režimu ořezávací systém. Když je potřeba komponentu vykreslit, systém vytvoří hranice oříznutí, mimo které se součást nesmí dotýkat obrazových bodů, a pak je komponenta vyzvána k malování obrazových bodů v tomto poli. Tento systém funguje velmi dobře v paměťových omezených systémech, protože když se něco změní, stačí se dotknout postižené součásti - žádné dvě součásti nikdy nepřispívají k barvě jednoho pixelu.  
  
 WPF používá model malby "malířův algoritmus". To znamená, že místo oříznutí každé součásti je každá komponenta vyzvána k vykreslení ze zadní strany na přední stranu displeje. To umožňuje, aby každá komponenta přemalovala zobrazení předchozí součásti. Výhodou tohoto modelu je, že můžete mít složité, částečně průhledné tvary. S dnešním moderním grafickým hardwarem je tento model poměrně rychlý (což nebyl případ, kdy byly vytvořeny User32 / GDI).  
  
 Jak již bylo zmíněno dříve, základní filozofií WPF je přejít na více deklarativní, "vlastnosti" model programování. Ve vizuálním systému se to objeví na několika zajímavých místech.  
  
 Za prvé, pokud si myslíte o zachovaném režimu grafického systému, je to opravdu odklon od imperativní DrawLine / DrawLine typ modelu, na data orientovaný model - nový Line()/new Line(). Tento přechod na vykreslování řízené daty umožňuje vyjádřit složité operace v pokynech k výkresu pomocí vlastností. Typy odvozené z <xref:System.Windows.Media.Drawing> jsou účinně objektový model pro vykreslování.  
  
 Za druhé, pokud vyhodnotíte animační systém, uvidíte, že je téměř zcela deklarativní. Namísto vyžadování vývojáře vypočítat další umístění nebo další barvu, můžete vyjádřit animace jako sadu vlastností na objekt animace. Tyto animace pak můžete vyjádřit záměr vývojáře nebo návrháře (přesunout toto tlačítko odtud tam za 5 sekund) a systém může určit nejúčinnější způsob, jak toho dosáhnout.  
  
<a name="System_Windows_UIElement"></a>
## <a name="systemwindowsuielement"></a>System.Windows.UIElement  
 <xref:System.Windows.UIElement>definuje základní subsystémy včetně rozložení, vstupu a událostí.  
  
 Layout je základní koncept wpf. V mnoha systémech je buď pevná sada modelů rozložení (HTML podporuje tři modely pro rozvržení; tok, absolutní a tabulky) nebo žádný model pro rozvržení (Uživatel32 opravdu podporuje pouze absolutní umístění). WPF začal s předpokladem, že vývojáři a návrháři chtěli flexibilní, rozšiřitelný model rozložení, který by mohl být řízen hodnotami vlastností spíše než imperativní logikou. Na <xref:System.Windows.UIElement> úrovni je zavedena základní smlouva o rozvržení <xref:System.Windows.UIElement.Measure%2A> <xref:System.Windows.UIElement.Arrange%2A> – dvoufázový model s a projde.  
  
 <xref:System.Windows.UIElement.Measure%2A>umožňuje komponentě určit, jakou velikost by chtěla mít. Toto je samostatná fáze od, <xref:System.Windows.UIElement.Arrange%2A> protože existuje mnoho situací, kdy nadřazený prvek požádá dítě, aby několikrát změřilo, aby určilo jeho optimální polohu a velikost. Skutečnost, že nadřazené prvky požádat podřízené prvky k měření demonstruje další klíčovou filozofii WPF – velikost obsahu. Všechny ovládací prvky v WPF podporují možnost velikosti na přirozenou velikost jejich obsahu. To usnadňuje lokalizaci a umožňuje dynamické rozložení prvků při změně velikosti. Fáze <xref:System.Windows.UIElement.Arrange%2A> umožňuje rodiči umístit a určit konečnou velikost každého dítěte.  
  
 Mnoho času je často strávil mluvit o výstupní <xref:System.Windows.Media.Visual> straně WPF - a související objekty. Nicméně tam je obrovské množství inovací na vstupní straně stejně. Pravděpodobně nejzásadnější změnou vstupního modelu pro WPF je konzistentní model, podle kterého jsou vstupní události směrovány systémem.  
  
 Vstup pochází jako signál na ovladači zařízení režimu jádra a dostane směrovány do správného procesu a vlákna prostřednictvím složitého procesu zahrnující jádro systému Windows a User32. Jakmile user32 zpráva odpovídající vstupu je směrována na WPF, je převeden na WPF nezpracované vstupní zprávy a odeslány dispečer. WPF umožňuje nezpracované vstupní události, které mají být převedeny na více skutečných událostí, povolení funkce jako "MouseEnter" mají být implementovány na nízké úrovni systému se zaručeným doručením.  
  
 Každá vstupní událost je převedena alespoň na dvě události – událost "náhled" a skutečná událost. Všechny události v WPF mají pojem směrování prostřednictvím stromu elementu. Události jsou řekl, aby "bublina", pokud se procházet z cíle do stromu ke kořeni, a jsou řekl, aby "tunel", pokud začínají na kořen a přejít dolů k cíli. Vstupní náhled událostí tunelového propojení, povolení libovolný prvek ve stromu příležitost filtrovat nebo provést akci na události. Pravidelné (non-preview) události pak bublina od cíle až do kořene.  
  
 Toto rozdělení mezi tunelovou a bublinovou fázi umožňuje, aby implementace funkcí, jako jsou akcelerátory klávesnice, fungovala konzistentním způsobem ve složeném světě. V User32 byste implementovat akcelerátory klávesnice tím, že má jednu globální tabulku obsahující všechny akcelerátory, které chcete podporovat (Ctrl+ N mapování na "Nový"). V dispečer pro vaši aplikaci byste volat **TranslateAccelerator,** který by sniff vstupní zprávy v User32 a zjistit, zda všechny uzavřeno registrovaný akcelerátor. V WPF by to nefungovalo, protože systém je plně "kompozitelný" - každý prvek zvládne a používá jakýkoli klávesový akcelerátor. S tímto dvoufázový model pro vstup umožňuje komponenty implementovat vlastní "TranslateAccelerator".  
  
 Chcete-li tento krok <xref:System.Windows.UIElement> dále, také zavádí pojem CommandBindings. Příkazový systém WPF umožňuje vývojářům definovat funkce z hlediska koncového <xref:System.Windows.Input.ICommand>bodu příkazu – něco, co implementuje . Vazby příkazů umožňují elementu definovat mapování mezi vstupním gestem (Ctrl+N) a příkazem (Nový). Vstupní gesta a definice příkazů jsou rozšiřitelné a mohou být propojeny v době použití. Díky tomu je triviální, například umožnit koncovému uživateli přizpůsobit vazby klíčů, které chtějí použít v rámci aplikace.  
  
 K tomuto bodu v tématu, "jádro" funkce WPF – funkce implementované v sestavení PresentationCore, byly zaměření. Při vytváření WPF, čisté oddělení mezi základní kusy (jako je smlouva o rozvržení s opatření <xref:System.Windows.Controls.Grid> **a** **uspořádat)** a rámcové kusy (jako je implementace konkrétního rozložení, jako je) byl požadovaný výsledek. Cílem bylo poskytnout bod rozšiřitelnosti nízko v zásobníku, který by umožnil externím vývojářům v případě potřeby vytvořit vlastní architektury.  
  
<a name="System_Windows_FrameworkElement"></a>
## <a name="systemwindowsframeworkelement"></a>System.Windows.FrameworkElement  
 <xref:System.Windows.FrameworkElement>lze na ně pohlížet dvěma různými způsoby. Zavádí sadu zásad a přizpůsobení v subsystémech zavedených v nižších vrstvách WPF. Zavádí také sadu nových subsystémů.  
  
 Primární zásady <xref:System.Windows.FrameworkElement> zavedené je kolem rozložení aplikace. <xref:System.Windows.FrameworkElement>navazuje na základní layout smlouvy <xref:System.Windows.UIElement> zavedené a přidává pojem rozložení "slot", který usnadňuje pro autory rozložení mít konzistentní sadu vlastnosti řízené rozložení sémantiku. Vlastnosti <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>jako <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.Margin%2A> , a (abychom jmenovali několik) poskytují všechny součásti odvozené z <xref:System.Windows.FrameworkElement> konzistentního chování uvnitř kontejnerů rozložení.  
  
 <xref:System.Windows.FrameworkElement>také poskytuje snadnější api expozice mnoha funkcí matné vrstvy WPF. Například <xref:System.Windows.FrameworkElement> poskytuje přímý přístup k <xref:System.Windows.FrameworkElement.BeginStoryboard%2A> animaci prostřednictvím metody. A <xref:System.Windows.Media.Animation.Storyboard> poskytuje způsob, jak skript více animací proti sadu vlastností.  
  
 Dvě nejdůležitější věci, <xref:System.Windows.FrameworkElement> které zavádí jsou datové vazby a styly.  
  
 Podsystém datové vazby ve WPF by měl být poměrně známý každému, kdo použil formuláře systému Windows nebo ASP.NET pro vytvoření aplikace [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. V každém z těchto systémů existuje jednoduchý způsob, jak vyjádřit, že chcete, aby jedna nebo více vlastností z daného prvku byla vázána na část dat. WPF má plnou podporu pro vazby vlastností, transformace a seznam vazby.  
  
 Jednou z nejzajímavějších vlastností datové vazby ve WPF je zavedení datových šablon. Šablony dat umožňují deklarativně určit, jak by měla být část dat vizualizována. Namísto vytváření vlastního uživatelského rozhraní, které může být vázáno na data, můžete problém místo toho otočit a nechat data určit zobrazení, které bude vytvořeno.  
  
 Styling je opravdu lehká forma datové vazby. Pomocí stylu můžete svázat sadu vlastností ze sdílené definice s jednou nebo více instancemi prvku. Styly získat použít na prvek buď explicitní <xref:System.Windows.FrameworkElement.Style%2A> odkaz (nastavením vlastnosti) nebo implicitně přisunutím styl s typem CLR prvku.  
  
<a name="System_Windows_Controls_Control"></a>
## <a name="systemwindowscontrolscontrol"></a>System.Windows.Controls.Control  
 Nejdůležitější funkcí ovládacího prvku je šablonování. Pokud si myslíte o wpf složení systému jako systém uchování režimu vykreslování, šablonování umožňuje ovládací prvek popsat jeho vykreslování parametrizovaným, deklarativním způsobem. A <xref:System.Windows.Controls.ControlTemplate> je opravdu nic víc než skript k vytvoření sadu podřízených prvků, s vazby na vlastnosti, které nabízí ovládací prvek.  
  
 <xref:System.Windows.Controls.Control>Poskytuje sadu vlastností <xref:System.Windows.Controls.Control.Foreground%2A>zásob <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Control.Padding%2A>, , abychom jmenovali několik, které autoři šablony pak mohou použít k přizpůsobení zobrazení ovládacího prvku. Implementace ovládacího prvku poskytuje datový model a model interakce. Model interakce definuje sadu příkazů (například Zavřít pro okno) a vazby na vstupní gesta (jako je klepnutí na červený Kříže v horním rohu okna). Datový model poskytuje sadu vlastností pro přizpůsobení modelu interakce nebo přizpůsobení zobrazení (určeno šablonou).  
  
 Toto rozdělení mezi datový model (vlastnosti), model interakce (příkazy a události) a model zobrazení (šablony) umožňuje úplné přizpůsobení vzhledu a chování ovládacího prvku.  
  
 Společným aspektem datového modelu ovládacích prvků je model obsahu. Pokud se podíváte <xref:System.Windows.Controls.Button>na ovládací prvek jako , uvidíte, že <xref:System.Object>má vlastnost s názvem "Obsah" typu . Ve formulářích Windows a ASP.NET by tato vlastnost obvykle byla řetězcem , který však omezuje typ obsahu, který můžete umístit do tlačítka. Obsah tlačítka může být jednoduchý řetězec, komplexní datový objekt nebo celý strom prvků. V případě datového objektu se šablona dat používá k vytvoření zobrazení.  
  
<a name="Summary"></a>
## <a name="summary"></a>Souhrn  
 WPF je navržen tak, aby vám umožnil vytvářet dynamické prezentační systémy založené na datech. Každá část systému je navržena tak, aby vytvářela objekty prostřednictvím sad vlastností, které řídí chování. Datová vazba je základní součástí systému a je integrována v každé vrstvě.  
  
 Tradiční aplikace vytvoří zobrazení a pak se svážou na některá data. V WPF je vše o ovládacím prvku, každý aspekt zobrazení, generován nějakým typem datové vazby. Text nalezený uvnitř tlačítka se zobrazí vytvořením složeného ovládacího prvku uvnitř tlačítka a vazbou jeho zobrazení na vlastnost obsahu tlačítka.  
  
 Když začnete vyvíjet aplikace založené na WPF, měl by se cítit velmi povědomě. Vlastnosti, použití objektů a vazbu dat můžete nastavit v podstatě stejným způsobem jako pomocí formulářů Windows nebo ASP.NET. S hlubší zkoumání architektury WPF, zjistíte, že existuje možnost pro vytváření mnohem bohatší aplikace, které zásadně zacházet s daty jako základní ovladač aplikace.  
  
## <a name="see-also"></a>Viz také

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
