---
title: Metadata vlastnosti rozhraní .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WPF], framework properties
- framework property metadata [WPF]
ms.assetid: 9962f380-b885-4b61-a62e-457397083fea
ms.openlocfilehash: 8fb6e1b4cf6aed9454e9e9f1a77277d2f3611ca8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186657"
---
# <a name="framework-property-metadata"></a>Metadata vlastnosti rozhraní .NET Framework
Možnosti metadat vlastností rozhraní jsou hlášeny pro vlastnosti prvků objektu, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] které jsou považovány za na úrovni architektury WPF v architektuře. Obecně platí, že wpf na úrovni rozhraní označení znamená, že funkce, jako je [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vykreslování, datové vazby a vylepšení systému vlastností jsou zpracovány prezentace rozhraní API a spustitelné soubory. Metadata vlastností framework jsou těmito systémy dotazována k určení vlastností konkrétních vlastností prvku.  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>Požadavky  
 Toto téma předpokládá, že rozumíte vlastnostem závislostí z pohledu příjemce existujících vlastností závislostí na [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] třídách a že jste si přečetli přehled [vlastností závislostí](dependency-properties-overview.md). Měli byste také číst [metadata vlastnosti závislostí](dependency-property-metadata.md).  
  
<a name="What_Is_Communicated_by_Framework_Property"></a>
## <a name="what-is-communicated-by-framework-property-metadata"></a>Co je sděleno metadaty vlastností rozhraní  
 Metadata vlastností framework lze rozdělit do následujících kategorií:  
  
- Vlastnosti rozložení vykazování, které ovlivňují prvek (<xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A>, <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>). <xref:System.Windows.FrameworkPropertyMetadata.AffectsRender%2A> Tyto příznaky můžete nastavit v metadatech, pokud vlastnost ovlivňuje tyto příslušné <xref:System.Windows.FrameworkElement.MeasureOverride%2A>  /  <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> aspekty a také implementujete metody ve vaší třídě pro poskytování konkrétního chování vykreslování a informací do systému rozložení. Tato implementace by obvykle zkontrolovat zneplatnění vlastností ve vlastnostech závislostí, kde některé z těchto vlastností rozložení byly true v metadatech vlastnosti a pouze tyto zneplatnění by vyžadovalo vyžádání nového průchodu rozložení.  
  
- Vlastnosti rozložení vykazování, které<xref:System.Windows.FrameworkPropertyMetadata.AffectsParentArrange%2A> <xref:System.Windows.FrameworkPropertyMetadata.AffectsParentMeasure%2A>ovlivňují nadřazený prvek prvku ( , ). Některé příklady, kde jsou tyto <xref:System.Windows.Documents.FixedPage.Left%2A?displayProperty=nameWithType> <xref:System.Windows.Documents.Paragraph.KeepWithNext%2A?displayProperty=nameWithType>příznaky nastaveny ve výchozím nastavení jsou a .  
  
- <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A>. Ve výchozím nastavení vlastnosti závislostí nedědí hodnoty. <xref:System.Windows.FrameworkPropertyMetadata.OverridesInheritanceBehavior%2A>umožňuje cestu dědičnosti také cestovat do vizuálního stromu, který je nezbytný pro některé scénáře skládání ovládacího prvku.  
  
    > [!NOTE]
    > Termín "dědí" v kontextu hodnoty vlastností znamená něco specificképro vlastnosti závislostí; to znamená, že podřízené prvky mohou dědit hodnotu vlastnosti skutečné závislosti [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] z nadřazených prvků z důvodu schopnosti systému vlastností na úrovni wpf. Nemá nic společného přímo s typem spravovaného kódu a dědičností členů prostřednictvím odvozených typů. Podrobnosti naleznete v [tématu Dědičnost hodnoty nemovitosti](property-value-inheritance.md).  
  
- Charakteristiky vazby<xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A> <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A>za údaje o údajích ( , ). Ve výchozím nastavení vlastnosti závislostí v rámci podporují datové vazby s chováním jednosměrné vazby. Můžete zakázat datové vazby, pokud pro něj nebyl žádný scénář (protože jsou určeny k flexibilní a rozšiřitelné, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] není mnoho příkladů těchto vlastností ve výchozích rozhraních API). Můžete nastavit vazbu mít obousměrné výchozí vlastnosti, které spojují chování ovládacího<xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> prvku mezi jeho součásti ( je příklad) nebo kde<xref:System.Windows.Controls.TextBox.Text%2A> obousměrná vazba je společný a očekávaný scénář pro uživatele (je příklad). Změna metadat souvisejících s datovou vazbou ovlivní pouze výchozí hodnotu. na základě vazby, že výchozí lze vždy změnit. Podrobnosti o režimech vazby a vazbě obecně naleznete v [tématu Přehled datové vazby](../../../desktop-wpf/data/data-binding-overview.md).  
  
- Vykazování, zda by měly být vlastnosti do deníku zapisovány aplikacemi nebo službami, které podporují ukládání do deníku (<xref:System.Windows.FrameworkPropertyMetadata.Journal%2A>). Pro obecné prvky není ukládání do deníku ve výchozím nastavení povoleno, ale je selektivně povoleno pro některé ovládací prvky pro vstup uživatele. Tato vlastnost je určena ke čtení služby ukládání do deníku, včetně [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] provádění ukládání do deníku a je obvykle nastavena na uživatelské ovládací prvky, jako je například výběr uživatelů v rámci seznamů, které by měly být trvalé v rámci navigační kroky. Informace o deníku naleznete v tématu [Navigační přehled](../app-development/navigation-overview.md).  
  
<a name="Reading_FrameworkPropertyMetadata"></a>
## <a name="reading-frameworkpropertymetadata"></a>Čtení Framework PropertyMetadata  
 Každá z výše uvedených vlastností <xref:System.Windows.FrameworkPropertyMetadata> jsou specifické vlastnosti, které přidá do své okamžité základní třídy <xref:System.Windows.UIPropertyMetadata>. Každá z těchto `false` vlastností bude ve výchozím nastavení. Požadavek metadat pro vlastnost, kde je důležité znát hodnotu těchto vlastností, by se měl pokusit přetypovat vrácená metadata do <xref:System.Windows.FrameworkPropertyMetadata>položky a podle potřeby zkontrolovat hodnoty jednotlivých vlastností.  
  
<a name="Specifying_Metadata"></a>
## <a name="specifying-metadata"></a>Určení metadat  
 Když vytvoříte novou instanci metadat pro účely použití metadat na novou registraci vlastnosti závislosti, máte <xref:System.Windows.PropertyMetadata> na výběr, kterou <xref:System.Windows.FrameworkPropertyMetadata>třídu metadat použít: základní nebo některé odvozené třídy, jako je například . Obecně byste měli <xref:System.Windows.FrameworkPropertyMetadata>použít , zejména v případě, že [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vaše vlastnost má nějakou interakci s vlastností systému a funkce, jako je rozložení a datové vazby. Další možností pro složitější scénáře <xref:System.Windows.FrameworkPropertyMetadata> je odvodit z vytvořit vlastní metadata vykazování třídy s další informace prováděné v jeho členy. Nebo můžete <xref:System.Windows.PropertyMetadata> použít <xref:System.Windows.UIPropertyMetadata> nebo sdělit stupeň podpory funkcí implementace.  
  
 Pro existující<xref:System.Windows.DependencyProperty.AddOwner%2A> vlastnosti ( nebo <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> volání) byste měli vždy přepsat typem metadat používaným původní registrací.  
  
 Pokud vytváříte <xref:System.Windows.FrameworkPropertyMetadata> instanci, existují dva způsoby, jak naplnit tato metadata hodnotami pro konkrétní vlastnosti, které komunikují vlastnosti vlastností rozhraní:  
  
1. Použijte <xref:System.Windows.FrameworkPropertyMetadata> podpis konstruktoru, `flags` který umožňuje parametr. Tento parametr by měl být vyplněn všemi požadovanými kombinovanými hodnotami příznaků výčtu. <xref:System.Windows.FrameworkPropertyMetadataOptions>  
  
2. Použijte jeden z podpisů `flags` bez parametru a potom nastavte <xref:System.Windows.FrameworkPropertyMetadata> `true` každou logickou vlastnost sestavy pro každou požadovanou změnu charakteristiky. Pokud tak učiníte, musíte nastavit tyto vlastnosti před vytvořením všech prvků s touto vlastností závislosti; Logické vlastnosti jsou čtení a zápis, aby bylo `flags` možné toto chování vyhnout se parametru a stále naplnit metadata, ale metadata musí být účinně zapečetěny před použitím vlastností. Proto pokus o nastavení vlastností po vyžádání metadat bude neplatná operace.  
  
<a name="Framework_Property_Metadata_Merge_Behavior"></a>
## <a name="framework-property-metadata-merge-behavior"></a>Chování sloučení metadat vlastností frameworku  
 Když přepíšete metadata vlastností architektury, různé charakteristiky metadat jsou sloučeny nebo nahrazeny.  
  
- <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>je sloučena. Pokud přidáte nový <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>, toto zpětné volání je uloženo v metadatech. Pokud nezadáte <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> v přepsání, hodnota <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> je povýšen jako odkaz z nejbližšípředchůdce, který ji zadal v metadatech.  
  
- Skutečné chování systému <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> vlastností pro je, že implementace pro všechny vlastníky metadat v hierarchii jsou zachovány a přidány do tabulky, s pořadím provádění systémem vlastností je, že zpětná volání nejvýrazněji odvozené třídy jsou vyvolány jako první. Zděděná zpětná volání spustit pouze jednou, počítání jako vlastněné třídy, která je umístila do metadat.  
  
- <xref:System.Windows.PropertyMetadata.DefaultValue%2A>je nahrazen. Pokud nezadáte <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> v přepsání, hodnota <xref:System.Windows.PropertyMetadata.DefaultValue%2A> pochází z nejbližšípředchůdce, který ji zadal v metadatech.  
  
- <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>implementace jsou nahrazeny. Pokud přidáte nový <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>, toto zpětné volání je uloženo v metadatech. Pokud nezadáte <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> v přepsání, hodnota <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> je povýšen jako odkaz z nejbližšípředchůdce, který ji zadal v metadatech.  
  
- Chování systému vlastností <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> je, že je vyvolána pouze v bezprostřední metadata. Nejsou zachovány <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> žádné odkazy na jiné implementace v hierarchii.  
  
- Příznaky výčtu <xref:System.Windows.FrameworkPropertyMetadataOptions> jsou kombinovány jako bitové operace OR.  Pokud zadáte <xref:System.Windows.FrameworkPropertyMetadataOptions>, původní možnosti nebudou přepsány.  Chcete-li změnit možnost, nastavte <xref:System.Windows.FrameworkPropertyMetadata>odpovídající vlastnost na . Pokud například původní <xref:System.Windows.FrameworkPropertyMetadata> objekt <xref:System.Windows.FrameworkPropertyMetadataOptions.NotDataBindable?displayProperty=nameWithType> nastaví příznak, můžete <xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A?displayProperty=nameWithType> jej `false`změnit nastavením na .  
  
 Toto chování <xref:System.Windows.FrameworkPropertyMetadata.Merge%2A>je implementováno společností , a může být přepsáno na odvozených třídách metadat.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.DependencyProperty.GetMetadata%2A>
- [Metadata vlastností závislosti](dependency-property-metadata.md)
- [Přehled vlastností závislosti](dependency-properties-overview.md)
- [Vlastní vlastnosti závislosti](custom-dependency-properties.md)
