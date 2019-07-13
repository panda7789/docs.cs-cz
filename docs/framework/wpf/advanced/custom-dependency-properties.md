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
ms.openlocfilehash: 659497543d40c8eda18b55b4d98feac976c5abf5
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/12/2019
ms.locfileid: "67860248"
---
# <a name="custom-dependency-properties"></a>Vlastní vlastnosti závislosti

Toto téma popisuje důvody, které [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vývojáře aplikací a autoři komponenty může být vhodné vytvořit vlastnost vlastní závislosti a popisuje implementaci, jakož i některé možnosti implementace, které může zlepšit výkon, Použitelnost nebo všestrannost vlastnost.

<a name="prerequisites"></a>

## <a name="prerequisites"></a>Požadavky

Toto téma předpokládá, že rozumíte vlastnosti závislosti z pohledu příjemce vlastnosti existujícího závislosti na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] třídy a čtení [přehled vlastností závislosti](dependency-properties-overview.md) tématu. Pokud chcete postupovat podle příkladů v tomto tématu, měli byste také znát [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] a vědět, jak psát [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikací.

<a name="whatis"></a>

## <a name="what-is-a-dependency-property"></a>Co je vlastnost závislosti?

Můžete povolit, co by jinak byly [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] vlastnost pro podporu používání stylů pro vytváření datových vazeb, dědičnosti, animace a výchozí hodnoty implementací jako vlastnost závislosti. Závislé vlastnosti jsou vlastnosti, které jsou registrované [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnost systému voláním <xref:System.Windows.DependencyProperty.Register%2A> – metoda (nebo <xref:System.Windows.DependencyProperty.RegisterReadOnly%2A>), a které se zálohují na <xref:System.Windows.DependencyProperty> identifikátor pole. Vlastnosti závislostí lze použít pouze <xref:System.Windows.DependencyObject> typy, ale <xref:System.Windows.DependencyObject> je poměrně vysoké [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] třídy hierarchie, takže většina tříd k dispozici v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] může podporovat vlastnosti závislosti. Další informace o vlastnosti závislosti a některé terminologie a konvencemi použitými pro popis v tomto [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)], naleznete v tématu [přehled vlastností závislosti](dependency-properties-overview.md).

<a name="example_dp"></a>

## <a name="examples-of-dependency-properties"></a>Příklady vlastností závislosti

Příkladem vlastnosti závislosti, které jsou implementovány v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] třídy zahrnují <xref:System.Windows.Controls.Control.Background%2A> vlastnost, <xref:System.Windows.FrameworkElement.Width%2A> vlastnost a <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost mezi mnoha dalších. Každá vlastnost závislosti vystavené třídy má odpovídající veřejné statické pole typu <xref:System.Windows.DependencyProperty> zveřejněné na stejné třídy. Toto je identifikátor pro vlastnost závislosti. Tento identifikátor má název, pomocí konvence: název vlastnosti závislostí s řetězcem `Property` připojí k němu. Například odpovídající <xref:System.Windows.DependencyProperty> identifikátor pole <xref:System.Windows.Controls.Control.Background%2A> vlastnost <xref:System.Windows.Controls.Control.BackgroundProperty>. Identifikátor ukládá informace o vlastnosti závislosti, jako byl zaregistrován a tento identifikátor se pak použije později pro další operace, které zahrnují vlastnost závislosti, jako je například volání <xref:System.Windows.DependencyObject.SetValue%2A>.

Jak je uvedeno v [přehled vlastností závislosti](dependency-properties-overview.md), všechny vlastnosti závislostí v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (s výjimkou nejvíce připojené vlastnosti) jsou také [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] vlastnosti z důvodu implementace "zabezpečenou obálku". Proto z kódu, můžete získat nebo nastavit vlastnosti závislosti voláním [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] přístupové objekty, které definují obálkami stejným způsobem, že použijete jiné [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] vlastnosti. Jako příjemce vlastnosti zavedené závislosti, nepoužíváte obvykle <xref:System.Windows.DependencyObject> metody <xref:System.Windows.DependencyObject.GetValue%2A> a <xref:System.Windows.DependencyObject.SetValue%2A>, které jsou spojovací bod do základního vlastnost systému. Místo toho stávající implementaci [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] mít vlastnosti již volána <xref:System.Windows.DependencyObject.GetValue%2A> a <xref:System.Windows.DependencyObject.SetValue%2A> v rámci `get` a `set` implementace Obálka vlastnosti odpovídajícím způsobem pomocí pole identifikátoru . Pokud implementujete vlastní závislost vlastnost sami, pak je bude být definování obálku podobným způsobem.

<a name="backing_with_dp"></a>

## <a name="when-should-you-implement-a-dependency-property"></a>Pokud je implementace vlastnosti závislosti?

Pokud implementujete vlastnost ve třídě, tak dlouho, dokud vaše třída odvozena z <xref:System.Windows.DependencyObject>, máte možnost zálohovat vaše vlastnost s <xref:System.Windows.DependencyProperty> identifikátor a tím k němu vlastnost závislosti. S vaší vlastnost, vlastnost závislosti není vždy nutné nebo vhodné a bude záviset na požadavcích scénáře. V některých případech je odpovídající typickou techniku zálohovat vaše vlastnost s privátní pole. Ale měli byste implementovat vaše vlastnost jako vlastnost závislosti pokaždé, když chcete, aby vaše vlastnost pro podporu jeden nebo více z následujících [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] možnosti:

- Chcete, aby vaše vlastnost být nastavitelná při čekání ve stylu. Další informace najdete v tématu [styly a šablony](../controls/styling-and-templating.md).

- Chcete, aby vaše vlastnost pro podporu vytváření datových vazeb. Další informace o vlastnosti závislosti datové vazby, naleznete v tématu [vazby vlastností dvou ovládacích](../data/how-to-bind-the-properties-of-two-controls.md).

- Chcete, aby vaše vlastnost jako nastavitelnou s odkazem na dynamický prostředek. Další informace najdete v tématu [prostředky XAML](xaml-resources.md).

- Chcete automaticky dědí nadřazený element ve stromové struktuře element hodnotu vlastnosti. V takovém případě se zaregistrujte <xref:System.Windows.DependencyProperty.RegisterAttached%2A> metoda, i když můžete také vytvořit vlastnost obálku pro [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] přístup. Další informace najdete v tématu [dědičnost hodnoty vlastnosti](property-value-inheritance.md).

- Chcete, aby vaše vlastnost jako animovatelné. Další informace najdete v tématu [přehled animace](../graphics-multimedia/animation-overview.md).

- V systému vlastností na sestavu chcete při předchozí hodnotu vlastnosti nebylo změněno pomocí akce provedené v systému vlastností prostředí nebo uživatele nebo pro čtení a použitím stylů. Na základě metadat vlastnosti, můžete zadat vaše vlastnost metodu zpětného volání, která bude volána pokaždé, když systém vlastností určuje, že hodnota vlastnosti byla změněna platností. Pojmem, je převod hodnoty vlastnosti. Další informace najdete v tématu [vlastnost závislosti zpětné volání a ověření](dependency-property-callbacks-and-validation.md).

- Chcete používat zavedené metadat, které jsou také používány [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] procesy, jako je například vytváření sestav, zda změna hodnoty vlastnosti by měla vyžadují systém rozložení chcete vizuály pro daný element. Nebo chcete být schopni pomocí přepsání metadata tak, aby odvozené třídy můžete změnit na základě metadat vlastnosti, jako je například výchozí hodnota.

- Chcete, aby vlastnosti vlastního ovládacího prvku pro příjem Návrhář WPF Visual Studio podporují, jako je například **vlastnosti** okno úpravy. Další informace najdete v tématu [Přehled vytváření ovládacího prvku](../controls/control-authoring-overview.md).

Při zkoumání těchto scénářů, měli byste také zvážit, zda můžete dosáhnout váš scénář přepsání metadat existující vlastnost závislosti, nikoli implementací úplně novou vlastnost. Určuje, zda je praktické přepis metadat závisí na vašem scénáři a jak tento scénář připomíná implementace v existujícím [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] třídy a vlastnosti závislosti. Další informace o přepsání metadat na existující vlastnosti najdete v tématu [Metadata vlastností závislosti](dependency-property-metadata.md).

<a name="checklist"></a>

## <a name="checklist-for-defining-a-dependency-property"></a>Kontrolní seznam pro definování vlastnost závislosti

Definovat vlastnosti závislosti se skládá ze čtyř různých koncepty. Tyto koncepty nejsou nutně striktní příklady kroků, protože některé z nich skončit se kombinovat jako jeden řádek kódu v implementaci:

- (Volitelné) Vytvořte vlastnost metadata pro vlastnost závislosti.

- Zaregistrujte název vlastnosti v systému vlastností zadáním typu vlastníka a typ hodnoty vlastnosti. Metadata vlastnosti zadejte také použít.

- Definování <xref:System.Windows.DependencyProperty> identifikátor jako `public` `static` `readonly` na typ vlastníka.

- Definování [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] "zabezpečenou obálku" vlastnost, jejíž název odpovídá názvu vlastnosti závislosti. Implementace [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] "zabezpečenou obálku" vlastnost `get` a `set` přístupové objekty pro připojení k vlastnost závislosti, která zálohuje ho.

<a name="registering"></a>

### <a name="registering-the-property-with-the-property-system"></a>Vlastnosti registrace v systému vlastností

Aby vaše vlastnost jako vlastnost závislosti musí zaregistrovat tuto vlastnost do tabulky udržuje v systému vlastností a poskytněte jedinečný identifikátor, který se používá jako kvalifikátor pro pozdější operace vlastností systému. Tyto operace může být interní operace nebo váš vlastní kód volání rozhraní API systému vlastností. K registraci vlastnost zavoláte <xref:System.Windows.DependencyProperty.Register%2A> metoda v těle vaší třídy (uvnitř třídy, ale mimo všechny definice členů). Identifikátor pole také poskytuje <xref:System.Windows.DependencyProperty.Register%2A> volání metody, jako návratovou hodnotu. Z důvodu, který <xref:System.Windows.DependencyProperty.Register%2A> se provádí volání mimo jiný člen je definice, protože tuto hodnotu použijete přiřadit a vytvořit `public` `static` `readonly` pole typu <xref:System.Windows.DependencyProperty> jako součást vaší třídy. Toto pole bude identifikátor pro vaše vlastnost závislosti.

[!code-csharp[WPFAquariumSln#RegisterAG](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerag)]
[!code-vb[WPFAquariumSln#RegisterAG](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerag)]

<a name="nameconventions"></a>

### <a name="dependency-property-name-conventions"></a>Konvence název vlastnosti závislosti

Jsou zavedené zásady vytváření názvů týkající se vlastnosti závislosti, které je třeba provést ve všech ale výjimečných okolností.

Samotné vlastnosti závislosti budou mít základní název "AquariumGraphic" jako v tomto příkladu je zadána jako první parametr <xref:System.Windows.DependencyProperty.Register%2A>. Tento název musí být jedinečný v rámci každého typu registrace. Vlastnosti závislostí zděděné z základní typy se považují za již součástí registrace typu; názvy zděděné vlastnosti nelze zaregistrovat znovu. Existuje ale postup pro přidání třídy jako vlastník vlastnost závislostí i v případě, že tuto vlastnost závislosti není zděděno; Podrobnosti najdete v tématu [Metadata vlastností závislosti](dependency-property-metadata.md).

Při vytváření identifikátor pole název tohoto pole podle názvu vlastnosti jste zaregistrovali, a navíc přípona `Property`. Toto pole je svůj identifikátor pro vlastnost závislosti, a to se později použijí jako vstup pro <xref:System.Windows.DependencyObject.SetValue%2A> a <xref:System.Windows.DependencyObject.GetValue%2A> volání, které provedete v obálky, všechny ostatní kódu přístup ke vlastnost ve vlastním kódu, všechny externí kód přístup můžete povolit , vlastnost systému a potenciálně podle [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesory.

> [!NOTE]
> Definování vlastnosti závislosti do těla třídy je obvyklá implementace, ale je také možné definovat vlastnosti závislosti v statický konstruktor třídy. Tento přístup může mít smysl, pokud potřebujete více než jeden řádek kódu k inicializaci vlastnosti závislosti.

<a name="wrapper1"></a>

### <a name="implementing-the-wrapper"></a>Implementace zabezpečenou "obálku"

Implementace obálky by měly volat <xref:System.Windows.DependencyObject.GetValue%2A> v `get` implementaci a <xref:System.Windows.DependencyObject.SetValue%2A> v `set` (původní volání registrace a pole jsou zde uvedená implementace příliš pro přehlednost).

Vše kromě výjimečných okolností vaší implementace obálky by měl provádět pouze <xref:System.Windows.DependencyObject.GetValue%2A> a <xref:System.Windows.DependencyObject.SetValue%2A> akce, v uvedeném pořadí. Důvodem je popsáno v tématu [vlastnosti závislostí a načítání XAML](xaml-loading-and-dependency-properties.md).

Všechny existující vlastnosti veřejné závislosti, které jsou k dispozici na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] třídy použijte tento model implementace jednoduchou obálku, většina složitost fungování vlastnosti závislostí je buď ze své podstaty chování systému vlastnost nebo je implementované pomocí jiné koncepty, jako je vlastnost nebo konverze za změňte zpětná volání prostřednictvím vlastnosti metadat.

[!code-csharp[WPFAquariumSln#AGWithWrapper](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
[!code-vb[WPFAquariumSln#AGWithWrapper](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]

Znovu podle konvence, název vlastnosti obálky musí být stejný jako název zvolené a zadané jako první parametr <xref:System.Windows.DependencyProperty.Register%2A> volání, které registrované vlastnost. Pokud vaše vlastnost podle úmluvy, to nezakáže nutně všechna možná použití, ale narazíte na několik významné problémy:

- Nebudou fungovat některé aspekty – styly a šablony.

- Většina nástrojů a návrháři musíte spoléhat na konvence pojmenování a správně serializovat [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], nebo k poskytování pomoci návrháře prostředí na úrovni na vlastnost.

- Aktuální provádění [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zavaděč zcela vynechá obálkami a spoléhá na zásady vytváření názvů při zpracování hodnot atributů. Další informace najdete v tématu [vlastnosti závislostí a načítání XAML](xaml-loading-and-dependency-properties.md).

<a name="metadata"></a>

### <a name="property-metadata-for-a-new-dependency-property"></a>Metadata vlastností pro novou vlastnost závislosti

Při registraci vlastnost závislosti registrace prostřednictvím systému vlastnost vytvoří objekt metadat, který uchovává vlastnost charakteristiky. Mnohé z těchto vlastností mají výchozí hodnoty, které jsou nastaveny, pokud je vlastnost zaregistrován u jednoduchého podpisy <xref:System.Windows.DependencyProperty.Register%2A>. Další podpisy <xref:System.Windows.DependencyProperty.Register%2A> vám umožňují určit metadata, která chcete, aby při registraci vlastnost. Nejběžnější metadata pro vlastnosti závislosti se jim dát výchozí hodnotu, která je použita pro nové instance, které používají vlastnost.

Pokud vytváříte vlastnost závislosti, která existuje na odvozenou třídu <xref:System.Windows.FrameworkElement>, můžete použít více specializované třídy metadat <xref:System.Windows.FrameworkPropertyMetadata> místo základní třídy <xref:System.Windows.PropertyMetadata> třídy. Konstruktor pro <xref:System.Windows.FrameworkPropertyMetadata> třída obsahuje více podpisů, kde můžete určit různé vlastnosti metadat v kombinaci. Pokud chcete zadat jenom výchozí hodnotu, použijte podpisu, který přijímá jeden parametr typu <xref:System.Object>. Předá parametr objektu jako výchozí typ konkrétní hodnotu vlastnictví (Zadaná výchozí hodnota musí být typ, který jste zadali jako `propertyType` parametr <xref:System.Windows.DependencyProperty.Register%2A> volání).

Pro <xref:System.Windows.FrameworkPropertyMetadata>, můžete také zadat metadata možnost příznaky vlastnictví. Tyto příznaky jsou převedena na diskrétní vlastnosti na metadata vlastnosti po registraci a slouží ke komunikaci určité podmínky pro procesy, jako je například modul rozložení.

#### <a name="setting-appropriate-metadata-flags"></a>Nastavení příznaků příslušná Metadata

- Pokud vlastnost (nebo změny v jeho hodnotu) má vliv [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], a konkrétně ovlivní způsob, jakým by měl systém rozložení velikost nebo vykreslit prvek na stránce nastavit jeden nebo více z následujících příznaků: <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure>, <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange>, <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender>.

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure> Označuje, že ke změně této vlastnosti vyžaduje změnu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vykreslování, ve kterém obsahujícího objektu může vyžadovat víc nebo míň místa v rámci nadřazené. Například vlastnost "Šířka" by měl mít tento příznak nastaven.

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange> Označuje, že ke změně této vlastnosti vyžaduje změnu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vykreslování, které obvykle nevyžaduje změnu ve vyhrazené místo, ale značí to, že se změnila pozice v rámci oboru. Například vlastnost "Zarovnání" by měl mít tento příznak nastaven.

  - <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender> Označuje, že některé další došlo ke změně, která nebude mít vliv na rozložení a míry, ale vyžaduje další vykreslování. Příkladem může být vlastnost, která změní barvu existujícího prvku, jako je například "Pozadí".

  - Tyto příznaky jsou často používá jako protokol v metadatech pro vaše vlastní implementace přepsání vlastnosti systému nebo rozložení zpětných volání. Například můžete mít <xref:System.Windows.DependencyObject.OnPropertyChanged%2A> zpětné volání, které bude volat <xref:System.Windows.UIElement.InvalidateArrange%2A> pokud nějaká vlastnost instance změna hodnoty určité sestavy a má <xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A> jako `true` ve svých metadatech.

- Některé vlastnosti může mít vliv na vykreslování vlastnosti nadřazeného nadřazeného elementu, způsoby nenabízející změny ve výše uvedené požadované velikosti. Příkladem je <xref:System.Windows.Documents.Paragraph.MinOrphanLines%2A> vlastnost použít v modelu dokument toku, kde můžete změny vlastnosti měnit celkovou vykreslování plovoucí dokument, který obsahuje odstavce. Použití <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentArrange> nebo <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentMeasure> k identifikaci obdobné případy v vlastní vlastnosti.

- Vlastnosti závislostí ve výchozím nastavení, podporují datové vazby. Datové vazby pro případy, můžete zakázat záměrně neexistuje žádné reálné scénáře pro datové vazby nebo výkonu v datové vazbě pro velké objekty je rozpoznána jako problém.

- Ve výchozím nastavení datové vazby <xref:System.Windows.Data.Binding.Mode%2A> pro výchozí vlastnosti závislostí <xref:System.Windows.Data.BindingMode.OneWay>. Můžete vždycky změnit vazbu tak <xref:System.Windows.Data.BindingMode.TwoWay> za instanci vazby; podrobnosti najdete v článku [určení směru vazby](../data/how-to-specify-the-direction-of-the-binding.md). Ale jako autor vlastnost závislosti, můžete použít vlastnost <xref:System.Windows.Data.BindingMode.TwoWay> režimu vazby ve výchozím nastavení. Příklad existující vlastnost závislosti je <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A?displayProperty=nameWithType>; scénář pro tuto vlastnost je, že <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> nastavení logiku a skládání z <xref:System.Windows.Controls.MenuItem> interakci s výchozího stylu motivu. <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> Datové vazby vlastnost logiky nativně používá k uchování stavu vlastnosti podle jiné vlastnosti stavu a volání metody. Další příklad vlastnost, která vytvoří vazbu <xref:System.Windows.Data.BindingMode.TwoWay> ve výchozím nastavení je <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>.

- Dědičnost vlastnosti ve vlastnosti vlastní závislosti můžete také povolit tak, že nastavíte <xref:System.Windows.FrameworkPropertyMetadataOptions.Inherits> příznak. Dědičnost vlastnosti je užitečné pro scénáře, kde prvky nadřazené a podřízené prvky mají vlastnosti společné, a dává smysl pro podřízené prvky mají konkrétní hodnotu nastavit na stejnou hodnotu jako nadřazený ho nastavit. Příklad odvoditelný vlastnosti je <xref:System.Windows.FrameworkElement.DataContext%2A>, který se používá pro operace umožňující důležité scénáře hlavní podrobnosti pro prezentaci dat vytvoření vazby. Tím, že <xref:System.Windows.FrameworkElement.DataContext%2A> odvoditelný, všechny podřízené prvky dědit daného kontextu dat také. Z důvodu dědičnost hodnoty vlastnosti můžou určovat kontext dat. v kořenovém adresáři stránky nebo aplikace a nemusíte respecify pro vazby ve všech možných podřízené prvky. <xref:System.Windows.FrameworkElement.DataContext%2A> také je typickým příkladem pro ilustraci, že dědičnost přepíše výchozí hodnotu, ale vždy nastavíte místně na žádné konkrétní podřízené element. Podrobnosti najdete v tématu [použití vzoru seznam-podrobnosti s hierarchickými daty](../data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md). Dědičnost hodnoty vlastnosti nemá možný výkon a proto by měly používat střídmě, Podrobnosti najdete v tématu [dědičnost hodnoty vlastnosti](property-value-inheritance.md).

- Nastavte <xref:System.Windows.FrameworkPropertyMetadataOptions.Journal> příznak označující, pokud vaše vlastnost závislosti by měly být zjištěna nebo používané službami záznamu do deníku navigace. Příkladem je <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A> vlastnost; jakékoli položky vybrané ve výběru ovládací prvek by měl nastavit jako trvalý, když přejde do historie záznamu do deníku.

<a name="RODP"></a>

## <a name="read-only-dependency-properties"></a>Vlastnosti závislosti jen pro čtení

Můžete definovat vlastnosti závislosti, která je jen pro čtení. Scénáře pro proč může definovat vaše vlastnost jen pro čtení jsou však poněkud liší, jako je postup pro registraci v systému vlastností a zveřejnění identifikátoru. Další informace najdete v tématu [vlastnosti závislosti jen pro čtení](read-only-dependency-properties.md).

<a name="CTDP"></a>

## <a name="collection-type-dependency-properties"></a>Vlastnosti závislostí typu kolekce

Vlastnosti závislostí typu kolekce mají některé další implementace problémy vzít v úvahu. Podrobnosti najdete v tématu [vlastnosti závislostí typu kolekce](collection-type-dependency-properties.md).

<a name="SecurityC"></a>

## <a name="dependency-property-security-considerations"></a>Aspekty zabezpečení vlastností závislosti

Vlastnosti závislosti by měl být deklarován jako veřejné vlastnosti. Pole identifikátoru vlastnosti závislosti by měl být deklarován jako veřejné statické pole. I v případě, že při pokusu deklarovat jiných úrovních přístupu (například chráněné), vlastnost závislosti vždy přistupuje prostřednictvím identifikátor v kombinaci s vlastností systému rozhraní API. Z důvodu metadata vytváření sestav, nebo hodnotu stanovení rozhraní API, která jsou součástí vlastnosti systému, jako například potenciálně přístupný i chráněné identifikátor pole <xref:System.Windows.LocalValueEnumerator>. Další informace najdete v tématu [zabezpečení vlastností závislosti](dependency-property-security.md).

<a name="DPCtor"></a>

## <a name="dependency-properties-and-class-constructors"></a>Vlastnosti závislostí a konstruktor třídy

Je zásadně ve spravovaném kódu programování (často vynucuje sada nástrojů pro analýzu kódu jako je například FxCop), které třídy konstruktory by neměl volat virtuální metody. Je to proto, že konstruktory lze volat jako základní inicializace konstruktoru odvozené třídy, a zadáte virtuální metodu pomocí konstruktoru mohou nastat za stavu neúplná inicializace vytváří instanci objektu. Když odvozujete z jiné třídy, která už je odvozena z <xref:System.Windows.DependencyObject>, je třeba si uvědomit, že samotný systém vlastnosti volání a interně poskytuje virtuální metody. Tyto virtuální metody jsou součástí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnost systémových služeb. Přepsání metody umožňuje odvozené třídy se účastnit stanovení hodnotu. Aby se zabránilo problémům s inicializace za běhu, by neměl nastavíte závislost hodnoty vlastností v rámci konstruktory tříd, pokud podle vzoru velmi konkrétní konstruktor. Podrobnosti najdete v tématu [bezpečné zabezpečené vzory konstruktoru pro DependencyObjects](safe-constructor-patterns-for-dependencyobjects.md).

## <a name="see-also"></a>Viz také:

- [Přehled vlastností závislosti](dependency-properties-overview.md)
- [Metadata vlastností závislosti](dependency-property-metadata.md)
- [Přehled vytváření ovládacích prvků](../controls/control-authoring-overview.md)
- [Vlastnosti závislostí typu kolekce](collection-type-dependency-properties.md)
- [Zabezpečení vlastností závislosti](dependency-property-security.md)
- [Vlastnosti závislostí a načítání XAML](xaml-loading-and-dependency-properties.md)
- [Zabezpečené vzory konstruktoru pro DependencyObjects](safe-constructor-patterns-for-dependencyobjects.md)
