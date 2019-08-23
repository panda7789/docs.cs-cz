---
title: Metadata vlastnosti rozhraní .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WPF], framework properties
- framework property metadata [WPF]
ms.assetid: 9962f380-b885-4b61-a62e-457397083fea
ms.openlocfilehash: c08cf28880d86331e3b561f1749333d401ba903e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964206"
---
# <a name="framework-property-metadata"></a>Metadata vlastnosti rozhraní .NET Framework
Možnosti metadat pro vlastnost rozhraní jsou hlášeny pro vlastnosti objektů, které se považují za úroveň rozhraní WPF v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] architektuře. Obecně označení na úrovni architektury WPF znamená, že funkce, jako je vykreslování, vázání dat a upřesnění systému vlastností, jsou zpracovávány [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozhraními API prezentace a spustitelnými soubory. Metadata vlastnosti rozhraní jsou dotazována těmito systémy, aby bylo možné určit vlastnosti konkrétního prvku specifické pro danou funkci.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 V tomto tématu se předpokládá, že rozumíte vlastnostem závislosti z perspektivy uživatele existujících vlastností závislosti ve [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] třídách a přečetli jste si [Přehled vlastností závislosti](dependency-properties-overview.md). Měli byste také mít [Metadata vlastností závislosti](dependency-property-metadata.md)čtení.  
  
<a name="What_Is_Communicated_by_Framework_Property"></a>   
## <a name="what-is-communicated-by-framework-property-metadata"></a>Co se komunikuje s metadaty vlastností rozhraní  
 Metadata vlastnosti rozhraní mohou být rozdělena do následujících kategorií:  
  
- Vlastnosti rozložení pro vytváření sestav, které ovlivňují<xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A>element <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>( <xref:System.Windows.FrameworkPropertyMetadata.AffectsRender%2A>,,). Můžete nastavit tyto příznaky v metadatech, pokud vlastnost ovlivňuje tyto aspekty a Vy také implementujete <xref:System.Windows.FrameworkElement.MeasureOverride%2A>  /  <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> metody ve třídě pro poskytování konkrétního chování vykreslování a informací do rozložení. souborů. Obvykle by tato implementace kontrolovala zrušení vlastností u vlastností závislosti, kde některá z těchto vlastností rozložení byla v metadatech vlastností pravdivá, a jenom taková neplatná by vyžadovala vyžádání nového průchodu rozložení.  
  
- Vlastnosti rozložení sestavy, které ovlivňují nadřazený element elementu (<xref:System.Windows.FrameworkPropertyMetadata.AffectsParentArrange%2A>, <xref:System.Windows.FrameworkPropertyMetadata.AffectsParentMeasure%2A>). Některé příklady, kde jsou tyto příznaky nastaveny ve výchozím <xref:System.Windows.Documents.FixedPage.Left%2A?displayProperty=nameWithType> nastavení <xref:System.Windows.Documents.Paragraph.KeepWithNext%2A?displayProperty=nameWithType>, jsou a.  
  
- <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A>. Ve výchozím nastavení vlastnosti závislosti nedědí hodnoty. <xref:System.Windows.FrameworkPropertyMetadata.OverridesInheritanceBehavior%2A>umožňuje cestám dědičnosti také cestovat do vizuálního stromu, který je nezbytný pro některé scénáře skládání ovládacích prvků.  
  
    > [!NOTE]
    > Pojem "Inherits" v kontextu hodnot vlastností znamená něco specifického pro vlastnosti závislosti; To znamená, že podřízené prvky mohou dědit skutečnou hodnotu vlastnosti závislosti z nadřazených prvků z důvodu schopnosti na úrovni architektury WPF v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systému vlastností. Není nic dělat přímo s typem spravovaného kódu a dědičnosti členů prostřednictvím odvozených typů. Podrobnosti najdete v tématu [Dědičnost hodnot vlastností](property-value-inheritance.md).  
  
- Charakteristiky vazby dat pro vytváření<xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A>sestav <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A>(,). Ve výchozím nastavení vlastnosti závislosti v rozhraní podporují datovou vazbu s jednosměrným chováním vazby. Datovou vazbu můžete zakázat, pokud v nějakém případě neexistoval žádný scénář (protože mají být flexibilní a rozšiřitelné, není k dispozici mnoho příkladů těchto vlastností ve výchozích [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozhraních API). Je možné nastavit, aby vazba měla oboustrannou výchozí hodnotu pro vlastnosti, které spojuje chování ovládacího prvku mezi jeho součástmi (<xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> příkladem) nebo v případě, že Obousměrná vazba je nejběžnějším a očekávaným scénářem pro uživatele (<xref:System.Windows.Controls.TextBox.Text%2A> příklad). Změna datové vazby má vliv jenom na výchozí hodnoty. na základě vazby je možné, že výchozí hodnota může být vždy změněna. Podrobné informace o režimech vazeb a vazbách obecně naleznete v tématu [Přehled datových vazeb](../data/data-binding-overview.md).  
  
- Vytváření sestav, zda mají být vlastnosti zadávány aplikacemi nebo službami, které podporují<xref:System.Windows.FrameworkPropertyMetadata.Journal%2A>deníking (). V případě obecných prvků není deník ve výchozím nastavení povolený, ale je selektivně povolen pro určité ovládací prvky vstupu uživatele. Tato vlastnost je určena ke čtení ze služby Journal Services, včetně [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementace deníku, a obvykle je nastavena na uživatelské ovládací prvky, jako jsou výběry uživatele v rámci seznamů, které by měly být trvale v rámci jednotlivých kroků navigace. Informace o deníku najdete v tématu [Přehled navigace](../app-development/navigation-overview.md).  
  
<a name="Reading_FrameworkPropertyMetadata"></a>   
## <a name="reading-frameworkpropertymetadata"></a>Čtení FrameworkPropertyMetadata  
 Každá z výše uvedených vlastností je specifických vlastností, které <xref:System.Windows.FrameworkPropertyMetadata> přidá do své bezprostřední základní třídy. <xref:System.Windows.UIPropertyMetadata> Každá z těchto vlastností bude `false` ve výchozím nastavení standardně. Požadavek na metadata pro vlastnost, která má vědět, že hodnota těchto vlastností je důležitý, by měl být proveden pokus o <xref:System.Windows.FrameworkPropertyMetadata>přetypování vrácených metadat na hodnotu a pak podle potřeby zkontroluje hodnoty jednotlivých vlastností.  
  
<a name="Specifying_Metadata"></a>   
## <a name="specifying-metadata"></a>Zadání metadat  
 Při vytváření nové instance metadat pro účely použití metadat do nové registrace vlastnosti závislosti máte možnost, kterou třídu metadat použít: základní <xref:System.Windows.PropertyMetadata> nebo některé odvozené třídy, jako je například. <xref:System.Windows.FrameworkPropertyMetadata> Obecně platí, že byste měli <xref:System.Windows.FrameworkPropertyMetadata>použít, zejména pokud má vaše vlastnost nějakou interakci se systémem vlastností [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a funkcemi, jako je například rozložení a datová vazba. Další možností pro pokročilejší scénáře je odvozovat z <xref:System.Windows.FrameworkPropertyMetadata> a vytvořit vlastní třídu generování sestav metadat s dalšími informacemi předanými ve svých členech. Nebo můžete použít <xref:System.Windows.PropertyMetadata> nebo <xref:System.Windows.UIPropertyMetadata> ke sdělování stupně podpory pro funkce vaší implementace.  
  
 U existujících vlastností (<xref:System.Windows.DependencyProperty.AddOwner%2A> nebo <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> volání) byste měli vždy přepsat typ metadat, který používá původní registrace.  
  
 Pokud vytváříte <xref:System.Windows.FrameworkPropertyMetadata> instanci, existují dva způsoby, jak tato metadata naplnit hodnotami pro konkrétní vlastnosti, které komunikují charakteristiky vlastností rozhraní:  
  
1. Použijte signaturu `flags` konstruktoru, který povoluje parametr. <xref:System.Windows.FrameworkPropertyMetadata> Tento parametr by měl být vyplněn všemi požadovanými kombinovanými hodnotami <xref:System.Windows.FrameworkPropertyMetadataOptions> příznaků výčtu.  
  
2. Použijte jeden z podpisů bez `flags` parametru a pak nastavte každou <xref:System.Windows.FrameworkPropertyMetadata> vlastnost pro vytváření sestav logických vlastností `true` na hodnotu pro každou požadovanou charakteristickou změnu. Pokud to uděláte, musíte nastavit tyto vlastnosti před tím, než se vytvoří všechny prvky s touto vlastností závislosti. vlastnosti logické hodnoty jsou pro čtení i zápis, aby bylo možné toto chování zabránit `flags` parametru a zároveň naplnit metadata, ale metadata musí být před použitím vlastností skutečně zapečetěná. Proto se při pokusu o nastavení vlastností po vyžádání metadat bude jednat o neplatnou operaci.  
  
<a name="Framework_Property_Metadata_Merge_Behavior"></a>   
## <a name="framework-property-metadata-merge-behavior"></a>Chování sloučení metadat vlastností architektury  
 Při přepsání metadat vlastností rozhraní jsou různé charakteristiky metadat buď sloučeny, nebo nahrazeny.  
  
- <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>je sloučena. Pokud přidáte nové <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>, toto zpětné volání je uloženo v metadatech. Pokud <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> v přepsání nezadáte, <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> hodnota se zvýší jako odkaz z nejbližšího předchůdce, který ho zadal v metadatech.  
  
- Skutečným chováním systémových vlastností <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> pro je, že implementace všech vlastníků metadat v hierarchii jsou zachovány a přidány do tabulky, s pořadím provádění se systémem vlastností, které jsou zpětně prováděna zpětná volání z nejhlouběji odvozené třídy. vyvoláno jako první. Zděděná zpětná volání se spouštějí pouze jednou a počítají se jako vlastněné třídou, která je umístila do metadat.  
  
- <xref:System.Windows.PropertyMetadata.DefaultValue%2A>je nahrazen. Pokud <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> v přepsání nezadáte, <xref:System.Windows.PropertyMetadata.DefaultValue%2A> hodnota se dostane z nejbližšího předchůdce, který ho zadal v metadatech.  
  
- <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>implementace jsou nahrazeny. Pokud přidáte nové <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>, toto zpětné volání je uloženo v metadatech. Pokud <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> v přepsání nezadáte, <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> hodnota se zvýší jako odkaz z nejbližšího předchůdce, který ho zadal v metadatech.  
  
- Chování vlastností systému je pouze <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> v případě, že je vyvolána pouze v bezprostředních metadatech. Neuchovávají se žádné <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> odkazy na jiné implementace v hierarchii.  
  
- Příznaky <xref:System.Windows.FrameworkPropertyMetadataOptions> výčtu jsou zkombinovány jako bitové nebo operace.  Pokud zadáte <xref:System.Windows.FrameworkPropertyMetadataOptions>, původní možnosti nebudou přepsány.  Chcete-li změnit možnost, nastavte odpovídající vlastnost na <xref:System.Windows.FrameworkPropertyMetadata>. Například pokud původní <xref:System.Windows.FrameworkPropertyMetadata> objekt <xref:System.Windows.FrameworkPropertyMetadataOptions.NotDataBindable?displayProperty=nameWithType> nastaví příznak, můžete jej změnit nastavením <xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A?displayProperty=nameWithType> na `false`.  
  
 Toto chování je implementováno <xref:System.Windows.FrameworkPropertyMetadata.Merge%2A>nástrojem a lze je přepsat na odvozených třídách metadat.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.DependencyProperty.GetMetadata%2A>
- [Metadata vlastností závislosti](dependency-property-metadata.md)
- [Přehled vlastností závislosti](dependency-properties-overview.md)
- [Vlastní vlastnosti závislosti](custom-dependency-properties.md)
