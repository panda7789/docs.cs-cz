---
title: Architektura WPF
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
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 29c8e2d632c37a299389b1bdc7f3f19f7df2f7e7
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="wpf-architecture"></a>Architektura WPF
Toto téma obsahuje Průvodce hierarchie tříd Windows Presentation Foundation (WPF). Pokrývá většinu hlavní dílčích systémů [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]a popisuje způsob, jakým interagují. Také podrobnosti některé z těchto možností provedené architekty z [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)].  
  
  
<a name="System_Object"></a>   
## <a name="systemobject"></a>System.Object  
 Primární [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] programovací model je k dispozici prostřednictvím spravovaného kódu. Na začátku ve fázi návrhu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] došlo k několika jednáních, o kterých mají být vykresleny řádku až nespravované těm, které jsou součástí správy systému. [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] Poskytuje celou řadu funkcí, které usnadňují vývoj zvýšit produktivitu a robustní (včetně správy paměti, zpracování chyb, obecný systém typů atd.), ale začne s náklady.  
  
 Hlavní součástí [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] jsou zobrazené na obrázku níže. Red oddíly diagramu (PresentationFramework, PresentationCore a milcore) jsou části kódu hlavní [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Pouze jeden z nich, nespravované součástí – milcore je. Milcore je zapsán v nespravovaném kódu, aby bylo možné povolit úzkou integraci s [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)]. Všechna zobrazení v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] se provádí prostřednictvím [!INCLUDE[TLA2#tla_dx](../../../../includes/tla2sharptla-dx-md.md)] modul, povolení pro efektivní hardwaru a softwaru vykreslování. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] také vyžaduje přesné řízení paměti a spouštění. Modul složení v milcore je velmi výkon citlivé a požadované zkoušet mnoho výhod [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] k získání výkonu.  
  
 ![Pozice WPF v rozhraní .NET Framework. ] (../../../../docs/framework/wpf/advanced/media/wpf-architect1.PNG "wpf_architect1")  
  
 Komunikace mezi spravovanými a nespravovanými částí [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] je popsána dále v tomto tématu. Zbývající spravované programovací model je popsáno níže.  
  
<a name="System_Threading_DispatcherObject"></a>   
## <a name="systemthreadingdispatcherobject"></a>System.Threading.DispatcherObject  
 Většinu objektů v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] odvozena od <xref:System.Windows.Threading.DispatcherObject>, který nabízí základní konstrukce týkajících se souběžností a dělení na vlákna. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] je založena na systému zasílání zpráv implementují dispečera. To funguje podobně jako známé [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] message pump; ve skutečnosti [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] dispečera User32 zprávy používá k provedení křížového vlákno volání.  
  
 Existují ve skutečnosti dvě základní koncepty když hovoříte o souběžnost v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] – spřažení dispečera a přístup z více vláken.  
  
 Během fáze návrhu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], cílem bylo přesunout na jedno vlákno spuštění, ale bez vláken "spřažené" modelu. Spřažení podprocesu se stane, když součást používá k uložení nějaký typ stavu identitu provádění vlákna. Nejběžnější formu to je použít místní úložiště vláken (TLS) k uložení stavu. Spřažení podprocesu vyžaduje, aby každý logický podproces provádění vlastnit pouze jeden fyzický přístup z více vláken v operačním systému, který se může stát náročná na paměť. Díky tomu se průběžně modelu vláken pro WPF synchronizován se existující model vláken User32 jednoho zařazování spuštění s spřažení vláken. Hlavním důvodem byla interoperabilita – systémy jako [!INCLUDE[TLA2#tla_ole2.0](../../../../includes/tla2sharptla-ole2-0-md.md)], do schránky a Internet Explorer všechny vyžadují spuštění jedno vlákno spřažení (STA).  
  
 Vzhledem k tomu, že máte objektů s STA dělení na vlákna, potřebujete způsob, jak komunikovat mezi vlákny a ověření umístěné na správném vlákno. V tomto dokumentu je role dispečera. Dispečer je základní zpráva odeslání systém s více seřazený podle priority fronty. Příklady zprávy jsou nezpracovaná vstupní oznámení (přesunout myš), funkce framework (rozložení) nebo příkazy uživatele (spustit tuto metodu). Odvozené z <xref:System.Windows.Threading.DispatcherObject>, můžete vytvořit [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objektu, který má STA chování a budou mít ukazatel dispečera v okamžiku vytvoření.  
  
<a name="System_Windows_DependencyObject"></a>   
## <a name="systemwindowsdependencyobject"></a>System.Windows.DependencyObject  
 Jedním z primárních architektury filozofiemi použít v sestavení [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] byl předvolbu pro vlastnosti prostřednictvím metody nebo události. Vlastnosti jsou deklarativní a umožní že vám umožní snadno určit záměr místo akce. Podporováno také modelu řízené nebo databázových systému pro zobrazení obsahu uživatelské rozhraní. Tato filosofie měl určený vliv vytváření další vlastnosti, které může vytvořit vazbu, aby bylo možné lépe řídit chování aplikace.  
  
 Aby bylo možné používat další systému vycházejí z vlastnosti bohatší vlastnosti systému, než co [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] poskytuje bylo potřeba. Jednoduchý příklad této zvučnost je oznámení o změnách. Pokud chcete povolit dva způsobem vazba, je nutné obou stranách vazby pro podporu upozornění na změnu. Aby bylo možné používat chování vázaný na hodnoty vlastností, budete muset být upozorněni, když se změní hodnota vlastnosti. [!INCLUDE[TLA#tla_netframewk](../../../../includes/tlasharptla-netframewk-md.md)] Má rozhraní, **INotifyPropertyChange**, což umožňuje objekt k publikování oznámení o změnách, ale je volitelné.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] poskytuje bohatší vlastnost systém a odvozené z <xref:System.Windows.DependencyObject> typu. Vlastnost systému se skutečně "závislosti" Vlastnosti systému, že sleduje závislosti mezi vlastnost výrazy a při změně závislosti automaticky revalidates hodnot vlastností. Například, pokud máte vlastnost, která dědí (jako je <xref:System.Windows.Controls.Control.FontSize%2A>), systém se automaticky aktualizuje, pokud se vlastnost změní na nadřazený element, který dědí hodnotu.  
  
 Základ pro [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] vlastnost systém je koncept výraz vlastnosti. V této první verzi [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], systém vlastnost výraz se zavře a výrazy jsou uvedeny jako součást rozhraní. Výrazy jsou proto vlastnost systém nemá vazbu dat, styly, nebo dědičnosti pevné programového, ale spíš poskytované novější vrstvy v rámci.  
  
 Vlastnost systému také poskytuje zhuštěného úložiště hodnot vlastností. Protože objekty může mít desítek (Pokud ne, stovky) vlastností a většina hodnoty jsou v jejich stavu výchozí (zděděná, styly, která nastavuje atd.), Ne každé instanci objektu musí mít úplnou váhu všech vlastností definovanou.  
  
 Poslední nová funkce systému vlastnost je znalost problematicky přidružené vlastnosti. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] elementy jsou postavené na princip složení a opětovné používání součásti. Se často stává, že některé obsahující element (například <xref:System.Windows.Controls.Grid> rozložení element) potřebovat další data na podřízené elementy mohla kontrolovat své chování (např. informace o řádku nebo sloupce). Místo přidružení všechny tyto vlastnosti k každý element, je povoleno libovolného objektu k poskytování definic vlastností pro jakýkoliv jiný objekt. Toto je podobná "expando" funkce jazyka JavaScript.  
  
<a name="System_Windows_Media_Visual"></a>   
## <a name="systemwindowsmediavisual"></a>System.Windows.Media.Visual  
 S definované systémem je dalším krokem získávání pixelů na obrazovce. <xref:System.Windows.Media.Visual> Třída poskytuje pro vytváření stromu vizuální objekty, každá volitelně obsahuje pokyny k vykreslení a metadata o tom, jak vykreslit tyto pokyny (výstřižek, transformaci, atd.). <xref:System.Windows.Media.Visual> je navržený jako velmi jednoduché a flexibilní, takže většinu funkcí sady mít žádné veřejné [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] ohrožení a jsou velmi závislá na funkce chráněné zpětného volání.  
  
 <xref:System.Windows.Media.Visual> vstupní bod, který je ve skutečnosti [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] složení systému. <xref:System.Windows.Media.Visual> bod připojení mezi tyto dvě subsystémy spravovaný [!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] a nespravované milcore.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Zobrazí data pomocí procházení nespravované datové struktury milcore spravuje. Těchto struktur, označují jako složení uzly představují hierarchické zobrazení stromu s vykreslování pokyny v každém uzlu. Tento strom, znázorněné na obrázku pravé straně přístupný jenom prostřednictvím zasílání zpráv protokolu.  
  
 Při programování [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], vytvoříte <xref:System.Windows.Media.Visual> elementy a odvozené typy, které interně sdělit stromu složení prostřednictvím tohoto zasílání zpráv protokolu. Každý <xref:System.Windows.Media.Visual> v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] může vytvořit jeden, jeden nebo několik uzlů složení.  
  
 ![Windows Presentation Foundation vizuálním stromu. ] (../../../../docs/framework/wpf/advanced/media/wpf-architecture2.PNG "wpf_architecture2")  
  
 Je velmi důležité architektury podrobností Všimněte zde – celý strom vizuály a kreslení pokyny se uloží do mezipaměti. V podmínkách grafiky [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] používá systém zachované vykreslování. To umožňuje systému překreslit tempem vysoké aktualizace bez systému složení blokování na zpětná volání a uživatelského kódu. To pomáhá zabránit vzhled aplikací, která neodpovídá.  
  
 Další důležité podrobností, která není skutečně projevuje diagramu je, jak systém ve skutečnosti provádí složení.  
  
 V User32 a [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)], systém funguje v systému výstřižek přímý režim. Když součásti nutné k vykreslení, systém vytvoří výstřižek hranice mimo kterých součást není dovoleno touch pixelů a potom komponentu se zobrazí výzva k vyplnění pixelů v tomto poli. Tento systém se velmi dobře funguje v systémech omezené pamětí vzhledem k tomu, když dojde ke změně máte jenom touch tato součást – žádné dvě součásti někdy podílet se na barvu jednoho pixelů.  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] používá "Kopírovat na algoritmus" vykreslování modelu. To znamená, že místo výstřižek jednotlivé komponenty, jednotlivé komponenty se zobrazí výzva k vykreslení ze zadní před zobrazení. To umožňuje jednotlivé komponenty pro malování přes předchozí komponenty zobrazení. Výhodou tohoto modelu je, že můžete mít složitý, částečně transparentní tvarů. S hardwarem dnešní moderní grafiky, tento model je poměrně rychlé (který není případě při User32 / [!INCLUDE[TLA2#tla_gdi](../../../../includes/tla2sharptla-gdi-md.md)] byly vytvořeny).  
  
 Jak je uvedeno nahoře, základní princip [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] je přesunout do další deklarativní model "vlastnost zaměřená na" programování. V systému visual to se zobrazí v několika zajímavé místech.  
  
 První, pokud si myslíte o grafické systému udržených režimu, to skutečně přechází od imperativní DrawLine/DrawLine typ modelu, na datový model orientované – nový řádek () / new Line(). Tento přesun do řízených daty vykreslování umožňuje komplexní operací na kreslení pokynů vyjádřit pomocí vlastnosti. Typ odvozovaný z: <xref:System.Windows.Media.Drawing> jsou efektivně objektový model pro vykreslování.  
  
 Druhý Pokud můžete vyhodnotit animace systému, uvidíte, že je téměř úplně deklarativní. Místo nutnosti vývojáře k výpočtu další umístění nebo další barvu, lze vyjádřit animací jako sadu vlastností objektu animace. Tyto animací můžete pak express záměr vývojář nebo Návrhář (přesunout toto tlačítko zde k dispozici v 5 sekund), a systém můžete určit, co nejúčinnější způsob, jak provést tuto akci.  
  
<a name="System_Windows_UIElement"></a>   
## <a name="systemwindowsuielement"></a>System.Windows.UIElement  
 <xref:System.Windows.UIElement> definuje základní subsystémy, včetně rozložení, vstup a události.  
  
 Rozložení je základní koncept v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. V mnoha systémů je buď pevné sada rozložení modely (HTML podporuje tři modely pro rozložení; toku, absolutní a tabulky) nebo bez modelu rozložení (User32 opravdu jen podporuje absolutní umístění). [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] spuštění za předpokladu, že vývojářů a návrhářů, chtěli flexibilní a rozšiřitelný rozložení model, který může být vycházejí z hodnoty vlastností, nikoli imperativní logiku. Na <xref:System.Windows.UIElement> úrovně, uvádíme základní kontrakt rozložení – dvě fáze model s <xref:System.Windows.UIElement.Measure%2A> a <xref:System.Windows.UIElement.Arrange%2A> předá.  
  
 <xref:System.Windows.UIElement.Measure%2A> Umožňuje součást kolik velikost ji chcete provést. Toto je samostatný fáze z <xref:System.Windows.UIElement.Arrange%2A> vzhledem k tomu, že je v mnoha situacích, kde nadřazený element požádá podřízené měření několikrát určit její optimální pozice a velikosti. Skutečnost, že nadřazené elementy požádejte podřízených elementů k měření ukazuje jiné klíče filosofie z [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] – velikost k obsahu. Všechny ovládací prvky v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] podporují možnost velikost fyzické velikosti jejich obsah. To výrazně usnadňuje lokalizaci a umožňuje dynamické rozložení elementů při velikosti věcí. <xref:System.Windows.UIElement.Arrange%2A> Fáze umožňuje nadřazený pozice a stanovit konečné velikosti jednotlivých podřízených.  
  
 Mnoho času je často stráví posuzování výstupu [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] – <xref:System.Windows.Media.Visual> a související objekty. Je ale rozsáhlou inovací na vstupní straně. Pravděpodobně nejvíce zásadní změna v vstupní modelu pro [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] je konzistentní model, podle kterého se směrují vstupní události prostřednictvím systému.  
  
 Vstup pochází jako signál na zařízení ovladač režimu jádra a získá směrovat na správná proces a vlákno komplikované proces zahrnující jádro systému Windows a User32. Jakmile zpráva User32 odpovídající vstup směrována na [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], se převede do [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] nezpracovaná vstupní zprávy a odesílají do dispečera. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Umožňuje nezpracovaná vstupních událostech, které má být převeden na více skutečné událostí povolení funkcí, jako je "MouseEnter" k implementaci na nízké úrovni systému s garantované doručení.  
  
 Každá vstupní událost bude převedena na alespoň dvě události – "náhled" události a skutečné události. Všechny události v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] mít hodnoty směrování prostřednictvím stromu elementu. Události jsou označeny jako "bublinový", pokud z cíle nahoru k procházení do kořenového adresáře a jsou označeny jako "tunelování" Pokud, spusťte v kořenovém adresáři a procházení dolů cíl. Zadejte preview události tunelové propojení, povolení libovolný element ve stromové struktuře příležitost filtrovat nebo provést akci pro událost. Běžné události (bez preview) se pak bublinový cíl až kořenu.  
  
 Toto rozdělení mezi fázi tunelové propojení a bublin umožňuje provádění funkcí jako klávesové zkratky v konzistentním způsobem v složené world fungovat. V User32 by implementovat klávesové zkratky tak, že jeden globální tabulku obsahující všechny akcelerátorů, který jste chtěli podporu (Ctrl + N mapování "New"). V dispečera pro vaši aplikaci volání **TranslateAccelerator** který by vstupní zpráv v User32, sledovat a zjistit, je-li žádné odpovídat akcelerátor registrované. V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] to nebude fungovat, protože systém je plně "složení" – libovolný element, můžete zpracovat a použít všechny klávesové zkratky. Tento model dvě fáze pro vstup umožní součásti, které implementují vlastní "TranslateAccelerator".  
  
 Tento krok jeden provádět další, <xref:System.Windows.UIElement> také zavádí představu o CommandBindings. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Příkaz systému umožňuje vývojářům něco definovat funkci z hlediska koncového bodu příkaz – Tento implementuje <xref:System.Windows.Input.ICommand>. Příkaz vazby povolit element definovat mapování mezi vstupní gesto (Ctrl + N) a příkaz (Nový). Vstupní gesta i příkaz definice jsou rozšiřitelný a může být drátové společně v době použití. Díky tomu trivial, například aby koncový uživatel Chcete-li přizpůsobit vazeb klíče, které chcete použít v rámci aplikace.  
  
 K tomuto bodu v tématu "základní" funkce [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] – funkce implementované v sestavení PresentationCore byly fokus. Při sestavování [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], vyčistit oddělení mezi základní součásti (jako kontrakt rozložení s **měr** a **uspořádat**) a částí framework (např. provádění konkrétní rozložení jako <xref:System.Windows.Controls.Grid>) byla požadovaném výsledku. Cílem bylo potřeba nízkou v zásobníku, který by umožnil externí vývojářům vytvářet své vlastní architektury, pokud bod rozšiřitelnosti.  
  
<a name="System_Windows_FrameworkElement"></a>   
## <a name="systemwindowsframeworkelement"></a>System.Windows.FrameworkElement  
 <xref:System.Windows.FrameworkElement> může být prohlédli dvěma různými způsoby. Přináší sadu zásad a vlastní nastavení na subsystémy byla zavedená v nižších vrstvách z [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Také zavádí sadu nové subsystémy.  
  
 Zásady primárního zaváděné <xref:System.Windows.FrameworkElement> je kolem rozložení aplikace. <xref:System.Windows.FrameworkElement> staví na základní rozložení kontrakt zaváděné <xref:System.Windows.UIElement> a přidá představu o rozložení "slotu", který usnadňuje rozložení autorům obsahují sadu vlastnosti řízených sémantiku rozložení. Vlastnosti, například <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>, <xref:System.Windows.FrameworkElement.MinWidth%2A>, a <xref:System.Windows.FrameworkElement.Margin%2A> (pro pojmenování několik) poskytnout všechny součásti, které jsou odvozené z <xref:System.Windows.FrameworkElement> konzistentní chování uvnitř kontejnerů rozložení.  
  
 <xref:System.Windows.FrameworkElement> také poskytuje snadnější [!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)] vystavení mnoho funkcí najít v jednotlivých vrstvách základní [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]. Například <xref:System.Windows.FrameworkElement> poskytuje přímý přístup k animace prostřednictvím <xref:System.Windows.FrameworkElement.BeginStoryboard%2A> metoda. A <xref:System.Windows.Media.Animation.Storyboard> poskytuje způsob, jak skript více animací proti sadu vlastností.  
  
 Dva nejdůležitějších věcí, <xref:System.Windows.FrameworkElement> zavádí jsou datové vazby a stylů.  
  
 Subsystém vazby dat v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] by měl být relativně každý uživatel, který byl použit [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] nebo [!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)] pro vytváření aplikací [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. V každé z těchto systémů je jednoduchý způsob, jak express, který má jeden nebo více vlastností z daného elementu bylo vázané na část dat. [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] má plnou podporu pro vlastnost vazby, transformaci a seznamu vazby.  
  
 Jeden z nejvíce zajímavé funkce datové vazby v [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] je zavedení dat šablony. Šablony dat umožní deklarativně zadejte, jak by měla vizualizovat část data. Místo vytváření vlastní uživatelské rozhraní, které mohou být vázány na data, můžete místo toho otáčení, problém a nechte data určit zobrazení, která bude vytvořena.  
  
 Stylů je ve skutečnosti lightweight formě datové vazby. Pomocí styly můžete můžete vázat sadu vlastností z sdílené definice na jeden nebo více instancí elementu. Styly získat použitá pro element buď explicitní odkaz (nastavením <xref:System.Windows.FrameworkElement.Style%2A> vlastnost) nebo implicitně tím, že přidružíte styl se [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] typ elementu.  
  
<a name="System_Windows_Controls_Control"></a>   
## <a name="systemwindowscontrolscontrol"></a>System.Windows.Controls.Control  
 Nejdůležitější funkce ovládacího prvku je ukázka. Pokud si myslíte o na WPF složení systému jako systém zachované režimu vykreslování, umožňuje Ukázka ovládacího prvku k popisu vykreslování parametrizované, deklarativní způsobem. A <xref:System.Windows.Controls.ControlTemplate> je ve skutečnosti nic jiného než skript pro vytvoření sady podřízených elementů s vazby na vlastnosti, které nabízí ovládacího prvku.  
  
 <xref:System.Windows.Controls.Control> poskytuje sadu uložených vlastností <xref:System.Windows.Controls.Control.Foreground%2A>, <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Padding%2A>, a další, které šablony autoři pak můžete použít k přizpůsobení zobrazení ovládacího prvku. Implementace ovládacího prvku poskytuje datový model a model interakce. Model interakce definuje sadu příkazů (např. Zavřete pro okno) a vazby jako vstup gesta (jako je například kliknutí na červené X v horním rohu okna). Datový model poskytuje sada vlastností k přizpůsobení modelu interakce nebo přizpůsobení zobrazení (určené šabloně).  
  
 Toto rozdělení mezi datový model (Vlastnosti), modelu interakce (příkazů a událostí) a zobrazení modelu (šablony) umožňuje úplného přizpůsobení vzhledu a chování ovládacího prvku.  
  
 Běžné aspekt datový model ovládacích prvků je modelu obsahu. Pokud se podíváte na ovládací prvek jako <xref:System.Windows.Controls.Button>, zobrazí se, že má vlastnost s názvem "Obsah" typu <xref:System.Object>. V [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] a [!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)], tato vlastnost by obvykle řetězec – ale která omezuje typ obsahu, můžete umístit do tlačítko. Obsah pro tlačítko může být buď jednoduchý řetězec, objekt komplexní dat nebo strom celý elementu. V případě objekt dat datová šablona slouží k vytvoření zobrazení.  
  
<a name="Summary"></a>   
## <a name="summary"></a>Souhrn  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] slouží ke umožňují vytvářet dynamické, systémy prezentace řízených daty. Každý součástí systému slouží k vytváření objektů prostřednictvím sady vlastností daná jednotka chování. Datová vazba je základní součástí systému a jsou integrované v každé vrstvě.  
  
 Tradiční aplikace vytvořit zobrazení a pak vytvořte vazbu k některým datům. V [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], vše, co o řízení, každý aspekt zobrazení, je generován nějaký typ datové vazby. Vytvoření ovládacího prvku složený uvnitř tlačítko a jeho zobrazení vytvoření vazby na vlastnost obsahu na tlačítko se zobrazí text prvku tlačítko Najít.  
  
 Když začnete vývoj [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] na základě aplikací, musí mít velmi dobře. Můžete nastavit vlastnosti, použijte objektů a dat vazby prakticky stejně, můžete pomocí [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] nebo [!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)]. S hlubší rozbor do architektura [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], zjistíte, že existuje možnost pro vytvoření mnohem širší aplikace, které zásadně data považovat ovladač jádra aplikace.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Visual>  
 <xref:System.Windows.UIElement>  
 <xref:System.Windows.Input.ICommand>  
 <xref:System.Windows.FrameworkElement>  
 <xref:System.Windows.Threading.DispatcherObject>  
 <xref:System.Windows.Input.CommandBinding>  
 <xref:System.Windows.Controls.Control>  
 [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Rozložení](../../../../docs/framework/wpf/advanced/layout.md)  
 [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
