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
ms.openlocfilehash: f4a6e6c2a63e58c40e0cca9c67b12d1f65af0d2e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053142"
---
# <a name="wpf-architecture"></a>Architektura WPF
Toto téma obsahuje prohlídku s průvodcem hierarchie tříd Windows Presentation Foundation (WPF). Zabírá většinu hlavních subsystémy [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]a popisuje způsob, jakým interagují. Je také podrobné informace o některých volby provedené architektů [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  

<a name="System_Object"></a>   
## <a name="systemobject"></a>System.Object  
 Primární [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] programovací model je přístupný prostřednictvím spravovaného kódu. Již v rané fázi ve fázi návrhu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] došlo k několika jednáních o kde má být vykreslena spojnice mezi spravované součásti systému a nespravovaných předpon. [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] Nabízí celou řadu funkcí, které usnadňují vývoj, vyšší produktivitu a robustní (včetně správy paměti, zpracování chyb, obecný systém typů, atd.), ale jejich stinnou.  
  
 Hlavní součásti [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] jsou znázorněné na následujícím obrázku. Červené části diagramu (PresentationFramework PresentationCore a milcore) jsou části kódu hlavní [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Pouze jeden z nich je nespravované součásti – milcore. Je Milcore napsanou v nespravovaném kódu, chcete-li povolit úzkou integraci s [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]. Zobrazení v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] se provádí prostřednictvím [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] umožňující efektivní hardwarové a softwarové vykreslování. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] také vyžaduje přesné řízení paměti a spuštění. Kompoziční modul v milcore je velmi výkonné citlivé a požadované ztráty mnoho výhod [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] získáte výkon.  
  
 ![Pozice WPF v rozhraní .NET Framework. ](./media/wpf-architect1.PNG "wpf_architect1")  
  
 Komunikace mezi spravovanými a nespravovanými části [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] je popsána dále v tomto tématu. Zbývající spravované programovací model je popsána níže.  
  
<a name="System_Threading_DispatcherObject"></a>   
## <a name="systemthreadingdispatcherobject"></a>System.Threading.DispatcherObject  
 Většina objektů v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] jsou odvozeny z <xref:System.Windows.Threading.DispatcherObject>, která poskytuje základní konstrukce týkající se souběžnosti a dělení na vlákna. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] je založen na systému zasílání zpráv implementují dispečer. Tento postup funguje stejně jako známé [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] pumpu zpráv; ve skutečnosti [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dispečer User32 zprávy používá k provedení křížového vlákna volání.  
  
 Jsou ve skutečnosti dvě klíčové koncepty diskuse o souběžnosti v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] – spřažení dispečer a vlákna.  
  
 Během fáze návrhu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], cílem bylo přesunutí na jedno vlákno provádění, ale non-thread "spřažené" modelu. Spřažení vláken se stane, když součást identity spuštěné vlákno používá k ukládání nějaký typ stavu. Nejběžnější forma to je používat místní úložiště vláken (TLS) k uložení stavu. Spřažení vláken vyžaduje, aby každé logické vlákno provádění vlastnit pouze jedno fyzické vlákno v operačním systému, který může být náročné na paměť. Nakonec se udržovat synchronizované s existující model vláken User32 jeden jednovláknového spuštění s spřažení vláken modelu vláken pro WPF. Hlavním důvodem byla vzájemná funkční spolupráce – systémů, jako jsou [!INCLUDE[TLA2#tla_ole2.0](../../../../includes/tla2sharptla-ole2-0-md.md)], schránky a prohlížeče Internet Explorer všechny vyžadují jedno vlákno provádění spřažení (STA).  
  
 Vzhledem k tomu, že máte objektů s dělení na vlákna STA, budete potřebovat způsob, jak komunikovat mezi vlákny a ověřit, které jsou na správnému vláknu. Zde je role dispečer. Dispečer je základní zpráva odesílání systému s více frontami seřazený podle priority. Zprávy příklady vstupní neupravená oznámení (myši přesunut), funkce framework (rozložení) nebo uživatelských příkazů (spuštění této metody). Odvozením z <xref:System.Windows.Threading.DispatcherObject>, vytvoříte [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objekt, který má STA chování a bude předán ukazatel dispečerem v okamžiku vytvoření.  
  
<a name="System_Windows_DependencyObject"></a>   
## <a name="systemwindowsdependencyobject"></a>System.Windows.DependencyObject  
 Jeden z primární architektury filozofiemi používaných pro sestavování [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] byl předvolbu pro vlastnosti prostřednictvím metody nebo události. Vlastnosti jsou deklarativní a umožňují vám umožní snadno určit záměr místo akce. Podporováno také modelem řízené nebo data driven, systém pro zobrazení obsah uživatelského rozhraní. Tento přístup měl zamýšlený účinek vytváření více vlastností, které by mohl vytvořit vazbu, aby bylo možné lépe řídit chování aplikace.  
  
 Pokud chcete mít více systému řízené vlastnostmi bohatší vlastnost systému, než co [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] poskytuje bylo potřeba. Jednoduchý příklad tohoto kombinujícím je oznámení o změnách. Chcete-li povolit dva stejně, jako vazby, je nutné obou stranách vazby pro podporu oznámení o změně. Pokud chcete upravit chování vázané na hodnoty vlastností, je potřeba upozorněni při změně hodnoty vlastnosti. Rozhraní Microsoft .NET Framework má rozhraní, **INotifyPropertyChange**, která umožňuje publikovat oznámení o změnách, i když je volitelné.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] poskytuje bohatší systém vlastnost odvozený od <xref:System.Windows.DependencyObject> typu. V systému vlastností je skutečně vlastností systému "závislost" sleduje závislosti mezi vlastnost výrazy a automaticky revalidates hodnoty vlastností při změně závislosti. Například, pokud má-li vlastnost, která dědí (jako je <xref:System.Windows.Controls.Control.FontSize%2A>), systém se automaticky aktualizuje, pokud se změní vlastnost u nadřazené položky, která dědí hodnotu elementu.  
  
 Základem [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] vlastnost systému je Princip výraz vlastnosti. V tomto prvním vydání sady [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], systém výraz vlastností se zavře a výrazů je k dispozici jako součást rozhraní framework. Výrazy jsou proto vlastnost systém nemá vazbu dat, práce se styly, nebo dědičnosti pevný programového, ale místo toho poskytuje vyšší vrstvy v rámci.  
  
 V systému vlastností také poskytuje zhuštěného úložiště hodnot vlastností. Protože objekty může mít jen pár (Pokud není stovky) vlastností a většina z hodnot je ve svém výchozím stavu (zděděné nastavuje styly, atd.), Ne každé instanci objektu musí mít úplnou váhu každé vlastnosti definované v něm.  
  
 Poslední nová funkce v systému vlastností je znalost problematicky připojené vlastnosti. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] prvky jsou postavené na principu složení a opakované použití komponenty. To je často případ, že za některé obsahující element (jako <xref:System.Windows.Controls.Grid> element rozložení) potřebovat další data v podřízených elementů mohla kontrolovat své chování (např. informace o řádek/sloupec). Ne všechny tyto vlastnosti přidružení k každý prvek, libovolný objekt může poskytnout vlastnost definice pro jakýkoli jiný objekt. To se podobá "expando" funkce jazyka JavaScript.  
  
<a name="System_Windows_Media_Visual"></a>   
## <a name="systemwindowsmediavisual"></a>System.Windows.Media.Visual  
 Se systémem definované dalším krokem je stále pixelů na obrazovce. <xref:System.Windows.Media.Visual> Poskytuje třídy pro vytváření strom vizuální objekty, každá volitelně obsahuje pokyny k vykreslení a metadata o tom, jak vykreslit tyto pokyny (oříznutí, transformace, atd.). <xref:System.Windows.Media.Visual> je navržený jako velmi jednoduchý a flexibilní, takže většinu funkcí mít žádné veřejné [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] vystavení a často využívají chráněný zpětného volání funkce.  
  
 <xref:System.Windows.Media.Visual> je vstupním bodem k opravdu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] složení systému. <xref:System.Windows.Media.Visual> bod připojení mezi těmito dvěma podsystémy spravovanou [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] a nespravovaných milcore.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Zobrazí data podle procházení spravuje milcore nespravované datové struktury. Tyto struktury nazývaných složení uzly, které představují hierarchické zobrazení stromu s vykreslování pokynů v každém uzlu. Tento strom znázorněné na obrázku níže, pravé straně přístupný jenom přes protokol zasílání zpráv.  
  
 Při programování [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], vytvoříte <xref:System.Windows.Media.Visual> elementy a odvozené typy, které interně komunikovat s stromové struktuře kompozice přes tento protokol zasílání zpráv. Každý <xref:System.Windows.Media.Visual> v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] můžou vytvořit jednu, žádný nebo několik uzlů složení.  
  
 ![Windows Presentation Foundation vizuálního stromu. ](./media/wpf-architecture2.PNG "wpf_architecture2")  
  
 Je velmi důležité architektury podrobností a Všimněte si zde – celý strom vizuály a vykreslování pokynů se uloží do mezipaměti. V podmínkách grafiky [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] využívá uchovanou vykreslování systém. To umožňuje systému repaint na vysokou obnovovací frekvence bez systému složení blokování na zpětná volání do uživatelského kódu. To pomáhá zabránit vzhledu aplikace reagovat.  
  
 Další důležité podrobnosti, který není ve skutečnosti patrné v diagramu je, jak systém ve skutečnosti provádí složení.  
  
 V User32 a [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)], že systém funguje v systému výstřižek přímý režim. Když součásti nutné k vykreslení, systém určí výstřižek hranice mimo které komponenta není povolena na dotyk pixely a pak je komponenta dotaz má Vymalovat pixelů do pole. Tento systém se velice dobře funguje v systémech omezené pamětí vzhledem k tomu, že když se něco změní máte jenom touch ovlivněné komponenty – žádné dvě součásti nikdy přispět k barva jeden pixel.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] používá "malířův algoritmus" Malování modelu. To znamená, že místo oříznutí jednotlivé komponenty, jednotlivých komponent se zobrazí výzva k vykreslení ze zadní do popředí zobrazení. Díky tomu má Vymalovat za předchozí komponenty zobrazení jednotlivých komponent. Výhodou tohoto modelu je, že můžete mít složité a částečně transparentní obrazce. Tento model s dnešní moderní grafický hardware, je poměrně rychlé (který není tento případ při User32 / [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] byly vytvořeny).  
  
 Jak už bylo zmíněno dříve, core filozofie z [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] je přesunout do více deklarativní model "vlastnost na střed" programování. V systému visual tím se zobrazí za pár zajímavých míst.  
  
 První, pokud si myslíte o grafické systému uchovanou režimu, to je ve skutečnosti přesun směrem od imperativní DrawLine/DrawLine typ modelu, do datového modelu orientovaného – (nový řádek) / nová Line(). Tento krok k vykreslení na základě dat umožňuje složité operace na vykreslování pokynů vyjádřit pomocí vlastnosti. Typy odvozené od <xref:System.Windows.Media.Drawing> se prakticky objektový model pro vykreslování.  
  
 Za druhé Pokud při hodnocení systému animace, uvidíte, že je téměř zcela deklarativní. Nemusíte mít pro vývojáře k výpočtu dalšího umístění nebo další barvu, můžete vyjádřit animace jako sadu vlastností pro objekt animace. Tyto animace budete pak můžete vyjádřit záměr vývojář nebo Návrhář (přesunout toto tlačítko z tohoto místa během 5 sekund), a systém může určit nejefektivnější postup provést tuto akci.  
  
<a name="System_Windows_UIElement"></a>   
## <a name="systemwindowsuielement"></a>System.Windows.UIElement  
 <xref:System.Windows.UIElement> definuje základní subsystémy, včetně rozložení, vstupu a události.  
  
 Rozložení je základní koncept v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. V řadě systémů je buď fixní sadu modely rozložení (HTML podporuje tři modely pro rozložení, tok, absolutní a tabulky) nebo žádný model pro rozložení (User32 ve skutečnosti pouze podporuje absolutní umístění). [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] spuštění za předpokladu, že vývojářům a návrhářům chtěla model flexibilní a rozšiřitelné rozložení, který by mohl být řízena hodnoty vlastností, nikoli imperativní logikou. Na <xref:System.Windows.UIElement> úrovně, se používá základní kontrakt pro rozložení – dvě fáze model s využitím <xref:System.Windows.UIElement.Measure%2A> a <xref:System.Windows.UIElement.Arrange%2A> předá.  
  
 <xref:System.Windows.UIElement.Measure%2A> umožňuje komponentě, chcete-li určit, kolik velikost je vhodné provést. Toto je samostatné fáze z <xref:System.Windows.UIElement.Arrange%2A> vzhledem k tomu, že existuje mnoho situací, ve kterém nadřazený element požádá podřízené k měření několikrát, chcete-li zjistit jeho optimální umístění a velikost. Skutečnost, že nadřazené elementy požádejte podřízených elementů k měření ukazuje další klíče filozofií [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] – velikost obsahu. Všechny ovládací prvky v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] možnost Upravit velikost fyzické velikosti svého obsahu. Jednodušší lokalizace a umožňuje dynamické rozložení prvků při velikosti věci. <xref:System.Windows.UIElement.Arrange%2A> Fáze umožňuje nadřazené umístění a určit konečné velikosti jednotlivých podřízených.  
  
 Velké množství času se často neztrácí mluvit o výstupu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] – <xref:System.Windows.Media.Visual> a souvisejících objektů. Je ale obrovské množství inovace na vstupní straně. Pravděpodobně nejdůležitější změny ve vstupním modelu pro [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] je konzistentní model, podle kterého se události vstupu směrují prostřednictvím systému.  
  
 Vstup pochází jako signál na ovladač zařízení režimu jádra a směrování do správné procesu a vlákně komplikované procesem zahrnující jádra Windows a User32. Jakmile User32 zpráva odpovídající vstupní směrována na [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], je převeden na [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] nezpracovaná vstupní zprávy a odeslaných dispečeru. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Umožňuje nezpracovaných událostí vstupu pro převod na více skutečných událostí, povolení funkce, jako je "MouseEnter" k implementaci na nízké úrovni systému s garantované doručení.  
  
 Každá událost vstupu je převedena na alespoň dvě události – "náhled" události a skutečné události. Všechny události v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] mají pojmu směrování přes stromem prvků. Události se říká, že "vyvolat" dojde k jejich přechod z cílové směrem nahoru do kořenového adresáře a jsou označeny jako "tunelu" dojde k jejich spuštění v kořenovém adresáři a přechod na cíl. Zadejte tunelové propojení událostí ve verzi preview, povoluje libovolný element ve stromové struktuře příležitost k filtrování nebo provádět akce na události. Běžné události (jinak než ve verzi preview) pak bublinový z cíle až po kořen.  
  
 Toto rozdělení tunelového propojení a bubliny fáze díky implementaci funkcí, jako jsou klávesové zkratky fungují v konzistentním způsobem složené světě. V User32 by implementovat klávesové zkratky tím, že jeden globální tabulku obsahující všechny akcelerátory, které jste chtěli podporu (Ctrl + N mapování "New"). Dispečerem pro vaše aplikace volat **TranslateAccelerator** který by vstupní zprávy v User32, sledovat a určit, pokud žádný odpovídající registrované akcelerátoru. V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] to nebude fungovat, protože systém je plně "sestavitelný" – libovolný prvek může zpracovat a použít všechny klávesové zkratky. Tento model dvě fáze pro vstup umožňuje součásti k implementaci vlastních "TranslateAccelerator".  
  
 Tento krok provádět další, <xref:System.Windows.UIElement> také zavádí pojem CommandBindings. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Příkaz systému umožňuje vývojářům definovat funkci z hlediska koncového bodu příkaz – něco tohoto implementuje <xref:System.Windows.Input.ICommand>. Příkaz vazby umožňují prvek, který chcete definovat mapování mezi vstupní gest (Ctrl + N) a příkaz (Nový). Vstupní gesta i definice příkazu jsou rozšiřitelné a může být přes drátové sítě společně v době použití. Díky tomu je jednoduché, například povolit koncovým uživatelům přizpůsobení klávesové zkratky, které chcete použít v rámci aplikace.  
  
 K tomuto bodu v tématu "základní" funkce z [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] – funkce implementované v sestavení PresentationCore byly fokus. Při sestavování [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], vyčistit oddělení mezi základními částmi (jako jsou smlouvy pro rozložení s **míru** a **uspořádat**) a framework (například provádění konkrétní rozložení, jako je <xref:System.Windows.Controls.Grid>) byl požadovaného výsledku. Cílem bylo poskytovat potřebné bodu rozšiřitelnosti nízké v zásobníku, která by umožňovala externí mohou vývojáři vytvářet vlastní rozhraní, pokud.  
  
<a name="System_Windows_FrameworkElement"></a>   
## <a name="systemwindowsframeworkelement"></a>System.Windows.FrameworkElement  
 <xref:System.Windows.FrameworkElement> Můžete se podívali na dvěma různými způsoby. Představuje sadu zásad a vlastní nastavení na subsystémy zavedené v nižších vrstvách [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Zavádí také sadu nových subsystémů.  
  
 Primární zavedené zásady <xref:System.Windows.FrameworkElement> spočívá v rozložení aplikace. <xref:System.Windows.FrameworkElement> navazuje na rozložení základní kontrakt zavedené <xref:System.Windows.UIElement> a přidá rozeznávání rozložení slotu"", které usnadňují autorům rozložení mají konzistentní sadu vlastností řízené sémantiku rozložení. Vlastnosti, jako je <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>, <xref:System.Windows.FrameworkElement.MinWidth%2A>, a <xref:System.Windows.FrameworkElement.Margin%2A> (to jsou některé) poskytují všechny součásti odvozený od <xref:System.Windows.FrameworkElement> konzistentní chování uvnitř kontejnerů rozložení.  
  
 <xref:System.Windows.FrameworkElement> poskytuje také snazší [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] vystavení mnoho funkcí najít v jednotlivých vrstvách core [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Například <xref:System.Windows.FrameworkElement> poskytuje přímý přístup k animace prostřednictvím <xref:System.Windows.FrameworkElement.BeginStoryboard%2A> metody. A <xref:System.Windows.Media.Animation.Storyboard> poskytuje způsob, jak skriptu animací několik proti sadu vlastností.  
  
 Dvě nejdůležitější věci, které <xref:System.Windows.FrameworkElement> zavádí se styly a datové vazby.  
  
 Subsystém vazby dat v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] by měl být poměrně znát všichni, někdy, který je používán [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] nebo [!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)] pro vytváření aplikací [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. V každém z těchto systémů je jednoduchý způsob, jak express, který má jednu nebo více vlastností z daného elementu jako vázaný na část dat. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] obsahuje plnou podporu pro vytvoření vazby pro vlastnost, transformaci a seznam vazby.  
  
 Jednou z nejzajímavějších funkcí datové vazby v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] je zavedení datové šablony. Datové šablony umožňují deklarativně specifikovat, jak by měl být část dat vizualizovat. Místo vytváření vlastního uživatelského rozhraní, které může být vázaný na data, můžete místo toho otočení problém a nechte data určit zobrazení, která bude vytvořena.  
  
 Používání stylů pro je opravdu jednoduchý formulář datovou vazbu. Pomocí stylu, které lze svázat sadu vlastností ze sdílené definice jednu nebo víc instancí elementu. Styly získat použitá pro element buď explicitní odkaz (nastavením <xref:System.Windows.FrameworkElement.Style%2A> vlastnost) nebo implicitně tím, že přidružíte style, jehož [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] typ elementu.  
  
<a name="System_Windows_Controls_Control"></a>   
## <a name="systemwindowscontrolscontrol"></a>System.Windows.Controls.Control  
 Nejdůležitější funkce ovládacího prvku je šablon. Pokud si myslíte o systému pro WPF složení jako systém uchovanou režimu vykreslování, umožňuje šablonování ovládacího prvku k podrobnému popisu, jeho vykreslení parametrizované, deklarativní způsobem. A <xref:System.Windows.Controls.ControlTemplate> není ve skutečnosti nic jiného než skript k vytvoření sady podřízených elementů pomocí vazby na vlastnosti, které ovládací prvek.  
  
 <xref:System.Windows.Controls.Control> poskytuje sadu uložených vlastností <xref:System.Windows.Controls.Control.Foreground%2A>, <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Padding%2A>, další, které autoři šablony potom můžete použít k přizpůsobení zobrazení typu ovládacího prvku. Implementace ovládacího prvku poskytuje datový model a model interakce. Model interakce definuje sadu příkazů (např. Zavřete okna) a vazby vstup gesta (např. když kliknete na červené X v horním rohu okna). Datový model obsahuje sadu vlastností, které mají upravit interakce model nebo přizpůsobit zobrazení (určené šabloně).  
  
 Toto rozdělení mezi datového modelu (Vlastnosti), model interakce (příkazů a událostí) a zobrazení modelu (šablony) umožní kompletně si přizpůsobit vzhled a chování ovládacího prvku.  
  
 Běžné aspekt datový model ovládacích prvků je model obsahu. Když se podíváte na ovládací prvek, jako jsou <xref:System.Windows.Controls.Button>, uvidíte, že má vlastnost s názvem "Obsah" typu <xref:System.Object>. V [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] a [!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)], tato vlastnost by obvykle řetězec – ale typ obsahu, která omezuje můžete umístit tlačítku. Obsah pro tlačítko může být buď jednoduchým řetězcem, komplexní datového objektu nebo celý stromu. V případě datový objekt šablony slouží k vytvoření zobrazení.  
  
<a name="Summary"></a>   
## <a name="summary"></a>Souhrn  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] slouží k tomu, abyste k vytvoření dynamické, prezentace systémů řízených daty. Každé části systému slouží k vytváření objektů prostřednictvím sady vlastností, daná chování jednotky. Datová vazba je základní součástí systému a je integrována v každé vrstvě.  
  
 Tradiční aplikace vytvořit zobrazení a pak vytvořit vazbu k některým datům. V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], všechno, co o řízení všech aspektů zobrazení je generován nějaký typ datové vazby. Vytvoření složeného ovládacího prvku uvnitř na tlačítko a jeho zobrazení vytvoření vazby na vlastnost obsahu na tlačítko se zobrazí text prvku tlačítko Najít.  
  
 Když začnete vyvíjet [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] na základě aplikací, by měl mít pocit povědomý. Můžete nastavit vlastnosti, používat objekty, a vytvořit datovou vazbu s: téměř stejným způsobem můžete pomocí [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] nebo [!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)]. Pomocí hlubší šetření architektuře [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], zjistíte, že existuje možnost vytváření mnohem bohatší aplikací, které jsou v podstatě zacházet s daty jako základní ovladač aplikace.  
  
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
