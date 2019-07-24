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
ms.openlocfilehash: 1352876b79e103d20d08382ab088f7777c6fe2ae
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401578"
---
# <a name="custom-dependency-properties"></a>Vlastní vlastnosti závislosti

Toto téma popisuje důvody, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] proč můžou vývojáři aplikací a tvůrci součástí vytvořit vlastní vlastnost závislosti, a popisuje kroky implementace a také některé možnosti implementace, které mohou zlepšit výkon. použitelnost nebo univerzálnost vlastnosti.

<a name="prerequisites"></a>

## <a name="prerequisites"></a>Požadavky

V tomto tématu se předpokládá, že rozumíte vlastnostem závislosti z perspektivy uživatele existujících vlastností závislosti ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] třídách a přečetli jste si přehled o [vlastnostech závislosti](dependency-properties-overview.md) v tématu. Chcete-li postupovat podle příkladů v tomto tématu, měli byste také [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pochopit a vědět, jak [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] psát aplikace.

<a name="whatis"></a>

## <a name="what-is-a-dependency-property"></a>Co je vlastnost závislosti?

Můžete povolit, co by jinak bylo vlastnost modulu CLR (Common Language Runtime) pro podporu stylů, datových vazeb, dědičnosti, animací a výchozích hodnot, a to implementací jako vlastnosti závislosti. Vlastnosti závislosti jsou vlastnosti, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] které jsou zaregistrovány v systému vlastností <xref:System.Windows.DependencyProperty.Register%2A> zavoláním metody <xref:System.Windows.DependencyProperty.RegisterReadOnly%2A>(nebo) a, které jsou zajištěny <xref:System.Windows.DependencyProperty> polem identifikátor. Vlastnosti závislosti <xref:System.Windows.DependencyObject> lze použít pouze podle typů, ale <xref:System.Windows.DependencyObject> v hierarchii [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tříd je poměrně vysoké, takže většina tříd, které jsou k dispozici [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v nástroji, může podporovat vlastnosti závislostí. Další informace o vlastnostech závislosti a některých terminologii a konvencích používaných k jejich popisu najdete v [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)]tématu [Přehled vlastností závislosti](dependency-properties-overview.md).

<a name="example_dp"></a>

## <a name="examples-of-dependency-properties"></a>Příklady vlastností závislosti

Příklady vlastností závislosti, které jsou implementované na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] třídy, <xref:System.Windows.Controls.Control.Background%2A> zahrnují vlastnost, <xref:System.Windows.FrameworkElement.Width%2A> vlastnost a <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost, mezi mnoho dalších. Každá vlastnost závislosti vystavená třídou má odpovídající veřejné statické pole typu <xref:System.Windows.DependencyProperty> vystavené u stejné třídy. Toto je identifikátor vlastnosti závislosti. Identifikátor je pojmenován pomocí konvence: název vlastnosti závislosti s připojeným řetězcem `Property` . Například odpovídající <xref:System.Windows.DependencyProperty> pole identifikátoru <xref:System.Windows.Controls.Control.Background%2A> pro vlastnost je <xref:System.Windows.Controls.Control.BackgroundProperty>. Identifikátor ukládá informace o vlastnosti závislosti, jak byla registrována, a identifikátor je poté použit později pro jiné operace, které zahrnují vlastnost Dependency, jako je například volání <xref:System.Windows.DependencyObject.SetValue%2A>.

Jak je uvedeno v [přehledu vlastností závislosti](dependency-properties-overview.md), všechny vlastnosti závislosti v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (kromě nejpřipojených vlastností) jsou také vlastnostmi CLR z důvodu implementace "Obálka". Z kódu proto můžete získat nebo nastavit vlastnosti závislosti voláním přístupových objektů CLR, které definují obálky, stejným způsobem, jako byste používali jiné vlastnosti CLR. Jako spotřebitel zavedených vlastností závislosti nepoužíváte <xref:System.Windows.DependencyObject> obvykle metody <xref:System.Windows.DependencyObject.GetValue%2A> a <xref:System.Windows.DependencyObject.SetValue%2A>, které jsou spojovacím bodem pro základní systém vlastností. Namísto toho již existující implementace vlastností CLR bude <xref:System.Windows.DependencyObject.GetValue%2A> volána a <xref:System.Windows.DependencyObject.SetValue%2A> v rámci `get` obálky a `set` v implementaci obálky vlastnosti, pomocí pole identifikátoru odpovídajícím způsobem. Pokud sami implementujete vlastní vlastnost závislosti, budete obálku definovat podobným způsobem.

<a name="backing_with_dp"></a>

## <a name="when-should-you-implement-a-dependency-property"></a>Kdy by měla být implementována vlastnost závislosti?

Při implementaci vlastnosti pro třídu, pokud je třída odvozena z <xref:System.Windows.DependencyObject>, máte možnost tuto vlastnost zálohovat <xref:System.Windows.DependencyProperty> s identifikátorem, a tedy nastavit vlastnost závislosti. Vlastnost závislosti není vždy nutná ani vhodná a bude záviset na potřebách vašeho scénáře. V některých případech je vhodná typická metoda zálohování vlastnosti s privátním polem. Vlastnost byste však měli implementovat jako vlastnost závislosti vždy, když chcete, aby vlastnost podporovala jednu nebo více z následujících [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] možností:

- Chcete vlastnost nastavit ve stylu. Další informace najdete v tématu [stylování a šablonování](../controls/styling-and-templating.md).

- Chcete, aby vlastnost podporovala datovou vazbu. Další informace o vlastnostech závislosti datových vazeb naleznete v tématu [vazba vlastností dvou ovládacích prvků](../data/how-to-bind-the-properties-of-two-controls.md).

- Chcete nastavit vlastnost, která má být nastavená pomocí dynamického odkazu na prostředek. Další informace naleznete v tématu [prostředky XAML](xaml-resources.md).

- Chcete automaticky zdědit hodnotu vlastnosti z nadřazeného prvku ve stromu elementu. V tomto případě se pomocí <xref:System.Windows.DependencyProperty.RegisterAttached%2A> metody zaregistrujete i v případě, že také vytvoříte obálku vlastnosti pro přístup k CLR. Další informace najdete v tématu [Dědičnost hodnot vlastností](property-value-inheritance.md).

- Chcete, aby byla vlastnost animovaná. Další informace najdete v tématu [Přehled animací](../graphics-multimedia/animation-overview.md).

- Chcete, aby systém vlastností nahlásil, kdy byla předchozí hodnota vlastnosti změněna akcemi provedenými systémem vlastností, prostředím nebo uživatelem, nebo čtením a použitím stylů. Pomocí metadat vlastností může vlastnost specifikovat metodu zpětného volání, která bude vyvolána pokaždé, když systém vlastností určí, že vaše hodnota vlastnosti byla změněna na konečně. Související koncept je konverze hodnoty vlastnosti. Další informace najdete v tématu [zpětná volání vlastností závislosti a ověřování](dependency-property-callbacks-and-validation.md).

- Chcete použít vytvořené konvence metadat, které jsou používány [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] i procesy, jako je například vytváření sestav, zda má změna hodnoty vlastnosti vyžadovat, aby systém rozložení přetvářely vizuály pro prvek. Nebo chcete mít možnost použít přepsání metadat, aby odvozené třídy mohly měnit vlastnosti založené na metadatech, jako je například výchozí hodnota.

- Chcete, aby vlastnosti vlastního ovládacího prvku přijímaly podporu návrháře WPF v aplikaci Visual Studio, například úpravy okna **vlastností** . Další informace najdete v tématu [Přehled tvorby řízení](../controls/control-authoring-overview.md).

Při prostudování těchto scénářů byste měli také zvážit, zda můžete dosáhnout svého scénáře přepsáním metadat existující vlastnosti závislosti, nikoli implementací zcela nové vlastnosti. Bez ohledu na to, jestli je přepsání metadat praktické, záleží na vašem scénáři a na tom, jak přesně [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] se scénář podobá implementaci v existujících vlastnostech a třídách závislosti. Další informace o přepsání metadat u existujících vlastností najdete v tématu [metadata vlastnosti závislosti](dependency-property-metadata.md).

<a name="checklist"></a>

## <a name="checklist-for-defining-a-dependency-property"></a>Kontrolní seznam pro definování vlastnosti závislosti

Definování vlastnosti závislosti se skládá ze čtyř různých konceptů. Tyto koncepty nejsou nutně striktní kroky postupu, protože některé z těchto zakončení jsou kombinovány jako samostatné řádky kódu v implementaci:

- Volitelné Vytvořte metadata vlastnosti pro vlastnost závislosti.

- Zaregistrujte název vlastnosti se systémem vlastností a určete typ vlastníka a typ hodnoty vlastnosti. Zadejte také metadata vlastnosti, pokud je použita.

- <xref:System.Windows.DependencyProperty> Definujte identifikátor `public` jakopole`static`v typuvlastníka.`readonly`

- Definujte vlastnost "Obálka" CLR, jejíž název odpovídá názvu vlastnosti závislosti. Implementací vlastností `get` "Obálka" a `set` přístupových objektů CLR se připojte k vlastnosti závislosti, která ji zálohuje.

<a name="registering"></a>

### <a name="registering-the-property-with-the-property-system"></a>Registrace vlastnosti se systémem vlastností

Aby vlastnost byla vlastností závislosti, musíte tuto vlastnost zaregistrovat do tabulky udržované systémem vlastností a přidělit jí jedinečný identifikátor, který se použije jako kvalifikátor pro pozdější operace se systémem vlastností. Tyto operace mohou být interními operacemi nebo vlastní kód, který volá rozhraní API systému vlastností. Chcete-li zaregistrovat vlastnost, zavoláte <xref:System.Windows.DependencyProperty.Register%2A> metodu v těle vaší třídy (uvnitř třídy, ale mimo jakékoli definice členů). Pole identifikátor je také zajištěno <xref:System.Windows.DependencyProperty.Register%2A> voláním metody, jako návratová hodnota. Důvod, proč je <xref:System.Windows.DependencyProperty.Register%2A> volání provedeno mimo jiné definice členů, je, že použijete tuto návratovou hodnotu k přiřazení a `readonly` `public` `static` vytvoření pole typu <xref:System.Windows.DependencyProperty> jako součást vaší třídy. Toto pole se zobrazí jako identifikátor vlastnosti závislosti.

[!code-csharp[WPFAquariumSln#RegisterAG](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerag)]
[!code-vb[WPFAquariumSln#RegisterAG](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerag)]

<a name="nameconventions"></a>

### <a name="dependency-property-name-conventions"></a>Konvence názvů vlastností závislosti

Existují zásady vytváření názvů týkající se vlastností závislosti, které je třeba dodržovat ve všech výjimečných případech.

Samotná vlastnost Dependency bude mít základní název "AquariumGraphic" jako v tomto příkladu, který je uveden jako první parametr <xref:System.Windows.DependencyProperty.Register%2A>. Tento název musí být jedinečný v rámci každého typu registrace. Vlastnosti závislosti zděděné prostřednictvím základních typů jsou považovány za již součástí typu registrace; názvy děděných vlastností nelze znovu zaregistrovat. Nicméně existuje technika, jak přidat třídu jako vlastníka vlastnosti závislosti, i když tato vlastnost závislosti není zděděná; Podrobnosti najdete v tématu [Metadata vlastností závislosti](dependency-property-metadata.md).

Při vytváření pole identifikátoru pojmenujte toto pole názvem vlastnosti, jak jste ji zaregistrovali, a příponou `Property`. Toto pole je váš identifikátor pro vlastnost závislosti a později se použije jako vstup pro <xref:System.Windows.DependencyObject.SetValue%2A> volání a <xref:System.Windows.DependencyObject.GetValue%2A> , která provedete v obálkách, jakýmkoli jiným kódem přístup k vlastnosti pomocí vlastního kódu, a to pomocí jakéhokoli přístupu k externímu kódu, který povolíte. , systémem vlastností a potenciálně [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesory.

> [!NOTE]
> Definování vlastnosti Dependency v těle třídy je typická implementace, ale je také možné definovat vlastnost závislosti ve statickém konstruktoru třídy. Tento přístup může být smysl, pokud potřebujete více než jeden řádek kódu pro inicializaci vlastnosti závislosti.

<a name="wrapper1"></a>

### <a name="implementing-the-wrapper"></a>Implementace "obálky"

Vaše implementace obálky by měla <xref:System.Windows.DependencyObject.GetValue%2A> volat `get` v `set` implementaci a <xref:System.Windows.DependencyObject.SetValue%2A> v implementaci (pro přehlednost se tady zobrazuje i původní volání registrace a pole).

Ve všech výjimečných případech by vaše implementace obálky měly provádět pouze <xref:System.Windows.DependencyObject.GetValue%2A> akce a <xref:System.Windows.DependencyObject.SetValue%2A> , v uvedeném pořadí. Důvod tohoto postupu je popsán v tématu [vlastnosti načítání a závislostí XAML](xaml-loading-and-dependency-properties.md).

Všechny stávající vlastnosti veřejné závislosti, které jsou k dispozici na těchto [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] třídách, používají tento jednoduchý model implementace obálky; většina složitosti, jak vlastnosti závislosti fungují, jsou buď v podstatě chování systému vlastností, nebo je. implementováno prostřednictvím jiných konceptů, jako jsou například konverze a zpětná volání změny vlastností prostřednictvím metadat vlastností.

[!code-csharp[WPFAquariumSln#AGWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
[!code-vb[WPFAquariumSln#AGWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]

Znovu podle konvence, název vlastnosti obálky musí být stejný jako název zvolený a uvedený jako první parametr <xref:System.Windows.DependencyProperty.Register%2A> volání, který vlastnost zaregistroval. Pokud vaše vlastnost nedodržuje konvenci, nemusí to nutně zakázat všechna možná použití, ale dojde k několika významným problémům:

- Některé aspekty stylů a šablon nebudou fungovat.

- Většina nástrojů a návrhářů musí spoléhat na správnou serializaci [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]zásad vytváření názvů nebo poskytnutí pomoci pro prostředí návrháře na úrovni jednotlivých vlastností.

- Aktuální implementace [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zavaděče obchází obálky zcela a spoléhá na konvence pojmenování při zpracovávání hodnot atributů. Další informace naleznete v tématu [vlastnosti načítání a závislostí XAML](xaml-loading-and-dependency-properties.md).

<a name="metadata"></a>

### <a name="property-metadata-for-a-new-dependency-property"></a>Metadata vlastností nové vlastnosti závislosti

Při registraci vlastnosti závislosti se při registraci prostřednictvím systému vlastností vytvoří objekt metadat, který ukládá vlastnosti vlastností. Mnohé z těchto vlastností mají výchozí hodnoty, které jsou nastaveny, pokud je vlastnost registrována s jednoduchými podpisy <xref:System.Windows.DependencyProperty.Register%2A>. Další podpisy <xref:System.Windows.DependencyProperty.Register%2A> umožňují zadat metadata, která chcete při registraci vlastnosti použít. Nejběžnějším metadatům pro vlastnosti závislosti je poskytnout jim výchozí hodnotu, která je použita na nové instance, které používají vlastnost.

Pokud vytváříte vlastnost závislosti, která existuje pro odvozenou třídu <xref:System.Windows.FrameworkElement>třídy, můžete místo základní <xref:System.Windows.PropertyMetadata> třídy použít více specializovaných tříd <xref:System.Windows.FrameworkPropertyMetadata> metadat. Konstruktor pro <xref:System.Windows.FrameworkPropertyMetadata> třídu má několik signatur, kde můžete určit různé charakteristiky metadat v kombinaci. Chcete-li zadat pouze výchozí hodnotu, použijte signaturu, která přijímá jeden parametr typu <xref:System.Object>. Předejte tento parametr objektu jako výchozí hodnotu konkrétního typu pro vaši vlastnost (zadaná výchozí hodnota musí být typ, který jste zadali jako `propertyType` parametr <xref:System.Windows.DependencyProperty.Register%2A> v volání).

Pro <xref:System.Windows.FrameworkPropertyMetadata>můžete pro vlastnost zadat také příznaky možností metadat. Tyto příznaky se po registraci převedou na diskrétní vlastnosti v metadatech vlastností a používají se ke sdělování určitých podmíněných procesů, jako je například modul rozložení.

#### <a name="setting-appropriate-metadata-flags"></a>Nastavení odpovídajících příznaků metadat

- Pokud vaše vlastnost (nebo změny v její [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]hodnotě) ovlivňuje a zejména ovlivňuje, jak má systém rozložení změnit velikost nebo vykreslení prvku na stránce, nastavte jeden nebo více následujících příznaků: <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure>, <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange>, <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender>.

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure>označuje, že změna této vlastnosti vyžaduje změnu pro [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vykreslování, kde nadřazený objekt může vyžadovat více nebo méně místa v rámci nadřazeného objektu. Například vlastnost Width by měla mít nastavenou příznak.

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange>indikuje, že změna této vlastnosti vyžaduje změnu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vykreslování, která obvykle nevyžaduje změnu ve vyhrazeném prostoru, ale znamená, že se změnilo umístění v rámci prostoru. Například vlastnost "Alignment" by měla mít nastavenou příznak.

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender>označuje, že došlo k nějaké jiné změně, která nebude mít vliv na rozložení a míru, ale vyžaduje další vykreslování. Příkladem může být vlastnost, která změní barvu existujícího prvku, například "Background".

  - Tyto příznaky se často používají jako protokol v metadatech pro vlastní přepsání implementací systému vlastností nebo zpětných volání rozložení. Například můžete mít <xref:System.Windows.DependencyObject.OnPropertyChanged%2A> zpětné volání, které bude volat <xref:System.Windows.UIElement.InvalidateArrange%2A> , pokud jakákoli vlastnost instance hlásí změnu hodnoty a má <xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A> jako `true` v metadatech.

- Některé vlastnosti mohou ovlivnit vlastnosti vykreslování obsahujícího nadřazeného prvku, a to jak nad, tak i nad změnami v požadované velikosti uvedené výše. Příkladem je <xref:System.Windows.Documents.Paragraph.MinOrphanLines%2A> vlastnost použitá v modelu toku dokumentů, kde změny této vlastnosti mohou změnit celkové vykreslování dokumentu toku, který obsahuje daný odstavec. Použijte <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentArrange> nebo<xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentMeasure> k identifikaci podobných případů ve vlastních vlastnostech.

- Ve výchozím nastavení vlastnosti závislosti podporují datovou vazbu. Datovou vazbu můžete záměrně zakázat pro případy, kdy není k dispozici reálný scénář pro datovou vazbu nebo kde je jako problém rozpoznán výkon datové vazby pro velký objekt.

- Ve výchozím nastavení jsou datové <xref:System.Windows.Data.Binding.Mode%2A> vazby pro vlastnosti závislosti standardně nastavené na. <xref:System.Windows.Data.BindingMode.OneWay> Můžete vždycky změnit vazbu na <xref:System.Windows.Data.BindingMode.TwoWay> instanci vazby. Podrobnosti najdete v tématu [určení směru vazby](../data/how-to-specify-the-direction-of-the-binding.md). Jako autor vlastnosti závislosti ale můžete zvolit, aby vlastnost ve výchozím nastavení používala <xref:System.Windows.Data.BindingMode.TwoWay> režim vazby. Příkladem existující vlastnosti závislosti je <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A?displayProperty=nameWithType>; scénář pro tuto vlastnost je <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> to, že logika nastavení <xref:System.Windows.Controls.MenuItem> a skládání interakce s výchozím stylem motivu. Logika <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> vlastnosti používá nativně datovou vazbu k udržení stavu vlastnosti v souladu s jinými vlastnostmi stavu a voláními metody. Další příklad vlastnosti, která je <xref:System.Windows.Data.BindingMode.TwoWay> ve výchozím nastavení <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>svázána, je.

- Dědičnost vlastností můžete povolit také v vlastní vlastnosti závislosti nastavením <xref:System.Windows.FrameworkPropertyMetadataOptions.Inherits> příznaku. Dědičnost vlastností je užitečná pro situaci, kdy nadřazené prvky a podřízené prvky mají vlastnost společné a dává smysl pro podřízené prvky, aby tato konkrétní hodnota vlastnosti byla nastavena na stejnou hodnotu jako nadřazená sada. Příklad dědičné vlastnosti je <xref:System.Windows.FrameworkElement.DataContext%2A>, který se používá pro operace vazby k povolení důležitého scénáře hlavních podrobností pro prezentaci dat. <xref:System.Windows.FrameworkElement.DataContext%2A> Díky dědění jsou všechny podřízené elementy děděny i kontexty dat. Z důvodu dědičnosti hodnoty vlastností lze určit kontext dat na stránce nebo v kořenovém adresáři aplikace a nemusíte ho znovu zadávat pro vazby ve všech možných podřízených elementech. <xref:System.Windows.FrameworkElement.DataContext%2A>je také dobrým příkladem k ilustraci, že dědičnost přepisuje výchozí hodnotu, ale může být vždy nastavena lokálně na jakýkoli konkrétní podřízený element; Podrobnosti najdete v tématu [použití vzoru hlavní-podrobnosti s hierarchickými daty](../data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md). Dědičnost hodnot vlastností má možné náklady na výkon, a proto by se měla používat bez omezeného výkonu. Podrobnosti najdete v tématu [Dědičnost hodnot vlastností](property-value-inheritance.md).

- <xref:System.Windows.FrameworkPropertyMetadataOptions.Journal> Nastavte příznak určující, zda má být vlastnost závislosti zjištěna nebo používána službami navigace v deníku. Příkladem je <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A> vlastnost; každá položka vybraná v ovládacím prvku výběru by měla být při procházení historie deníku trvale zachovaná.

<a name="RODP"></a>

## <a name="read-only-dependency-properties"></a>Vlastnosti závislosti jen pro čtení

Můžete definovat vlastnost závislosti, která je jen pro čtení. Nicméně scénáře, proč můžete definovat vlastnost jen pro čtení, se trochu liší, jak je postup pro jejich registraci se systémem vlastností a vystavení identifikátoru. Další informace najdete v tématu [vlastnosti závislosti jen pro čtení](read-only-dependency-properties.md).

<a name="CTDP"></a>

## <a name="collection-type-dependency-properties"></a>Vlastnosti závislostí typu kolekce

Vlastnosti závislostí typu kolekce obsahují některé další problémy s implementací, které je potřeba vzít v úvahu. Podrobnosti najdete v tématu [vlastnosti závislostí typu kolekce](collection-type-dependency-properties.md).

<a name="SecurityC"></a>

## <a name="dependency-property-security-considerations"></a>Otázky zabezpečení vlastností závislosti

Vlastnosti závislosti by měly být deklarovány jako veřejné vlastnosti. Pole s identifikátorem vlastnosti závislosti by měly být deklarovány jako veřejná statická pole. I v případě, že se pokusíte deklarovat jiné úrovně přístupu (například chráněné), vlastnost závislosti může být vždy přístupná prostřednictvím identifikátoru v kombinaci s rozhraními API systému vlastností. I pole chráněného identifikátoru je potenciálně dostupné kvůli rozhraním API pro generování sestav metadat nebo k určování hodnot, které jsou součástí systému <xref:System.Windows.LocalValueEnumerator>vlastností, jako je například. Další informace najdete v tématu [zabezpečení vlastností závislosti](dependency-property-security.md).

<a name="DPCtor"></a>

## <a name="dependency-properties-and-class-constructors"></a>Vlastnosti závislosti a konstruktory tříd

V programování spravovaného kódu je obecná zásada (často se vynutila nástroji pro analýzu kódu, jako je FxCop), které konstruktory třídy by neměly volat virtuální metody. Důvodem je, že konstruktory mohou být volány jako základní inicializace konstruktoru odvozené třídy a zadání virtuální metody prostřednictvím konstruktoru může nastat v neúplném stavu inicializace instance objektu, který je konstruován. Při odvozování z jakékoliv třídy, která již je odvozena z <xref:System.Windows.DependencyObject>, byste měli vědět, že systém vlastností sám volá a zpřístupňuje virtuální metody interně. Tyto virtuální metody jsou součástí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systémových služeb vlastností. Přepsání metod umožní, aby se odvozené třídy účastnily určení hodnoty. Chcete-li se vyhnout potenciálním problémům s inicializací modulu runtime, neměli byste nastavit hodnoty vlastností závislosti v rámci konstruktorů třídy, pokud nedodržujete velmi konkrétní vzorek konstruktoru. Podrobnosti najdete v tématu [bezpečné vzory konstruktoru pro DependencyObjects](safe-constructor-patterns-for-dependencyobjects.md).

## <a name="see-also"></a>Viz také:

- [Přehled vlastností závislosti](dependency-properties-overview.md)
- [Metadata vlastností závislosti](dependency-property-metadata.md)
- [Přehled vytváření ovládacích prvků](../controls/control-authoring-overview.md)
- [Vlastnosti závislostí typu kolekce](collection-type-dependency-properties.md)
- [Zabezpečení vlastností závislosti](dependency-property-security.md)
- [Vlastnosti závislostí a načítání XAML](xaml-loading-and-dependency-properties.md)
- [Zabezpečené vzory konstruktoru pro DependencyObjects](safe-constructor-patterns-for-dependencyobjects.md)
