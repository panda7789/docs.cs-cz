---
title: Metadata vlastnosti rozhraní .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WPF], framework properties
- framework property metadata [WPF]
ms.assetid: 9962f380-b885-4b61-a62e-457397083fea
ms.openlocfilehash: f313c17a278a7b51379c4da9389c01eedf4a1e62
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57379273"
---
# <a name="framework-property-metadata"></a>Metadata vlastnosti rozhraní .NET Framework
Možnosti metadata vlastnosti architektury jsou hlášeny pro vlastnosti považuje za na rozhraní WPF v úrovni elementů objektu [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] architektury. Obecně znamená označení úrovni rozhraní WPF této funkce, jako je vykreslování, datové vazby, a vlastnost systému upřesnění jsou zpracovávány [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prezentace [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] a spustitelné soubory. Metadata vlastnosti architektury je dotazován tyto systémy určit vlastnosti specifické pro funkce vlastností konkrétní elementu.  
  
 
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 Toto téma předpokládá, že rozumíte vlastnosti závislosti z pohledu příjemce vlastnosti existujícího závislosti na [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] třídy a čtení [přehled vlastností závislosti](dependency-properties-overview.md). Doporučujeme mít přečíst [Metadata vlastností závislosti](dependency-property-metadata.md).  
  
<a name="What_Is_Communicated_by_Framework_Property"></a>   
## <a name="what-is-communicated-by-framework-property-metadata"></a>Jaké informace se předávají pomocí Metadata vlastnosti architektury  
 Metadata vlastnosti architektury je možné rozdělit do těchto kategorií:  
  
-   Vytváření sestav vlastnosti rozložení, které ovlivňují elementu (<xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A>, <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>, <xref:System.Windows.FrameworkPropertyMetadata.AffectsRender%2A>). Může nastavit tyto příznaky v metadatech, pokud vlastnost ovlivňuje tyto aspekty příslušné a také při implementaci <xref:System.Windows.FrameworkElement.MeasureOverride%2A>  /  <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> metody ve třídě poskytnout informace o rozložení a chování specifické vykreslení systém. Obvykle by tyto implementace vyhledávat vlastnost invalidations ve vlastnosti DependencyProperty, kde některé z těchto vlastností rozložení byly v metadatech vlastnost hodnotu true, a pouze ty invalidations by vyžadovalo přechod požaduje novou předání rozložení.  
  
-   Generování sestav vlastnosti rozložení, které ovlivňují elementu nadřazeného elementu (<xref:System.Windows.FrameworkPropertyMetadata.AffectsParentArrange%2A>, <xref:System.Windows.FrameworkPropertyMetadata.AffectsParentMeasure%2A>). Tady je několik příkladů kde jsou ve výchozím nastavení tyto příznaky <xref:System.Windows.Documents.FixedPage.Left%2A?displayProperty=nameWithType> a <xref:System.Windows.Documents.Paragraph.KeepWithNext%2A?displayProperty=nameWithType>.  
  
-   <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A>. Ve výchozím nastavení nedědí vlastnosti závislosti hodnoty. <xref:System.Windows.FrameworkPropertyMetadata.OverridesInheritanceBehavior%2A> Umožňuje cestu dědičnosti také projít do vizuálního stromu, který je potřebný pro některé scénáře skládání ovládacího prvku.  
  
    > [!NOTE]
    >  Termín "dědí" v kontextu znamená hodnoty vlastnosti jako specifický pro vlastnosti závislosti; To znamená, že může být z podřízených prvků dědit z nadřazených prvků hodnota vlastnosti skutečné závislosti z důvodu funkce úrovni rozhraní WPF [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systému vlastností. To nemá nic společného přímo pomocí spravovaného kódu dědičnosti typů a členů prostřednictvím odvozené typy. Podrobnosti najdete v tématu [dědičnost hodnoty vlastnosti](property-value-inheritance.md).  
  
-   Generování sestav vazby vlastností dat (<xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A>, <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A>). Ve výchozím nastavení podporují vlastnosti závislosti v rámci datové vazby, chování jednosměrné vazby. Vytváření datových vazeb může zakázat, pokud žádné scénáře nebyly tak (protože jsou určeny jako flexibilní a rozšiřitelné, nejsou k dispozici mnoho příkladů takových vlastnosti ve výchozím [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]). Můžete například nastavit vazbu mít obousměrný výchozí hodnoty pro vlastnosti, které spojovat ovládací prvek chování mezi její část součásti (<xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> je příkladem) nebo kde Obousměrná vazba je běžné a očekávané scénář pro uživatele (<xref:System.Windows.Controls.TextBox.Text%2A> je příklad). Změna metadata související s vazby dat ovlivňuje pouze výchozí; na základě neumožňující vazbu, že výchozí lze kdykoli změnit. Podrobné informace o režimech vazby a vazby v obecné, naleznete v tématu [Data Binding Overview](../data/data-binding-overview.md).  
  
-   Vytváření sestav, zda má být vlastnosti deníku aplikace nebo služby, které podporují záznamu do deníku (<xref:System.Windows.FrameworkPropertyMetadata.Journal%2A>). Obecné elementy záznamu do deníku není ve výchozím nastavení povolené, ale selektivně je povolený pro některé uživatele, vstupní ovládací prvky. Tato vlastnost je určena ke čtení záznamu do deníku služby včetně [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] provádění záznamu do deníku a se obvykle nastavuje pouze na uživatelské ovládací prvky, jako je například volby uživatele v rámci seznamy, které by měl být zachován po kroky navigace. Informace o deníku, naleznete v tématu [Přehled navigace](../app-development/navigation-overview.md).  
  
<a name="Reading_FrameworkPropertyMetadata"></a>   
## <a name="reading-frameworkpropertymetadata"></a>Čtení FrameworkPropertyMetadata  
 Vlastnosti propojené výše jsou konkrétní vlastnosti, která <xref:System.Windows.FrameworkPropertyMetadata> přidá do své přímé základní třídy <xref:System.Windows.UIPropertyMetadata>. Každá z těchto vlastností bude `false` ve výchozím nastavení. Žádost o metadata pro vlastnosti, kde je důležité vědět, hodnoty těchto vlastností má pokusit o přetypovat vráceného metadata <xref:System.Windows.FrameworkPropertyMetadata>a podle potřeby zkontrolujte hodnoty jednotlivých vlastností.  
  
<a name="Specifying_Metadata"></a>   
## <a name="specifying-metadata"></a>Určení metadat  
 Když vytvoříte novou instanci metadat pro účely použití metadat na nové registrace vlastnost závislosti, máte taky možnost výběru z třídy metadat: základní <xref:System.Windows.PropertyMetadata> nebo některé odvozené třídy jako <xref:System.Windows.FrameworkPropertyMetadata>. Obecně byste měli použít <xref:System.Windows.FrameworkPropertyMetadata>, zejména v případě, že vaše vlastnost má všechny interakce s vlastností systému a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkce, jako je rozložení a datové vazby. Další možností pro složitější scénáře je odvozen od <xref:System.Windows.FrameworkPropertyMetadata> vytvořit vlastní metadata reporting třída s atributem dodatečné informace přenášejí v jejích členů. Nebo můžete použít <xref:System.Windows.PropertyMetadata> nebo <xref:System.Windows.UIPropertyMetadata> komunikovat stupeň podpora pro funkce implementace.  
  
 Pro existující vlastnosti (<xref:System.Windows.DependencyProperty.AddOwner%2A> nebo <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> volání), kterou byste měli vždy přepsat s typem metadat používané původní registrace.  
  
 Pokud vytváříte <xref:System.Windows.FrameworkPropertyMetadata> instance, existují dva způsoby, jak naplnit těchto metadat se hodnoty konkrétní vlastnosti, které komunikují charakteristiky vlastnost framework:  
  
1.  Použití <xref:System.Windows.FrameworkPropertyMetadata> podpis konstruktoru, který umožňuje `flags` parametru. Tento parametr by měl být vyplněny všechna požadovaná kombinované hodnoty <xref:System.Windows.FrameworkPropertyMetadataOptions> výčet příznaků.  
  
2.  Použijte jednu z podpisy bez `flags` parametr a nastavte vlastnost typu Boolean vyvářet <xref:System.Windows.FrameworkPropertyMetadata> k `true` pro každé požadované charakteristické změnit. Pokud to uděláte, musíte nastavit tyto vlastnosti předtím, než jsou vytvořeny všechny prvky s touto vlastností závislostí; čtení a zápis, aby bylo možné povolit toto chování vyhnout jsou logické vlastnosti `flags` parametr a stále vyplnit metadata, ale metadata musí být efektivně zapečetěné před použitím vlastnosti. Díky tomu se pokus o nastavení vlastnosti po metadata požadovala bude neplatná operace.  
  
<a name="Framework_Property_Metadata_Merge_Behavior"></a>   
## <a name="framework-property-metadata-merge-behavior"></a>Chování sloučení Metadata vlastností rozhraní Framework  
 Při přepsání metadata vlastnosti architektury vlastnosti rozdílná metadata jsou sloučené nebo nahradit.  
  
-   <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> se sloučí. Pokud chcete přidat nový <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>, že zpětné volání je uložená v metadatech. Pokud nezadáte <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> v přepsání, hodnota <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> povýšen jako odkaz v nejbližším podřízeném objektu, který je zadán v metadatech.  
  
-   Skutečné vlastnost chování systému pro <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> je, že implementace pro všechny vlastníky metadat v hierarchii se zachovají a přidá do tabulky, pomocí pořadí provádění vlastnosti systému, který se zpětná volání nejhlouběji odvozené třídy Otevře se nejdřív. Zděděné zpětná volání spustit jenom jednou, počítací vlastněné třídu, která je umístěna v metadatech.  
  
-   <xref:System.Windows.PropertyMetadata.DefaultValue%2A> nahrazuje. Pokud nezadáte <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> v přepsání, hodnota <xref:System.Windows.PropertyMetadata.DefaultValue%2A> pochází z nejbližším podřízeném objektu, který je zadán v metadatech.  
  
-   <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> implementace se nahradí. Pokud chcete přidat nový <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>, že zpětné volání je uložená v metadatech. Pokud nezadáte <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> v přepsání, hodnota <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> povýšen jako odkaz v nejbližším podřízeném objektu, který je zadán v metadatech.  
  
-   Chování vlastnosti systému je to jenom <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> v metadatech okamžité je vyvolána. Žádné odkazy na další <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> implementace v hierarchii se zachovají.  
  
-   Příznaky z <xref:System.Windows.FrameworkPropertyMetadataOptions> výčtu jsou zkombinované jako bitová operace OR.  Pokud zadáte <xref:System.Windows.FrameworkPropertyMetadataOptions>, původní možnosti se nepřepíšou.  Chcete-li změnit možnost, nastavte odpovídající vlastnost <xref:System.Windows.FrameworkPropertyMetadata>. Například pokud původní <xref:System.Windows.FrameworkPropertyMetadata> objektu sady <xref:System.Windows.FrameworkPropertyMetadataOptions.NotDataBindable?displayProperty=nameWithType> příznak, který můžete změnit nastavením <xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A?displayProperty=nameWithType> k `false`.  
  
 Toto chování je implementováno <xref:System.Windows.FrameworkPropertyMetadata.Merge%2A>a u tříd odvozených metadat je možné přepsat.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.DependencyProperty.GetMetadata%2A>
- [Metadata vlastností závislosti](dependency-property-metadata.md)
- [Přehled vlastností závislosti](dependency-properties-overview.md)
- [Vlastní vlastnosti závislosti](custom-dependency-properties.md)
