---
title: Pokyny pro návrh ovládacích prvků s podporou stylů
ms.date: 03/30/2017
helpviewer_keywords:
- style design for controls [WPF]
- controls [WPF], style design
ms.assetid: c52dde45-a311-4531-af4c-853371c4d5f4
ms.openlocfilehash: 756cc821b1a9fe20741e390a1fe6e84d12cc6363
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59148158"
---
# <a name="guidelines-for-designing-stylable-controls"></a>Pokyny pro návrh ovládacích prvků s podporou stylů
Tento dokument shrnuje sadu osvědčených postupů, které je třeba zvážit při návrhu ovládací prvek, který máte v úmyslu být snadno s podporou stylů a templatable. Jsme obdrželi na tuto sadu osvědčených postupů prostřednictvím spoustu omyl a při práci na – styly ovládacích prvků motivu pro předdefinované [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sada ovládacích prvků. Jsme zjistili, že úspěšné stylů je co nejvíce funkcí dobře navržené objektový model je styl samotného. Jeho zamýšlenou cílovou skupinou pro tento dokument je ovládací prvek autora, ne Autor stylu.  
  
  <a name="Terminology"></a>   
## <a name="terminology"></a>Terminologie  
 "Styly a šablony" najdete suite technologie, které umožňují vytvořit ovládací prvek odložení visual aspekty ovládacího prvku na styl a šablony ovládacího prvku. Tato sada technologií zahrnuje:  
  
-   Styly (včetně metody Set vlastnosti aktivační události a scénáře).  
  
-   Prostředky.  
  
-   Šablony ovládacích prvků.  
  
-   Datové šablony.  
  
 Úvod do styly a šablony, najdete v části [styly a šablony](styling-and-templating.md).  
  
<a name="Before_You_Start__Understanding_Your_Control"></a>   
## <a name="before-you-start-understanding-your-control"></a>Než začnete: Princip ovládacího prvku  
 Před přechodem do těchto pokynů, je důležité pochopit a jste definovali běžné použití ovládacího prvku. Používání stylů pro zpřístupňuje často unruly sadu možností. Ovládací prvky, které jsou zapsány do použít široce (v mnoha aplikacích od mnoha vývojářů) pro rozpoznávání tváře před obrovskou výzvou – styly lze dalekosáhlý ke změnám vizuálního vzhledu ovládacího prvku. Upravený ovládací prvek ve skutečnosti nemusí vypadat i ovládacího prvku Autor záměry. Protože je v podstatě boundless flexibilitou, kterou nabízejí stylů, vám pomůže představu o běžné použití vám pomohou určit rozsah vaše rozhodnutí.  
  
 Informace o tom běžné použití ovládacího prvku, je vhodné uvažovat o návrh hodnoty ovládacího prvku. Co váš ovládací prvek přenést do tabulky, která může nabídnout žádnou kontrolu? Běžné použití neznamená žádné konkrétní vizuálního vzhledu, ale spíše filozofií ovládacího prvku a přiměřené sadu očekávání o jejím využití. Toto pochopení umožňuje vytvořit některé předpoklady o modelu složení a chování definované stylu ovládacího prvku v obvyklém případě. V případě třídy <xref:System.Windows.Controls.ComboBox>, například vysvětlení běžné použití vám neposkytne žádné přehledy o, jestli konkrétní <xref:System.Windows.Controls.ComboBox> má zaoblené rohy, ale poskytne vám přehled o tom, fakt, který <xref:System.Windows.Controls.ComboBox> pravděpodobně potřebuje automaticky otevírané okno a nějakým způsobem při přepínání, jestli je otevřený.  
  
<a name="General_Guidelines"></a>   
## <a name="general-guidelines"></a>Obecné pokyny  
  
-   **Nevynucovat výhradně kontrakty šablony.** Kontrakt šablony ovládacího prvku může obsahovat elementy, příkazy, vazby, aktivační události nebo nastavení i vlastnosti, které jsou požadované nebo očekávané pro ovládací prvek fungovat správně.  
  
    -   Minimalizujte kontrakty co největší míře.  
  
    -   Návrh kolem předpokladem, že během návrhu čas (to znamená, že při použití návrhářský nástroj) je běžné, že šablony ovládacího prvku ve stavu nekompletní. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nenabízí "vytváření" stavu infrastruktury, takže ovládací prvky mají být vytvořeny s předpokladem, že takový stav, může být platný.  
  
    -   Jiného aspektu kontrakt šablony nedodrží nevyvolají výjimky. Společně tyto řádky panelů by neměla vyvolávat výjimky, pokud mají podřízené položky příliš mnoho nebo příliš málo.  
  
-   **Faktor periferní funkce do šablony pomocné prvky.** Každý ovládací prvek by měl na jeho základní funkce a návrh hodnoty true a určené běžné použití ovládacího prvku. Který chcete ukončit, použijte složení a pomocné prvky v rámci šablony pro povolení periferní chování a vizualizace, to znamená, tyto chování a vizualizace, které se nepodílejí na základní funkce ovládacího prvku. Pomocné rutiny elementy spadají do tří kategorií:  
  
    -   **Samostatné** pomocné rutiny typy jsou veřejné a opakovaně použitelné ovládací prvky nebo primitivních elementů, které se používá "anonymní" v šabloně, to znamená, že je seznámen druhé pomocný element ani upravený ovládací prvek. Technicky vzato libovolný element může být anonymního typu, ale v tomto kontextu termín popisuje tyto typy, které provádí zapouzdření specializované funkce, které umožňují cílové scénáře.  
  
    -   **Na základě typu** pomocné prvky jsou nové typy, které provádí zapouzdření speciální funkce. Tyto prvky jsou obvykle navrženy s zúžit rozsah funkcí než běžné ovládací prvky nebo primitiv. Na rozdíl od samostatné pomocné prvky uvědomte o kontext, ve kterém se používají a obvykle musí sdílet data s ovládacím prvkem, jejichž šabloně patří pomocné rutiny založené na typ prvků.  
  
    -   **S názvem** pomocné prvky jsou běžné ovládací prvky nebo primitivních elementů, které ovládací prvek očekává v rámci jeho šablonu podle názvu. Tyto prvky jsou uvedeny dobře známým názvem v rámci šablony, aby bylo možné pro ovládací prvek pro hledání elementu a pracovat s nimi prostřednictvím kódu programu. Může existovat pouze jeden element se zadaným názvem v žádné šablony.  
  
     Následující tabulka uvádí prvky pomocné rutiny náhradník – styly ovládacích prvků ještě dnes (Tento seznam není vyčerpávající):  
  
    |Prvek|Type|Používá|  
    |-------------|----------|-------------|  
    |<xref:System.Windows.Controls.ContentPresenter>|Na základě typu|<xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.Frame>, a tak dále (všechny <xref:System.Windows.Controls.ContentControl> typy)|  
    |<xref:System.Windows.Controls.ItemsPresenter>|Na základě typu|<xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.Menu>, a tak dále (všechny <xref:System.Windows.Controls.ItemsControl> typy)|  
    |<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|s názvem|<xref:System.Windows.Controls.ToolBar>|  
    |<xref:System.Windows.Controls.Primitives.Popup>|Samostatné|<xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.ToolBar>, <xref:System.Windows.Controls.Menu>, <xref:System.Windows.Controls.ToolTip>, a tak dále|  
    |<xref:System.Windows.Controls.Primitives.RepeatButton>|s názvem|<xref:System.Windows.Controls.Slider>, <xref:System.Windows.Controls.Primitives.ScrollBar>, a tak dále|  
    |<xref:System.Windows.Controls.Primitives.ScrollBar>|s názvem|<xref:System.Windows.Controls.ScrollViewer>|  
    |<xref:System.Windows.Controls.ScrollViewer>|Samostatné|<xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.Menu>, <xref:System.Windows.Controls.Frame>, a tak dále|  
    |<xref:System.Windows.Controls.Primitives.TabPanel>|Samostatné|<xref:System.Windows.Controls.TabControl>|  
    |<xref:System.Windows.Controls.TextBox>|s názvem|<xref:System.Windows.Controls.ComboBox>|  
    |<xref:System.Windows.Controls.Primitives.TickBar>|Na základě typu|<xref:System.Windows.Controls.Slider>|  
  
-   **Minimalizovat požadované vazby zadané uživatelem nebo nastavení vlastnosti v prvcích pomocné rutiny**. Je běžné, že pomocný element tak, aby vyžadovala některé vazby nebo nastavení vlastností mohl fungovat správně v šabloně ovládacího prvku. Pomocný element a ovládací prvek bez vizuálního vzhledu, snažte se co nejvíce zavede tato nastavení. Při nastavení vlastnosti nebo vytvoření vazby, mělo dbát na přepsat hodnoty nastavené uživatelem. Osvědčené postupy pro jsou následující:  
  
    -   Pojmenované pomocné prvky by měly být identifikovány nadřazený a nadřazeného zavede všechna požadovaná nastavení na elementu pomocné rutiny.  
  
    -   Pomocné rutiny založené na typ prvků zavede všechna požadovaná nastavení na sami. To může vyžadovat pomocný element dotaz pro informace o kontextu, ve kterém se používá, včetně jeho `TemplatedParent` (typ ovládacího prvku šablony, ve kterém je používán). Například <xref:System.Windows.Controls.ContentPresenter> automaticky vytvoří vazbu `Content` vlastnost jeho `TemplatedParent` k jeho <xref:System.Windows.Controls.ContentPresenter.Content%2A> vlastnost při použití v <xref:System.Windows.Controls.ContentControl> odvozeného typu.  
  
    -   Tímto způsobem nelze optimalizované samostatné pomocné prvky, protože podle definice pomocný element ani nadřazený ví o dalších.  
  
-   **Použijte vlastnost název na příznak prvky v rámci šablony**. Ovládací prvek, který potřebuje najít element v jeho styl za účelem přístupu k prostřednictvím kódu programu by k tomu použít `Name` vlastnost a `FindName` paradigma. Ovládací prvek by neměla vrátit výjimku, pokud element nebyl nalezen, ale bez upozornění a bez výpadku zakázat funkce, které vyžaduje tento prvek.  
  
-   **Použijte osvědčené postupy pro vyjádření stav ovládacího prvku a chování ve stylu.** Následující je uspořádaný seznam osvědčených postupů pro vyjádření změní stav ovládacího prvku a chování ve stylu. Měli byste použít první položky na seznamu, který umožňuje vašemu scénáři.  
  
    1.  Vytvoření vazby pro vlastnost. Příklad: vytvoření vazby mezi <xref:System.Windows.Controls.ComboBox.IsDropDownOpen%2A?displayProperty=nameWithType> a <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A?displayProperty=nameWithType>.  
  
    2.  Aktivuje změny vlastností nebo z animací vlastností. Příklad: při najetí myší stav <xref:System.Windows.Controls.Button>.  
  
    3.  příkaz. Příklad: <xref:System.Windows.Controls.Primitives.ScrollBar.LineUpCommand>  /  <xref:System.Windows.Controls.Primitives.ScrollBar.LineDownCommand> v <xref:System.Windows.Controls.Primitives.ScrollBar>.  
  
    4.  Samostatné pomocné prvky. Příklad: <xref:System.Windows.Controls.Primitives.TabPanel> v <xref:System.Windows.Controls.TabControl>.  
  
    5.  Typy založené na typu pomocné rutiny. Příklad: <xref:System.Windows.Controls.ContentPresenter> v <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Primitives.TickBar> v <xref:System.Windows.Controls.Slider>.  
  
    6.  Název pomocné prvky. Příklad: <xref:System.Windows.Controls.TextBox> v <xref:System.Windows.Controls.ComboBox>.  
  
    7.  Probublání události z typů s názvem pomocné rutiny. Pokud naslouchat probublání události z prvku style je potřeba povolit, že element generování události lze jednoznačně identifikovat. Příklad: <xref:System.Windows.Controls.Primitives.Thumb> v <xref:System.Windows.Controls.ToolBar>.  
  
    8.  Vlastní `OnRender` chování. Příklad: <xref:Microsoft.Windows.Themes.ButtonChrome> v <xref:System.Windows.Controls.Button>.  
  
-   **Použití aktivačních procedur styl (na rozdíl od šablon aktivační události) střídmě**. Triggery, které ovlivňují vlastnosti prvků v šabloně musí být deklarována v šabloně. Triggery, které ovlivňují vlastnosti ovládacího prvku (žádné `TargetName`) mohou být deklarovány ve stylu, pokud si nejste jisti, že změna šablony by měl také zničit aktivační událost.  
  
-   **Bylo v souladu s existující styl vzorce.** V mnoha případech existuje více způsobů k vyřešení problému. Mějte a při nejbližším konzistentní s existujícím řízení používání stylů pro vzory. To je obzvláště důležité pro ovládací prvky, které jsou odvozeny z stejné základní typ (například <xref:System.Windows.Controls.ContentControl>, <xref:System.Windows.Controls.ItemsControl>, <xref:System.Windows.Controls.Primitives.RangeBase>, a tak dále).  
  
-   **Vystavení vlastností k podpoře běžných scénářů přizpůsobení bez retemplating**. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nepodporuje modulární/přizpůsobitelné částí, takže uživatelského ovládacího prvku je zbývá jenom dva způsoby přizpůsobení: nastavení vlastnosti přímo nebo nastavení vlastnosti pomocí stylů. To na paměti je třeba zařízení surface omezený počet vlastností určenou pro scénáře přizpůsobení velmi běžné, s vysokou prioritou, které by jinak vyžadovaly retemplating. Tady jsou osvědčené postupy pro kdy a jak se povolily scénáře přizpůsobení:  
  
    -   Velmi vlastního by měl vystavena jako vlastnosti na ovládacím prvku a používat šablonu.  
  
    -   Přizpůsobení méně běžné (i když vzácného není) by měl vystavena jako připojené vlastnosti a používat šablonu.  
  
    -   Je to přijatelné pro známé, ale zřídka přizpůsobení tak, aby vyžadovala retemplating.  
  
<a name="Theme_Considerations"></a>   
## <a name="theme-considerations"></a>Důležité informace o motiv  
  
-   **Styly motivů má pokusit o mít sémantiku konzistentní vlastnost přes všechny motivy, ale je zaručeno**. Jako součást jeho dokumentaci by měl mít ovládací prvek dokument popisující sémantiku vlastnost ovládacího prvku, to znamená, "význam" vlastnosti ovládacího prvku. Například <xref:System.Windows.Controls.ComboBox> ovládací prvek by měl definovat význam <xref:System.Windows.Controls.Control.Background%2A> vlastnosti v rámci <xref:System.Windows.Controls.ComboBox>. Výchozí styly pro ovládací prvek se má pokusit o postupujte podle sémantiky přes všechny motivy definované v tomto dokumentu. Ovládací prvek uživatelů, na druhé straně měli vědět, že vlastnost sémantiku můžete změnit z motiv pro motiv. V některých případech nemusí být v rámci visual omezení vyžaduje konkrétní motivu anyAttribute dané vlastnosti. (Klasické nastavení, například nemá jeden ohraničení, pro které `Thickness` lze použít pro mnoho ovládacích prvků.)  
  
-   **Styly motivů není nutné mít sémantiku konzistentní trigger přes všechny motivy**. Chování vystavené stylu ovládacího prvku pomocí aktivační události nebo animace se mohou lišit od motiv pro motiv. Ovládací prvek uživatelé by měli být vědomi, že ovládací prvek nebude využívat nutně stejný mechanismus pro dosažení určitého chování napříč všechny motivy. Jeden motiv, například může pomocí animace express chování při najetí myší kde používá jiný motiv aktivační události. To může vést k nekonzistenci v chování a zachovávání s rozlišením na vlastní ovládací prvky. (Při změně hodnoty vlastnosti na pozadí, třeba nemusí mít vliv na stav při najetí myší ovládací prvek Pokud státu je vyjádřena pomocí aktivační události. Nicméně pokud státu při najetí myší je implementovaná pomocí animace, změna na pozadí by mohlo způsobit neopravitelně narušení animace a proto přechod stavu.)  
  
-   **Styly motivů není nutné mít sémantiku konzistentní "layout" přes všechny motivy**. Například výchozí styl není potřeba zajistit, že se ovládací prvek zabírají stejné množství velikost ve všech motivy nebo zaručit, že ovládací prvek bude mít stejný obsah rozpětí / odsazení mezi všechny motivy.  
  
## <a name="see-also"></a>Viz také:

- [Styly a šablony](styling-and-templating.md)
- [Přehled řízeného vytváření](control-authoring-overview.md)
