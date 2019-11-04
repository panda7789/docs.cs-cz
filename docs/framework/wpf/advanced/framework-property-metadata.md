---
title: Metadata vlastnosti rozhraní .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WPF], framework properties
- framework property metadata [WPF]
ms.assetid: 9962f380-b885-4b61-a62e-457397083fea
ms.openlocfilehash: 3e40dfbcbe88f424337ee5a32fb3e3aaaddd68d0
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460461"
---
# <a name="framework-property-metadata"></a>Metadata vlastnosti rozhraní .NET Framework
Možnosti metadat pro vlastnost rozhraní jsou hlášeny pro vlastnosti objektů, které se považují za úroveň rozhraní WPF v architektuře [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. Obecně označení na úrovni architektury WPF znamená, že funkce, jako je vykreslování, vázání dat a upřesnění systému vlastností, jsou zpracovávány rozhraními API a spustitelnými soubory [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prezentace. Metadata vlastnosti rozhraní jsou dotazována těmito systémy, aby bylo možné určit vlastnosti konkrétního prvku specifické pro danou funkci.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 V tomto tématu se předpokládá, že rozumíte vlastnostem závislosti z perspektivy uživatele existujících vlastností závislosti na třídách [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] a přečtěte si [Přehled vlastností závislosti](dependency-properties-overview.md). Měli byste také mít [Metadata vlastností závislosti](dependency-property-metadata.md)čtení.  
  
<a name="What_Is_Communicated_by_Framework_Property"></a>   
## <a name="what-is-communicated-by-framework-property-metadata"></a>Co se komunikuje s metadaty vlastností rozhraní  
 Metadata vlastnosti rozhraní mohou být rozdělena do následujících kategorií:  
  
- Vlastnosti rozložení sestavy, které ovlivňují prvek (<xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A>, <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A><xref:System.Windows.FrameworkPropertyMetadata.AffectsRender%2A>). Můžete nastavit tyto příznaky v metadatech, pokud vlastnost ovlivňuje příslušné aspekty a Vy implementujete <xref:System.Windows.FrameworkElement.MeasureOverride%2A> / <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> metody ve vaší třídě, aby poskytovaly specifické chování vykreslování a informace do systému rozložení. Obvykle by tato implementace kontrolovala zrušení vlastností u vlastností závislosti, kde některá z těchto vlastností rozložení byla v metadatech vlastností pravdivá, a jenom taková neplatná by vyžadovala vyžádání nového průchodu rozložení.  
  
- Vlastnosti rozložení sestavy, které ovlivňují nadřazený element elementu (<xref:System.Windows.FrameworkPropertyMetadata.AffectsParentArrange%2A>, <xref:System.Windows.FrameworkPropertyMetadata.AffectsParentMeasure%2A>). Některé příklady, kde jsou tyto příznaky nastaveny ve výchozím nastavení, jsou <xref:System.Windows.Documents.FixedPage.Left%2A?displayProperty=nameWithType> a <xref:System.Windows.Documents.Paragraph.KeepWithNext%2A?displayProperty=nameWithType>.  
  
- <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A>. Ve výchozím nastavení vlastnosti závislosti nedědí hodnoty. <xref:System.Windows.FrameworkPropertyMetadata.OverridesInheritanceBehavior%2A> umožňuje cestám dědičnosti také cestovat do vizuálního stromu, který je nezbytný pro některé scénáře skládání ovládacích prvků.  
  
    > [!NOTE]
    > Pojem "Inherits" v kontextu hodnot vlastností znamená něco specifického pro vlastnosti závislosti; To znamená, že podřízené prvky mohou dědit skutečnou hodnotu vlastnosti závislosti z nadřazených prvků z důvodu schopnosti na úrovni architektury WPF rozhraní [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systému vlastností. Není nic dělat přímo s typem spravovaného kódu a dědičnosti členů prostřednictvím odvozených typů. Podrobnosti najdete v tématu [Dědičnost hodnot vlastností](property-value-inheritance.md).  
  
- Charakteristiky vázání dat pro sestavy (<xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A>, <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A>). Ve výchozím nastavení vlastnosti závislosti v rozhraní podporují datovou vazbu s jednosměrným chováním vazby. Můžete zakázat datovou vazbu, pokud pro ni neexistoval žádný scénář (protože mají být flexibilní a rozšiřitelné, neexistuje mnoho příkladů těchto vlastností ve výchozích [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozhraní API). Je možné nastavit, aby vazba měla oboustrannou výchozí hodnotu pro vlastnosti, které spojuje chování ovládacího prvku mezi jeho součástmi (<xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> je příklad) nebo kde Obousměrná vazba je nejběžnějším a očekávaným scénářem pro uživatele (<xref:System.Windows.Controls.TextBox.Text%2A> je příklad). Změna datové vazby má vliv jenom na výchozí hodnoty. na základě vazby je možné, že výchozí hodnota může být vždy změněna. Podrobné informace o režimech vazeb a vazbách obecně naleznete v tématu [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md).  
  
- Vytváření sestav, zda mají být vlastnosti zadávány aplikacemi nebo službami, které podporují deníky (<xref:System.Windows.FrameworkPropertyMetadata.Journal%2A>). V případě obecných prvků není deník ve výchozím nastavení povolený, ale je selektivně povolen pro určité ovládací prvky vstupu uživatele. Tato vlastnost je určena ke čtení ze služby Journal Services, včetně [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementace deníku, a obvykle je nastavena na uživatelské ovládací prvky, jako jsou výběry uživatele v rámci seznamů, které by měly být trvale v rámci jednotlivých kroků navigace. Informace o deníku najdete v tématu [Přehled navigace](../app-development/navigation-overview.md).  
  
<a name="Reading_FrameworkPropertyMetadata"></a>   
## <a name="reading-frameworkpropertymetadata"></a>Čtení FrameworkPropertyMetadata  
 Každá z výše uvedených vlastností je specifických vlastností, které <xref:System.Windows.FrameworkPropertyMetadata> přidá do své bezprostřední základní třídy <xref:System.Windows.UIPropertyMetadata>. Každá z těchto vlastností bude ve výchozím nastavení `false`. Žádost o metadata pro vlastnost, která má vědět, že hodnota těchto vlastností je důležitá, by měla při pokusu o přetypování vrácených metadat na <xref:System.Windows.FrameworkPropertyMetadata>a pak podle potřeby kontrolovat hodnoty jednotlivých vlastností.  
  
<a name="Specifying_Metadata"></a>   
## <a name="specifying-metadata"></a>Zadání metadat  
 Při vytváření nové instance metadat pro účely použití metadat do nové registrace vlastnosti závislosti máte možnost, kterou třídu metadat použít: základní <xref:System.Windows.PropertyMetadata> nebo některá odvozená třída, jako je například <xref:System.Windows.FrameworkPropertyMetadata>. Obecně platí, že byste měli použít <xref:System.Windows.FrameworkPropertyMetadata>, zejména v případě, že vaše vlastnost má jakoukoli interakci se systémem vlastností a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkcí, jako je například rozložení a datová vazba. Další možností pro pokročilejší scénáře je odvozovat z <xref:System.Windows.FrameworkPropertyMetadata> vytvořit vlastní třídu generování sestav metadat s dalšími informacemi předanými ve svých členech. Případně můžete pomocí <xref:System.Windows.PropertyMetadata> nebo <xref:System.Windows.UIPropertyMetadata> sdělit stupeň podpory pro funkce vaší implementace.  
  
 U existujících vlastností (<xref:System.Windows.DependencyProperty.AddOwner%2A> nebo <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> volání) byste měli vždy přepsat typ metadat používaný původní registrací.  
  
 Pokud vytváříte instanci <xref:System.Windows.FrameworkPropertyMetadata>, existují dva způsoby, jak tato metadata naplnit hodnotami pro konkrétní vlastnosti, které komunikují charakteristiky vlastností rozhraní:  
  
1. Použijte podpis konstruktoru <xref:System.Windows.FrameworkPropertyMetadata>, který umožňuje `flags` parametr. Tento parametr by měl být vyplněn všemi požadovanými kombinovanými hodnotami příznaků výčtu <xref:System.Windows.FrameworkPropertyMetadataOptions>.  
  
2. Použijte jednu z podpisů bez parametru `flags` a pak nastavte každou vlastnost pro vytváření sestav logických hodnot na <xref:System.Windows.FrameworkPropertyMetadata> na `true` pro každou požadovanou charakteristický typ změny. Pokud to uděláte, musíte nastavit tyto vlastnosti před tím, než se vytvoří všechny prvky s touto vlastností závislosti. Logické vlastnosti jsou pro čtení i zápis, aby bylo možné toto chování zabránit parametru `flags` a pořád naplnit metadata, ale metadata musí být před použitím vlastností skutečně zapečetěná. Proto se při pokusu o nastavení vlastností po vyžádání metadat bude jednat o neplatnou operaci.  
  
<a name="Framework_Property_Metadata_Merge_Behavior"></a>   
## <a name="framework-property-metadata-merge-behavior"></a>Chování sloučení metadat vlastností architektury  
 Při přepsání metadat vlastností rozhraní jsou různé charakteristiky metadat buď sloučeny, nebo nahrazeny.  
  
- <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> se sloučí. Pokud přidáte novou <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>, toto zpětné volání je uloženo v metadatech. Pokud nezadáte <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> v přepsání, hodnota <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> bude povýšena jako odkaz z nejbližšího předchůdce, který ho zadal v metadatech.  
  
- Skutečným chováním systému vlastností pro <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> je, že implementace všech vlastníků metadat v hierarchii jsou zachovány a přidány do tabulky, s pořadím provádění se systémem vlastností, které jsou vyvolány zpětná volání odvozené odvozené třídy. první. Zděděná zpětná volání se spouštějí pouze jednou a počítají se jako vlastněné třídou, která je umístila do metadat.  
  
- <xref:System.Windows.PropertyMetadata.DefaultValue%2A> je nahrazeno. Pokud nezadáte <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> v přepsání, hodnota <xref:System.Windows.PropertyMetadata.DefaultValue%2A> pochází z nejbližšího předchůdce, který ho zadal v metadatech.  
  
- implementace <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> jsou nahrazeny. Pokud přidáte novou <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>, toto zpětné volání je uloženo v metadatech. Pokud nezadáte <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> v přepsání, hodnota <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> bude povýšena jako odkaz z nejbližšího předchůdce, který ho zadal v metadatech.  
  
- Chování vlastností systému je, že je vyvolána pouze <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> v bezprostředních metadatech. Nejsou zachovány žádné odkazy na jiné implementace <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> v hierarchii.  
  
- Příznaky <xref:System.Windows.FrameworkPropertyMetadataOptions> výčtu jsou zkombinovány jako bitové operace nebo.  Pokud zadáte <xref:System.Windows.FrameworkPropertyMetadataOptions>, původní možnosti nebudou přepsány.  Chcete-li změnit možnost, nastavte odpovídající vlastnost v <xref:System.Windows.FrameworkPropertyMetadata>. Například pokud původní objekt <xref:System.Windows.FrameworkPropertyMetadata> nastaví příznak <xref:System.Windows.FrameworkPropertyMetadataOptions.NotDataBindable?displayProperty=nameWithType>, můžete to změnit nastavením <xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A?displayProperty=nameWithType> na `false`.  
  
 Toto chování je implementováno pomocí <xref:System.Windows.FrameworkPropertyMetadata.Merge%2A>a lze je přepsat na odvozených třídách metadat.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.DependencyProperty.GetMetadata%2A>
- [Metadata vlastností závislosti](dependency-property-metadata.md)
- [Přehled vlastností závislosti](dependency-properties-overview.md)
- [Vlastní vlastnosti závislosti](custom-dependency-properties.md)
