---
title: Vlastní vlastnosti závislosti
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- implementing [WPF], wrappers
- registering properties [WPF]
- properties [WPF], metadata
- metadata [WPF], for properties
- custom dependency properties [WPF]
- properties [WPF], registering
- wrappers [WPF], implementing
- dependency properties [WPF], custom
ms.assetid: e6bfcfac-b10d-4f58-9f77-a864c2a2938f
ms.openlocfilehash: 8e3ac7207a5ef05b94e97f005ecd17d5078669a4
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740883"
---
# <a name="custom-dependency-properties"></a>Vlastní vlastnosti závislosti

Toto téma popisuje důvody, které [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vývojáři aplikací a tvůrci komponent mohou vytvořit vlastní vlastnost závislosti, a popisuje kroky implementace a také některé možnosti implementace, které mohou zlepšit výkon, použitelnost , nebo univerzálnost vlastnosti.

<a name="prerequisites"></a>

## <a name="prerequisites"></a>Požadavky

V tomto tématu se předpokládá, že rozumíte vlastnostem závislosti z perspektivy uživatele existujících vlastností závislosti na třídách [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a přečtěte si téma [Přehled vlastností závislosti](dependency-properties-overview.md) . Chcete-li postupovat podle příkladů v tomto tématu, měli byste také pochopit [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] a vědět, jak psát [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.

<a name="whatis"></a>

## <a name="what-is-a-dependency-property"></a>Co je vlastnost závislosti?

Můžete povolit, co by jinak bylo vlastnost modulu CLR (Common Language Runtime) pro podporu stylů, datových vazeb, dědičnosti, animací a výchozích hodnot, a to implementací jako vlastnosti závislosti. Vlastnosti závislostí jsou vlastnosti, které jsou zaregistrovány v systému vlastností [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zavoláním metody <xref:System.Windows.DependencyProperty.Register%2A> (nebo <xref:System.Windows.DependencyProperty.RegisterReadOnly%2A>) a, které jsou vyvolány polem identifikátoru <xref:System.Windows.DependencyProperty>. Vlastnosti závislostí lze použít pouze <xref:System.Windows.DependencyObject> typy, ale <xref:System.Windows.DependencyObject> je poměrně vysoké v hierarchii tříd [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], takže většina tříd, které jsou k dispozici v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], mohou podporovat vlastnosti závislostí. Další informace o vlastnostech závislosti a některých terminologii a konvencích používaných k jejich popisu v této sadě SDK najdete v tématu [Přehled vlastností závislostí](dependency-properties-overview.md).

<a name="example_dp"></a>

## <a name="examples-of-dependency-properties"></a>Příklady vlastností závislosti

Příklady vlastností závislosti, které jsou implementované na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] třídy, zahrnují vlastnost <xref:System.Windows.Controls.Control.Background%2A>, vlastnost <xref:System.Windows.FrameworkElement.Width%2A> a vlastnost <xref:System.Windows.Controls.TextBox.Text%2A>, mezi mnoho dalších. Každá vlastnost závislosti vystavená třídou má odpovídající veřejné statické pole typu <xref:System.Windows.DependencyProperty> vystavené na stejné třídě. Toto je identifikátor vlastnosti závislosti. Identifikátor je pojmenován pomocí konvence: název vlastnosti závislosti s řetězcem `Property` k němu připojen. Například odpovídající pole identifikátoru <xref:System.Windows.DependencyProperty> pro vlastnost <xref:System.Windows.Controls.Control.Background%2A> je <xref:System.Windows.Controls.Control.BackgroundProperty>. Identifikátor ukládá informace o vlastnosti závislosti, jak byla registrována, a identifikátor je poté použit později pro jiné operace, které zahrnují vlastnost Dependency, jako je například volání <xref:System.Windows.DependencyObject.SetValue%2A>.

Jak je uvedeno v [přehledu vlastností závislosti](dependency-properties-overview.md), všechny vlastnosti závislosti v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (kromě přidružených vlastností) jsou také vlastnostmi CLR z důvodu implementace "Obálka". Z kódu proto můžete získat nebo nastavit vlastnosti závislosti voláním přístupových objektů CLR, které definují obálky, stejným způsobem, jako byste používali jiné vlastnosti CLR. Jako spotřebitel navázaných vlastností závislosti nepoužíváte obvykle <xref:System.Windows.DependencyObject> metody <xref:System.Windows.DependencyObject.GetValue%2A> a <xref:System.Windows.DependencyObject.SetValue%2A>, které jsou spojovacím bodem pro základní systém vlastností. Namísto toho již existující implementace vlastností CLR bude volána <xref:System.Windows.DependencyObject.GetValue%2A> a <xref:System.Windows.DependencyObject.SetValue%2A> v rámci `get` a `set`ch implementačních vlastností vlastnosti, pomocí pole identifikátoru odpovídajícím způsobem. Pokud sami implementujete vlastní vlastnost závislosti, budete obálku definovat podobným způsobem.

<a name="backing_with_dp"></a>

## <a name="when-should-you-implement-a-dependency-property"></a>Kdy by měla být implementována vlastnost závislosti?

Při implementaci vlastnosti pro třídu, pokud je třída odvozena z <xref:System.Windows.DependencyObject>, máte možnost tuto vlastnost zálohovat s identifikátorem <xref:System.Windows.DependencyProperty> a tedy nastavit vlastnost závislosti. Vlastnost závislosti není vždy nutná ani vhodná a bude záviset na potřebách vašeho scénáře. V některých případech je vhodná typická metoda zálohování vlastnosti s privátním polem. Vlastnost byste však měli implementovat jako vlastnost závislosti vždy, když chcete, aby vlastnost podporovala jednu nebo více z následujících možností [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:

- Chcete vlastnost nastavit ve stylu. Další informace najdete v tématu [stylování a šablonování](../controls/styling-and-templating.md).

- Chcete, aby vlastnost podporovala datovou vazbu. Další informace o vlastnostech závislosti datových vazeb naleznete v tématu [vazba vlastností dvou ovládacích prvků](../data/how-to-bind-the-properties-of-two-controls.md).

- Chcete nastavit vlastnost, která má být nastavená pomocí dynamického odkazu na prostředek. Další informace naleznete v tématu [prostředky XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).

- Chcete automaticky zdědit hodnotu vlastnosti z nadřazeného prvku ve stromu elementu. V tomto případě se zaregistrujte pomocí metody <xref:System.Windows.DependencyProperty.RegisterAttached%2A>, a to i v případě, že pro přístup k CLR vytvoříte také obálku vlastností. Další informace najdete v tématu [Dědičnost hodnot vlastností](property-value-inheritance.md).

- Chcete, aby byla vlastnost animovaná. Další informace najdete v tématu [Přehled animací](../graphics-multimedia/animation-overview.md).

- Chcete, aby systém vlastností nahlásil, kdy byla předchozí hodnota vlastnosti změněna akcemi provedenými systémem vlastností, prostředím nebo uživatelem, nebo čtením a použitím stylů. Pomocí metadat vlastností může vlastnost specifikovat metodu zpětného volání, která bude vyvolána pokaždé, když systém vlastností určí, že vaše hodnota vlastnosti byla změněna na konečně. Související koncept je konverze hodnoty vlastnosti. Další informace najdete v tématu [zpětná volání vlastností závislosti a ověřování](dependency-property-callbacks-and-validation.md).

- Chcete použít vytvořené konvence metadat, které používá i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] procesy, jako je například vytváření sestav, zda změna hodnoty vlastnosti musí vyžadovat, aby systém rozložení přetvářely vizuály pro prvek. Nebo chcete mít možnost použít přepsání metadat, aby odvozené třídy mohly měnit vlastnosti založené na metadatech, jako je například výchozí hodnota.

- Chcete, aby vlastnosti vlastního ovládacího prvku přijímaly podporu návrháře WPF v aplikaci Visual Studio, například úpravy okna **vlastností** . Další informace najdete v tématu [Přehled tvorby řízení](../controls/control-authoring-overview.md).

Při prostudování těchto scénářů byste měli také zvážit, zda můžete dosáhnout svého scénáře přepsáním metadat existující vlastnosti závislosti, nikoli implementací zcela nové vlastnosti. Bez ohledu na to, jestli je přepsání metadat praktické, záleží na vašem scénáři a na tom, jak se tento scénář podobá implementaci ve stávajících [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastností a třídách závislosti. Další informace o přepsání metadat u existujících vlastností najdete v tématu [metadata vlastnosti závislosti](dependency-property-metadata.md).

<a name="checklist"></a>

## <a name="checklist-for-defining-a-dependency-property"></a>Kontrolní seznam pro definování vlastnosti závislosti

Definování vlastnosti závislosti se skládá ze čtyř různých konceptů. Tyto koncepty nejsou nutně striktní kroky postupu, protože některé z těchto zakončení jsou kombinovány jako samostatné řádky kódu v implementaci:

- Volitelné Vytvořte metadata vlastnosti pro vlastnost závislosti.

- Zaregistrujte název vlastnosti se systémem vlastností a určete typ vlastníka a typ hodnoty vlastnosti. Zadejte také metadata vlastnosti, pokud je použita.

- Zadejte <xref:System.Windows.DependencyProperty> identifikátor jako `public` `static` `readonly` pole v typu vlastníka.

- Definujte vlastnost "Obálka" CLR, jejíž název odpovídá názvu vlastnosti závislosti. Implementací `get` vlastností "Obálka" a `set` přistupujících objektů se připojte k vlastnosti závislosti, která ji zálohuje.

<a name="registering"></a>

### <a name="registering-the-property-with-the-property-system"></a>Registrace vlastnosti se systémem vlastností

Aby vlastnost byla vlastností závislosti, musíte tuto vlastnost zaregistrovat do tabulky udržované systémem vlastností a přidělit jí jedinečný identifikátor, který se použije jako kvalifikátor pro pozdější operace se systémem vlastností. Tyto operace mohou být interními operacemi nebo vlastní kód, který volá rozhraní API systému vlastností. Chcete-li zaregistrovat vlastnost, zavoláte metodu <xref:System.Windows.DependencyProperty.Register%2A> v těle vaší třídy (uvnitř třídy, ale mimo jakékoli definice členů). Pole identifikátor je také k dispozici ve volání metody <xref:System.Windows.DependencyProperty.Register%2A> jako návratová hodnota. Důvod, proč se volání <xref:System.Windows.DependencyProperty.Register%2A> provádí mimo jiné definice členů, je, že použijete tuto návratovou hodnotu k přiřazení a vytvoření `public` `static` `readonly` pole typu <xref:System.Windows.DependencyProperty> jako součást vaší třídy. Toto pole se zobrazí jako identifikátor vlastnosti závislosti.

[!code-csharp[WPFAquariumSln#RegisterAG](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerag)]
[!code-vb[WPFAquariumSln#RegisterAG](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerag)]

<a name="nameconventions"></a>

### <a name="dependency-property-name-conventions"></a>Konvence názvů vlastností závislosti

Existují zásady vytváření názvů týkající se vlastností závislosti, které je třeba dodržovat ve všech výjimečných případech.

Samotná vlastnost Dependency bude mít jako v tomto příkladu základní název "AquariumGraphic", který je uveden jako první parametr <xref:System.Windows.DependencyProperty.Register%2A>. Tento název musí být jedinečný v rámci každého typu registrace. Vlastnosti závislosti zděděné prostřednictvím základních typů jsou považovány za již součástí typu registrace; názvy děděných vlastností nelze znovu zaregistrovat. Nicméně existuje technika, jak přidat třídu jako vlastníka vlastnosti závislosti, i když tato vlastnost závislosti není zděděná; Podrobnosti najdete v tématu [Metadata vlastností závislosti](dependency-property-metadata.md).

Při vytváření pole identifikátoru pojmenujte toto pole názvem vlastnosti, jak jste ji zaregistrovali, a příponou `Property`. Toto pole je vaším identifikátorem pro vlastnost závislosti a později se použije jako vstup pro <xref:System.Windows.DependencyObject.SetValue%2A> a <xref:System.Windows.DependencyObject.GetValue%2A> volání, která provedete v obálkách, jakýmkoli jiným kódem přístup k vlastnosti vlastním kódem. , jakýmkoli přístupem k externímu kódu, který povolíte, systémem vlastností a potenciálně [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesory.

> [!NOTE]
> Definování vlastnosti Dependency v těle třídy je typická implementace, ale je také možné definovat vlastnost závislosti ve statickém konstruktoru třídy. Tento přístup může být smysl, pokud potřebujete více než jeden řádek kódu pro inicializaci vlastnosti závislosti.

<a name="wrapper1"></a>

### <a name="implementing-the-wrapper"></a>Implementace "obálky"

Vaše implementace obálky by měla volat <xref:System.Windows.DependencyObject.GetValue%2A> v implementaci `get` a <xref:System.Windows.DependencyObject.SetValue%2A> v `set` implementaci (pro přehlednost se tady zobrazují původní volání registrace a pole).

Ve všech výjimečných případech by vaše implementace obálky měly provádět pouze akce <xref:System.Windows.DependencyObject.GetValue%2A> a <xref:System.Windows.DependencyObject.SetValue%2A>, v uvedeném pořadí. Důvod tohoto postupu je popsán v tématu [vlastnosti načítání a závislostí XAML](xaml-loading-and-dependency-properties.md).

Všechny existující vlastnosti veřejné závislosti, které jsou k dispozici na třídách [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] používají tento jednoduchý model implementace obálky; Většina složitosti, jak fungují vlastnosti závislostí, jsou buď v podstatě chování systému vlastností, nebo jsou implementovány prostřednictvím jiných konceptů, jako jsou například konverze a zpětná volání změn vlastností prostřednictvím metadat vlastností.

[!code-csharp[WPFAquariumSln#AGWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
[!code-vb[WPFAquariumSln#AGWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]

Podle konvence, název vlastnosti obálky musí být stejný jako název zvolený a uvedený jako první parametr volání <xref:System.Windows.DependencyProperty.Register%2A>, které tuto vlastnost zaregistrovaly. Pokud vaše vlastnost nedodržuje konvenci, nemusí to nutně zakázat všechna možná použití, ale dojde k několika významným problémům:

- Některé aspekty stylů a šablon nebudou fungovat.

- Většina nástrojů a návrhářů musí spoléhat na konvence pojmenování, aby byly správně serializovány [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], nebo poskytovala pomoc prostředí návrháře na úrovni jednotlivých vlastností.

- Aktuální implementace [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ho zavaděče [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] obchází obálky zcela a spoléhá na konvence pojmenování při zpracovávání hodnot atributů. Další informace naleznete v tématu [vlastnosti načítání a závislostí XAML](xaml-loading-and-dependency-properties.md).

<a name="metadata"></a>

### <a name="property-metadata-for-a-new-dependency-property"></a>Metadata vlastností nové vlastnosti závislosti

Při registraci vlastnosti závislosti se při registraci prostřednictvím systému vlastností vytvoří objekt metadat, který ukládá vlastnosti vlastností. Mnohé z těchto vlastností mají výchozí hodnoty, které jsou nastaveny, pokud je vlastnost zaregistrována pomocí jednoduchých signatur <xref:System.Windows.DependencyProperty.Register%2A>. Další signatury <xref:System.Windows.DependencyProperty.Register%2A> umožňují zadat metadata, která chcete při registraci vlastnosti použít. Nejběžnějším metadatům pro vlastnosti závislosti je poskytnout jim výchozí hodnotu, která je použita na nové instance, které používají vlastnost.

Pokud vytváříte vlastnost závislosti, která existuje pro odvozenou třídu <xref:System.Windows.FrameworkElement>, můžete použít lépe specializované třídy metadat <xref:System.Windows.FrameworkPropertyMetadata> spíše než základní třída <xref:System.Windows.PropertyMetadata>. Konstruktor pro třídu <xref:System.Windows.FrameworkPropertyMetadata> má několik signatur, kde můžete určit různé charakteristiky metadat v kombinaci. Chcete-li zadat pouze výchozí hodnotu, použijte signaturu, která přijímá jeden parametr typu <xref:System.Object>. Předejte tento parametr objektu jako výchozí hodnotu konkrétního typu pro vaši vlastnost (zadaná výchozí hodnota musí být typ, který jste zadali jako parametr `propertyType` v volání <xref:System.Windows.DependencyProperty.Register%2A>).

Pro <xref:System.Windows.FrameworkPropertyMetadata>můžete pro vlastnost zadat také příznaky možností metadat. Tyto příznaky se po registraci převedou na diskrétní vlastnosti v metadatech vlastností a používají se ke sdělování určitých podmíněných procesů, jako je například modul rozložení.

#### <a name="setting-appropriate-metadata-flags"></a>Nastavení odpovídajících příznaků metadat

- Pokud vaše vlastnost (nebo změny v její hodnotě) má vliv na [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]a zejména ovlivňuje, jak má systém rozložení změnit velikost nebo vykreslení prvku na stránce, nastavte jeden nebo více následujících příznaků: <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure>, <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange><xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender>.

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure> označuje, že změna této vlastnosti vyžaduje změnu pro [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vykreslování, kde nadřazený objekt může vyžadovat více nebo méně místa v rámci nadřazeného objektu. Například vlastnost Width by měla mít nastavenou příznak.

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange> označuje, že změna této vlastnosti vyžaduje změnu pro [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vykreslování, která obvykle nevyžaduje změnu ve vyhrazeném prostoru, ale znamená, že se změnilo umístění v rámci prostoru. Například vlastnost "Alignment" by měla mít nastavenou příznak.

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender> označuje, že došlo k nějaké jiné změně, která neovlivní rozložení a míru, ale vyžaduje další vykreslování. Příkladem může být vlastnost, která změní barvu existujícího prvku, například "Background".

  - Tyto příznaky se často používají jako protokol v metadatech pro vlastní přepsání implementací systému vlastností nebo zpětných volání rozložení. Například může být <xref:System.Windows.DependencyObject.OnPropertyChanged%2A> zpětné volání, které bude volat <xref:System.Windows.UIElement.InvalidateArrange%2A>, pokud jakákoli vlastnost instance hlásí změnu hodnoty a má <xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A> jako `true` ve svých metadatech.

- Některé vlastnosti mohou ovlivnit vlastnosti vykreslování obsahujícího nadřazeného prvku, a to jak nad, tak i nad změnami v požadované velikosti uvedené výše. Příkladem je vlastnost <xref:System.Windows.Documents.Paragraph.MinOrphanLines%2A> použitá v modelu toku dokumentů, kde změny této vlastnosti mohou změnit celkové vykreslování dokumentu toku, který obsahuje daný odstavec. Použijte <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentArrange> nebo <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentMeasure> k identifikaci podobných případů ve vlastních vlastnostech.

- Ve výchozím nastavení vlastnosti závislosti podporují datovou vazbu. Datovou vazbu můžete záměrně zakázat pro případy, kdy není k dispozici reálný scénář pro datovou vazbu nebo kde je jako problém rozpoznán výkon datové vazby pro velký objekt.

- Ve výchozím nastavení se výchozí hodnota <xref:System.Windows.Data.BindingMode.OneWay><xref:System.Windows.Data.Binding.Mode%2A> vazby dat pro vlastnosti závislostí. Můžete vždycky změnit vazbu, která se má <xref:System.Windows.Data.BindingMode.TwoWay> na instanci vazby. Podrobnosti najdete v tématu [určení směru vazby](../data/how-to-specify-the-direction-of-the-binding.md). Jako autor vlastnosti závislosti ale můžete zvolit, aby vlastnost ve výchozím nastavení použila <xref:System.Windows.Data.BindingMode.TwoWay> režim vazby. Příkladem existující vlastnosti závislosti je <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A?displayProperty=nameWithType>; scénář této vlastnosti je, že <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> nastavení logiky a skládání <xref:System.Windows.Controls.MenuItem> interakci s výchozím stylem motivu. <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> logika vlastností používá datovou vazbu nativně k udržení stavu vlastnosti v souladu s dalšími vlastnostmi stavu a voláními metody. Další příklad vlastnosti, která je ve výchozím nastavení svázána <xref:System.Windows.Data.BindingMode.TwoWay>, je <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>.

- Dědičnost vlastností můžete povolit také u vlastní vlastnosti závislosti nastavením příznaku <xref:System.Windows.FrameworkPropertyMetadataOptions.Inherits>. Dědičnost vlastností je užitečná pro situaci, kdy nadřazené prvky a podřízené prvky mají vlastnost společné a dává smysl pro podřízené prvky, aby tato konkrétní hodnota vlastnosti byla nastavena na stejnou hodnotu jako nadřazená sada. Příklad dědičné vlastnosti je <xref:System.Windows.FrameworkElement.DataContext%2A>, který se používá pro operace vazby k povolení důležitého scénáře hlavních podrobností pro prezentaci dat. Tím, že <xref:System.Windows.FrameworkElement.DataContext%2A> zděditelné, všechny podřízené elementy dědí tento kontext dat také. Z důvodu dědičnosti hodnoty vlastností lze určit kontext dat na stránce nebo v kořenovém adresáři aplikace a nemusíte ho znovu zadávat pro vazby ve všech možných podřízených elementech. <xref:System.Windows.FrameworkElement.DataContext%2A> je také dobrým příkladem k ilustraci, že dědičnost přepisuje výchozí hodnotu, ale může být vždy nastavena místně na všech konkrétních podřízených elementech; Podrobnosti najdete v tématu [použití vzoru hlavní-podrobnosti s hierarchickými daty](../data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md). Dědičnost hodnot vlastností má možné náklady na výkon, a proto by se měla používat bez omezeného výkonu. Podrobnosti najdete v tématu [Dědičnost hodnot vlastností](property-value-inheritance.md).

- Nastavením příznaku <xref:System.Windows.FrameworkPropertyMetadataOptions.Journal> určete, zda má být vlastnost závislosti zjištěna nebo používána službami navigace v deníku. Příkladem je vlastnost <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A>; při přechodu na historii deníku by měla být jakákoli položka vybraná v ovládacím prvku Výběr trvalá.

<a name="RODP"></a>

## <a name="read-only-dependency-properties"></a>Vlastnosti závislosti jen pro čtení

Můžete definovat vlastnost závislosti, která je jen pro čtení. Nicméně scénáře, proč můžete definovat vlastnost jen pro čtení, se trochu liší, jak je postup pro jejich registraci se systémem vlastností a vystavení identifikátoru. Další informace najdete v tématu [vlastnosti závislosti jen pro čtení](read-only-dependency-properties.md).

<a name="CTDP"></a>

## <a name="collection-type-dependency-properties"></a>Vlastnosti závislostí typu kolekce

Vlastnosti závislostí typu kolekce obsahují některé další problémy s implementací, které je potřeba vzít v úvahu. Podrobnosti najdete v tématu [vlastnosti závislostí typu kolekce](collection-type-dependency-properties.md).

<a name="SecurityC"></a>

## <a name="dependency-property-security-considerations"></a>Otázky zabezpečení vlastností závislosti

Vlastnosti závislosti by měly být deklarovány jako veřejné vlastnosti. Pole s identifikátorem vlastnosti závislosti by měly být deklarovány jako veřejná statická pole. I v případě, že se pokusíte deklarovat jiné úrovně přístupu (například chráněné), vlastnost závislosti může být vždy přístupná prostřednictvím identifikátoru v kombinaci s rozhraními API systému vlastností. I pole chráněného identifikátoru je potenciálně dostupné kvůli rozhraním API pro generování sestav metadat nebo k určování hodnot, které jsou součástí systému vlastností, jako je například <xref:System.Windows.LocalValueEnumerator>. Další informace najdete v tématu [zabezpečení vlastností závislosti](dependency-property-security.md).

<a name="DPCtor"></a>

## <a name="dependency-properties-and-class-constructors"></a>Vlastnosti závislosti a konstruktory tříd

V programování spravovaného kódu je obecná zásada (často se vynutila nástroji pro analýzu kódu, jako je FxCop), které konstruktory třídy by neměly volat virtuální metody. Důvodem je, že konstruktory mohou být volány jako základní inicializace konstruktoru odvozené třídy a zadání virtuální metody prostřednictvím konstruktoru může nastat v neúplném stavu inicializace instance objektu, který je konstruován. Při odvozování z jakékoliv třídy, která již je odvozena z <xref:System.Windows.DependencyObject>, byste měli být vědomi, že systém vlastností sám volá a zpřístupňuje virtuální metody interně. Tyto virtuální metody jsou součástí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systémových služeb vlastností. Přepsání metod umožní, aby se odvozené třídy účastnily určení hodnoty. Chcete-li se vyhnout potenciálním problémům s inicializací modulu runtime, neměli byste nastavit hodnoty vlastností závislosti v rámci konstruktorů třídy, pokud nedodržujete velmi konkrétní vzorek konstruktoru. Podrobnosti najdete v tématu [bezpečné vzory konstruktoru pro DependencyObjects](safe-constructor-patterns-for-dependencyobjects.md).

## <a name="see-also"></a>Viz také:

- [Přehled vlastností závislosti](dependency-properties-overview.md)
- [Metadata vlastností závislosti](dependency-property-metadata.md)
- [Přehled vytváření ovládacích prvků](../controls/control-authoring-overview.md)
- [Vlastnosti závislostí typu kolekce](collection-type-dependency-properties.md)
- [Zabezpečení vlastností závislosti](dependency-property-security.md)
- [Vlastnosti závislostí a načítání XAML](xaml-loading-and-dependency-properties.md)
- [Zabezpečené vzory konstruktoru pro DependencyObjects](safe-constructor-patterns-for-dependencyobjects.md)
