---
title: Přehled datových vazeb
description: Seznamte se s různými zdroji dat, které můžete přidat do projektu v Windows Presentation Foundation pro .NET Core. Zdroje dat mohou být vázány na prvky XAML pro vytváření dynamických aplikací.
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
# <a name="data-binding-overview-in-wpf"></a>Přehled datových vazeb v subsystému WPF

Datová vazba v Windows Presentation Foundation (WPF) poskytuje jednoduchý a konzistentní způsob, jak aplikace prezentovat a interagovat s daty. Prvky mohou být vázány na data z nejrůznějších zdrojů dat ve formě objektů rozhraní .NET a XML. Jakékoli <xref:System.Windows.Controls.ContentControl> jako <xref:System.Windows.Controls.Button> a všechny <xref:System.Windows.Controls.ItemsControl>, jako například <xref:System.Windows.Controls.ListBox> a <xref:System.Windows.Controls.ListView>, mají vestavěnou funkcionalitu, která umožňuje flexibilní styl jednotlivých datových položek nebo kolekcí datových položek. Zobrazení řazení, filtrování a seskupování lze vytvořit nad daty.

Funkce datové vazby v subsystému WPF má několik výhod oproti tradičním modelům, včetně základní podpory pro datovou vazbu prostřednictvím široké škály vlastností, flexibilní reprezentace dat uživatelského rozhraní a vyčištění oddělení obchodní logiky z uživatelského rozhraní.

V tomto článku se dozvíte, jak se základní koncepce týkají datových vazeb WPF, a <xref:System.Windows.Data.Binding> pak pokrýváme použití třídy a dalších funkcí datové vazby.

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="what-is-data-binding"></a>Co je datová vazba?

Datová vazba je proces, který vytváří připojení mezi uživatelským rozhraním aplikace a zobrazenými daty. Pokud má vazba správné nastavení a data poskytují správná oznámení, při změně její hodnoty prvky, které jsou vázány na data, se automaticky projeví změny. Vazba dat také znamená, že pokud se změní vnější reprezentace dat v prvku, pak se podkladová data dají automaticky aktualizovat, aby odrážela změnu. Například pokud uživatel upraví hodnotu v `TextBox` prvku, podkladová datová hodnota se automaticky aktualizuje, aby odrážela tuto změnu.

Typickým použitím datové vazby je umístit data serveru nebo místní konfigurační data do formulářů nebo jiných ovládacích prvků uživatelského rozhraní. V rámci WPF je tento koncept rozbalený tak, aby zahrnoval vázání široké škály vlastností do nejrůznějších zdrojů dat. V jazyce WPF lze vlastnosti závislosti prvků svázat s objekty rozhraní .NET (včetně objektů ADO.NET nebo objektů přidružených k webovým službám a webovým vlastnostem) a dat XML.

Příklad datové vazby najdete v následujícím uživatelském rozhraní aplikace z [ukázky vytváření datových vazeb][data-binding-demo], která zobrazuje seznam položek aukce.

![Snímek obrazovky ukázek datových vazeb](./media/data-binding-overview/demo.png "DataBinding_DataBindingDemo")

Aplikace demonstruje následující funkce datové vazby:

- Obsah seznamu je svázán s kolekcí objektů *AuctionItem* . Objekt *AuctionItem* má vlastnosti, jako je *Popis*, *StartPrice*, *StartDate*, *kategorie*, *SpecialFeatures*a tak dále.

- Data (objekty*AuctionItem* ) zobrazená v `ListBox` je šablonovaná tak, aby se pro každou položku zobrazoval popis a aktuální cena. Šablona je vytvořena pomocí <xref:System.Windows.DataTemplate>. Kromě toho vzhled každé položky závisí na hodnotě *SpecialFeatures* *AuctionItem* , která se zobrazuje. Pokud je hodnota *SpecialFeatures* pro *AuctionItem* *Color*, položka má modrý okraj. Pokud je hodnota *zvýrazněna*, má položka oranžové ohraničení a hvězdičku. Část [data šablonování](#data-templating) poskytuje informace o šablonování dat.

- Uživatel může data seskupit, filtrovat nebo seřadit pomocí `CheckBoxes` poskytnutého. Na obrázku výše jsou vybrány **kategorie seskupit podle** a **Seřadit podle kategorie a datum** `CheckBoxes` . Možná jste si všimli, že se data seskupují podle kategorie produktu a název kategorie je v abecedním pořadí. Z obrázku je obtížné si všimnout, ale položky jsou také seřazené podle počátečního data v rámci každé kategorie. Řazení se provádí pomocí *zobrazení kolekce*. Část [vazba na kolekce](#binding-to-collections) popisuje zobrazení kolekcí.

- Když uživatel vybere položku, zobrazí se <xref:System.Windows.Controls.ContentControl> podrobnosti o vybrané položce. Toto prostředí se nazývá *scénář hlavní-podrobnosti*. V části [scénář hlavní-podrobnosti](#master-detail-binding-scenario) najdete informace o tomto typu vazby.

- Typ vlastnosti *StartDate* je <xref:System.DateTime>, což vrátí datum, které obsahuje čas do milisekundy. V této aplikaci se použil vlastní převaděč, aby se zobrazil kratší řetězec data. V části [Převod dat](#data-conversion) jsou k dispozici informace o převaděčích.

Když uživatel vybere tlačítko *Přidat produkt* , dojde k následujícímu formuláři.

![Přidat stránku se seznamem produktů](./media/data-binding-overview/demo-addproductlisting.png "DataBinding_Demo_AddProductListing")

Uživatel může upravit pole ve formuláři, zobrazit náhled seznamu produktů pomocí krátkých nebo podrobných podoken náhledu a `Submit` přidat nový seznam produktů. Všechna existující seskupení, filtrování a nastavení řazení budou platit pro novou položku. V tomto konkrétním případě se položka zadaná do výše uvedeného obrázku zobrazí jako druhá položka v kategorii *počítač* .

Nezobrazuje se v tomto obrázku je logika ověřování poskytnutá v *počátečním datu* <xref:System.Windows.Controls.TextBox>. Pokud uživatel zadá neplatné datum (neplatné formátování nebo minulé datum), bude uživatel upozorněn s <xref:System.Windows.Controls.ToolTip> a červeným vykřičníkem vedle. <xref:System.Windows.Controls.TextBox> Část [ověření dat](#data-validation) popisuje, jak vytvořit logiku ověřování.

Předtím, než přejdete k různým funkcím datových vazeb, které jsou uvedené výše, se nejprve podíváme na základní koncepty, které jsou důležité pro porozumění datové vazbě WPF.

## <a name="basic-data-binding-concepts"></a>Základní koncepty datových vazeb

Bez ohledu na to, který prvek vytvoříte, a povaze zdroje dat, každá vazba vždy následuje za modelem znázorněným následujícím obrázkem.

![Diagram, který zobrazuje model základní datové vazby.](./media/data-binding-overview/basic-data-binding-diagram.png)

Jak ukazuje obrázek, vazba dat je v podstatě most mezi cílem vaší vazby a vaším zdrojem vazby. Obrázek ukazuje následující základní koncepty datových vazeb WPF:

- Každá vazba obvykle obsahuje čtyři komponenty:

  - Objekt cíle vazby.
  - Vlastnost target.
  - Zdroj vazby.
  - Cesta k hodnotě ve zdroji vazby, která se má použít.
  
  > Například pokud chcete vytvořit svázání obsahu `TextBox` s `Employee.Name` vlastností, cílový objekt je `TextBox`, vlastnost target je <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost, hodnota, která má být použita, je *název*a zdrojový objekt je objekt *Employee* .

- Vlastnost target musí být vlastnost závislosti. Většina <xref:System.Windows.UIElement> vlastností je vlastnosti závislosti a většina vlastností závislosti, s výjimkou pouze pro čtení, podporuje vazby dat ve výchozím nastavení. (Pouze typy odvozené z <xref:System.Windows.DependencyObject> mohou definovat vlastnosti závislosti a všechny <xref:System.Windows.UIElement> typy odvoditelné `DependencyObject`z.)

- I když se na obrázku nezobrazují, je třeba poznamenat, že zdrojový objekt vazby není omezen na vlastní objekt .NET. Datová vazba WPF podporuje data ve formě objektů .NET a XML. Chcete-li poskytnout několik příkladů, váš zdroj vazby může <xref:System.Windows.UIElement>být, objekt seznamu, objekt ADO.NET nebo objekt WebServices nebo uzel XmlNode, který obsahuje data XML. Další informace najdete v tématu [Přehled zdrojů vazby](../../framework/wpf/data/binding-sources-overview.md).

Je důležité si uvědomit, že při vytváření vazby navážete cíl vazby *na* zdroj vazby. Například pokud zobrazujete některá podkladová data XML v datové vazbě, můžete vytvořit <xref:System.Windows.Controls.ListBox> vazbu `ListBox` na data XML.

Chcete-li vytvořit vazbu, použijte <xref:System.Windows.Data.Binding> objekt. Zbývající část tohoto článku popisuje mnoho konceptů přidružených k a některé z vlastností a použití `Binding` objektu.

### <a name="direction-of-the-data-flow"></a>Směr toku dat

Jak je znázorněno na šipce na předchozím obrázku, tok dat vazby může přejít z cíle vazby na zdroj vazby (například když uživatel upraví hodnotu a `TextBox`) a/nebo ze zdroje vazby na cíl vazby (například pokud je váš `TextBox` obsah aktualizován o změny ve zdroji vazby), pokud zdroj vazby poskytuje správná oznámení.

Můžete chtít, aby vaše aplikace mohla povolit uživatelům změnit data a rozšířit je zpátky do zdrojového objektu. Nebo možná nebudete chtít povolit uživatelům aktualizovat zdrojová data. Tok dat můžete řídit nastavením <xref:System.Windows.Data.Binding.Mode?displayProperty=nameWithType>.

Tento obrázek znázorňuje různé typy toku dat:

![Tok dat datových vazeb](./media/data-binding-overview/databinding-dataflow.png "DataBinding_DataFlow")

- <xref:System.Windows.Data.BindingMode.OneWay>vazba způsobí, že změny vlastnosti source automaticky aktualizují cílovou vlastnost, ale změny vlastnosti target nejsou rozšířeny zpět do vlastnosti source. Tento typ vazby je vhodný v případě, že ovládací prvek, který je svázán, je implicitně určen jen pro čtení. Například můžete vytvořit vazbu ke zdroji, jako je burzovní, nebo možná vaše cílová vlastnost nemá žádné řídicí rozhraní pro provádění změn, jako je například barva pozadí vázaného na data tabulky. Pokud nepotřebujete monitorovat změny vlastnosti target, vyhněte se režii v <xref:System.Windows.Data.BindingMode.OneWay> <xref:System.Windows.Data.BindingMode.TwoWay> režimu vytváření vazeb pomocí režimu vazby.

- <xref:System.Windows.Data.BindingMode.TwoWay>Při vytvoření vazby dojde ke změně vlastnosti source nebo vlastnosti target na hodnotu automaticky aktualizovat druhou. Tento typ vazby je vhodný pro upravitelné formuláře nebo jiné plně interaktivní scénáře uživatelského rozhraní. Většina vlastností je výchozím <xref:System.Windows.Data.BindingMode.OneWay> nastavením pro vazbu, ale některé vlastnosti závislosti (obvykle vlastnosti ovládacích prvků upravitelných uživatelem, <xref:System.Windows.Controls.TextBox.Text?displayProperty=nameWithType> jako je zaškrtávací políčko a [zaškrtávací políčko](xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked) - <xref:System.Windows.Data.BindingMode.TwoWay> zaškrtnuto jako výchozí pro vazbu. Programový způsob, jak určit, zda je vlastnost závislosti svázána jednosměrná nebo obousměrná ve výchozím nastavení, má získat metadata vlastnosti pomocí <xref:System.Windows.DependencyProperty.GetMetadata%2A?displayProperty=nameWithType> a poté ověřit logickou hodnotu <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A?displayProperty=nameWithType> vlastnosti.

- <xref:System.Windows.Data.BindingMode.OneWayToSource>je opakem <xref:System.Windows.Data.BindingMode.OneWay> vazby; aktualizuje vlastnost source při změně vlastnosti target. Jedním z příkladů scénářů je, že pokud potřebujete znovu vyhodnotit zdrojovou hodnotu z uživatelského rozhraní.

- Není znázorněno na obrázku je <xref:System.Windows.Data.BindingMode.OneTime> vazba, což způsobí, že vlastnost source inicializuje cílovou vlastnost, ale nerozšíří následné změny. Pokud se změní kontext dat nebo se objekt v kontextu dat změní, změna se *neprojeví* ve vlastnosti target. Tento typ vazby je vhodný, pokud je snímek aktuálního stavu vhodný nebo že jsou data skutečně statická. Tento typ vazby je vhodný také v případě, že chcete inicializovat cílovou vlastnost s určitou hodnotou ze zdrojové vlastnosti a datový kontext není známý předem. Tento režim je v podstatě jednodušší formou <xref:System.Windows.Data.BindingMode.OneWay> vazby, která poskytuje lepší výkon v případech, kdy se zdrojová hodnota nemění.

Aby bylo možné zjistit změny ve zdroji <xref:System.Windows.Data.BindingMode.OneWay> ( <xref:System.Windows.Data.BindingMode.TwoWay> platí pro vazby a), musí zdroj implementovat vhodný mechanismus pro oznamování změn <xref:System.ComponentModel.INotifyPropertyChanged>vlastností, jako je například. Viz [How to: Implementace oznámení změny vlastností](../../framework/wpf/data/how-to-implement-property-change-notification.md) pro příklad <xref:System.ComponentModel.INotifyPropertyChanged> implementace.

<xref:System.Windows.Data.Binding.Mode?displayProperty=nameWithType> Vlastnost poskytuje další informace o režimech vazby a příklad, jak určit směr vazby.

### <a name="what-triggers-source-updates"></a>Jaké aktualizace zdroje triggerů

Vazby, které <xref:System.Windows.Data.BindingMode.TwoWay> jsou <xref:System.Windows.Data.BindingMode.OneWayToSource> nebo naslouchají změnám ve vlastnosti target a šíří je zpátky do zdroje, označované jako aktualizace zdroje. Můžete například upravit text textového pole, aby se změnila zdrojová hodnota zdroje.

Je však aktualizována zdrojová hodnota při úpravách textu nebo po dokončení úprav textu a ovládací prvek ztratí fokus? <xref:System.Windows.Data.Binding.UpdateSourceTrigger?displayProperty=nameWithType> Vlastnost určuje, která aktivuje aktualizaci zdroje. V bodech pravé šipky na následujícím obrázku je znázorněna role <xref:System.Windows.Data.Binding.UpdateSourceTrigger?displayProperty=nameWithType> vlastnosti.

![Diagram, který zobrazuje roli vlastnosti UpdateSourceTrigger.](./media/data-binding-overview/data-binding-updatesource-trigger.png)

Pokud je `UpdateSourceTrigger` <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged?displayProperty=nameWithType>hodnota, pak hodnota, na kterou se odkazuje šipka vpravo u <xref:System.Windows.Data.BindingMode.TwoWay> nebo <xref:System.Windows.Data.BindingMode.OneWayToSource> vazby, se aktualizuje ihned po změně vlastnosti target. Pokud je `UpdateSourceTrigger` <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus>však hodnota, pak je tato hodnota aktualizována pouze s novou hodnotou, pokud cílová vlastnost ztratí fokus.

Podobně jako u <xref:System.Windows.Data.Binding.Mode%2A> vlastnosti mají různé vlastnosti závislosti jiné výchozí <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> hodnoty. Výchozí hodnota pro většinu vlastností závislosti je <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>, zatímco `TextBox.Text` vlastnost má výchozí hodnotu. <xref:System.Windows.Data.UpdateSourceTrigger.LostFocus> `PropertyChanged`znamená, že se zdrojové aktualizace většinou vyskytují vždy, když se změní cílová vlastnost. Rychlé změny jsou pro zaškrtávací políčka a další jednoduché ovládací prvky jemné. Nicméně pro textová pole, která se aktualizují po každém stisku klávesy, může snížit výkon a odepřít uživateli normální možnost Backspace a opravit chyby před potvrzením nové hodnoty.

Informace o <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> tom, jak najít výchozí hodnotu vlastnosti závislosti, najdete na stránce vlastností.

Následující tabulka uvádí ukázkový scénář pro každou <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> hodnotu pomocí <xref:System.Windows.Controls.TextBox> příkladu.

| Hodnota UpdateSourceTrigger | Když je zdrojová hodnota aktualizována | Ukázkový scénář pro textové pole |
| ------------------------- | ---------------------------------- | ---------------------------- |
| `LostFocus`(výchozí pro <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>) | Když ovládací prvek TextBox ztratí fokus. | Textové pole, které je přidruženo k logice ověřování (viz [ověření dat](#data-validation) níže). |
| `PropertyChanged` | Při psaní do <xref:System.Windows.Controls.TextBox>. | Ovládací prvky TextBox v okně chatovací místnosti |
| `Explicit` | Při volání <xref:System.Windows.Data.BindingExpression.UpdateSource%2A>aplikace. | Ovládací prvky TextBox ve upravitelném formuláři (aktualizuje zdrojové hodnoty pouze v případě, že uživatel klikne na tlačítko Odeslat). |

Příklad naleznete v tématu [How to: Control When a text TextBox Update source](../../framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md).

## <a name="creating-a-binding"></a>Vytvoření vazby

Chcete-li obnovit některé z konceptů popsaných v předchozích částech, vytvoříte vazbu pomocí <xref:System.Windows.Data.Binding> objektu a každá vazba obvykle má čtyři součásti: cíl vazby, cílovou vlastnost, zdroj vazby a cestu ke zdrojové hodnotě, která se má použít. Tato část popisuje, jak nastavit vazbu.

Vezměte v úvahu následující příklad, ve kterém je zdrojový objekt vazby třída s názvem *Mojedata* , která je definována v oboru názvů *SDKSample* . Pro demonstrační účely má *Mojedata* vlastnost String s názvem *Color* , jejíž hodnota je nastavená na "Red". Proto tento příklad vygeneruje tlačítko s červeným pozadím.

[!code-xaml[BindNonTextProperty](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/AutoConvertPropertyToColor.xaml#BindAutoConvertColor)]

Další informace o syntaxi deklarace vazby a příklady, jak nastavit vazbu v kódu, najdete v tématu [Přehled deklarací vazeb](../../framework/wpf/data/binding-declarations-overview.md).

Pokud tento příklad použijeme pro náš základní diagram, bude výsledný obrázek vypadat jako na následujícím obrázku. Na tomto obrázku je <xref:System.Windows.Data.BindingMode.OneWay> popsána vazba, protože <xref:System.Windows.Data.BindingMode.OneWay> vlastnost Background podporuje vazby ve výchozím nastavení.

![Diagram, který zobrazuje vlastnost pozadí datové vazby.](./media/data-binding-overview/data-binding-button-background-example.png)

Může se stát, proč tato vazba funguje i v případě, že vlastnost *Color* je typu String, <xref:System.Windows.Controls.Control.Background%2A> zatímco vlastnost je typu <xref:System.Windows.Media.Brush>. Tato vazba používá výchozí převod typu, který je popsán v části [Převod dat](#data-conversion) .

### <a name="specifying-the-binding-source"></a>Určení zdroje vazby

Všimněte si, že v předchozím příkladu je zdroj vazby určen nastavením vlastnosti [DockPanel. DataContext](xref:System.Windows.FrameworkElement.DataContext) . <xref:System.Windows.Controls.Button> Pak zdědí <xref:System.Windows.FrameworkElement.DataContext%2A> hodnotu z <xref:System.Windows.Controls.DockPanel>, která je jeho nadřazeným prvkem. Pro opakování iterace je zdrojový objekt vazby jednou ze čtyř nezbytných komponent vazby. Proto bez zadání zdrojového objektu vazby neprovede vazba nic.

Existuje několik způsobů, jak zadat zdrojový objekt vazby. Použití <xref:System.Windows.FrameworkElement.DataContext%2A> vlastnosti u nadřazeného elementu je užitečné, pokud vytváříte vazbu více vlastností ke stejnému zdroji. V některých případech ale může být vhodnější zadat zdroj vazby u jednotlivých deklarací vazeb. Pro předchozí příklad namísto použití <xref:System.Windows.FrameworkElement.DataContext%2A> vlastnosti lze určit zdroj vazby nastavením <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> vlastnosti přímo na deklaraci vazby tlačítka, jak je uvedeno v následujícím příkladu.

[!code-xaml[BindNonTextPropertyCompactBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/AutoConvertPropertyToColor.xaml#BindAutoConvertColorCompactBinding)]

<xref:System.Windows.FrameworkElement.DataContext%2A> Kromě nastavení vlastnosti u prvku přímo, dědění <xref:System.Windows.FrameworkElement.DataContext%2A> hodnoty z předchůdce (například tlačítka v prvním příkladu) a explicitního určení zdroje vazby nastavením <xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType> vlastnosti u vazby (například tlačítka v posledním příkladu), můžete také použít <xref:System.Windows.Data.Binding.ElementName?displayProperty=nameWithType> vlastnost nebo <xref:System.Windows.Data.Binding.RelativeSource?displayProperty=nameWithType> vlastnost k určení zdroje vazby. Tato <xref:System.Windows.Data.Binding.ElementName%2A> vlastnost je užitečná, pokud vytváříte vazbu na jiné prvky ve vaší aplikaci, například při použití posuvníku k úpravě šířky tlačítka. <xref:System.Windows.Data.Binding.RelativeSource%2A> Vlastnost je užitečná, pokud je vazba určena v <xref:System.Windows.Controls.ControlTemplate> nebo <xref:System.Windows.Style>. Další informace naleznete v tématu [How to: Určete zdroj vazby](../../framework/wpf/data/how-to-specify-the-binding-source.md).

### <a name="specifying-the-path-to-the-value"></a>Zadání cesty k hodnotě

Pokud je zdrojem vazby objekt, použijte <xref:System.Windows.Data.Binding.Path?displayProperty=nameWithType> vlastnost k určení hodnoty, která se má použít pro vazbu. Pokud vytváříte vazbu na data XML, použijete <xref:System.Windows.Data.Binding.XPath?displayProperty=nameWithType> vlastnost k určení hodnoty. V některých případech může být vhodné použít <xref:System.Windows.Data.Binding.Path%2A> vlastnost i v případě, že vaše data jsou XML. Například pokud chcete získat přístup k vlastnosti název vráceného objektu XmlNode (jako výsledek dotazu XPath), měli byste použít <xref:System.Windows.Data.Binding.Path%2A> vlastnost kromě <xref:System.Windows.Data.Binding.XPath%2A> vlastnosti.

Další informace najdete v <xref:System.Windows.Data.Binding.Path%2A> tématu vlastnosti a <xref:System.Windows.Data.Binding.XPath%2A> .

I když jsme zdůraznili, že <xref:System.Windows.Data.Binding.Path%2A> hodnota, která se má použít, je jedna ze čtyř nezbytných komponent vazby, ve scénářích, které chcete svázat s celým objektem, by hodnota, která se má použít, byla stejná jako zdrojový objekt vazby. V těchto případech platí, že se nedá zadat <xref:System.Windows.Data.Binding.Path%2A>. Představte si následující příklad.

[!code-xaml[EmptyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/EmptyBinding.xaml#EmptyBinding)]

Výše uvedený příklad používá prázdnou syntaxi vazby: {Binding}. V tomto případě <xref:System.Windows.Controls.ListBox> dědí objekt DataContext z nadřazeného elementu DockPanel (nezobrazuje se v tomto příkladu). Není-li zadána cesta, výchozí hodnota je svázána s celým objektem. Jinými slovy, v tomto příkladu byla cesta ponechána, protože je <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost svázána s celým objektem. (Podrobné informace najdete v části [vazba na kolekce](#binding-to-collections) .)

Kromě vazby ke kolekci je tento scénář také užitečný, pokud chcete vytvořit vazbu k celému objektu místo pouze jediné vlastnosti objektu. Například pokud je zdrojový objekt typu <xref:System.String>, můžete chtít vytvořit svázání pouze s samotným řetězcem. Dalším běžným scénářem je, když chcete vytvořit vazby prvku k objektu s několika vlastnostmi.

Možná budete muset použít vlastní logiku, aby data byla smysluplná na vlastnost cíle vazby. Vlastní logika může být ve formě vlastního převaděče, pokud neexistuje výchozí převod typu. Informace o převaděčích najdete v tématu [Převod dat](#data-conversion) .

### <a name="binding-and-bindingexpression"></a>Vytváření vazeb a pokoušel obnovit BindingExpression

Než začnete používat další funkce a použití datových vazeb, je vhodné začlenit <xref:System.Windows.Data.BindingExpression> třídu. Jak jste viděli v předchozích částech, <xref:System.Windows.Data.Binding> třída je třída vysoké úrovně pro deklaraci vazby; poskytuje mnoho vlastností, které umožňují určit charakteristiky vazby. Související třída <xref:System.Windows.Data.BindingExpression>je základní objekt, který udržuje spojení mezi zdrojem a cílem. Vazba obsahuje všechny informace, které lze sdílet mezi několika výrazy vazby. <xref:System.Windows.Data.BindingExpression> Je výraz instance, který nelze sdílet a obsahuje všechny informace o instanci <xref:System.Windows.Data.Binding>.

Vezměte v úvahu následující příklad, `myDataObject` `MyData` kde je instance třídy `myBinding` , je zdrojový <xref:System.Windows.Data.Binding> objekt a `MyData` je definována třída, která obsahuje řetězcovou vlastnost s názvem. `MyDataProperty` Tento příklad váže textový obsah `myText`instance <xref:System.Windows.Controls.TextBlock>a na. `MyDataProperty`

[!code-csharp[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/ManualBinding.cs#CodeOnlyBinding)]
[!code-vb[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/ManualBinding.vb#CodeOnlyBinding)]

Stejný objekt *myBinding* můžete použít k vytvoření dalších vazeb. Například můžete použít objekt *myBinding* k navázání textového obsahu zaškrtávacího políčka na *MyDataProperty*. V takovém případě budou k dispozici dvě instance <xref:System.Windows.Data.BindingExpression> sdílení objektu *myBinding* .

<xref:System.Windows.Data.BindingExpression> Objekt je vrácen voláním <xref:System.Windows.Data.BindingOperations.GetBindingExpression%2A> objektu vázaného na data. Následující články ukazují některé z použití <xref:System.Windows.Data.BindingExpression> třídy:

- [Získání objektu vazby z vlastnosti cíle vazby](../../framework/wpf/data/how-to-get-the-binding-object-from-a-bound-target-property.md)

- [Určuje, kdy se text v textovém poli aktualizuje na zdroj.](../../framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md)

## <a name="data-conversion"></a>Převod dat

V oddílu [vytvoření vazby](#creating-a-binding) je tlačítko červené, protože jeho <xref:System.Windows.Controls.Control.Background%2A> vlastnost je svázána s vlastností řetězce s hodnotou "Red". Tato řetězcová hodnota funguje, protože u <xref:System.Windows.Media.Brush> typu je k dispozici konvertor typu pro převod řetězcové hodnoty <xref:System.Windows.Media.Brush>na.

Přidání těchto informací na obrázek vypadá oddíl [vytvoření vazby](#creating-a-binding) jako takový.

![Diagram, který zobrazuje výchozí vlastnost datové vazby.](./media/data-binding-overview/data-binding-button-default-conversion.png)

Ale co když místo abyste měli vlastnost typu String, váš zdrojový objekt vazby má vlastnost *Color* typu <xref:System.Windows.Media.Color>? V takovém případě, aby vazba fungovala, musíte nejprve změnit hodnotu vlastnosti *Color* na objekt, který <xref:System.Windows.Controls.Control.Background%2A> vlastnost přijímá. Je nutné vytvořit vlastní převaděč implementací <xref:System.Windows.Data.IValueConverter> rozhraní, jak je uvedeno v následujícím příkladu.

[!code-csharp[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/ColorBrushConverter.cs#ColorBrushConverter)]
[!code-vb[CodeOnlyBinding](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/ColorBrushConverter.vb#ColorBrushConverter)]

Další informace naleznete v tématu <xref:System.Windows.Data.IValueConverter>.

Místo výchozího převodu se teď používá vlastní převaděč a náš diagram vypadá takto.

![Diagram znázorňující vlastní převaděč datových vazeb](./media/data-binding-overview/data-binding-converter-color-example.png)

K opakování iterací mohou být výchozí převody k dispozici z důvodu konvertorů typu, které jsou k dispozici v typu vázaného na. Toto chování bude záviset na tom, které převaděče typů jsou v cíli k dispozici. Pokud máte pochybnosti, vytvořte vlastní převaděč.

Níže jsou uvedeny některé typické scénáře, kdy je vhodné implementovat převaděč dat:

- Vaše data by se měla zobrazit odlišně v závislosti na jazykové verzi. Například může být vhodné implementovat převodník měny nebo převaděč data/času v závislosti na konvencích používaných v konkrétní jazykové verzi.

- Použitá data nemusí nutně mít za cíl změnit textovou hodnotu vlastnosti, ale místo toho je třeba změnit jinou hodnotu, jako je například zdroj obrázku nebo barva nebo styl zobrazovaného textu. Převaděče lze v této instanci použít převodem vazby vlastnosti, která pravděpodobně není vhodná, jako je například vazba textového pole na vlastnost pozadí buňky tabulky.

- Více než jeden ovládací prvek nebo více vlastností ovládacích prvků je svázán se stejnými daty. V takovém případě může primární vazba pouze zobrazit text, zatímco jiné vazby zpracovávají konkrétní problémy se zobrazením, ale stále používají stejnou vazbu jako informace o zdroji.

- Vlastnost target má kolekci vazeb, které jsou vyjmenovány <xref:System.Windows.Data.MultiBinding>. Pro <xref:System.Windows.Data.MultiBinding>můžete použít vlastní <xref:System.Windows.Data.IMultiValueConverter> pro vytvoření konečné hodnoty z hodnot vazeb. Barvy lze například vypočítat z hodnot červené, modré a zelené, což může být hodnoty ze stejných nebo odlišných zdrojových objektů vazby. Příklady <xref:System.Windows.Data.MultiBinding> a informace najdete v tématu.

## <a name="binding-to-collections"></a>Vazba na kolekce

Zdrojový objekt vazby lze považovat za jeden objekt, jehož vlastnosti obsahují data nebo jako kolekci dat polymorfních objektů, které jsou často seskupeny (například výsledek dotazu do databáze). Zatím jsme probrali pouze vazbu na jednotlivé objekty. Vazba na shromažďování dat je ale běžným scénářem. Například běžným scénářem je <xref:System.Windows.Controls.ItemsControl> použití <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.ListView>nebo <xref:System.Windows.Controls.TreeView> k zobrazení kolekce dat, například v aplikaci zobrazené v části [co je datová vazba](#what-is-data-binding) .

Naštěstí je náš základní diagram stále použit. Pokud vytváříte vazbu <xref:System.Windows.Controls.ItemsControl> ke kolekci, diagram vypadá takto.

![Diagram, který zobrazuje objekt ItemsControl datové vazby.](./media/data-binding-overview/data-binding-itemscontrol.png)

Jak je znázorněno v tomto diagramu, pro <xref:System.Windows.Controls.ItemsControl> svázání s objektem kolekce <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A?displayProperty=nameWithType> , vlastnost je vlastnost, která má být použita. Můžete si představit `ItemsSource` jako obsah v <xref:System.Windows.Controls.ItemsControl>. Vazba je <xref:System.Windows.Data.BindingMode.OneWay> způsobená tím `ItemsSource` , že `OneWay` vlastnost ve výchozím nastavení podporuje vazby.

### <a name="how-to-implement-collections"></a>Implementace kolekcí

Můžete vytvořit výčet pro libovolnou kolekci, která implementuje <xref:System.Collections.IEnumerable> rozhraní. Chcete-li však nastavit dynamické vazby tak, aby vložení nebo odstranění v kolekci automaticky aktualizovaly uživatelské rozhraní, kolekce musí implementovat <xref:System.Collections.Specialized.INotifyCollectionChanged> rozhraní. Toto rozhraní zpřístupňuje událost, která by měla být vyvolána při každé změně příslušné kolekce.

WPF poskytuje <xref:System.Collections.ObjectModel.ObservableCollection%601> třídu, která je vestavěnou implementací kolekce dat, která zpřístupňuje <xref:System.Collections.Specialized.INotifyCollectionChanged> rozhraní. Aby bylo možné plně podporovat přenos hodnot dat ze zdrojových objektů na cíle, každý objekt v kolekci, který podporuje vlastnosti s možností vazby, <xref:System.ComponentModel.INotifyPropertyChanged> musí implementovat také rozhraní. Další informace najdete v tématu [Přehled zdrojů vazby](../../framework/wpf/data/binding-sources-overview.md).

<xref:System.Collections.ObjectModel.ObservableCollection%601> Před implementací vlastní kolekce zvažte použití nebo jednu z existujících tříd kolekce, například <xref:System.Collections.Generic.List%601>, <xref:System.Collections.ObjectModel.Collection%601>a <xref:System.ComponentModel.BindingList%601>, mezi mnoho dalších. Máte-li pokročilý scénář a chcete implementovat vlastní kolekci, zvažte použití <xref:System.Collections.IList>, které poskytuje neobecnou kolekci objektů, které mohou být jednotlivě k dispozici prostřednictvím indexu, a proto poskytuje nejlepší výkon.

### <a name="collection-views"></a>Zobrazení kolekcí

<xref:System.Windows.Controls.ItemsControl> Po navázání na shromažďování dat můžete chtít data řadit, filtrovat nebo seskupovat. K tomu je třeba použít zobrazení kolekce, což jsou třídy, které implementují <xref:System.ComponentModel.ICollectionView> rozhraní.

#### <a name="what-are-collection-views"></a>Co jsou zobrazení kolekcí?

Zobrazení kolekce je vrstva nad kolekcí zdrojů vazby, která umožňuje procházet a zobrazovat zdrojovou kolekci na základě dotazů řazení, filtrování a seskupování, aniž by bylo nutné měnit podkladovou zdrojovou kolekci. Zobrazení kolekce také udržuje ukazatel na aktuální položku v kolekci. Pokud zdrojová kolekce implementuje <xref:System.Collections.Specialized.INotifyCollectionChanged> rozhraní, jsou změny vyvolané <xref:System.Collections.Specialized.INotifyCollectionChanged.CollectionChanged> událostí rozšířeny do zobrazení.

Vzhledem k tomu, že zobrazení nemění zdrojové kolekce, ke každé zdrojové kolekci může být přidruženo více zobrazení. Například můžete mít kolekci objektů *Task* . Pomocí zobrazení můžete stejná data zobrazit různými způsoby. Například na levé straně stránky můžete chtít zobrazit úkoly seřazené podle priority a na pravé straně seskupené podle oblasti.

#### <a name="how-to-create-a-view"></a>Postup vytvoření zobrazení

Jedním ze způsobů, jak vytvořit a použít zobrazení, je vytvořit instanci objektu zobrazení přímo a pak ho použít jako zdroj vazby. Zvažte například [ukázkovou aplikaci datové vazby][data-binding-demo] , která je zobrazena v části [co je datová vazba](#what-is-data-binding) . Aplikace je implementovaná tak, aby <xref:System.Windows.Controls.ListBox> se místo kolekce dat přímo navázala na zobrazení v rámci shromažďování dat. Následující příklad je extrahován z ukázkové aplikace [datové vazby][data-binding-demo] . <xref:System.Windows.Data.CollectionViewSource> Třída je proxy kód XAML třídy, ze <xref:System.Windows.Data.CollectionView>které dědí. V tomto konkrétním příkladu <xref:System.Windows.Data.CollectionViewSource.Source%2A> je v zobrazení svázána s kolekcí *AuctionItems* (typu <xref:System.Collections.ObjectModel.ObservableCollection%601>) aktuálního objektu aplikace.

[!code-xaml[CollectionView](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#CollectionView)]

*ListingDataView* prostředků pak slouží jako zdroj vazby pro prvky v aplikaci, jako je <xref:System.Windows.Controls.ListBox>například.

[!code-xaml[ListBoxCollectionView](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#ListBoxCollectionView)]

Chcete-li vytvořit další zobrazení pro stejnou kolekci, můžete vytvořit jinou <xref:System.Windows.Data.CollectionViewSource> instanci a přidělit jí jiný `x:Key` název.

V následující tabulce jsou uvedeny typy dat zobrazení, které jsou vytvořeny jako výchozí zobrazení kolekce, <xref:System.Windows.Data.CollectionViewSource> nebo podle typu zdrojové kolekce.

| Typ zdrojové kolekce                    | Typ zobrazení kolekce | Poznámky |
| ----------------------------------------- | -------------------- | ----- |
| <xref:System.Collections.IEnumerable>     | Interní typ založený na<xref:System.Windows.Data.CollectionView> | Položky nelze seskupit. |
| <xref:System.Collections.IList>           | <xref:System.Windows.Data.ListCollectionView> | Způsobem. |
| <xref:System.ComponentModel.IBindingList> | <xref:System.Windows.Data.BindingListCollectionView> | |

#### <a name="using-a-default-view"></a>Použití výchozího zobrazení

Zadání zobrazení kolekce jako zdroje vazby je jedním ze způsobů, jak vytvořit a použít zobrazení kolekce. WPF také vytvoří výchozí zobrazení kolekce pro každou kolekci použitou jako zdroj vazby. Pokud vytváříte vazby přímo ke kolekci, WPF se váže k výchozímu zobrazení. Toto výchozí zobrazení je sdíleno všemi vazbami na stejnou kolekci, takže změna ve výchozím zobrazení podle jednoho vázaného ovládacího prvku nebo kódu (například řazení nebo změna ukazatele na aktuální položku, která je popsána dále) se projeví ve všech ostatních vazbách ke stejné kolekci.

Chcete-li získat výchozí zobrazení, použijte <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> metodu. Příklad najdete v tématu [získání výchozího zobrazení sběru dat](../../framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md).

#### <a name="collection-views-with-adonet-datatables"></a>Zobrazení kolekcí s ADO.NET datatabulkami

Pro zlepšení výkonu, zobrazení kolekce pro ADO.NET <xref:System.Data.DataTable> nebo <xref:System.Data.DataView> objekty delegovat řazení a filtrování do, <xref:System.Data.DataView>což způsobí, že řazení a filtrování budou sdíleny napříč všemi zobrazeními kolekce zdroje dat. Chcete-li každé zobrazení kolekce Povolit řazení a filtrování nezávisle, inicializujte každé zobrazení <xref:System.Data.DataView> kolekce vlastním objektem.

#### <a name="sorting"></a>Řazení

Jak bylo zmíněno dříve, zobrazení mohou použít řazení do kolekce. V případě, že v příslušné kolekci existuje, vaše data mohou nebo nemusí mít příslušné vlastní pořadí. Zobrazení přes kolekci umožňuje stanovit objednávku nebo změnit výchozí pořadí na základě porovnávacích kritérií, která zadáte. Vzhledem k tomu, že se jedná o zobrazení dat na základě klienta, je běžným scénářem, že uživatel může chtít seřadit sloupce tabulkových dat podle hodnoty, se kterou sloupec odpovídá. Pomocí zobrazení lze toto řazení řízené uživatelem použít, a to bez provedení jakýchkoli změn v podkladové kolekci nebo při opakovaném dotazování na obsah kolekce. Příklad naleznete v tématu [seřazení sloupce GridView při kliknutí na záhlaví](../../framework/wpf/controls/how-to-sort-a-gridview-column-when-a-header-is-clicked.md).

Následující příklad ukazuje logiku řazení "řadit podle kategorie a data" <xref:System.Windows.Controls.CheckBox> uživatelského rozhraní aplikace v části [co je datová vazba](#what-is-data-binding) .

[!code-csharp[AddSortChecked](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#AddSortChecked)]
[!code-vb[AddSortChecked](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#AddSortChecked)]

#### <a name="filtering"></a>Filtrování

Zobrazení mohou také použít filtr na kolekci, aby zobrazení zobrazilo pouze určitou podmnožinu úplné kolekce. Můžete filtrovat podmínku v datech. Například vzhledem k tomu, že aplikace je prováděna v části [co je datová vazba](#what-is-data-binding) , obsahuje logika "Zobrazit pouze úkoly" <xref:System.Windows.Controls.CheckBox> logiku pro odfiltrování položek, které jsou $25 nebo více náklady. Následující kód je spuštěn pro nastavení *ShowOnlyBargainsFilter* jako obslužné rutiny <xref:System.Windows.Data.CollectionViewSource.Filter> události, <xref:System.Windows.Controls.CheckBox> když je vybrána možnost.

[!code-csharp[ListingViewFilter](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#ListingViewFilter)]
[!code-vb[ListingViewFilter](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#ListingViewFilter)]

Obslužná rutina události *ShowOnlyBargainsFilter* má následující implementaci.

[!code-csharp[FilterEvent](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#FilterEvent)]
[!code-vb[FilterEvent](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#FilterEvent)]

Pokud používáte jednu z <xref:System.Windows.Data.CollectionView> tříd přímo namísto <xref:System.Windows.Data.CollectionViewSource>, měli byste použít <xref:System.Windows.Data.CollectionView.Filter%2A> vlastnost k určení zpětného volání. Příklad naleznete [v tématu Filtrování dat v zobrazení](../../framework/wpf/data/how-to-filter-data-in-a-view.md).

#### <a name="grouping"></a>Seskupování

S výjimkou interní třídy, která zobrazí <xref:System.Collections.IEnumerable> kolekci, všechna zobrazení kolekcí podporují *seskupení*, které umožňuje uživateli rozdělit kolekci v zobrazení kolekce do logických skupin. Skupiny můžou být explicitní, kde uživatel zadá seznam skupin nebo implicitně, kde se skupiny generují dynamicky v závislosti na datech.

Následující příklad ukazuje logiku "Group by Category" <xref:System.Windows.Controls.CheckBox>.

[!code-csharp[ListingGroupCheck](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml.cs#ListingGroupCheck)]
[!code-vb[ListingGroupCheck](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/CollectionView.xaml.vb#ListingGroupCheck)]

Další příklad seskupení naleznete v tématu [Group items in ListView, který implementuje prvek GridView](../../framework/wpf/controls/how-to-group-items-in-a-listview-that-implements-a-gridview.md).

#### <a name="current-item-pointers"></a>Ukazatele aktuální položky

Zobrazení také podporují pojem aktuální položky. Můžete procházet objekty v zobrazení kolekce. Při procházení přesunete ukazatel myši na položku, která umožňuje načíst objekt, který existuje v daném umístění v kolekci. Příklad naleznete v tématu [Navigace skrze objekty v CollectionView dat](../../framework/wpf/data/how-to-navigate-through-the-objects-in-a-data-collectionview.md).

Vzhledem k tomu, že WPF váže ke kolekci pouze pomocí zobrazení (buď zadané zobrazení, nebo výchozího zobrazení kolekce), mají všechny vazby na kolekce aktuální ukazatel na položku. Při vytváření vazby k zobrazení označuje znak lomítka ("/") v `Path` hodnotě aktuální položku zobrazení. V následujícím příkladu je kontext dat zobrazením kolekce. První řádek se váže ke kolekci. Druhý řádek vytvoří vazby na aktuální položku v kolekci. Třetí řádek se váže k `Description` vlastnosti aktuální položky v kolekci.

```xaml
<Button Content="{Binding }" />
<Button Content="{Binding Path=/}" />
<Button Content="{Binding Path=/Description}" />
```

Lomítko a vlastnost lze také navrstveny pro procházení hierarchie kolekcí. V následujícím příkladu se váže k aktuální položce kolekce s názvem `Offices`, která je vlastností aktuální položky zdrojové kolekce.

```xaml
<Button Content="{Binding /Offices/}" />
```

Ukazatel na aktuální položku může být ovlivněn jakýmkoli řazením nebo filtrováním, které je použito pro kolekci. Při řazení se zachová ukazatel aktuální položky na poslední vybrané položce, ale zobrazení kolekce se teď znovu rozstrukturuje. (Možná vybraná položka byla na začátku seznamu, ale teď může být vybraná položka někde uprostřed.) Filtrování zachová vybranou položku, pokud tento výběr po filtrování zůstane v zobrazení. V opačném případě je ukazatel aktuální položky nastaven na první položku filtrovaného zobrazení kolekce.

#### <a name="master-detail-binding-scenario"></a>Scénář vázání hlavní-podrobnosti

Pojem aktuální položky je užitečný nejen pro navigaci položek v kolekci, ale také pro scénář vázání hlavní-podrobnosti. V části [co je datová vazba](#what-is-data-binding) zvažte uživatelské rozhraní aplikace. V této aplikaci výběr v rámci <xref:System.Windows.Controls.ListBox> určuje obsah zobrazený v. <xref:System.Windows.Controls.ContentControl> Chcete-li jej vložit jiným způsobem, je <xref:System.Windows.Controls.ListBox> -li vybrána položka, <xref:System.Windows.Controls.ContentControl> zobrazí se podrobnosti o vybrané položce.

Scénář hlavní-podrobnosti můžete implementovat jednoduše tak, že se dva nebo více ovládacích prvků sváže se stejným zobrazením. Následující příklad v [ukázce vázání dat][data-binding-demo] ukazuje značky <xref:System.Windows.Controls.ListBox> a, <xref:System.Windows.Controls.ContentControl> které se zobrazí v uživatelském rozhraní aplikace v části [co je datová vazba](#what-is-data-binding) .

[!code-xaml[ListBoxContentControl](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#ListBoxContentControl)]

Všimněte si, že oba ovládací prvky jsou svázány se stejným zdrojem, statickým prostředkem *listingDataView* (viz definice tohoto prostředku v [části jak vytvořit zobrazení](#how-to-create-a-view)). Tato vazba funguje, protože pokud je objekt singleton ( <xref:System.Windows.Controls.ContentControl> v tomto případě) svázán se zobrazením kolekce, je automaticky <xref:System.Windows.Data.CollectionView.CurrentItem%2A> svázán se zobrazením. <xref:System.Windows.Data.CollectionViewSource> Objekty automaticky synchronizují měnu a výběr. Pokud ovládací prvek seznam není svázán s <xref:System.Windows.Data.CollectionViewSource> objektem jako v tomto příkladu, pak byste museli nastavit jeho <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> vlastnost na `true` hodnotu, aby fungovala.

Další příklady naleznete v tématu [vazba na kolekci a zobrazení informací na základě výběru](../../framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md) a [použití vzoru hlavní-podrobnosti s hierarchickými daty](../../framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md).

Možná jste si všimli, že výše uvedený příklad používá šablonu. Ve skutečnosti by se data nezobrazovala způsobem, který chceme, bez použití šablon (to je explicitně použito <xref:System.Windows.Controls.ContentControl> a implicitně používaného rozhraním <xref:System.Windows.Controls.ListBox>). Nyní se v další části změní data šablonování.

## <a name="data-templating"></a>Šablony dat

Bez použití datových šablon by naše uživatelské rozhraní aplikace v části [co je datová vazba](#what-is-data-binding) vypadalo jako následující.

![Ukázka datových vazeb bez datových šablon](./media/data-binding-overview/demo-no-template.png)

Jak je znázorněno v příkladu v předchozí části, <xref:System.Windows.Controls.ListBox> ovládací prvek i je svázán <xref:System.Windows.Controls.ContentControl> s celým objektem kolekce (nebo se konkrétně jedná o zobrazení nad objektem kolekce) pro *AuctionItem*s. Bez konkrétních pokynů k zobrazení kolekce dat <xref:System.Windows.Controls.ListBox> zobrazuje zobrazení řetězcové vyjádření každého objektu v podkladové kolekci a <xref:System.Windows.Controls.ContentControl> zobrazuje řetězcovou reprezentaci objektu, ke kterému je vázáno.

Chcete-li tento problém vyřešit, aplikace <xref:System.Windows.DataTemplate?text=DataTemplates>definuje. Jak je znázorněno v příkladu v předchozí části, <xref:System.Windows.Controls.ContentControl> explicitně používá šablonu dat *detailsProductListingTemplate* . <xref:System.Windows.Controls.ListBox> Ovládací prvek implicitně používá následující šablonu dat při zobrazení objektů *AuctionItem* v kolekci.

[!code-xaml[AuctionItemDataTemplate](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/CollectionView.xaml#AuctionItemDataTemplate)]

Při použití těchto dvou datových šablon je výsledné uživatelské rozhraní ten, který je zobrazen v části [co je datová vazba](#what-is-data-binding) . Jak vidíte z tohoto snímku obrazovky, kromě toho, že vám umožní umístit data do ovládacích prvků, datové šablony vám umožní definovat přesvědčivé vizuály pro vaše data. <xref:System.Windows.DataTrigger>Například s se používají ve výše uvedeném <xref:System.Windows.DataTemplate> případě, že *AuctionItem*s s hodnotou *SpecialFeatures* *zvýraznění* by se zobrazila s oranžovým ohraničením a hvězdičkou.

Další informace o datových šablonách najdete v tématu [Přehled šablonování dat](../../framework/wpf/data/data-templating-overview.md).

## <a name="data-validation"></a>Ověřování dat

Většina aplikací, které přijímají uživatelský vstup, musí mít logiku ověřování, aby bylo možné zajistit, že uživatel zadal očekávané informace. Kontroly ověřování můžou být založené na typu, rozsahu, formátu nebo dalších požadavcích specifických pro aplikace. Tato část popisuje, jak ověřování dat funguje v subsystému WPF.

### <a name="associating-validation-rules-with-a-binding"></a>Přidružení ověřovacích pravidel k vazbě

Model datové vazby WPF umožňuje přidružení <xref:System.Windows.Data.Binding.ValidationRules%2A> k <xref:System.Windows.Data.Binding> objektu. Například následující <xref:System.Windows.Controls.TextBox> příklad váže spojení s vlastností s názvem `StartPrice` a přidá <xref:System.Windows.Controls.ExceptionValidationRule> objekt do <xref:System.Windows.Data.Binding.ValidationRules%2A?displayProperty=nameWithType> vlastnosti.

[!code-xaml[TextboxStartPrice](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#TextboxStartPrice)]

<xref:System.Windows.Controls.ValidationRule> Objekt ověří, zda je hodnota vlastnosti platná. WPF má dva typy předdefinovaných <xref:System.Windows.Controls.ValidationRule> objektů:

- <xref:System.Windows.Controls.ExceptionValidationRule> Kontroluje výjimky vyvolané během aktualizace vlastnosti zdroje vazby. V předchozím příkladu `StartPrice` je typu Integer. Když uživatel zadá hodnotu, kterou nelze převést na celé číslo, je vyvolána výjimka, což způsobí, že vazba bude označena jako neplatná. Alternativní syntaxí <xref:System.Windows.Controls.ExceptionValidationRule> explicitního nastavení je nastavení <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> vlastnosti `true` na objekt <xref:System.Windows.Data.Binding> nebo. <xref:System.Windows.Data.MultiBinding>

- <xref:System.Windows.Controls.DataErrorValidationRule> Objekt kontroluje chyby, které jsou vyvolány objekty, které implementují <xref:System.ComponentModel.IDataErrorInfo> rozhraní. Příklad použití tohoto ověřovacího pravidla naleznete v tématu <xref:System.Windows.Controls.DataErrorValidationRule>. Alternativní syntaxí <xref:System.Windows.Controls.DataErrorValidationRule> explicitního nastavení je nastavení <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> vlastnosti `true` na objekt <xref:System.Windows.Data.Binding> nebo. <xref:System.Windows.Data.MultiBinding>

Můžete také vytvořit vlastní ověřovací pravidlo odvozením z <xref:System.Windows.Controls.ValidationRule> třídy a implementací <xref:System.Windows.Controls.ValidationRule.Validate%2A> metody. Následující příklad ukazuje pravidlo používané *seznamem pro přidání produktu* "počáteční datum" <xref:System.Windows.Controls.TextBox> z oddílu [co je datová vazba](#what-is-data-binding) .

[!code-csharp[FutureDateRule](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/FutureDateRule.cs#FutureDateRule)]
[!code-vb[FutureDateRule](~/samples/snippets/desktop-guide/wpf/data-binding-overview/vb/FutureDateRule.vb#FutureDateRule)]

*StartDateEntryForm* <xref:System.Windows.Controls.TextBox> používá tento *FutureDateRule*, jak je znázorněno v následujícím příkladu.

[!code-xaml[TextboxStartDate](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#TextboxStartDate)]

Vzhledem k <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> tomu, <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>že se jedná o hodnotu, modul vazby aktualizuje zdrojovou hodnotu při každém stisknutí klávesy, což znamená, <xref:System.Windows.Data.Binding.ValidationRules%2A> že také kontroluje všechna pravidla v kolekci při každém stisknutí klávesy. Tato diskuze probereme dále v části proces ověřování.

### <a name="providing-visual-feedback"></a>Poskytování vizuálních názorů

Pokud uživatel zadá neplatnou hodnotu, možná budete chtít zadat zpětnou vazbu k chybě v uživatelském rozhraní aplikace. Jedním ze způsobů, jak tuto zpětnou vazbu poskytnout <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> , je nastavení připojené vlastnosti <xref:System.Windows.Controls.ControlTemplate>na vlastní. Jak je znázorněno v předchozí části, používá *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> s <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> názvem *validationTemplate*. Následující příklad ukazuje definici *validationTemplate*.

[!code-xaml[ControlTemplate](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#ControlTemplate)]

<xref:System.Windows.Controls.AdornedElementPlaceholder> Element určuje, kde by měl být umístěn ovládací prvek, který je upravován.

Kromě toho můžete také použít <xref:System.Windows.Controls.ToolTip> k zobrazení chybové zprávy. *StartDateEntryForm* i *StartPriceEntryForm*<xref:System.Windows.Controls.TextBox>ES používají styl *textStyleTextBox*, který vytvoří <xref:System.Windows.Controls.ToolTip> a zobrazí chybovou zprávu. Následující příklad ukazuje definici *textStyleTextBox*. Připojená vlastnost <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> je `true` v případě, že jedna nebo více vazeb vlastností vázaného prvku je v chybě.

[!code-xaml[TextBoxStyle](~/samples/snippets/desktop-guide/wpf/data-binding-overview/csharp/DataValidation.xaml#TextBoxStyle)]

<xref:System.Windows.Controls.Validation.ErrorTemplate%2A> Pokud dojde k chybě ověřování <xref:System.Windows.Controls.ToolTip>, bude mít *StartDateEntryForm* <xref:System.Windows.Controls.TextBox> v případě, že se vyskytne chyba ověření, podobně jako následující.

![Chyba ověření datové vazby](./media/data-binding-overview/demo-validation-date.png "DataBindingDemo_Validation")

<xref:System.Windows.Data.Binding> Pokud máte přidružená ověřovací pravidla, ale <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> u vázaného ovládacího prvku neurčíte, použije se výchozí <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> nastavení pro upozorňování uživatelů, když dojde k chybě ověření. Výchozí <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> je šablona ovládacího prvku, která definuje červené ohraničení ve vrstvě doplňků. Ve výchozím nastavení <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> a <xref:System.Windows.Controls.ToolTip>je uživatelské rozhraní *StartPriceEntryForm* <xref:System.Windows.Controls.TextBox> v případě chyby ověřování vypadat následovně.

![Chyba ověření datové vazby](./media/data-binding-overview/demo-validation-price.png "DataBindingDemo_ValidationDefault")

Příklad toho, jak poskytnout logiku pro ověření všech ovládacích prvků v dialogovém okně, naleznete v části vlastní dialogová okna v tématu [Přehled](../../framework/wpf/app-development/dialog-boxes-overview.md)dialogových oken.

### <a name="validation-process"></a>Proces ověření

K ověření obvykle dochází při přenosu hodnoty cíle do vlastnosti zdroje vazby. K tomuto přenosu dochází <xref:System.Windows.Data.BindingMode.TwoWay> u <xref:System.Windows.Data.BindingMode.OneWayToSource> vazeb a. K opakování iterace dojde k tomu, že aktualizace zdroje závisí na hodnotě <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> vlastnosti, jak je popsáno v oddílu [co Triggers source aktualizace](#what-triggers-source-updates) .

Následující položky popisují proces *ověřování* . Pokud během tohoto procesu dojde k chybě ověřování nebo k jinému typu chyby, proces se zastaví:

1. Modul vazby kontroluje, zda jsou definovány vlastní <xref:System.Windows.Controls.ValidationRule> objekty, jejichž <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> sada je nastavena na <xref:System.Windows.Controls.ValidationStep.RawProposedValue> hodnotu pro <xref:System.Windows.Data.Binding>to, v takovém případě volá <xref:System.Windows.Controls.ValidationRule.Validate%2A> metodu na každý <xref:System.Windows.Controls.ValidationRule> , dokud jedna z nich nespustí chybu nebo dokud všechny neprojde.

2. Modul vazby pak volá konvertor, pokud existuje.

3. Je-li převaděč úspěšný, modul vazby zkontroluje, zda jsou definovány vlastní <xref:System.Windows.Controls.ValidationRule> objekty, jejichž <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> sada je nastavena na <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> hodnotu pro <xref:System.Windows.Data.Binding>to, v takovém případě volá <xref:System.Windows.Controls.ValidationRule.Validate%2A> metodu na každý <xref:System.Windows.Controls.ValidationRule> , který <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> je nastaven <xref:System.Windows.Controls.ValidationStep.ConvertedProposedValue> na hodnotu, dokud jedna z nich neprojde do chyby nebo dokud všechny nepřestanou.

4. Modul vazby nastaví vlastnost source.

5. Modul vazby kontroluje, zda jsou definovány vlastní <xref:System.Windows.Controls.ValidationRule> objekty, jejichž <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> sada je nastavena na <xref:System.Windows.Controls.ValidationStep.UpdatedValue> hodnotu pro <xref:System.Windows.Data.Binding>to, v takovém případě volá <xref:System.Windows.Controls.ValidationRule.Validate%2A> metodu pro každý <xref:System.Windows.Controls.ValidationRule> , který <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> je nastaven <xref:System.Windows.Controls.ValidationStep.UpdatedValue> na hodnotu, dokud jedna z nich neproběhne v případě chyby nebo dokud všechny z nich neprojde. Pokud <xref:System.Windows.Controls.DataErrorValidationRule> je přidružen k vazbě a <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> je nastaven na výchozí hodnotu, <xref:System.Windows.Controls.ValidationStep.UpdatedValue> <xref:System.Windows.Controls.DataErrorValidationRule> je v tomto okamžiku zaškrtnuto. V tomto okamžiku je zaškrtnuta veškerá vazba <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A> s nastavenou na `true` hodnotu.

6. Modul vazby kontroluje, zda jsou definovány vlastní <xref:System.Windows.Controls.ValidationRule> objekty, jejichž <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> sada je nastavena na <xref:System.Windows.Controls.ValidationStep.CommittedValue> hodnotu pro <xref:System.Windows.Data.Binding>to, v takovém případě volá <xref:System.Windows.Controls.ValidationRule.Validate%2A> metodu pro každý <xref:System.Windows.Controls.ValidationRule> , který <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> je nastaven <xref:System.Windows.Controls.ValidationStep.CommittedValue> na hodnotu, dokud jedna z nich neproběhne v případě chyby nebo dokud všechny z nich neprojde.

Pokud v <xref:System.Windows.Controls.ValidationRule> průběhu tohoto procesu nedojde k žádnému předání, modul vazby vytvoří <xref:System.Windows.Controls.ValidationError> objekt a přidá jej do <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> kolekce vázaného elementu. Předtím, než modul vazby modul <xref:System.Windows.Controls.ValidationRule> spustí objekty v kterémkoli daném kroku, odebere všechny <xref:System.Windows.Controls.ValidationError> , které byly přidány do <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> vlastnosti připojené prvku vázaného elementu v průběhu tohoto kroku. Například pokud je, jejichž <xref:System.Windows.Controls.ValidationRule> <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> <xref:System.Windows.Controls.ValidationStep.UpdatedValue> nastavení je neúspěšné, při příštím procesu ověření vytvoří modul vazby modul, který <xref:System.Windows.Controls.ValidationError> bezprostředně před tím, než zavolá metodu <xref:System.Windows.Controls.ValidationRule> , která je <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> nastavena na <xref:System.Windows.Controls.ValidationStep.UpdatedValue>hodnotu.

Pokud <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> není prázdné, <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> připojená vlastnost prvku je nastavena na `true`. Pokud <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A> <xref:System.Windows.Data.Binding> je vlastnost ovládacího prvku nastavena na `true`, pak modul vazby vyvolá <xref:System.Windows.Controls.Validation.Error?displayProperty=nameWithType> připojenou událost na elementu.

Všimněte si také, že platný přenos hodnoty v obou směrech (cíl do zdroje nebo zdroj do cíle) vymaže <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> připojenou vlastnost.

Pokud vazba buď <xref:System.Windows.Controls.ExceptionValidationRule> obsahuje přidruženou, nebo má <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> vlastnost nastavenou na `true` a výjimka je vyvolána, když modul vazby nastaví zdroj, modul vazby zkontroluje, zda existuje. <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> Máte možnost použít <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> zpětné volání k poskytnutí vlastní obslužné rutiny pro zpracování výjimek. Pokud <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A> není zadán <xref:System.Windows.Data.Binding>, vytvoří modul vazby modul <xref:System.Windows.Controls.ValidationError> s výjimkou a přidá jej do <xref:System.Windows.Controls.Validation.Errors%2A?displayProperty=nameWithType> kolekce vázaného elementu.

## <a name="debugging-mechanism"></a>Mechanismus ladění

Můžete nastavit připojenou vlastnost <xref:System.Diagnostics.PresentationTraceSources.TraceLevel%2A?displayProperty=nameWithType> objektu souvisejícího s vazbou pro příjem informací o stavu konkrétní vazby.

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Controls.DataErrorValidationRule>
- [Vytvoření vazby k výsledkům dotazu LINQ](../../framework/wpf/data/how-to-bind-to-the-results-of-a-linq-query.md)
- [Datová vazba](../../framework/wpf/advanced/optimizing-performance-data-binding.md)
- [Ukázka datových vazeb][data-binding-demo]
- [Články s postupy](../../framework/wpf/data/data-binding-how-to-topics.md)
- [Vytvoření vazby ke zdroji dat ADO.NET](../../framework/wpf/data/how-to-bind-to-an-ado-net-data-source.md)

[data-binding-demo]: https://github.com/microsoft/WPF-Samples/tree/master/Sample%20Applications/DataBindingDemo "Ukázková aplikace datové vazby"
