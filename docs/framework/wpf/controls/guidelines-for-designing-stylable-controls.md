---
title: "Pokyny pro návrh ovládacích prvků s podporou stylů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- style design for controls [WPF]
- controls [WPF], style design
ms.assetid: c52dde45-a311-4531-af4c-853371c4d5f4
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6707a434f64838467033966c9093e1e415b1fb31
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="guidelines-for-designing-stylable-controls"></a>Pokyny pro návrh ovládacích prvků s podporou stylů
Tento dokument shrnuje sadu osvědčené postupy vzít v úvahu při navrhování řídit, která chcete být snadno stylable a templatable. Jsme byla do této skupiny prostřednictvím spoustu omyl a osvědčené postupy při práci s styly ovládacího prvku motivu pro integrované [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sadou ovládacích prvků. Jsme zjistili, že úspěšné stylů je tolik funkcí dobře navrženou objektový model jako je styl sám sebe. Předpokládanou cílovou skupinou pro tento dokument je ovládací prvek autora, ne Autor styl.  
  
  <a name="Terminology"></a>   
## <a name="terminology"></a>Terminologie  
 "Stylů a ukázka" odkazují na sadu technologií, které umožňují řízení autorovi odložení visual aspektů ovládacího prvku na styl a šablony ovládacího prvku. Tato sada technologií, zahrnuje:  
  
-   Styly (včetně nastavením vlastností, aktivační události a scénářů).  
  
-   Prostředky.  
  
-   Ovládací prvek šablony.  
  
-   Data šablony.  
  
 Úvod do stylů a ukázka, najdete v části [stylů a ukázka](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
<a name="Before_You_Start__Understanding_Your_Control"></a>   
## <a name="before-you-start-understanding-your-control"></a>Než začnete: Principy vlastního ovládacího prvku  
 Před přechodem do těchto pokynů, je důležité pochopit a definovali běžné použití vlastního ovládacího prvku. Stylů zpřístupní často unruly sadu možnosti. Ovládací prvky, které se zapisují do použije široce (v mnoha aplikacích mnoho vývojáři) čelí výzvě stylů lze dalekosáhlou změnit vzhled ovládacího prvku. Ve skutečnosti ovládacího prvku s vzhledem nemusí i vypadat podobně jako autor řízení záměry. Vzhledem k tomu, že je v podstatě rozsáhlého flexibilitu, které nabízí stylů, můžete vám pomohou určit rozsah svoje rozhodnutí o představu o běžné využití.  
  
 Pro pochopení využití běžné ovládacího prvku, je dobré myslet nabízená hodnota ovládacího prvku. Co přináší vlastní ovládací prvek pro tabulky, která vám může nabídnout žádný další ovládací prvek? Běžné použití neznamená konkrétní vzhled, ale spíš filosofie ovládacího prvku a přiměřené sadu očekávání o jeho používání. Toto pochopení umožňuje provést některé předpoklady o složení modelu a definované styl chování ovládacího prvku v běžně. U <xref:System.Windows.Controls.ComboBox>, například pochopení běžné využití nebude získáte žádné přehledy o zda konkrétní <xref:System.Windows.Controls.ComboBox> má zaoblenými hranami, ale jeho vám poskytne přehled o fakt, <xref:System.Windows.Controls.ComboBox> pravděpodobně musí automaticky otevírané okno a Některé způsob při přepínání, zda je otevřený.  
  
<a name="General_Guidelines"></a>   
## <a name="general-guidelines"></a>Obecné pokyny  
  
-   **Nevynucovat výhradně kontrakty šablony.** Kontrakt šablony ovládacího prvku může obsahovat elementy, příkazy, vazby, aktivační události nebo nastavení i vlastností, které jsou potřeba nebo se očekává pro ovládací prvek fungovat správně.  
  
    -   Minimalizujte kontrakty co nejvíc.  
  
    -   Návrh kolem předpoklad, že při návrhu čas (při používání nástroje návrhu) je běžné pro ovládací prvek šablonu neúplné stav. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]nenabízí "skládání" stav infrastruktury, a aby ovládacích prvků mají být vytvořené s tím, že takový stav může být platný.  
  
    -   Pokud nedodržíte kteréhokoli aspektu kontraktu šablony nevyvolá výjimku výjimky. Toho by neměl panelů generování výjimek, pokud mají příliš mnoho nebo příliš málo podřízených objektů.  
  
-   **Faktor periferní funkce do šablony pomocné prvky.** Každý ovládací prvek by měl zaměřuje na jeho základní funkce a hodnotu true a definované běžné použití ovládacího prvku. Do které ukončení, použijte složení a pomocné prvky v rámci šablony periferní chování a vizualizace, který je povolit, tyto chování a vizualizací, které nepřispívají k základní funkce ovládacího prvku. Pomocné prvky spadají do tří kategorií:  
  
    -   **Samostatné** podpůrné typy jsou veřejné a opakovaně použitelné ovládací prvky nebo primitiv, které jsou používány "anonymně" v šabloně, znamená, že pomocný element ani ovládacího prvku s vzhledem známa dalších. Technicky libovolný element, může být anonymní typ, ale v tomto kontextu termín popisuje tyto typy, které zapouzdření speciální funkce umožňující cílové scénáře.  
  
    -   **Na základě typu** pomocné prvky jsou nové typy, které zapouzdřují speciální funkce. Tyto prvky jsou obvykle navrženy s rozsahem užší funkcí než běžné ovládací prvky nebo primitiv. Na rozdíl od samostatná pomocná elementy na základě typu pomocné prvky jsou informace o kontextu, ve kterém se používají a obvykle musí sdílet data s ovládacím prvkem, jejichž šablony patří.  
  
    -   **S názvem** pomocné prvky jsou běžné ovládací prvky nebo primitiv, které ovládacího prvku očekává, že najít v rámci jeho šablony podle názvu. Tyto prvky jsou uvedeny známý název v rámci šablony, která umožňuje ovládacího prvku k nalezen element a pracovat s ním prostřednictvím kódu programu. Může existovat pouze jeden element se zadaným názvem v žádné šablony.  
  
     V následující tabulce jsou pomocné prvky zaměstnaní – styly ovládacích prvků dnes (Tento seznam není vyčerpávající):  
  
    |Prvek|Typ|Používá|  
    |-------------|----------|-------------|  
    |<xref:System.Windows.Controls.ContentPresenter>|Na základě typu|<xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.Frame>a tak dále (všechny <xref:System.Windows.Controls.ContentControl> typy)|  
    |<xref:System.Windows.Controls.ItemsPresenter>|Na základě typu|<xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.Menu>a tak dále (všechny <xref:System.Windows.Controls.ItemsControl> typy)|  
    |<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|S názvem|<xref:System.Windows.Controls.ToolBar>|  
    |<xref:System.Windows.Controls.Primitives.Popup>|Samostatné|<xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.ToolBar>, <xref:System.Windows.Controls.Menu>, <xref:System.Windows.Controls.ToolTip>a tak dále|  
    |<xref:System.Windows.Controls.Primitives.RepeatButton>|S názvem|<xref:System.Windows.Controls.Slider>, <xref:System.Windows.Controls.Primitives.ScrollBar>a tak dále|  
    |<xref:System.Windows.Controls.Primitives.ScrollBar>|S názvem|<xref:System.Windows.Controls.ScrollViewer>|  
    |<xref:System.Windows.Controls.ScrollViewer>|Samostatné|<xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.Menu>, <xref:System.Windows.Controls.Frame>a tak dále|  
    |<xref:System.Windows.Controls.Primitives.TabPanel>|Samostatné|<xref:System.Windows.Controls.TabControl>|  
    |<xref:System.Windows.Controls.TextBox>|S názvem|<xref:System.Windows.Controls.ComboBox>|  
    |<xref:System.Windows.Controls.Primitives.TickBar>|Na základě typu|<xref:System.Windows.Controls.Slider>|  
  
-   **Minimalizovat požadované vazby zadán uživatel nebo nastavení vlastností na pomocné prvky**. Je běžné pro pomocný element tak, aby vyžadovala určité vazby nebo nastavení vlastností, aby mohl správně fungovat v rámci šablony ovládacího prvku. Pomocný element a šablonované řízení, v maximální míře, zavede tato nastavení. Při nastavení vlastností nebo vytvoření vazby, mělo dbát na přepsat hodnoty nastavený uživatelem. Konkrétní osvědčené postupy jsou následující:  
  
    -   Mělo by být určené pojmenované pomocné prvky nadřízený objekt a nadřazeného by měl vytvořit všechna požadovaná nastavení na pomocný element.  
  
    -   Na základě typu pomocné prvky zavede všechna požadovaná nastavení na sami. To může vyžadovat pomocný element dotazu pro informace o kontextu, ve kterém je používán, včetně jeho `TemplatedParent` (typ ovládacího prvku šablony, ve kterém je používán). Například <xref:System.Windows.Controls.ContentPresenter> automaticky vytvoří vazbu `Content` vlastnost jeho `TemplatedParent` k jeho <xref:System.Windows.Controls.ContentPresenter.Content%2A> vlastnost při použití v <xref:System.Windows.Controls.ContentControl> odvozeného typu.  
  
    -   Tímto způsobem nelze optimalizovat samostatná pomocná elementy, protože podle definice pomocný element ani nadřazený ví o dalších.  
  
-   **Použijte vlastnost název příznak elementů v rámci šablon**. Ovládací prvek, který je potřeba při vyhledávání prvku v jeho styl aby k němu přístup prostřednictvím kódu programu by to provést pomocí `Name` vlastnost a `FindName` zlepší. Ovládací prvek nesmí vyvolat výjimku, pokud element nebyl nalezen, ale bez upozornění a řádně zakázat funkce, která vyžaduje daný element.  
  
-   **Použijte osvědčené postupy pro vyjádření řízení stavu a chování ve stylu.** Následuje seznam pořadí osvědčené postupy pro vyjádření změny stavu ovládacího prvku a chování ve stylu. Měli byste použít první položky v seznamu, který umožňuje vašemu scénáři.  
  
    1.  Vlastnost vazby. Příklad: vytvoření vazby mezi <xref:System.Windows.Controls.ComboBox.IsDropDownOpen%2A?displayProperty=nameWithType> a <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A?displayProperty=nameWithType>.  
  
    2.  Aktivuje změny vlastností nebo vlastnost animace. Příklad: hover stav <xref:System.Windows.Controls.Button>.  
  
    3.  Příkaz. Příklad: <xref:System.Windows.Controls.Primitives.ScrollBar.LineUpCommand>  /  <xref:System.Windows.Controls.Primitives.ScrollBar.LineDownCommand> v <xref:System.Windows.Controls.Primitives.ScrollBar>.  
  
    4.  Samostatná pomocná elementy. Příklad: <xref:System.Windows.Controls.Primitives.TabPanel> v <xref:System.Windows.Controls.TabControl>.  
  
    5.  Typy založený na typu pomocné rutiny. Příklad: <xref:System.Windows.Controls.ContentPresenter> v <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Primitives.TickBar> v <xref:System.Windows.Controls.Slider>.  
  
    6.  S názvem pomocné prvky. Příklad: <xref:System.Windows.Controls.TextBox> v <xref:System.Windows.Controls.ComboBox>.  
  
    7.  Probublala události z typů s názvem pomocné rutiny. Pokud naslouchat probublala události z style element, byste měli vyžadovat, aby element generování události lze jednoznačně identifikovat. Příklad: <xref:System.Windows.Controls.Primitives.Thumb> v <xref:System.Windows.Controls.ToolBar>.  
  
    8.  Vlastní `OnRender` chování. Příklad: <xref:Microsoft.Windows.Themes.ButtonChrome> v <xref:System.Windows.Controls.Button>.  
  
-   **Doporučujeme použít styl aktivační události (na rozdíl od šablony aktivační události)**. Aktivační události, které ovlivňují vlastnosti prvků v šabloně musí být deklarován v šabloně. Aktivační události, které ovlivňují vlastnosti na ovládací prvek (žádná `TargetName`) může být deklarován v styl, pokud si nejste jisti, že změna šablony by také destroy aktivační událost.  
  
-   **Být v souladu s existující vzory stylů.** Kolikrát existuje více způsobů k vyřešení problému. Mít na paměti, a když možné konzistentní s existujícím řídit vzory stylů. To je obzvláště důležité pro ovládací prvky, které jsou odvozeny od základní stejného typu (například <xref:System.Windows.Controls.ContentControl>, <xref:System.Windows.Controls.ItemsControl>, <xref:System.Windows.Controls.Primitives.RangeBase>a tak dále).  
  
-   **Vystavení vlastností k podpoře běžných scénářů přizpůsobení bez retemplating**. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]nepodporuje modulární, přizpůsobitelné částí, takže uživatel ovládací prvek je ponechán s pouze dvěma metody přizpůsobení: nastavení vlastností přímo nebo nastavení vlastností pomocí stylů. Si uvědomit je třeba surface omezený počet vlastností zaměřený na přizpůsobení s vysokou prioritou, velmi běžné scénáře, které by jinak vyžadovaly retemplating. Zde jsou doporučené postupy pro kdy a jak povolit scénáře přizpůsobení:  
  
    -   Velmi běžné úpravy by měl vystaveny jako vlastnosti na ovládací prvek a využívat šablonou.  
  
    -   Přizpůsobení méně běžné (ale ne stane se výjimečně) by měl zveřejněné jako připojené vlastnosti a využívat šablonou.  
  
    -   Je přijatelné pro přizpůsobení známé, ale výjimečných tak, aby vyžadovala retemplating.  
  
<a name="Theme_Considerations"></a>   
## <a name="theme-considerations"></a>Aspekty motiv  
  
-   **Styly motivů pokusit o mít konzistentní vlastnost sémantiku přes všechny motivy, ale ujistěte se, nejde zaručit**. V rámci jeho dokumentace by měl mít ovládací prvek dokumentu popisující sémantiku vlastnost ovládacího prvku, který je "význam" vlastnosti pro ovládací prvek. Například <xref:System.Windows.Controls.ComboBox> řízení měli definovat význam <xref:System.Windows.Controls.Control.Background%2A> vlastností v rámci <xref:System.Windows.Controls.ComboBox>. Výchozí styly pro ovládací prvek pokusit o postupujte podle sémantiku definovat v tomto dokumentu v rámci všech motivů. Řízení uživatelů, na druhé straně měli vědět, že vlastnost sémantiku můžete změnit z motivu motiv. V některých případech nemusí být v seznamu visual omezení vyžaduje konkrétní motiv vyjádřit kombinací dané vlastnosti. (Klasické nastavení, například jednoho ohraničení, ke které nemá `Thickness` lze použít pro mnoho ovládací prvky.)  
  
-   **Styly motivů nemusíte mít konzistentní aktivační událost sémantiku přes všechny motivy**. Chování vystavené styl řízení prostřednictvím aktivační události nebo animace se může lišit od motiv motiv. Řízení uživatelé měli vědět, že ovládacího prvku nebude využívat nutně shodný mechanismus, abyste dosáhli konkrétní chování všech motivů. Jeden motivu, může použít například animace do express hover chování kde používá jiný motiv aktivační událost. Výsledkem může být nekonzistence v chování zachovávání na vlastní ovládací prvky. (Změna vlastnost pozadí například nemusí ovlivnit stav hover ovládacího prvku Pokud tento stav je vyjádřit pomocí aktivační událost. Ale pokud hover stavu je implementovaná pomocí animace, změna na pozadí by mohlo způsobit neopravitelně narušení animace a proto přechod stavu.)  
  
-   **Styly motivů nemusíte mít konzistentní "rozložení" sémantiku přes všechny motivy**. Například výchozí styl nemusí zaručit, že bude ovládacího prvku zabírají stejnou úroveň velikost ve všech motivy nebo zaručit, že ovládacího prvku budou mít stejné obsahu okraje / odsazení mezi všechny motivů.  
  
## <a name="see-also"></a>Viz také  
 [Styly a šablony](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Přehled vytváření ovládacích prvků](../../../../docs/framework/wpf/controls/control-authoring-overview.md)
