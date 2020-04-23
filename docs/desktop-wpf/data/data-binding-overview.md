---
title: Přehled datových vazeb
description: Informace o různých zdrojích dat, které můžete přidat do projektu v systému Windows Presentation Foundation pro .NET Core. Zdroje dat mohou být vázány na prvky XAML a vytvářet dynamické aplikace.
author: thraka
ms.date: 09/19/2019
ms.author: adegeo
dev_langs:
- csharp
- vb
ms.openlocfilehash: 7f17ff094a35c04ba880c87c6966d7d249817516
ms.sourcegitcommit: b75a45f0cfe012b71b45dd9bf723adf32369d40c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "82072009"
---
# <a name="data-binding-overview-in-wpf"></a>Přehled datové vazby v WPF

Datová vazba v platformě WPF (Windows Presentation Foundation) poskytuje jednoduchý a konzistentní způsob, jak mohou aplikace prezentovat data a pracovat s nimi. Prvky mohou být vázány na data z různých zdrojů dat ve formě objektů .NET a XML. Všechny <xref:System.Windows.Controls.ContentControl> například <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.ItemsControl>a všechny <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.ListView>, jako jsou a , mají vestavěné funkce umožňující flexibilní styling jednotlivých datových položek nebo kolekce datových položek. Zobrazení řazení, filtrování a skupinlze vygenerovat nad daty.

Funkce datové vazby v WPF má několik výhod oproti tradičním modelům, včetně vlastní podpory datové vazby širokou škálou vlastností, flexibilní reprezentace rozhraní dat a čisté oddělení obchodní logiky od ui.

Tento článek nejprve popisuje koncepty základní wpf datové vazby a potom zahrnuje použití <xref:System.Windows.Data.Binding> třídy a další funkce datové vazby.

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="what-is-data-binding"></a>Co je datová vazba?

Datová vazba je proces, který naváže spojení mezi unovým uznatým režimem aplikace a daty, která zobrazí. Pokud vazba má správné nastavení a data poskytuje správná oznámení, když data změní svou hodnotu, prvky, které jsou vázány na data automaticky odrážet změny. Datová vazba může také znamenat, že pokud se změní vnější reprezentace dat v prvku, pak podkladová data mohou být automaticky aktualizována tak, aby odrážela změnu. Pokud například uživatel upraví hodnotu `TextBox` v prvku, základní hodnota dat se automaticky aktualizuje tak, aby odrážela tuto změnu.

Typické použití datové vazby je umístit server nebo místní konfigurační data do formulářů nebo jiných ovládacích prvků ui. V WPF tento koncept je rozšířen a zahrnuje vazbu širokou škálu vlastností na různé zdroje dat. Ve WPF mohou být vlastnosti závislostí prvků vázány na objekty .NET (včetně ADO.NET objektů nebo objektů přidružených k webovým službám a webovým vlastnostem) a dat xml.

Příklad datové vazby například podívejte se na následující ui aplikace z [ukázky datové vazby][data-binding-demo], která zobrazuje seznam položek aukce.

![Ukázkový snímek obrazovky datové vazby](./media/data-binding-overview/demo.png "DataBinding_DataBindingDemo")

Aplikace ukazuje následující funkce datové vazby:

- Obsah ListBox je vázán na kolekci *AuctionItem* objekty. Objekt *AuctionItem* má vlastnosti jako *Description*, *StartPrice*, *StartDate*, *Category*, *SpecialFeatures*a tak dále.

- Data *(AuctionItem* objekty) zobrazené v `ListBox` je šablona tak, aby popis a aktuální cena jsou zobrazeny pro každou položku. Šablona je vytvořena <xref:System.Windows.DataTemplate>pomocí . Kromě toho vzhled každé položky závisí na *SpecialFeatures* hodnotu *AuctionItem* se zobrazí. Pokud je hodnota *SpecialFeatures* *položky AuctionItem* *Barva*, má položka modré ohraničení. Pokud je hodnota *Zvýraznit*, má položka oranžové ohraničení a hvězdičku. Část [Data Templating](#data-templating) obsahuje informace o šablonování dat.

- Uživatel může data seskupit, `CheckBoxes` filtrovat nebo řadit pomocí dodaných dat. Na obrázku výše jsou vybrány **možnostI Seskupit podle kategorie** a **Seřadit podle kategorie a data.** `CheckBoxes` Možná jste si všimli, že data jsou seskupena na základě kategorie produktu a název kategorie je v abecedním pořadí. Je obtížné si všimnout z obrázku, ale položky jsou také seřazeny podle počátečního data v rámci každé kategorie. Řazení se provádí pomocí *zobrazení kolekce*. Vazby [kolekce](#binding-to-collections) části popisuje zobrazení kolekce.

- Když uživatel vybere položku, <xref:System.Windows.Controls.ContentControl> zobrazí se podrobnosti o vybrané položce. Tato zkušenost se nazývá *scénář hlavního detailu*. Část [Scénář hlavního textu](#master-detail-binding-scenario) obsahuje informace o tomto typu vazby.

- Typ vlastnosti *StartDate* <xref:System.DateTime>je , která vrací datum, které obsahuje čas do milisekundy. V této aplikaci byl použit vlastní převaděč tak, aby se zobrazil kratší řetězec data. Část [Převod dat](#data-conversion) obsahuje informace o převaděčích.

Když uživatel vybere tlačítko *Přidat produkt,* zobrazí se následující formulář.

![Stránka Přidat výpis produktů](./media/data-binding-overview/demo-addproductlisting.png "DataBinding_Demo_AddProductListing")

Uživatel může upravit pole ve formuláři, zobrazit náhled výpisu produktu pomocí `Submit` krátkých nebo podrobných panelů náhledu a vybrat přidání nového výpisu produktu. Pro novou položku se budou vztahovat všechna existující nastavení seskupení, filtrování a řazení. V tomto konkrétním případě se položka zadaná na výše uvedeném obrázku zobrazí jako druhá položka v kategorii *Počítač.*

Na tomto obrázku není zobrazena logika ověření uvedená v *počátečním datu* <xref:System.Windows.Controls.TextBox>. Pokud uživatel zadá neplatné datum (neplatné formátování nebo minulé datum), bude <xref:System.Windows.Controls.ToolTip> upozorněn a červeným vykřičníkem vedle <xref:System.Windows.Controls.TextBox>. Část [Ověření dat](#data-validation) popisuje, jak vytvořit logiku ověření.

Než přejdeme k různým funkcím výše popsané datové vazby, nejprve probereme základní koncepty, které jsou důležité pro pochopení datové vazby WPF.

## <a name="basic-data-binding-concepts"></a>Základní koncepty datové vazby

Bez ohledu na to, jaký prvek jste vazby a povahu zdroje dat, každá vazba vždy následuje model znázorněno na následujícím obrázku.

![Diagram, který zobrazuje základní model datové vazby.](./media/data-binding-overview/basic-data-binding-diagram.png)

Jak ukazuje obrázek, vazby dat je v podstatě most mezi cíl vazby a zdroj vazby. Obrázek ukazuje následující základní koncepty datové vazby WPF:

- Každá vazba má obvykle čtyři součásti:

  - Cílový objekt vazby.
  - Cílová vlastnost.
  - Zdroj vazby.
  - Cesta k hodnotě ve zdroji vazby, který chcete použít.
  
  > Chcete-li například svázat obsah `TextBox` a `Employee.Name` s vlastností, cílový `TextBox`objekt je vlastnost <xref:System.Windows.Controls.TextBox.Text%2A> , cílová vlastnost je vlastnost, hodnota, která má být používána, je *Name*a zdrojový objekt je Objekt *Employee.*

- Vlastnost target musí být vlastnost závislosti. Většina <xref:System.Windows.UIElement> vlastností jsou vlastnosti závislostí a většina vlastností závislostí, s výjimkou těch jen pro čtení, podporuje datové vazby ve výchozím nastavení. (Pouze typy odvozené z <xref:System.Windows.DependencyObject> můžete definovat <xref:System.Windows.UIElement> vlastnosti `DependencyObject`závislostí; a všechny typy odvozené z .)

- Ačkoli není zobrazenna obrázku, je třeba poznamenat, že zdrojový objekt vazby není omezen na vlastní objekt .NET. Datová vazba WPF podporuje data ve formě objektů .NET a XML. Chcete-li uvést některé příklady, <xref:System.Windows.UIElement>může být zdrojem vazby libovolný objekt seznamu, objekt ADO.NET nebo webových služeb nebo xmlnode, který obsahuje data XML. Další informace naleznete v [tématu Přehled zdrojů vazby](../../framework/wpf/data/binding-sources-overview.md).

Je důležité si uvědomit, že při vytváření vazby, jsou vazby *cíl* vazby na zdroj vazby. Pokud například zobrazujete některá podkladová <xref:System.Windows.Controls.ListBox> data XML v datové `ListBox` vazbě pomocí, svážete data XML.

Chcete-li vytvořit vazbu, <xref:System.Windows.Data.Binding> použijte objekt. Zbývající část tohoto článku popisuje mnoho konceptů spojených s a některé `Binding` vlastnosti a použití objektu.

### <a name="direction-of-the-data-flow"></a>Směr toku dat

Jak je uvedeno na šipku na předchozím obrázku, tok dat vazby může přejít z cíle vazby na zdroj vazby (například zdrojová hodnota se změní, když uživatel upraví hodnotu `TextBox`) a/nebo ze zdroje vazby na cíl vazby (například váš `TextBox` obsah je aktualizován změnami ve zdroji vazby), pokud zdroj vazby poskytuje správná oznámení.

Můžete chtít, aby vaše aplikace umožnila uživatelům změnit data a šířit je zpět do zdrojového objektu. Nebo možná nebudete chtít povolit uživatelům aktualizovat zdrojová data. Tok dat můžete řídit nastavením . <xref:System.Windows.Data.Binding.Mode?displayProperty=nameWithType>

Tento obrázek znázorňuje různé typy toku dat:

![Datový tok datové vazby](./media/data-binding-overview/databinding-dataflow.png "DataBinding_DataFlow")

- <xref:System.Windows.Data.BindingMode.OneWay>vazba způsobí, že změny vlastnosti source automaticky aktualizují cílovou vlastnost, ale změny vlastnosti target nejsou šířeny zpět do vlastnosti source. Tento typ vazby je vhodné, pokud je vázán ovládací prvek je implicitně jen pro čtení. Můžete se například vázat na zdroj, jako je burzovní burzovní burzovní burzovní burzovní burzovní burzovní, nebo možná vaše cílová vlastnost nemá žádné ovládací rozhraní pro provádění změn, jako je například barva pozadí svázaná s daty tabulky. Pokud není nutné sledovat změny cílové vlastnosti, <xref:System.Windows.Data.BindingMode.OneWay> pomocí režimu vazby <xref:System.Windows.Data.BindingMode.TwoWay> se vyhnete režii režimu vazby.

- <xref:System.Windows.Data.BindingMode.TwoWay>vazba způsobí změny zdrojové vlastnosti nebo cílové vlastnosti, které automaticky aktualizují druhou vlastnost. Tento typ vazby je vhodný pro upravitelné formuláře nebo jiné plně interaktivní scénáře nového nenasytného režimu. Většina vlastností výchozí <xref:System.Windows.Data.BindingMode.OneWay> vazbu, ale některé vlastnosti závislostí (obvykle <xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType> vlastnosti uživatelem upravitelné ovládací prvky, jako je například a [CheckBox.IsChecked](xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked) výchozí vazba. <xref:System.Windows.Data.BindingMode.TwoWay> Programový způsob, jak zjistit, zda závislost vlastnost váže jednosměrný nebo obousměrný ve výchozím <xref:System.Windows.DependencyProperty.GetMetadata%2A?displayProperty=nameWithType> nastavení je získat metadata <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A?displayProperty=nameWithType> vlastnosti s a potom zkontrolujte boolean hodnotu vlastnosti.

- <xref:System.Windows.Data.BindingMode.OneWayToSource>je opakem <xref:System.Windows.Data.BindingMode.OneWay> vazby; aktualizuje vlastnost source při změně vlastnosti target. Jeden příklad scénáře je, pokud stačí přehodnotit zdrojovou hodnotu z ui.

- Není znázorněno na <xref:System.Windows.Data.BindingMode.OneTime> obrázku je vazby, což způsobí, že vlastnost source inicializovat cíl vlastnost, ale nešíří následné změny. Pokud se změní kontext dat nebo objekt v kontextu dat, změna se *neprojeví* v cílové vlastnosti. Tento typ vazby je vhodné, pokud je vhodný snímek aktuálního stavu nebo data je skutečně statické. Tento typ vazby je také užitečné, pokud chcete inicializovat cílovou vlastnost s nějakou hodnotu ze zdrojové vlastnosti a kontext dat není předem znám. Tento režim je v <xref:System.Windows.Data.BindingMode.OneWay> podstatě jednodušší forma vazby, která poskytuje lepší výkon v případech, kdy se nezmění zdrojová hodnota.

Chcete-li zjistit změny <xref:System.Windows.Data.BindingMode.OneWay> <xref:System.Windows.Data.BindingMode.TwoWay> zdroje (použitelné pro a vazby), zdroj <xref:System.ComponentModel.INotifyPropertyChanged>musí implementovat vhodný mechanismus oznamování změny vlastnosti, jako je například . Viz [Postup: Implementovat oznámení o změně vlastnosti](../../framework/wpf/data/how-to-implement-property-change-notification.md) pro příklad <xref:System.ComponentModel.INotifyPropertyChanged> implementace.

Vlastnost <xref:System.Windows.Data.Binding.Mode?displayProperty=nameWithType> poskytuje další informace o režimech vazby a příklad, jak určit směr vazby.

### <a name="what-triggers-source-updates"></a>Co aktivuje zdrojové aktualizace

Vazby, <xref:System.Windows.Data.BindingMode.TwoWay> které <xref:System.Windows.Data.BindingMode.OneWayToSource> jsou nebo poslouchat změny v cílové vlastnosti a šířit je zpět do zdroje, označované jako aktualizace zdroje. Můžete například upravit text textového pole a změnit základní zdrojovou hodnotu.

Je však zdrojová hodnota aktualizována při úpravách textu nebo po dokončení úprav textu a ovládací prvek ztratí fokus? Vlastnost <xref:System.Windows.Data.Binding.UpdateSourceTrigger?displayProperty=nameWithType> určuje, co aktivuje aktualizaci zdroje. Tečky šipky vpravo na následujícím obrázku ilustrují roli vlastnosti. <xref:System.Windows.Data.Binding.UpdateSourceTrigger?displayProperty=nameWithType>

![Diagram, který zobrazuje roli UpdateSourceTrigger vlastnost.](./media/data-binding-overview/data-binding-updatesource-trigger.png)

Pokud `UpdateSourceTrigger` je <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged?displayProperty=nameWithType>hodnota , pak hodnota, na <xref:System.Windows.Data.BindingMode.TwoWay> kterou <xref:System.Windows.Data.BindingMode.OneWayToSource> se ukazuje šipka vpravo nebo vazby, je aktualizována, jakmile se změní vlastnost target. Pokud je `UpdateSourceTrigger` však <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>hodnota , pak je tato hodnota aktualizována pouze novou hodnotou, když cílová vlastnost ztratí fokus.

Podobně jako <xref:System.Windows.Data.Binding.Mode%2A> vlastnost mají různé vlastnosti <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> závislostí různé výchozí hodnoty. Výchozí hodnota pro většinu vlastností závislostí je <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, zatímco `TextBox.Text` vlastnost má výchozí hodnotu <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>. `PropertyChanged`znamená, že aktualizace zdroje obvykle dojít vždy, když se změní cílová vlastnost. Okamžité změny jsou v pořádku pro zaškrtávací políčka a další jednoduché ovládací prvky. U textových polí však aktualizace po každém stisknutí klávesy může snížit výkon a odepře uživateli obvyklou příležitost k backspace a opravit chyby při psaní před potvrzením nové hodnoty.

Informace <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> o tom, jak najít výchozí hodnotu vlastnosti závislosti, naleznete na stránce vlastností.

Následující tabulka obsahuje příklad scénáře <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> pro <xref:System.Windows.Controls.TextBox> každou hodnotu pomocí jako příklad.

| Hodnota UpdateSourceTrigger | Při aktualizaci zdrojové hodnoty | Příklad scénáře pro textbox |
| ------------------------- | ---------------------------------- | ---------------------------- |
| `LostFocus`(výchozí <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>pro ) | Když ovládací prvek TextBox ztratí fokus. | Textbox, který je spojen s logikou ověřování (viz [ověření dat](#data-validation) níže). |
| `PropertyChanged` | Při psaní do <xref:System.Windows.Controls.TextBox>. | Ovládací prvky TextBox v okně chatovací místnosti. |
| `Explicit` | Když aplikace <xref:System.Windows.Data.BindingExpression.UpdateSource%2A>volá . | TextBox ovládací prvky v upravitelné podobě (aktualizuje zdrojové hodnoty pouze v případě, že uživatel klepne na tlačítko odeslat). |

Příklad najdete v [tématu How to: Control when the TextBox text updates the source](../../framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md).

## <a name="creating-a-binding"></a>Vytvoření vazby

Chcete-li znovu některé koncepty popsané v předchozích částech, <xref:System.Windows.Data.Binding> vytvořte vazbu pomocí objektu a každá vazba má obvykle čtyři součásti: cíl vazby, cílovou vlastnost, zdroj vazby a cestu ke zdrojové hodnotě, která má být používána. Tato část popisuje, jak nastavit vazbu.

Vezměme si následující příklad, ve kterém zdrojový objekt vazby je třída s názvem *MyData,* která je definována v oboru názvů *SDKSample.* Pro účely demonstrace *má MyData* vlastnost řetězce s názvem *ColorName,* jejíž hodnota je nastavena na "Red". Tento příklad tedy generuje tlačítko s červeným pozadím.

[!code-xaml[BindNonTextProperty](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/AutoConvertPropertyToColor.xaml#BindAutoConvertColor)]

Další informace o syntaxi deklarace vazby a příklady nastavení vazby v kódu naleznete v [tématu Přehled deklarací vazby](../../framework/wpf/data/binding-declarations-overview.md).

Pokud použijeme tento příklad v našem základním diagramu, výsledný obrázek vypadá takto. Toto číslo <xref:System.Windows.Data.BindingMode.OneWay> popisuje vazbu, <xref:System.Windows.Data.BindingMode.OneWay> protože vlastnost Background ve výchozím nastavení podporuje vazbu.

![Diagram, který zobrazuje vlastnost pozadí datové vazby.](./media/data-binding-overview/data-binding-button-background-example.png)

Možná se divíte, proč tato vazba funguje, <xref:System.Windows.Controls.Control.Background%2A> i když <xref:System.Windows.Media.Brush> *ColorName* vlastnost je typu řetězec, zatímco vlastnost je typu . Tato vazba používá výchozí převod typu, který je popsán v části [Převod dat.](#data-conversion)

### <a name="specifying-the-binding-source"></a>Určení zdroje vazby

Všimněte si, že v předchozím příkladu je zdroj vazby určen nastavením vlastnosti [DockPanel.DataContext.](xref:System.Windows.FrameworkElement.DataContext) Potom <xref:System.Windows.Controls.Button> dědí <xref:System.Windows.FrameworkElement.DataContext%2A> hodnotu <xref:System.Windows.Controls.DockPanel>z , což je jeho nadřazený prvek. Chcete-li zopakovat, objekt zdroje vazby je jednou ze čtyř nezbytných součástí vazby. Proto bez zadaný objekt zdroje vazby by vazba neprovede nic.

Existuje několik způsobů, jak určit zdrojový objekt vazby. Použití <xref:System.Windows.FrameworkElement.DataContext%2A> vlastnosti nadřazeného prvku je užitečné, pokud vazby více vlastností na stejný zdroj. Někdy však může být vhodnější určit zdroj vazby na jednotlivé deklarace vazby. Pro předchozí příklad namísto <xref:System.Windows.FrameworkElement.DataContext%2A> použití vlastnosti můžete zadat zdroj <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> vazby nastavením vlastnosti přímo na deklaraci vazby tlačítka, jako v následujícím příkladu.

[!code-xaml[BindNonTextPropertyCompactBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/AutoConvertPropertyToColor.xaml#BindAutoConvertColorCompactBinding)]

Jiné než <xref:System.Windows.FrameworkElement.DataContext%2A> nastavení vlastnosti na prvek <xref:System.Windows.FrameworkElement.DataContext%2A> přímo, dědění hodnoty od předchůdce (například tlačítko v prvním příkladu) a explicitně určení zdroje vazby nastavením <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> <xref:System.Windows.Data.Binding.ElementName?displayProperty=nameWithType> vlastnosti <xref:System.Windows.Data.Binding.RelativeSource?displayProperty=nameWithType> na vazbě (například tlačítko poslední příklad), můžete také použít vlastnost nebo vlastnost k určení zdroje vazby. Vlastnost <xref:System.Windows.Data.Binding.ElementName%2A> je užitečná, když jste vazby na jiné prvky v aplikaci, například při použití posuvníku upravit šířku tlačítka. Vlastnost <xref:System.Windows.Data.Binding.RelativeSource%2A> je užitečná, pokud je <xref:System.Windows.Controls.ControlTemplate> vazba <xref:System.Windows.Style>zadána v nebo . Další informace naleznete v [tématu How to: Specify the binding source](../../framework/wpf/data/how-to-specify-the-binding-source.md).

### <a name="specifying-the-path-to-the-value"></a>Určení cesty k hodnotě

Pokud je váš zdroj vazby <xref:System.Windows.Data.Binding.Path?displayProperty=nameWithType> objekt, použijte vlastnost k určení hodnoty, která má být pro vazbu používána. Pokud se vážete k datům <xref:System.Windows.Data.Binding.XPath?displayProperty=nameWithType> XML, použijte vlastnost k určení hodnoty. V některých případech může být <xref:System.Windows.Data.Binding.Path%2A> použitelné pro použití vlastnosti i v případě, že vaše data jsou XML. Například pokud chcete získat přístup name vlastnost vrácené XmlNode (jako výsledek dotazu XPath), měli byste použít <xref:System.Windows.Data.Binding.Path%2A> vlastnost kromě vlastnosti. <xref:System.Windows.Data.Binding.XPath%2A>

Další informace naleznete <xref:System.Windows.Data.Binding.Path%2A> v <xref:System.Windows.Data.Binding.XPath%2A> tématu a vlastnosti.

I když jsme zdůraznili, že <xref:System.Windows.Data.Binding.Path%2A> hodnota to použít je jedním ze čtyř nezbytných součástí vazby, ve scénářích, které chcete vytvořit vazbu na celý objekt, hodnota, která má být stejná jako zdrojový objekt vazby. V těchto případech se použije na <xref:System.Windows.Data.Binding.Path%2A>nespecifikovat . Představte si následující příklad.

[!code-xaml[EmptyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/EmptyBinding.xaml#EmptyBinding)]

Výše uvedený příklad používá syntaxi prázdné vazby: {Binding}. V tomto případě <xref:System.Windows.Controls.ListBox> dědí DataContext z nadřazeného DockPanel element (není uvedeno v tomto příkladu). Pokud cesta není zadána, výchozí je vazba na celý objekt. Jinými slovy v tomto příkladu cesta byla vynechána, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> protože jsme vazby vlastnost celý objekt. (Viz [vazby na kolekce](#binding-to-collections) části pro podrobnou diskusi.)

Jiné než vazba na kolekci, tento scénář je také užitečné, pokud chcete vytvořit vazbu na celý objekt namísto pouze jednu vlastnost objektu. Například pokud je zdrojový objekt <xref:System.String>typu , můžete jednoduše vytvořit vazbu na samotný řetězec. Dalším běžným scénářem je, když chcete svázat prvek s objektem s několika vlastnostmi.

Možná budete muset použít vlastní logiku tak, aby data byla smysluplná pro vlastnost target bound. Vlastní logika může být ve formě vlastního převaděče, pokud výchozí převod typu neexistuje. Informace o převaděčích najdete v [tématu Převod dat.](#data-conversion)

### <a name="binding-and-bindingexpression"></a>Vazba a bindingexpression

Než se dostanete do jiných funkcí a použití datové <xref:System.Windows.Data.BindingExpression> vazby, je užitečné zavést třídu. Jak jste viděli v předchozích částech, <xref:System.Windows.Data.Binding> třída je třída na vysoké úrovni pro deklaraci vazby; poskytuje mnoho vlastností, které umožňují určit charakteristiky vazby. Související třída <xref:System.Windows.Data.BindingExpression>, je základní objekt, který udržuje spojení mezi zdrojem a cílem. Vazba obsahuje všechny informace, které mohou být sdíleny mezi několika výrazy vazby. A <xref:System.Windows.Data.BindingExpression> je výraz instance, který nelze sdílet a <xref:System.Windows.Data.Binding>obsahuje všechny informace o instanci .

Vezměme si `myDataObject` následující příklad, `MyData` kde `myBinding` je instance <xref:System.Windows.Data.Binding> třídy, je zdrojový objekt a `MyData` `MyDataProperty`je definovaná třída, která obsahuje vlastnost string s názvem . Tento příklad sváže textový `myText`obsah , <xref:System.Windows.Controls.TextBlock>instance `MyDataProperty`.

[!code-csharp[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/ManualBinding.cs#CodeOnlyBinding)]
[!code-vb[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/ManualBinding.vb#CodeOnlyBinding)]

Můžete použít stejný *objekt myBinding* k vytvoření dalších vazeb. Objekt *myBinding* můžete například použít k vytvoření vazby textového obsahu zaškrtávacího políčka na *vlastnost MyDataProperty*. V tomto scénáři budou existovat <xref:System.Windows.Data.BindingExpression> dvě instance sdílení *myBinding* objektu.

Objekt <xref:System.Windows.Data.BindingExpression> je vrácen <xref:System.Windows.Data.BindingOperations.GetBindingExpression%2A> voláním objektu vázaného na data. Následující články ukazují některé použití <xref:System.Windows.Data.BindingExpression> třídy:

- [Získání objektu vazby z vlastnosti cíle vazby](../../framework/wpf/data/how-to-get-the-binding-object-from-a-bound-target-property.md)

- [Určit, kdy text TextBox aktualizuje zdroj](../../framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md)

## <a name="data-conversion"></a>Převod dat

V [části Vytvoření vazby](#creating-a-binding) je tlačítko <xref:System.Windows.Controls.Control.Background%2A> červené, protože jeho vlastnost je vázána na vlastnost řetězce s hodnotou "Červená". Tato hodnota řetězce funguje, protože převaděč typu je k dispozici na <xref:System.Windows.Media.Brush> typu převést hodnotu řetězce na <xref:System.Windows.Media.Brush>.

Přidání těchto informací na obrázek [Vytvoření vazby](#creating-a-binding) části vypadá takto.

![Diagram, který zobrazuje vlastnost Default datové vazby.](./media/data-binding-overview/data-binding-button-default-conversion.png)

Však co v případě, že místo toho, aby *Color* vlastnost typu <xref:System.Windows.Media.Color>řetězce vazby zdrojový objekt má Color vlastnost typu ? V takovém případě, aby vazba pracovat, budete muset nejprve změnit Color <xref:System.Windows.Controls.Control.Background%2A> *hodnotu* vlastnosti do něčeho, co přijímá vlastnost. Budete muset vytvořit vlastní převaděč <xref:System.Windows.Data.IValueConverter> implementací rozhraní, jako v následujícím příkladu.

[!code-csharp[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/ColorBrushConverter.cs#ColorBrushConverter)]
[!code-vb[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/ColorBrushConverter.vb#ColorBrushConverter)]

Další informace naleznete v tématu <xref:System.Windows.Data.IValueConverter>.

Nyní se místo výchozího převodu používá vlastní převaděč a náš diagram vypadá takto.

![Diagram, který zobrazuje vlastní převaděč datové vazby.](./media/data-binding-overview/data-binding-converter-color-example.png)

Chcete-li zopakovat, výchozí převody mohou být k dispozici z důvodu převaděče typu, které jsou k dispozici v typu je vázán. Toto chování bude záviset na tom, které převaděče typu jsou k dispozici v cíli. V případě pochybností si vytvořte vlastní konvertor.

Níže jsou uvedeny některé typické scénáře, kde má smysl implementovat převaděč dat:

- Vaše data by měla být zobrazena odlišně, v závislosti na jazykové verzi. Můžete například implementovat převodník měn nebo převodník kalendářního data a času na základě konvencí používaných v určité jazykové verzi.

- Používaná data nemusí nutně změnit textovou hodnotu vlastnosti, ale místo toho jsou určena ke změně jiné hodnoty, například zdroje obrazu nebo barvy nebo stylu zobrazovaného textu. Převaděče lze použít v tomto případě převedením vazby vlastnosti, která se nemusí zdát vhodné, jako je například vazba textové pole na Pozadí vlastnost buňky tabulky.

- Více než jeden ovládací prvek nebo více vlastností ovládacích prvků jsou vázány na stejná data. V tomto případě primární vazby může pouze zobrazit text, vzhledem k tomu, že jiné vazby zpracovat konkrétní problémy zobrazení, ale stále používat stejnou vazbu jako zdrojové informace.

- Cílová vlastnost má kolekci vazeb, která <xref:System.Windows.Data.MultiBinding>se nazývá . Pro <xref:System.Windows.Data.MultiBinding>, můžete <xref:System.Windows.Data.IMultiValueConverter> použít vlastní k vytvoření konečné hodnoty z hodnot vazby. Například barva může být vypočítána z červených, modrých a zelených hodnot, což mohou být hodnoty ze stejných nebo různých zdrojových objektů vazby. Viz <xref:System.Windows.Data.MultiBinding> příklady a informace.

## <a name="binding-to-collections"></a>Vazba na kolekce

Zdrojový objekt vazby lze považovat buď za jeden objekt, jehož vlastnosti obsahují data, nebo jako shromažďování dat polymorfních objektů, které jsou často seskupeny (například výsledek dotazu do databáze). Zatím jsme diskutovali pouze o vazbě na jednotlivé objekty. Vazba na shromažďování dat je však běžný scénář. Běžným scénářem je například <xref:System.Windows.Controls.ItemsControl> použití <xref:System.Windows.Controls.ListBox>například <xref:System.Windows.Controls.ListView> <xref:System.Windows.Controls.TreeView> , nebo zobrazení kolekce dat, například v aplikaci zobrazené v části [Co je datová vazba.](#what-is-data-binding)

Naštěstí náš základní diagram stále platí. Pokud jste vazba na <xref:System.Windows.Controls.ItemsControl> kolekci, diagram vypadá takto.

![Diagram, který zobrazuje objekt ItemsControl datové vazby.](./media/data-binding-overview/data-binding-itemscontrol.png)

Jak je znázorněno v <xref:System.Windows.Controls.ItemsControl> tomto diagramu, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A?displayProperty=nameWithType> chcete-li svázat s objektem kolekce, vlastnost je vlastnost, která má být používána. Můžete si `ItemsSource` myslet, jak <xref:System.Windows.Controls.ItemsControl>obsah . Vazba <xref:System.Windows.Data.BindingMode.OneWay> je, `ItemsSource` protože `OneWay` vlastnost podporuje vazbu ve výchozím nastavení.

### <a name="how-to-implement-collections"></a>Jak implementovat kolekce

Můžete výčet přes všechny kolekce, která <xref:System.Collections.IEnumerable> implementuje rozhraní. Chcete-li však nastavit dynamické vazby tak, aby vložení nebo odstranění v kolekci automaticky <xref:System.Collections.Specialized.INotifyCollectionChanged> aktualizovat uživatelské rozhraní, kolekce musí implementovat rozhraní. Toto rozhraní zveřejňuje událost, která by měla být vyvolána při každé změně podkladové kolekce.

WPF poskytuje <xref:System.Collections.ObjectModel.ObservableCollection%601> třídu, která je vestavěnou implementací <xref:System.Collections.Specialized.INotifyCollectionChanged> kolekce dat, která zveřejňuje rozhraní. Chcete-li plně podporovat přenos datových hodnot ze zdrojových objektů na cíle, <xref:System.ComponentModel.INotifyPropertyChanged> musí každý objekt v kolekci, který podporuje vlastnosti s možností vazby, také implementovat rozhraní. Další informace naleznete v [tématu Přehled zdrojů vazby](../../framework/wpf/data/binding-sources-overview.md).

Před implementací vlastní kolekce <xref:System.Collections.ObjectModel.ObservableCollection%601> zvažte použití nebo jednu <xref:System.Collections.Generic.List%601> <xref:System.Collections.ObjectModel.Collection%601>z <xref:System.ComponentModel.BindingList%601>existujících tříd kolekce, například , , a , mezi mnoha dalšími. Pokud máte pokročilý scénář a chcete implementovat vlastní <xref:System.Collections.IList>kolekci, zvažte použití , který poskytuje neobecné kolekce objektů, které lze individuálně přistupovat index a tedy poskytuje nejlepší výkon.

### <a name="collection-views"></a>Zobrazení kolekcí

Jakmile <xref:System.Windows.Controls.ItemsControl> je vaše svázané se shromažďováním dat, můžete data seřadit, filtrovat nebo seskupit. Chcete-li to provést, použijte zobrazení kolekce, <xref:System.ComponentModel.ICollectionView> které jsou třídy, které implementují rozhraní.

#### <a name="what-are-collection-views"></a>Co jsou zobrazení kolekce?

Zobrazení kolekce je vrstva nad zdrojovou kolekcí vazby, která umožňuje procházet a zobrazovat zdrojovou kolekci na základě dotazů řazení, filtrování a skupin, aniž byste museli měnit samotnou základní zdrojovou kolekci. Zobrazení kolekce také udržuje ukazatel na aktuální položku v kolekci. Pokud zdrojkolekce implementuje <xref:System.Collections.Specialized.INotifyCollectionChanged> rozhraní, změny <xref:System.Collections.Specialized.INotifyCollectionChanged.CollectionChanged> vyvolané události jsou rozšířeny do zobrazení.

Vzhledem k tomu, že zobrazení nemění základní zdrojové kolekce, každá zdrojová kolekce může mít více zobrazení s ním spojené. Můžete mít například *kolekci* Task objekty. Při použití zobrazení můžete zobrazit stejná data různými způsoby. Na levé straně stránky můžete například zobrazit úkoly seřazené podle priority a na pravé straně seskupené podle oblasti.

#### <a name="how-to-create-a-view"></a>Jak vytvořit zobrazení

Jedním ze způsobů, jak vytvořit a použít zobrazení je konkretizovat objekt zobrazení přímo a pak jej použít jako zdroj vazby. Zvažte například ukázkovou aplikaci [datové vazby][data-binding-demo] zobrazenou v části [Co je datová vazba.](#what-is-data-binding) Aplikace je implementována <xref:System.Windows.Controls.ListBox> tak, že se váže na zobrazení přes shromažďování dat namísto shromažďování dat přímo. Následující příklad je extrahován z ukázkové aplikace [datové vazby.][data-binding-demo] Třída <xref:System.Windows.Data.CollectionViewSource> je proxy xaml třídy, která <xref:System.Windows.Data.CollectionView>dědí z . V tomto konkrétním <xref:System.Windows.Data.CollectionViewSource.Source%2A> příkladu zobrazení je vázána na *AuctionItems* kolekce (typu) <xref:System.Collections.ObjectModel.ObservableCollection%601>aktuální ho objektu aplikace.

[!code-xaml[CollectionView](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#CollectionView)]

Zdroj *výpisDataView* pak slouží jako zdroj vazby pro prvky v aplikaci, jako je například <xref:System.Windows.Controls.ListBox>.

[!code-xaml[ListBoxCollectionView](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#ListBoxCollectionView)]

Chcete-li vytvořit jiné zobrazení pro stejnou <xref:System.Windows.Data.CollectionViewSource> kolekci, můžete `x:Key` vytvořit jinou instanci a dát jí jiný název.

V následující tabulce je uvedeno, jaké datové typy <xref:System.Windows.Data.CollectionViewSource> zobrazení jsou vytvořeny jako výchozí zobrazení kolekce nebo podle typu zdrojové kolekce.

| Typ zdrojové kolekce                    | Typ zobrazení kolekce | Poznámky |
| ----------------------------------------- | -------------------- | ----- |
| <xref:System.Collections.IEnumerable>     | Interní typ založený na<xref:System.Windows.Data.CollectionView> | Položky nelze seskupit. |
| <xref:System.Collections.IList>           | <xref:System.Windows.Data.ListCollectionView> | Nejrychlejší. |
| <xref:System.ComponentModel.IBindingList> | <xref:System.Windows.Data.BindingListCollectionView> | |

#### <a name="using-a-default-view"></a>Použití výchozího zobrazení

Určení zobrazení kolekce jako zdroje vazby je jedním ze způsobů, jak vytvořit a použít zobrazení kolekce. WPF také vytvoří výchozí zobrazení kolekce pro každou kolekci, která se používá jako zdroj vazby. Pokud svážete přímo na kolekci, WPF váže na jeho výchozí zobrazení. Toto výchozí zobrazení je sdíleno všemi vazbami do stejné kolekce, takže změna provedená ve výchozím zobrazení jedním vázaným ovládacím prvkem nebo kódem (například řazení nebo změna ukazatele aktuální položky, popisovaná později) se projeví ve všech ostatních vazbách do stejné kolekce.

Chcete-li získat výchozí zobrazení, použijte metodu. <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> Příklad najdete v [tématu Získání výchozího zobrazení kolekce dat](../../framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md).

#### <a name="collection-views-with-adonet-datatables"></a>Zobrazení kolekce s ADO.NET datatables

Chcete-li zlepšit výkon, <xref:System.Data.DataTable> <xref:System.Data.DataView> zobrazení kolekce pro ADO.NET nebo <xref:System.Data.DataView>objekty delegovat řazení a filtrování na , což způsobí, že řazení a filtrování, které mají být sdíleny ve všech zobrazení kolekce zdroje dat. Chcete-li povolit každé zobrazení kolekce seřadit a filtrovat <xref:System.Data.DataView> nezávisle, inicializovat každé zobrazení kolekce s vlastním objektem.

#### <a name="sorting"></a>Řazení

Jak již bylo zmíněno dříve, zobrazení můžete použít pořadí řazení kolekce. Vzhledem k tomu, že existují v podkladové kolekci, vaše data mohou nebo nemusí mít relevantní, vlastní pořadí. Zobrazení nad kolekcí umožňuje uložit objednávku nebo změnit výchozí pořadí na základě kritérií porovnání, která zadáte. Vzhledem k tomu, že se jedná o zobrazení dat založené na klientovi, běžným scénářem je, že uživatel může chtít třídit sloupce tabulkových dat podle hodnoty, které sloupec odpovídá. Pomocí zobrazení lze použít toto uživatelem řízené řazení, znovu bez provedení jakýchkoli změn v podkladové kolekci nebo dokonce nutnosti opětovného dotazu na obsah kolekce. Příklad najdete v [tématu Seřazení sloupce GridView po klepnutí na záhlaví](../../framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md).

Následující příklad ukazuje logiku řazení "Seřadit podle <xref:System.Windows.Controls.CheckBox> kategorie a data" [What is data binding](#what-is-data-binding) uj.

[!code-csharp[AddSortChecked](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#AddSortChecked)]
[!code-vb[AddSortChecked](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#AddSortChecked)]

#### <a name="filtering"></a>Filtrování

Zobrazení můžete také použít filtr pro kolekci tak, aby zobrazení zobrazuje pouze určitou podmnožinu celé kolekce. Můžete filtrovat podle podmínky v datech. Například, jak to dělá aplikace v části [Co je datová vazba,](#what-is-data-binding) "Zobrazit pouze výhodné ceny" <xref:System.Windows.Controls.CheckBox> obsahuje logiku pro odfiltrování položek, které stojí $ 25 nebo více. Následující kód je spuštěn nastavit *ShowOnlyBargainsFilter* jako obslužnou rutinu <xref:System.Windows.Data.CollectionViewSource.Filter> události, <xref:System.Windows.Controls.CheckBox> když je vybrána.

[!code-csharp[ListingViewFilter](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#ListingViewFilter)]
[!code-vb[ListingViewFilter](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#ListingViewFilter)]

Obslužná rutina události *ShowOnlyBargainsFilter* má následující implementaci.

[!code-csharp[FilterEvent](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#FilterEvent)]
[!code-vb[FilterEvent](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#FilterEvent)]

Pokud používáte jednu <xref:System.Windows.Data.CollectionView> z tříd <xref:System.Windows.Data.CollectionViewSource>přímo místo <xref:System.Windows.Data.CollectionView.Filter%2A> , byste použít vlastnost k určení zpětného volání. Příklad najdete v tématu [Filtrování dat v zobrazení](../../framework/wpf/data/how-to-filter-data-in-a-view.md).

#### <a name="grouping"></a>Seskupování

S výjimkou vnitřní třídy, která zobrazí <xref:System.Collections.IEnumerable> kolekci, všechna zobrazení kolekce podporují *seskupení*, což umožňuje uživateli rozdělit kolekci v zobrazení kolekce do logických skupin. Skupiny mohou být explicitní, kde uživatel poskytuje seznam skupin nebo implicitní, kde jsou skupiny generovány dynamicky v závislosti na datech.

Následující příklad ukazuje logiku "Seskupit podle kategorie" <xref:System.Windows.Controls.CheckBox>.

[!code-csharp[ListingGroupCheck](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#ListingGroupCheck)]
[!code-vb[ListingGroupCheck](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#ListingGroupCheck)]

Další příklad seskupení naleznete [v tématu Položky skupiny v ListView, který implementuje GridView](../../framework/wpf/controls/how-to-group-items-in-a-listview-that-implements-a-gridview.md).

#### <a name="current-item-pointers"></a>Ukazatele aktuální položky

Zobrazení také podporují pojem aktuální položky. Můžete procházet objekty v zobrazení kolekce. Při navigaci přesouváte ukazatel položky, který umožňuje načíst objekt, který existuje v tomto konkrétním umístění v kolekci. Příklad naleznete v [tématu Procházení objektů v zobrazení collectionview dat](../../framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md).

Vzhledem k tomu, že WPF váže na kolekci pouze pomocí zobrazení (buď zobrazení, které zadáte, nebo výchozí zobrazení kolekce), všechny vazby do kolekcí mají ukazatel aktuální položky. Při vazbě na zobrazení znak lomítka `Path` ("/") v hodnotě označuje aktuální položku zobrazení. V následujícím příkladu je kontext dat zobrazení kolekce. První řádek se váže na kolekci. Druhý řádek se váže na aktuální položku v kolekci. Třetí řádek se váže `Description` na vlastnost aktuální položky v kolekci.

```xaml
<Button Content="{Binding }" />
<Button Content="{Binding Path=/}" />
<Button Content="{Binding Path=/Description}" />
```

Syntaxe lomítka a vlastnosti lze také stohovat k procházení hierarchie kolekcí. Následující příklad se váže na aktuální položku kolekce s názvem `Offices`, což je vlastnost aktuální položky zdrojové kolekce.

```xaml
<Button Content="{Binding /Offices/}" />
```

Aktuální položka ukazatel může být ovlivněna řazení nebo filtrování, která je použita pro kolekci. Řazení zachová ukazatel aktuální položky na poslední vybrané položce, ale zobrazení kolekce je nyní restrukturalizováno kolem něj. (Možná, že vybraná položka byla na začátku seznamu dříve, ale nyní vybraná položka může být někde uprostřed.) Filtrování zachová vybranou položku, pokud tento výběr zůstane po filtrování v zobrazení. V opačném případě je ukazatel aktuální položky nastaven na první položku zobrazení filtrované kolekce.

#### <a name="master-detail-binding-scenario"></a>Scénář vazby hlavního detailu

Pojem aktuální položky je užitečné nejen pro navigaci položek v kolekci, ale také pro scénář vazby hlavní podrobnosti. Zvažte znovu uhlavní ho v yi v aplikaci v části [Co je datová vazba.](#what-is-data-binding) V této aplikaci výběr <xref:System.Windows.Controls.ListBox> v rámci určuje <xref:System.Windows.Controls.ContentControl>obsah zobrazený v . Chcete-li ji umístit jiným <xref:System.Windows.Controls.ListBox> způsobem, když <xref:System.Windows.Controls.ContentControl> je položka vybrána, zobrazí se podrobnosti o vybrané položce.

Scénář hlavního podrobností můžete implementovat jednoduše tak, že dva nebo více ovládacích prvků bude vázáno na stejné zobrazení. Následující příklad z [ukázky datové vazby][data-binding-demo] <xref:System.Windows.Controls.ListBox> zobrazuje <xref:System.Windows.Controls.ContentControl> značky a zobrazí se na ui aplikace v část [Co je datová vazba.](#what-is-data-binding)

[!code-xaml[ListBoxContentControl](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#ListBoxContentControl)]

Všimněte si, že oba ovládací prvky jsou vázány na stejný zdroj, *výpisDataView* statický prostředek (viz definice tohoto prostředku v [Jak vytvořit zobrazení části](#how-to-create-a-view)). Tato vazba funguje, protože když <xref:System.Windows.Controls.ContentControl> singleton objekt (v tomto případě) je vázán <xref:System.Windows.Data.CollectionView.CurrentItem%2A> na zobrazení kolekce, automaticky váže na zobrazení. Objekty <xref:System.Windows.Data.CollectionViewSource> automaticky synchronizují měnu a výběr. Pokud váš ovládací prvek seznamu <xref:System.Windows.Data.CollectionViewSource> není vázán na objekt jako v <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> tomto `true` příkladu, budete muset nastavit jeho vlastnost, aby to fungovalo.

Další příklady naleznete [v tématech Vazba na kolekci a zobrazení informací na základě výběru](../../framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md) a [Použití vzoru podrobností předlohy s hierarchickými daty](../../framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md).

Možná jste si všimli, že výše uvedený příklad používá šablonu. Ve skutečnosti by údaje nebyly zobrazeny tak, jak bychom si přáli bez <xref:System.Windows.Controls.ContentControl> použití šablon (ten, <xref:System.Windows.Controls.ListBox>který výslovně používá a ten implicitně používaný ). Nyní se obracíme na data šablonování v další části.

## <a name="data-templating"></a>Šablony dat

Bez použití šablon dat by naše uživatelské uživatelské tlačítko aplikace v části [Co je datová vazba](#what-is-data-binding) vypadat takto.

![Ukázka datové vazby bez šablon dat](./media/data-binding-overview/demo-no-template.png)

Jak je znázorněno v příkladu <xref:System.Windows.Controls.ListBox> v předchozí <xref:System.Windows.Controls.ContentControl> části, ovládací prvek i jsou vázány na celý objekt kolekce (nebo konkrétněji zobrazení objektu kolekce) *AuctionItem*s. Bez konkrétní pokyny, jak zobrazit shromažďování <xref:System.Windows.Controls.ListBox> dat, zobrazí řetězec reprezentace každého objektu v podkladové kolekci a <xref:System.Windows.Controls.ContentControl> zobrazí řetězec reprezentace objektu, který je vázán.

Chcete-li tento problém vyřešit, aplikace definuje <xref:System.Windows.DataTemplate?text=DataTemplates>. Jak je znázorněno v příkladu <xref:System.Windows.Controls.ContentControl> v předchozí části, explicitně používá šablonu dat *detailsProductListingTemplate.* Ovládací <xref:System.Windows.Controls.ListBox> prvek implicitně používá následující šablonu dat při zobrazení *AuctionItem* objekty v kolekci.

[!code-xaml[AuctionItemDataTemplate](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#AuctionItemDataTemplate)]

Při použití těchto dvou DataTemplates výsledné uživatelské okno je jeden je uveden v co [je datové vazby](#what-is-data-binding) části. Jak můžete vidět z tohoto snímku obrazovky, kromě toho, že vám data umožňují umístit data do ovládacích prvků, datašablony vám umožní definovat přesvědčivé vizuály pro vaše data. Například <xref:System.Windows.DataTrigger>s se používají <xref:System.Windows.DataTemplate> ve výše tak, aby *AuctionItem*s *s SpecialFeatures* hodnota *HighLight* by být zobrazeny s oranžovou hranici a hvězdy.

Další informace o šablonách dat naleznete v [přehledu šablon dat](../../framework/wpf/data/data-templating-overview.md).

## <a name="data-validation"></a>Ověřování dat

Většina aplikací, které berou vstup uživatele, musí mít logiku ověření, aby bylo zajištěno, že uživatel zadal očekávané informace. Kontroly ověření mohou být založeny na typu, rozsahu, formátu nebo jiných požadavcích specifických pro aplikaci. Tato část popisuje, jak funguje ověření dat v WPF.

### <a name="associating-validation-rules-with-a-binding"></a>Sladění ověřovacích pravidel s vazbou

Model datové vazby WPF <xref:System.Windows.Data.Binding.ValidationRules%2A> umožňuje <xref:System.Windows.Data.Binding> přidružit k objektu. Například následující příklad váže <xref:System.Windows.Controls.TextBox> a na `StartPrice` vlastnost s <xref:System.Windows.Controls.ExceptionValidationRule> názvem <xref:System.Windows.Data.Binding.ValidationRules%2A?displayProperty=nameWithType> a přidá objekt vlastnost.

[!code-xaml[TextboxStartPrice](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#TextboxStartPrice)]

Objekt <xref:System.Windows.Controls.ValidationRule> zkontroluje, zda je hodnota vlastnosti platná. WPF má dva typy <xref:System.Windows.Controls.ValidationRule> předdefinovaných objektů:

- A <xref:System.Windows.Controls.ExceptionValidationRule> kontroly výjimky vyvolány během aktualizace vlastnosti zdroje vazby. V předchozím příkladu `StartPrice` je typ celé číslo. Když uživatel zadá hodnotu, kterou nelze převést na celé číslo, je vyvolána výjimka, což způsobí, že vazba bude označena jako neplatná. Alternativní syntaxe k <xref:System.Windows.Controls.ExceptionValidationRule> nastavení explicitně <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> je `true` nastavení <xref:System.Windows.Data.Binding> <xref:System.Windows.Data.MultiBinding> vlastnosti na váš nebo objekt.

- Objekt <xref:System.Windows.Controls.DataErrorValidationRule> kontroluje chyby, které jsou vyvolány objekty, které implementují <xref:System.ComponentModel.IDataErrorInfo> rozhraní. Příklad použití tohoto ověřovacího pravidla <xref:System.Windows.Controls.DataErrorValidationRule>naleznete v tématu . Alternativní syntaxe k <xref:System.Windows.Controls.DataErrorValidationRule> nastavení explicitně <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> je `true` nastavení <xref:System.Windows.Data.Binding> <xref:System.Windows.Data.MultiBinding> vlastnosti na váš nebo objekt.

Můžete také vytvořit vlastní ověřovací pravidlo odvozením <xref:System.Windows.Controls.ValidationRule> z třídy <xref:System.Windows.Controls.ValidationRule.Validate%2A> a implementací metody. Následující příklad ukazuje pravidlo používané v části Přidání <xref:System.Windows.Controls.TextBox> seznamu *produktů* "Datum zahájení" z části Co je [datová vazba.](#what-is-data-binding)

[!code-csharp[FutureDateRule](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/FutureDateRule.cs#FutureDateRule)]
[!code-vb[FutureDateRule](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/FutureDateRule.vb#FutureDateRule)]

*Funkce StartDateEntryForm* <xref:System.Windows.Controls.TextBox> používá toto *pravidlo FutureDateRule*, jak je znázorněno v následujícím příkladu.

[!code-xaml[TextboxStartDate](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#TextboxStartDate)]

Vzhledem <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> k <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>tomu, že hodnota je , modul vazby aktualizuje zdrojovou <xref:System.Windows.Data.Binding.ValidationRules%2A> hodnotu na každém stisknutí klávesy, což znamená, že také kontroluje každé pravidlo v kolekci na každém stisknutí klávesy. Dále o tom diskutujeme v části Proces ověření.

### <a name="providing-visual-feedback"></a>Poskytování vizuální zpětné vazby

Pokud uživatel zadá neplatnou hodnotu, můžete poskytnout nějakou zpětnou vazbu o chybě v uživatelském rozhraní aplikace. Jedním ze způsobů, jak poskytnout <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> takovou zpětnou <xref:System.Windows.Controls.ControlTemplate>vazbu, je nastavit připojenou vlastnost na vlastní . Jak je znázorněno v předchozí podčásti, <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> používá nazvaný *validationTemplate*. Následující příklad ukazuje definici *validationTemplate*.

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#ControlTemplate)]

Prvek <xref:System.Windows.Controls.AdornedElementPlaceholder> určuje, kde by měl být umístěn ovládací prvek, který je adorned umístěn.

Kromě toho můžete také <xref:System.Windows.Controls.ToolTip> použít k zobrazení chybové zprávy. Oba *StartDateEntryForm* a *StartPriceEntryForm*<xref:System.Windows.Controls.TextBox>es použít styl *textStyleTextBox*, který vytvoří, který zobrazí chybovou <xref:System.Windows.Controls.ToolTip> zprávu. Následující příklad ukazuje definici *textStyleTextBox*. Připojené vlastnosti <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> `true` je, když jeden nebo více vazeb na vlastnosti vázaného prvku jsou v omylu.

[!code-xaml[TextBoxStyle](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#TextBoxStyle)]

S vlastní <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> a <xref:System.Windows.Controls.ToolTip>, *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> vypadá takto, pokud je chyba ověření.

![Chyba ověření datové vazby](./media/data-binding-overview/demo-validation-date.png "DataBindingDemo_Validation")

Pokud <xref:System.Windows.Data.Binding> má přidružená ověřovací pravidla, <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> ale nezadáte na <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> vázané ovládací prvek, bude výchozí použít upozornit uživatele, pokud dojde k chybě ověření. Výchozí <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> je šablona ovládacího prvku, která definuje červené ohraničení ve vrstvě adorner. S výchozí <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> a <xref:System.Windows.Controls.ToolTip>, ui *StartPriceEntryForm* <xref:System.Windows.Controls.TextBox> vypadá takto, pokud je chyba ověření.

![Chyba ověření datové vazby](./media/data-binding-overview/demo-validation-price.png "DataBindingDemo_ValidationDefault")

Příklad, jak poskytnout logiku pro ověření všech ovládacích prvků v dialogovém okně, naleznete v části Vlastní dialogová okna v [přehledu dialogových oken](../../framework/wpf/app-development/dialog-boxes-overview.md).

### <a name="validation-process"></a>Proces ověření

K ověření obvykle dochází, když je hodnota cíle přenesena na vlastnost zdroje vazby. K tomuto <xref:System.Windows.Data.BindingMode.TwoWay> přenosu <xref:System.Windows.Data.BindingMode.OneWayToSource> dochází na a vazby. Chcete-li zopakovat, co způsobí, že <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> zdrojová aktualizace závisí na hodnotě vlastnosti, jak je popsáno v části [Co aktivuje zdrojové aktualizace.](#what-triggers-source-updates)

Následující položky popisují proces *ověření.* Pokud dojde k chybě ověření nebo jinému typu chyby kdykoli během tohoto procesu, proces se zastaví:

1. Modul vazby zkontroluje, <xref:System.Windows.Controls.ValidationRule> zda existují <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> nějaké <xref:System.Windows.Controls.ValidationStep.RawProposedValue> vlastní <xref:System.Windows.Data.Binding>objekty definované, jejichž <xref:System.Windows.Controls.ValidationRule.Validate%2A> je <xref:System.Windows.Controls.ValidationRule> nastavena na pro to , v takovém případě volá metodu na každém z nich, dokud jeden z nich narazí na chybu nebo dokud všechny z nich projít.

2. Modul vazby pak volá převaděč, pokud existuje.

3. Pokud převaděč úspěšné, modul vazby zkontroluje, <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> zda existují <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> všechny <xref:System.Windows.Data.Binding>vlastní <xref:System.Windows.Controls.ValidationRule> objekty definované, jejichž <xref:System.Windows.Controls.ValidationRule> je <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> nastavena na to , v takovém případě volá metodu <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> <xref:System.Windows.Controls.ValidationRule.Validate%2A> na každý, který má nastavena, dokud jeden z nich narazí na chybu nebo dokud všechny z nich projít.

4. Modul vazby nastaví vlastnost source.

5. Modul vazby zkontroluje, <xref:System.Windows.Controls.ValidationRule> zda existují <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> nějaké <xref:System.Windows.Controls.ValidationStep.UpdatedValue> vlastní <xref:System.Windows.Data.Binding>objekty definované, jejichž <xref:System.Windows.Controls.ValidationRule.Validate%2A> je <xref:System.Windows.Controls.ValidationRule> nastavena <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> na <xref:System.Windows.Controls.ValidationStep.UpdatedValue> pro to , v takovém případě volá metodu na každý, který má nastavena, dokud jeden z nich narazí na chybu nebo dokud všechny z nich projít. Pokud <xref:System.Windows.Controls.DataErrorValidationRule> je a přidružena <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> k vazbě a <xref:System.Windows.Controls.ValidationStep.UpdatedValue>její <xref:System.Windows.Controls.DataErrorValidationRule> je nastavena na výchozí, , je kontrolována v tomto okamžiku. V tomto okamžiku je <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> zkontrolována jakákoli vazba, která má nastavenou. `true`

6. Modul vazby zkontroluje, <xref:System.Windows.Controls.ValidationRule> zda existují <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> nějaké <xref:System.Windows.Controls.ValidationStep.CommittedValue> vlastní <xref:System.Windows.Data.Binding>objekty definované, jejichž <xref:System.Windows.Controls.ValidationRule.Validate%2A> je <xref:System.Windows.Controls.ValidationRule> nastavena <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> na <xref:System.Windows.Controls.ValidationStep.CommittedValue> pro to , v takovém případě volá metodu na každý, který má nastavena, dokud jeden z nich narazí na chybu nebo dokud všechny z nich projít.

Pokud <xref:System.Windows.Controls.ValidationRule> a neprojde kdykoli v průběhu tohoto procesu, modul vazby vytvoří <xref:System.Windows.Controls.ValidationError> objekt a přidá jej do <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> kolekce vázaný prvek. Před vazby motoru <xref:System.Windows.Controls.ValidationRule> spustí objekty v daném <xref:System.Windows.Controls.ValidationError> kroku, odebere všechny, které byly přidány do <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> připojené vlastnosti vázaného prvku během tohoto kroku. Například pokud <xref:System.Windows.Controls.ValidationRule> <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> a, jehož je nastavena na <xref:System.Windows.Controls.ValidationStep.UpdatedValue> selhání, při příštím procesu ověření dojde, modul vazby odebere, že <xref:System.Windows.Controls.ValidationError> bezprostředně před zavolá všechny, <xref:System.Windows.Controls.ValidationRule> které má nastavena <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> na <xref:System.Windows.Controls.ValidationStep.UpdatedValue>.

Pokud <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> není prázdný, <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojené vlastnost prvku je `true`nastavena na . Také pokud <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A> vlastnost <xref:System.Windows.Data.Binding> je nastavena `true`na , pak <xref:System.Windows.Controls.Validation.Error?displayProperty=nameWithType> vazby motoru vyvolá připojené události na prvek.

Všimněte si také, že platný přenos hodnoty v obou směrech <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> (cíl na zdroj nebo zdroj na cíl) vymaže připojené vlastnosti.

Pokud vazba má <xref:System.Windows.Controls.ExceptionValidationRule> přidružené s ním <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> nebo měl `true` vlastnost je nastavena a je vyvolána výjimka, když modul vazby <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>nastaví zdroj, modul vazby zkontroluje, zda je . Máte možnost použít zpětné <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> volání poskytnout vlastní obslužnou rutinu pro zpracování výjimek. Pokud <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> není zadán na <xref:System.Windows.Data.Binding>, modul vazby vytvoří <xref:System.Windows.Controls.ValidationError> s výjimkou <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> a přidá ji do kolekce vázaný prvek.

## <a name="debugging-mechanism"></a>Ladicí mechanismus

Můžete nastavit připojené vlastnosti <xref:System.Diagnostics.PresentationTraceSources.TraceLevel%2A?displayProperty=nameWithType> na objekt související s vazbou přijímat informace o stavu konkrétní vazby.

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Controls.DataErrorValidationRule>
- [Vazba na výsledky dotazu LINQ](../../framework/wpf/data/how-to-bind-to-the-results-of-a-linq-query.md)
- [Datová vazba](../../framework/wpf/advanced/optimizing-performance-data-binding.md)
- [Ukázka datové vazby][data-binding-demo]
- [Články s postupy](../../framework/wpf/data/data-binding-how-to-topics.md)
- [Vytvoření vazby ke zdroji dat ADO.NET](../../framework/wpf/data/how-to-bind-to-an-ado-net-data-source.md)

[data-binding-demo]: https://github.com/microsoft/WPF-Samples/tree/master/Sample%20Applications/DataBindingDemo "ukázková aplikace datové vazby"
