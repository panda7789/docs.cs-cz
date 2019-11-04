---
title: Pokyny pro návrh ovládacích prvků s podporou stylů
ms.date: 03/30/2017
helpviewer_keywords:
- style design for controls [WPF]
- controls [WPF], style design
ms.assetid: c52dde45-a311-4531-af4c-853371c4d5f4
ms.openlocfilehash: 0fbb515afbeac05168ced6f0a99f50eb29a5c848
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459661"
---
# <a name="guidelines-for-designing-stylable-controls"></a>Pokyny pro návrh ovládacích prvků s podporou stylů

Tento dokument shrnuje sadu osvědčených postupů, které je potřeba vzít v úvahu při navrhování ovládacího prvku, který máte v úmyslu snadno ovládacích a templatable. Do této sady osvědčených postupů jsme dostali spoustu zkušebních verzí a chybu při práci na stylech ovládacích prvků motivů pro předdefinovanou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sadu ovládacích prvků. Zjistili jsme, že úspěšné styly jsou stejně velké jako funkce modelu vhodně navrženého objektu, protože se jedná o samotný styl. Zamýšlená skupina pro tento dokument je autor ovládacího prvku, nikoli autor stylu.

<a name="Terminology"></a>

## <a name="terminology"></a>Terminologie

"Stylování a šablonování" odkazují na sadu technologií, které umožňují autorovi ovládacího prvku odložit vizuální aspekty ovládacího prvku na styl a šablonu ovládacího prvku. Tato sada technologií zahrnuje:

- Styly (včetně setter vlastností, triggerů a scénářů).

- Prostředky.

- Šablony ovládacích prvků.

- Datové šablony.

Úvod do stylů a šablonování naleznete v tématu [stylování a šablonování](../../../desktop-wpf/fundamentals/styles-templates-overview.md).

<a name="Before_You_Start__Understanding_Your_Control"></a>

## <a name="before-you-start-understanding-your-control"></a>Než začnete: Seznámení s vaším ovládacím prvkem

Před přechodem na tyto pokyny je důležité pochopit a nadefinovat společné použití vašeho ovládacího prvku. Styl zpřístupňuje často Unruly sadu možností. Ovládací prvky, které jsou zapsány k použití v podstatě (v mnoha aplikacích, mnoho vývojářů) čelí výzvám, které je možné použít k dosažení rozsáhlých změn vizuálního vzhledu ovládacího prvku. Ve skutečnosti se v ovládacím prvku ve stylu nemusí dokonce podobat záměru autora ovládacího prvku. Vzhledem k tomu, že flexibilita nabízená styly je v podstatě bez omezení, můžete využít nápad společného využití, který vám umožní určit rozsah rozhodnutí.

Chcete-li porozumět běžnému využití vašeho ovládacího prvku, je dobré se zabývat hodnotou ovládacího prvku. Co ovládací prvek přinese do tabulky, kterou jiný ovládací prvek nemůže nabídnout? Běžné použití neznamená žádný konkrétní vizuální vzhled, ale spíše filozofie ovládacího prvku a rozumnou sadu očekávání o jeho využití. Toto porozumění vám umožní udělat si některé předpoklady o modelu kompozice a chování ovládacího prvku v běžném případě podle stylu. V případě <xref:System.Windows.Controls.ComboBox>například porozumět běžnému využití, získáte žádné informace o tom, zda konkrétní <xref:System.Windows.Controls.ComboBox> obsahuje zaoblené rohy, ale poskytne vám přehled o tom, že <xref:System.Windows.Controls.ComboBox> pravděpodobně potřebuje automaticky otevírané okno a nějaký způsob, jak přepínání, zda je otevřen.

<a name="General_Guidelines"></a>

## <a name="general-guidelines"></a>Obecné pokyny

- **Nepoužívejte striktně vynutilo kontrakty šablony.** Šablona kontraktu ovládacího prvku se může skládat z prvků, příkazů, vazeb, triggerů nebo i nastavení vlastností, která jsou požadována nebo očekávána pro správné fungování ovládacího prvku.

  - Co nejvíce minimalizujte smlouvy.

  - Návrh kolem očekávání během návrhu (to znamená při použití nástroje pro návrh) je běžné, že šablona ovládacího prvku bude v nekompletním stavu. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nenabízí infrastrukturu stavu "sestavování", takže ovládací prvky musí být sestaveny se očekáváním, že takový stav může být platný.

  - Nevolejte výjimky, pokud není následován žádný aspekt kontraktu šablony. Na tyto řádky by panely neměly generovat výjimky, pokud mají příliš mnoho nebo příliš málo podřízených objektů.

- **Faktor periferních funkcí do pomocných prvků šablony.** Každý ovládací prvek by měl být zaměřen na jeho základní funkce a skutečnou polohu hodnoty a definovaný společným využitím ovládacího prvku. K tomuto účelu použijte kompozici a pomocné prvky v šabloně k povolení periferních chování a vizualizací, to znamená chování a vizualizace, které nepřispívají k základní funkci ovládacího prvku. Pomocné prvky spadají do tří kategorií:

  - **Samostatné** pomocné typy jsou veřejné a opakovaně použitelné ovládací prvky nebo primitivní prvky, které se používají anonymně v šabloně, což znamená, že ani pomocný prvek ani ovládací prvek se stylem nevědí. Technicky může být libovolný prvek anonymní typ, ale v tomto kontextu pojem popisuje tyto typy, které zapouzdřují specializované funkce pro povolení cílových scénářů.

  - Pomocné prvky **založené na typu** jsou nové typy, které zapouzdřují specializované funkce. Tyto prvky jsou obvykle navržené s užším rozsahem funkcí než běžné ovládací prvky nebo primitivní. Na rozdíl od samostatných pomocných prvků jsou pomocné prvky založené na typu vědomy kontextu, ve kterém jsou použity, a obvykle musí sdílet data s ovládacím prvkem, na jehož šablonu patří.

  - **Pojmenované** pomocné prvky jsou běžné ovládací prvky nebo primitivní prvky, které ovládací prvek očekává, že se v rámci šablony najde podle názvu. Tyto prvky mají v rámci šablony známý název, což umožňuje ovládacímu prvku najít prvek a pracovat s ním programově. V každé šabloně může být pouze jeden element se zadaným názvem.

  V následující tabulce jsou uvedeny pomocné prvky, které jsou již dnes použity pro styly ovládacích prvků (Tento seznam není vyčerpávající):

  |Prvek|Typ|Využíval|
  |-------------|----------|-------------|
  |<xref:System.Windows.Controls.ContentPresenter>|Založené na typu|<xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.Frame>atd. (všechny <xref:System.Windows.Controls.ContentControl> typy)|
  |<xref:System.Windows.Controls.ItemsPresenter>|Založené na typu|<xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.Menu>atd. (všechny <xref:System.Windows.Controls.ItemsControl> typy)|
  |<xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>|Jmenovanou|<xref:System.Windows.Controls.ToolBar>|
  |<xref:System.Windows.Controls.Primitives.Popup>|Skupin|<xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.ToolBar>, <xref:System.Windows.Controls.Menu>, <xref:System.Windows.Controls.ToolTip>atd.|
  |<xref:System.Windows.Controls.Primitives.RepeatButton>|Jmenovanou|<xref:System.Windows.Controls.Slider>, <xref:System.Windows.Controls.Primitives.ScrollBar>atd.|
  |<xref:System.Windows.Controls.Primitives.ScrollBar>|Jmenovanou|<xref:System.Windows.Controls.ScrollViewer>|
  |<xref:System.Windows.Controls.ScrollViewer>|Skupin|<xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.Menu>, <xref:System.Windows.Controls.Frame>atd.|
  |<xref:System.Windows.Controls.Primitives.TabPanel>|Skupin|<xref:System.Windows.Controls.TabControl>|
  |<xref:System.Windows.Controls.TextBox>|Jmenovanou|<xref:System.Windows.Controls.ComboBox>|
  |<xref:System.Windows.Controls.Primitives.TickBar>|Založené na typu|<xref:System.Windows.Controls.Slider>|

- **Minimalizujte požadované uživatelsky definované vazby nebo nastavení vlastností na pomocných prvcích**. Je běžné, že pomocný element vyžaduje určité vazby nebo nastavení vlastností, aby správně fungoval v rámci šablony ovládacího prvku. Pomocný prvek a ovládací prvek podle šablony by měl co nejvíc vytvořit tato nastavení. Při nastavování vlastností nebo vytváření vazeb je třeba vzít v potaz hodnoty nastavené uživatelem. Konkrétní osvědčené postupy jsou následující:

  - Pojmenované pomocné prvky by měly být identifikovány nadřazeným objektem a Nadřazená položka by měla vytvořit všechna požadovaná nastavení na pomocných prvcích.

  - Pomocné prvky založené na typu by měly vytvořit jakákoli požadovaná nastavení přímo na sebe. To může vyžadovat, aby se pomocný element dotazoval na kontext informací, ve kterém se používá, včetně jeho `TemplatedParent` (typ ovládacího prvku šablony, ve které se používá). Například <xref:System.Windows.Controls.ContentPresenter> automaticky váže vlastnost `Content` svého `TemplatedParent` na jeho <xref:System.Windows.Controls.ContentPresenter.Content%2A> vlastnost při použití v <xref:System.Windows.Controls.ContentControl> odvozeném typu.

  - Samostatné pomocné prvky nelze tímto způsobem optimalizovat, protože, dle definice nezpůsobí ani pomocný prvek ani nadřízený objekt ví o druhém.

- **Použijte vlastnost Name k označení prvků v rámci šablony**. Ovládací prvek, který potřebuje najít element ve stylu, aby k němu měl programově přístup, by měl používat vlastnost `Name` a `FindName` paradigma. Ovládací prvek by neměl vyvolat výjimku, pokud prvek nebyl nalezen, ale tiše a řádně zakázal funkčnost, která tento prvek vyžaduje.

- **Používejte osvědčené postupy pro vyjádření stavu a chování ovládacího prvku ve stylu.** Následuje uspořádaný seznam osvědčených postupů pro vyjádření změny stavu řízení a chování ve stylu. Měli byste použít první položku v seznamu, která umožňuje váš scénář.

  1. Vazba vlastnosti. Příklad: vazba mezi <xref:System.Windows.Controls.ComboBox.IsDropDownOpen%2A?displayProperty=nameWithType> a <xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A?displayProperty=nameWithType>.

  2. Byly aktivovány změny vlastností nebo animace vlastností. Příklad: stav najetí myší na <xref:System.Windows.Controls.Button>.

  3. Systému. Příklad: <xref:System.Windows.Controls.Primitives.ScrollBar.LineUpCommand> / <xref:System.Windows.Controls.Primitives.ScrollBar.LineDownCommand> v <xref:System.Windows.Controls.Primitives.ScrollBar>.

  4. Samostatné pomocné prvky. Příklad: <xref:System.Windows.Controls.Primitives.TabPanel> v <xref:System.Windows.Controls.TabControl>.

  5. Typy pomocníků založených na typech. Příklad: <xref:System.Windows.Controls.ContentPresenter> v <xref:System.Windows.Controls.Button><xref:System.Windows.Controls.Primitives.TickBar> v <xref:System.Windows.Controls.Slider>.

  6. Pojmenované pomocné prvky. Příklad: <xref:System.Windows.Controls.TextBox> v <xref:System.Windows.Controls.ComboBox>.

  7. Vybublinované události z pojmenovaných pomocných typů. Pokud naslouchat událostem z prvku stylu, měli byste vyžadovat, aby byl element, který událost vygeneroval, jednoznačně identifikovaný. Příklad: <xref:System.Windows.Controls.Primitives.Thumb> v <xref:System.Windows.Controls.ToolBar>.

  8. Vlastní chování `OnRender`. Příklad: <xref:Microsoft.Windows.Themes.ButtonChrome> v <xref:System.Windows.Controls.Button>.

- **Používejte k omezenému využití aktivačních procedur (na rozdíl od triggerů šablon)** . Aktivační události, které ovlivňují vlastnosti prvků v šabloně, musí být deklarovány v šabloně. Aktivační události, které mají vliv na vlastnosti ovládacího prvku (žádné `TargetName`), mohou být ve stylu deklarovány, pokud si nejste jisti, že změna šablony by měla také zničit Trigger.

- **Být konzistentní se stávajícími vzory stylu.** Často existuje několik způsobů, jak problém vyřešit. Mějte na paměti, že pokud je to možné, v souladu se stávajícími vzory stylu ovládacího prvku. To je obzvláště důležité pro ovládací prvky, které jsou odvozeny ze stejného základního typu (například <xref:System.Windows.Controls.ContentControl>, <xref:System.Windows.Controls.ItemsControl>, <xref:System.Windows.Controls.Primitives.RangeBase>a tak dále).

- **Vystavte vlastnosti pro povolení běžných scénářů přizpůsobení bez retemplating**. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] nepodporuje zapojitelné/přizpůsobitelné části, takže uživatel ovládacího prvku je ponechán pouze dvěma způsoby přizpůsobení: nastavení vlastností přímo nebo nastavování vlastností pomocí stylů. V takovém případě je vhodné vytvořit omezený počet vlastností cílených na velmi běžné a vysoce prioritní scénáře přizpůsobení, které by jinak vyžadovaly retemplating. Tady jsou osvědčené postupy, kdy a jak povolit scénáře přizpůsobení:

  - Velmi společná přizpůsobení by měla být vystavena jako vlastnosti ovládacího prvku a využívána šablonou.

  - Méně časté (ale ne zřídka) vlastní nastavení by mělo být zveřejněné jako připojené vlastnosti a spotřebované šablonou.

  - Je přijatelné pro známé, ale zřídka se vlastní nastavení, které vyžaduje retemplating.

<a name="Theme_Considerations"></a>

## <a name="theme-considerations"></a>Doporučení pro motiv

- **Styly motivů by se měly pokusit o konzistenci konzistentních vlastností ve všech motivech, ale nemají žádnou záruku**. V rámci své dokumentace by měl mít váš ovládací prvek dokument popisující sémantiku vlastností ovládacího prvku, což znamená "význam" vlastnosti ovládacího prvku. Například ovládací prvek <xref:System.Windows.Controls.ComboBox> by měl definovat význam vlastnosti <xref:System.Windows.Controls.Control.Background%2A> v rámci <xref:System.Windows.Controls.ComboBox>. Výchozí styly pro ovládací prvek by se měly pokusit postupovat podle sémantiky definované v tomto dokumentu ve všech motivech. Řízení uživatelů na druhé straně by mělo mít na paměti vědět, že sémantika vlastnosti může být změněna z motivu na motiv. V některých případech nemusí být daná vlastnost vyhodnotit pod vizuálními omezeními požadovanými konkrétním motivem. (Klasický motiv například nemá jednoduché ohraničení, na které `Thickness` lze použít pro mnoho ovládacích prvků.)

- **Styly motivů nemusejí mít jednotnou sémantiku triggeru ve všech motivech**. Chování, které je zveřejněné pomocí stylu ovládacího prvku prostřednictvím triggerů nebo animací, se může lišit od motivů k motivům. Řízení uživatelé by si měli být vědomi, že ovládací prvek nebude nutně používat stejný mechanismus pro dosažení konkrétního chování ve všech motivech. Jeden motiv může například použít animaci k vyjádření chování ukazatele myši, kde jiný motiv používá Trigger. To může mít za následek nekonzistence při zachování chování v přizpůsobených ovládacích prvcích. (Změna vlastnosti pozadí například nemusí ovlivnit stav ponechání ovládacího prvku, pokud je tento stav vyjádřen pomocí triggeru. Pokud je však stav při najetí myší implementován pomocí animace, změna na pozadí může irreparably přerušit animaci, a proto přechod stavu.)

- **Styly motivů nemusejí mít ve všech motivech konzistentní sémantiku "layout"** . Výchozí styl například nemusí zaručit, že ovládací prvek bude mít stejné množství velikosti ve všech motivech nebo zaručuje, že ovládací prvek bude mít stejné okraje obsahu nebo odsazení napříč všemi motivy.

## <a name="see-also"></a>Viz také:

- [Styly a šablony](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Přehled vytváření ovládacích prvků](control-authoring-overview.md)
