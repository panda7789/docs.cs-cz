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
ms.openlocfilehash: e4117d7add2a34d6d989d9222e7688361cf6b379
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646354"
---
# <a name="custom-dependency-properties"></a>Vlastní vlastnosti závislosti

Toto téma popisuje [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] důvody, které vývojáři aplikací a autoři komponent chtít vytvořit vlastní závislost vlastnost a popisuje kroky implementace, jakož i některé možnosti implementace, které mohou zlepšit výkon, použitelnost nebo všestrannost vlastnosti.

<a name="prerequisites"></a>

## <a name="prerequisites"></a>Požadavky

Toto téma předpokládá, že rozumíte vlastnostem závislostí z pohledu příjemce existujících vlastností závislostí na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] třídách a přečetli jste si téma Přehled [vlastností závislostí.](dependency-properties-overview.md) Chcete-li sledovat příklady v tomto tématu, měli byste také pochopit [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] a vědět, jak psát [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.

<a name="whatis"></a>

## <a name="what-is-a-dependency-property"></a>Co je vlastnost závislosti?

Můžete povolit, co by jinak bylo common language runtime (CLR) vlastnost pro podporu styling, datové vazby, dědičnosti, animace a výchozí hodnoty implementací jako vlastnost závislosti. Vlastnosti závislostí jsou vlastnosti, které jsou registrovány v systému [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastností voláním <xref:System.Windows.DependencyProperty.Register%2A> metody (nebo <xref:System.Windows.DependencyProperty.RegisterReadOnly%2A>) a které jsou zálohovány polem identifikátoru. <xref:System.Windows.DependencyProperty> Vlastnosti závislostí lze <xref:System.Windows.DependencyObject> použít pouze <xref:System.Windows.DependencyObject> typy, ale [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je poměrně vysoká v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hierarchii tříd, takže většina tříd, které jsou k dispozici v může podporovat vlastnosti závislostí. Další informace o vlastnostech závislostí a některých terminologiích a konvencích použitých k jejich popisu v této sadě SDK naleznete v [tématu Přehled vlastností závislostí](dependency-properties-overview.md).

<a name="example_dp"></a>

## <a name="examples-of-dependency-properties"></a>Příklady vlastností závislostí

Příklady vlastností závislostí, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] které jsou <xref:System.Windows.Controls.Control.Background%2A> implementovány <xref:System.Windows.FrameworkElement.Width%2A> na třídy patří vlastnost, vlastnost a <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost, mezi mnoho dalších. Každá vlastnost závislosti vystavená třídou má odpovídající <xref:System.Windows.DependencyProperty> veřejné statické pole typu vystavené na stejné třídě. Toto je identifikátor vlastnosti závislosti. Identifikátor je pojmenován pomocí konvence: název vlastnosti závislosti `Property` s připojeným řetězcem. Například odpovídající <xref:System.Windows.DependencyProperty> pole identifikátoru <xref:System.Windows.Controls.Control.Background%2A> pro <xref:System.Windows.Controls.Control.BackgroundProperty>vlastnost je . Identifikátor ukládá informace o vlastnosti závislosti tak, jak byla zaregistrována, a identifikátor se později použije <xref:System.Windows.DependencyObject.SetValue%2A>pro další operace zahrnující vlastnost závislosti, například volání .

Jak je uvedeno v [přehledu vlastností závislostí](dependency-properties-overview.md), všechny vlastnosti závislostí v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (s výjimkou většiny připojených vlastností) jsou také vlastnosti CLR z důvodu implementace "obálky". Proto z kódu můžete získat nebo nastavit vlastnosti závislostí voláním přístupových objektů CLR, které definují obálky stejným způsobem, jakým byste použili jiné vlastnosti CLR. Jako příjemce zavedených vlastností závislostí obvykle nepoužíváte <xref:System.Windows.DependencyObject.GetValue%2A> <xref:System.Windows.DependencyObject.SetValue%2A> <xref:System.Windows.DependencyObject> metody a , které jsou bodem připojení k systému základních vlastností. Spíše existující implementace clr vlastnosti budou <xref:System.Windows.DependencyObject.GetValue%2A> mít <xref:System.Windows.DependencyObject.SetValue%2A> již `get` `set` volány a v rámci a obálky implementace vlastnosti, pomocí pole identifikátor uvažování odpovídajícím způsobem. Pokud implementujete vlastní závislost vlastnost sami, pak bude definování obálky podobným způsobem.

<a name="backing_with_dp"></a>

## <a name="when-should-you-implement-a-dependency-property"></a>Kdy byste měli implementovat vlastnost závislosti?

Při implementaci vlastnosti na třídu, tak dlouho, <xref:System.Windows.DependencyObject>dokud vaše třída pochází z <xref:System.Windows.DependencyProperty> , máte možnost zálohovat vlastnost s identifikátorem a tím, aby byla vlastnost závislosti. S vlastnost í být závislost vlastnost není vždy nezbytné nebo vhodné a bude záviset na vašich potřebách scénáře. V některých případě je adekvátní typická technika zálohování vaší nemovitosti soukromým polem. Však byste měli implementovat vlastnost jako vlastnost závislosti vždy, když chcete, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aby vaše vlastnost pro podporu jedné nebo více z následujících funkcí:

- Chcete, aby vaše vlastnost byla nastavena ve stylu. Další informace naleznete [v tématu Styling a Templating](../../../desktop-wpf/fundamentals/styles-templates-overview.md).

- Chcete, aby vaše vlastnost pro podporu datové vazby. Další informace o vlastnostech závislostí datových vazeb naleznete [v tématu Bind the Properties of Two Controls](../data/how-to-bind-the-properties-of-two-controls.md).

- Chcete, aby vaše vlastnost byla nastavena s odkazem na dynamický prostředek. Další informace naleznete v tématu [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).

- Chcete zdědit hodnotu vlastnosti automaticky z nadřazeného prvku ve stromu prvků. V takovém případě se <xref:System.Windows.DependencyProperty.RegisterAttached%2A> zaregistrujte pomocí metody, i když také vytvoříte obálku vlastnosti pro přístup CLR. Další informace naleznete v [tématu Dědičnost hodnoty nemovitosti](property-value-inheritance.md).

- Chcete, aby váš majetek byl animovatelný. Další informace naleznete v [tématu Přehled animace](../graphics-multimedia/animation-overview.md).

- Chcete, aby systém vlastností hlásil, když byla předchozí hodnota vlastnosti změněna akcemi přijatými systémem vlastností, prostředím nebo uživatelem nebo čtením a používáním stylů. Pomocí metadat vlastnosti může vaše vlastnost určit metodu zpětného volání, která bude vyvolána pokaždé, když systém vlastností zjistí, že hodnota vaší vlastnosti byla definitivně změněna. Související koncept je nátlak hodnoty vlastnosti. Další informace naleznete [v tématu Zpětná volání vlastností závislostí a ověření](dependency-property-callbacks-and-validation.md).

- Chcete použít zavedené konvence metadat, které jsou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] také používány procesy, jako je například vykazování, zda změna hodnoty vlastnosti by měla vyžadovat rozložení systému překompletovat vizuály pro prvek. Nebo chcete mít možnost používat přepsání metadat tak, aby odvozené třídy mohly měnit charakteristiky založené na metadatech, jako je například výchozí hodnota.

- Chcete vlastnosti vlastního ovládacího prvku pro příjem podpory aplikace Visual Studio WPF Designer, jako jsou například úpravy okna **Vlastnosti.** Další informace naleznete [v tématu Přehled vytváření ovládacích prvku](../controls/control-authoring-overview.md).

Při zkoumání těchto scénářů, měli byste také zvážit, zda můžete dosáhnout vašeho scénáře přepsáním metadat existující vlastnosti závislosti, spíše než implementace zcela nové vlastnosti. Zda je praktické přepsání metadat, závisí na vašem scénáři a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] na tom, jak úzce se tento scénář podobá implementaci v existujících vlastnostech závislostí a třídách. Další informace o přepsání metadat na existující chod vlastností naleznete v [tématu Metadata vlastností závislostí](dependency-property-metadata.md).

<a name="checklist"></a>

## <a name="checklist-for-defining-a-dependency-property"></a>Kontrolní seznam pro definování vlastnosti závislosti

Definování vlastnosti závislosti se skládá ze čtyř odlišných konceptů. Tyto pojmy nejsou nutně přísné procedurální kroky, protože některé z nich nakonec kombinovat jako jeden řádky kódu v implementaci:

- (Nepovinné) Vytvořte metadata vlastnosti pro vlastnost závislosti.

- Zaregistrujte název vlastnosti v systému vlastností a zadejte typ vlastníka a typ hodnoty vlastnosti. Při použití také zadejte metadata vlastnosti.

- Definujte <xref:System.Windows.DependencyProperty> identifikátor `public` `static` `readonly` jako pole na typu vlastníka.

- Definujte vlastnost CLR "wrapper", jejíž název odpovídá názvu vlastnosti závislosti. Implementujte vlastnost i `get` `set` přístupové objekty CLR "wrapper" pro připojení k vlastnosti závislosti, která ji podporuje.

<a name="registering"></a>

### <a name="registering-the-property-with-the-property-system"></a>Registrace nemovitosti v systému vlastnictví

Aby vaše vlastnost byla vlastnost závislost, musíte zaregistrovat tuto vlastnost do tabulky spravované systémem vlastností a poskytnout jedinečný identifikátor, který se používá jako kvalifikátor pro pozdější operace systému vlastností. Tyto operace mohou být interní operace nebo vlastní kód volání vlastnostsystému API. Chcete-li zaregistrovat vlastnost, volání <xref:System.Windows.DependencyProperty.Register%2A> metody v rámci těla vaší třídy (uvnitř třídy, ale mimo všechny definice členů). Pole identifikátoru je také <xref:System.Windows.DependencyProperty.Register%2A> poskytováno voláním metody jako vrácená hodnota. Důvod, proč <xref:System.Windows.DependencyProperty.Register%2A> se volání provádí mimo jiné definice členů, je, že `public` `static` `readonly` tuto vrácenou hodnotu použijete k přiřazení a vytvoření pole typu <xref:System.Windows.DependencyProperty> jako součásti třídy. Toto pole se stane identifikátorem vlastnosti závislosti.

[!code-csharp[WPFAquariumSln#RegisterAG](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerag)]
[!code-vb[WPFAquariumSln#RegisterAG](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerag)]

<a name="nameconventions"></a>

### <a name="dependency-property-name-conventions"></a>Konvence názvů závislostí

Existují zavedené konvence pojmenování týkající se vlastností závislostí, které je nutné dodržovat za všech výjimečných okolností.

Samotná vlastnost závislosti bude mít základní název "AquariumGraphic" jako v tomto příkladu, který je uveden jako první parametr <xref:System.Windows.DependencyProperty.Register%2A>. Tento název musí být jedinečný v rámci každého typu registrace. Vlastnosti závislostí zděděné prostřednictvím základních typů jsou považovány za již součást typu registrace; názvy zděděných vlastností nelze znovu zaregistrovat. Existuje však technika pro přidání třídy jako vlastníka vlastnosti závislosti i v případě, že tato vlastnost závislosti není zděděna; Podrobnosti naleznete v [tématu Metadata vlastností závislostí](dependency-property-metadata.md).

Při vytváření pole identifikátoru pojmenujte toto pole názvem vlastnosti při registraci a příponou `Property`. Toto pole je identifikátor pro vlastnost závislosti a bude později <xref:System.Windows.DependencyObject.SetValue%2A> použit <xref:System.Windows.DependencyObject.GetValue%2A> jako vstup pro a volání, která provedete v obálkách, jakýmkoli jiným přístupem kódu k vlastnosti vlastním kódem, libovolným přístupem k externímu kódu, který povolíte, systémem vlastností a potenciálně procesory. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]

> [!NOTE]
> Definování vlastnosti závislosti v těle třídy je typická implementace, ale je také možné definovat vlastnost závislosti ve statickém konstruktoru třídy. Tento přístup může mít smysl, pokud potřebujete více než jeden řádek kódu pro inicializaci vlastnosti závislosti.

<a name="wrapper1"></a>

### <a name="implementing-the-wrapper"></a>Implementace "Obálky"

Vaše obálka implementace <xref:System.Windows.DependencyObject.GetValue%2A> by `get` měla <xref:System.Windows.DependencyObject.SetValue%2A> volat `set` v implementaci a v implementaci (původní registrační volání a pole jsou zde také zobrazeny pro přehlednost).

Ve všech, ale výjimečné okolnosti obálky implementace <xref:System.Windows.DependencyObject.GetValue%2A> <xref:System.Windows.DependencyObject.SetValue%2A> by měl provádět pouze a akce, v uvedeném pořadí. Důvod je popsán v tématu [Vlastnosti načítání a závislostí XAML](xaml-loading-and-dependency-properties.md).

Všechny existující vlastnosti veřejné závislosti, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] které jsou k dispozici na třídy použít tento jednoduchý model implementace obálky; většina složitosti, jak vlastnosti závislostí fungují, je buď ze své podstaty chování systému vlastností, nebo je implementována prostřednictvím jiných konceptů, jako je například nátlak nebo změna vlastnosti zpětná volání prostřednictvím metadat vlastností.

[!code-csharp[WPFAquariumSln#AGWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
[!code-vb[WPFAquariumSln#AGWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]

Opět podle konvence název obálky vlastnost musí být stejný jako název vybrán a <xref:System.Windows.DependencyProperty.Register%2A> uveden jako první parametr volání, které zaregistrovaly vlastnost. Pokud vaše vlastnost nedodržuje konvence, to nemusí nutně zakázat všechny možné použití, ale narazíte na několik pozoruhodných problémů:

- Některé aspekty stylů a šablon nebudou fungovat.

- Většina nástrojů a návrhářů musí spoléhat na [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]konvence pojmenování správně serializovat nebo poskytovat pomoc prostředí návrháře na úrovni vlastnosti.

- Aktuální implementace zavaděče [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zcela obchází obálky a spoléhá na konvence pojmenování při zpracování hodnot atributů. Další informace naleznete v tématu [Vlastnosti načítání a závislostí XAML](xaml-loading-and-dependency-properties.md).

<a name="metadata"></a>

### <a name="property-metadata-for-a-new-dependency-property"></a>Metadata vlastností pro novou vlastnost závislosti

Při registraci vlastnosti závislosti, registrace prostřednictvím systému vlastností vytvoří objekt metadat, který ukládá vlastnosti. Mnohé z těchto vlastností mají výchozí hodnoty, které jsou nastaveny, pokud je vlastnost registrována s jednoduchými podpisy aplikace <xref:System.Windows.DependencyProperty.Register%2A>. Jiné podpisy <xref:System.Windows.DependencyProperty.Register%2A> umožňují zadat metadata, která chcete při registraci vlastnosti. Nejběžnější metadata uvedená pro vlastnosti závislostí je poskytnout jim výchozí hodnotu, která je použita na nové instance, které používají vlastnost.

Pokud vytváříte vlastnost závislosti, která existuje v odvozené třídě <xref:System.Windows.FrameworkElement>, můžete použít specializovanější třídu <xref:System.Windows.PropertyMetadata> <xref:System.Windows.FrameworkPropertyMetadata> metadat spíše než základní třídu. Konstruktor pro <xref:System.Windows.FrameworkPropertyMetadata> třídu má několik podpisů, kde můžete zadat různé charakteristiky metadat v kombinaci. Chcete-li zadat pouze výchozí hodnotu, použijte podpis, který <xref:System.Object>přebírá jeden parametr typu . Předejte tento parametr objektu jako výchozí hodnotu pro vaši vlastnost specifickou pro typ `propertyType` (zadanou výchozí hodnotou musí být typ, který jste zadali jako parametr ve <xref:System.Windows.DependencyProperty.Register%2A> volání).

Pro <xref:System.Windows.FrameworkPropertyMetadata>aplikaci můžete také zadat příznaky možností metadat pro vaši vlastnost. Tyto příznaky jsou převedeny na diskrétní vlastnosti metadat vlastností po registraci a slouží ke komunikaci určité podmínky do jiných procesů, jako je například modul rozložení.

#### <a name="setting-appropriate-metadata-flags"></a>Nastavení příslušných příznaků metadat

- Pokud vaše vlastnost (nebo změny její [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]hodnoty) ovlivní , a zejména ovlivňuje, jak by měl systém rozložení velikost nebo <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure> <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange>vykreslení prvku na stránce, nastavte jeden nebo více z následujících příznaků: , , <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender>.

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure>označuje, že změna této vlastnosti [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vyžaduje změnu vykreslování, kde obsahující objekt může vyžadovat více nebo méně místa v nadřazeném objektu. Například vlastnost "Šířka" by měla mít tento příznak nastaven.

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange>označuje, že změna této vlastnosti [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vyžaduje změnu vykreslování, která obvykle nevyžaduje změnu vyhrazeného prostoru, ale označuje, že umístění v prostoru se změnilo. Například vlastnost "Zarovnání" by měla mít tento příznak nastaven.

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender>označuje, že došlo k jiné změně, která neovlivní rozložení a měření, ale vyžaduje jiné vykreslení. Příkladem může být vlastnost, která mění barvu existujícího prvku, například "Pozadí".

  - Tyto příznaky se často používají jako protokol v metadatech pro vlastní přepsat implementace systému vlastností nebo rozložení zpětná volání. Například můžete mít <xref:System.Windows.DependencyObject.OnPropertyChanged%2A> zpětné volání, <xref:System.Windows.UIElement.InvalidateArrange%2A> které bude volat, pokud jakákoli vlastnost <xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A> `true` instance hlásí změnu hodnoty a má jako v jeho metadata.

- Některé vlastnosti mohou ovlivnit charakteristiky vykreslování obsahujícího nadřazeného prvku, a to nad rámec výše uvedených změn požadované velikosti. Příkladem je <xref:System.Windows.Documents.Paragraph.MinOrphanLines%2A> vlastnost použitá v modelu dokumentu toku, kde změny této vlastnosti mohou změnit celkové vykreslování toku dokumentu, který obsahuje odstavec. Použijte <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentArrange> <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentMeasure> nebo identifikovat podobné případy ve svých vlastních vlastnostech.

- Ve výchozím nastavení podporují vlastnosti závislostí datovou vazbu. Můžete záměrně zakázat datové vazby, pro případy, kdy neexistuje žádný realistický scénář pro datové vazby nebo kde výkon v datové vazbě pro velký objekt je rozpoznán jako problém.

- Ve výchozím nastavení <xref:System.Windows.Data.Binding.Mode%2A> je datová vazba pro vlastnosti závislostí ve výchozím nastavení . <xref:System.Windows.Data.BindingMode.OneWay> Vždy můžete změnit vazbu <xref:System.Windows.Data.BindingMode.TwoWay> na vazby na instanci vazby; podrobnosti naleznete [v tématu Určení směru vazby](../data/how-to-specify-the-direction-of-the-binding.md). Ale jako autor vlastnosti závislosti, můžete zvolit, <xref:System.Windows.Data.BindingMode.TwoWay> aby vlastnost používat režim vazby ve výchozím nastavení. Příkladem existující vlastnosti závislosti <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A?displayProperty=nameWithType>je ; scénář pro tuto vlastnost <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> je, že logika nastavení <xref:System.Windows.Controls.MenuItem> a skládání interakce s výchozí styl motivu. Logika <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> vlastnosti používá nativně datové vazby k udržení stavu vlastnosti v souladu s jinými vlastnostmi stavu a voláním metod. Dalším příkladem vlastnosti, která se váže ve <xref:System.Windows.Data.BindingMode.TwoWay> výchozím nastavení je <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>.

- Můžete také povolit dědičnost vlastností ve <xref:System.Windows.FrameworkPropertyMetadataOptions.Inherits> vlastní vlastnosti závislosti nastavením příznaku. Dědičnost vlastností je užitečná pro scénář, kde nadřazené prvky a podřízené prvky mají společnou vlastnost a má smysl, aby podřízené prvky měly tuto konkrétní hodnotu vlastnosti nastavenou na stejnou hodnotu jako nadřazená sada. Příkladem dědičné vlastnosti je <xref:System.Windows.FrameworkElement.DataContext%2A>, který se používá pro operace vazby povolit důležitý scénář hlavního detailu pro prezentaci dat. Tím, <xref:System.Windows.FrameworkElement.DataContext%2A> že dědičné, všechny podřízené prvky dědí, že kontext dat také. Z důvodu dědičnosti hodnoty vlastnosti můžete zadat kontext dat v kořenovém adresáři stránky nebo aplikace a není nutné jej znovu zadat pro vazby ve všech možných podřízených prvcích. <xref:System.Windows.FrameworkElement.DataContext%2A>je také dobrým příkladem pro ilustraci, že dědičnost přepíše výchozí hodnotu, ale může být vždy nastavena místně na konkrétní podřízený prvek; Podrobnosti naleznete [v tématu Použití vzoru podrobností předlohy s hierarchickými daty](../data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md). Dědičnost hodnoty vlastnosti má možné náklady na výkon, a proto by měly být používány střídmě; Podrobnosti naleznete v [tématu Dědičnost hodnoty nemovitosti](property-value-inheritance.md).

- Nastavte <xref:System.Windows.FrameworkPropertyMetadataOptions.Journal> příznak označující, pokud by vaše vlastnost závislostí měla být zjištěna nebo používána službami ukládání do deníku navigace. Příkladem je <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A> vlastnost; všechny položky vybrané v ovládacím prvku výběru by měla být zachována při procházení historie ukládání do deníku.

<a name="RODP"></a>

## <a name="read-only-dependency-properties"></a>Vlastnosti závislosti jen pro čtení

Můžete definovat vlastnost závislosti, která je jen pro čtení. Scénáře, proč můžete definovat vlastnost jako jen pro čtení, se však poněkud liší, stejně jako postup pro jejich registraci v systému vlastností a vystavení identifikátoru. Další informace naleznete v [tématu Vlastnosti závislostí jen pro čtení](read-only-dependency-properties.md).

<a name="CTDP"></a>

## <a name="collection-type-dependency-properties"></a>Vlastnosti závislostí typu kolekce

Vlastnosti závislostí typu kolekce mají některé další problémy s implementací, které je třeba zvážit. Podrobnosti naleznete v [tématu Vlastnosti závislostí typu kolekce](collection-type-dependency-properties.md).

<a name="SecurityC"></a>

## <a name="dependency-property-security-considerations"></a>Důležité informace o zabezpečení vlastností závislostí

Vlastnosti závislostí by měly být deklarovány jako veřejné vlastnosti. Pole identifikátoru vlastnosti závislostí by měla být deklarována jako veřejná statická pole. I v případě, že se pokusíte deklarovat jiné úrovně přístupu (například chráněné), vlastnost závislosti lze vždy přistupovat prostřednictvím identifikátoru v kombinaci s vlastnostmi systému API. Dokonce i chráněné pole identifikátoru je potenciálně přístupné z důvodu vytváření vykazování <xref:System.Windows.LocalValueEnumerator>metadat nebo nastavení dat nastavení hodnot, které jsou součástí systému vlastností, například . Další informace naleznete [v tématu Zabezpečení vlastností závislostí](dependency-property-security.md).

<a name="DPCtor"></a>

## <a name="dependency-properties-and-class-constructors"></a>Vlastnosti závislostí a konstruktory tříd

Existuje obecný princip v programování spravovaného kódu (často vynuceno nástroji pro analýzu kódu, jako je FxCop), že konstruktory třídy by neměly volat virtuální metody. Důvodem je, že konstruktory lze volat jako základní inicializace konstruktoru odvozené třídy a zadání virtuální metody prostřednictvím konstruktoru může dojít v neúplném stavu inicializace instance objektu, který je vytvářen. Pokud je odvozenz jakékoli třídy, která již je odvozena z <xref:System.Windows.DependencyObject>, měli byste si být vědomi toho, že samotný systém vlastností volá a interně zveřejňuje virtuální metody. Tyto virtuální metody jsou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] součástí služeb systému vlastností. Přepsání metod umožňuje odvozené třídy k účasti na stanovení hodnoty. Chcete-li se vyhnout potenciálním problémům s inicializací za běhu, neměli byste nastavovat hodnoty vlastností závislostí v rámci konstruktorů tříd, pokud nedodržujete velmi specifický vzor konstruktoru. Podrobnosti naleznete [v tématu Bezpečné vzory konstruktoru pro Objekty závislostí](safe-constructor-patterns-for-dependencyobjects.md).

## <a name="see-also"></a>Viz také

- [Přehled vlastností závislosti](dependency-properties-overview.md)
- [Metadata vlastností závislosti](dependency-property-metadata.md)
- [Přehled vytváření ovládacích prvků](../controls/control-authoring-overview.md)
- [Vlastnosti závislostí typu kolekce](collection-type-dependency-properties.md)
- [Zabezpečení vlastností závislosti](dependency-property-security.md)
- [Vlastnost závislostí a načítání XAML](xaml-loading-and-dependency-properties.md)
- [Zabezpečené vzory konstruktoru pro DependencyObjects](safe-constructor-patterns-for-dependencyobjects.md)
