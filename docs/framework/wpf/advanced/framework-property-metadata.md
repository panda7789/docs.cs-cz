---
title: "Metadata vlastnosti rozhraní .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- metadata [WPF], framework properties
- framework property metadata [WPF]
ms.assetid: 9962f380-b885-4b61-a62e-457397083fea
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4fec11a973572dce9e8d6f77bf65ce31ee77eb41
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="framework-property-metadata"></a>Metadata vlastnosti rozhraní .NET Framework
Možnosti metadat vlastností Framework jsou hlášeny vlastností elementů objekt považuje za na rozhraní WPF v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] architektura. Obecné označení úrovni rozhraní WPF zahrnuje této funkce jako je například vykreslování, datové vazby, a vlastnost systému obecnější jsou zpracovávány [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prezentace [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] a spustitelné soubory. Metadata vlastnosti Framework je dotazován tak, že tyto systémy pro stanovení konkrétních funkcí vlastností určitý element vlastnosti.  
  
 
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 Toto téma předpokládá, že rozumíte vlastností závislostí z perspektivy příjemce existující vlastností závislostí na [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] třídy a mít ke čtení [přehled vlastností závislostí](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md). Měli byste také mít si přečíst [metadat vlastností závislostí](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md).  
  
<a name="What_Is_Communicated_by_Framework_Property"></a>   
## <a name="what-is-communicated-by-framework-property-metadata"></a>Jaké informace se předávají pomocí metadat vlastností Framework  
 Metadata vlastnosti Framework lze rozdělit do následujících kategorií:  
  
-   Vytváření sestav rozložení vlastnosti, které ovlivňují elementu (<xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A>, <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>, <xref:System.Windows.FrameworkPropertyMetadata.AffectsRender%2A>). V metadatech může nastavit tyto příznaky, pokud vlastnost ovlivňuje těchto příslušných aspekty, a také implementujete <xref:System.Windows.FrameworkElement.MeasureOverride%2A>  /  <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> metody ve třídě zadat konkrétní vykreslování chování a informace o rozložení systém. Takové implementace by obvykle, zkontrolujte vlastnost invalidations ve vlastnostech závislostí, kde některé z těchto vlastností rozložení byly ve metadata vlastnosti a pouze ty invalidations, vyžadovalo žádají o nové průchodu rozložení.  
  
-   Vytváření sestav rozložení vlastnosti, které ovlivňují nadřazeného elementu elementu (<xref:System.Windows.FrameworkPropertyMetadata.AffectsParentArrange%2A>, <xref:System.Windows.FrameworkPropertyMetadata.AffectsParentMeasure%2A>). Některé příklady, které jsou ve výchozím nastavení tyto příznaky jsou <xref:System.Windows.Documents.FixedPage.Left%2A?displayProperty=nameWithType> a <xref:System.Windows.Documents.Paragraph.KeepWithNext%2A?displayProperty=nameWithType>.  
  
-   <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A>. Ve výchozím nastavení vlastností závislostí nedědí hodnoty. <xref:System.Windows.FrameworkPropertyMetadata.OverridesInheritanceBehavior%2A>Umožňuje cestu dědičnosti také projít, do vizuálním stromu, který je potřebný pro některé scénáře řízení skládání.  
  
    > [!NOTE]
    >  Termín "dědí" v kontextu vlastnost hodnoty znamená něco konkrétní závislost vlastnosti; znamená to, že podřízené elementy může dědit vlastnosti hodnotu vlastnosti skutečné závislost z nadřazené elementy z důvodu funkce WPF úrovni rozhraní [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnost systému. Má co dělat přímo s spravovaného kódu typu a členy dědičnosti prostřednictvím odvozené typy. Podrobnosti najdete v tématu [dědičnost hodnotu vlastnosti](../../../../docs/framework/wpf/advanced/property-value-inheritance.md).  
  
-   Vytváření sestav vlastností vazby dat (<xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A>, <xref:System.Windows.FrameworkPropertyMetadata.BindsTwoWayByDefault%2A>). Ve výchozím nastavení vlastnosti závislosti v rámci podporují vytvoření datové vazby s chování jednosměrné vazby. Datová vazba může zakázat, pokud žádné scénář pro ni byly jakkoli (vzhledem k tomu, že by měla být flexibilní a rozšiřitelný, nejsou k dispozici mnoho příklady takových vlastnosti ve výchozí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]). Může nastavit vazbou, který bude mít obousměrný výchozí hodnoty pro vlastnosti, které společně tie chování ovládacího prvku mezi jeho jednotlivých součástí (<xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> je příklad) nebo kde vazba obousměrná je běžné a očekávané scénář pro uživatele (<xref:System.Windows.Controls.TextBox.Text%2A> je příklad). Změna metadat data související s vazby vliv pouze výchozí; na základě za vazby, můžete kdykoli změnit výchozí. Informace o režimech vazby a vazby v obecné najdete v tématu [přehled vazby dat](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
-   Vytváření sestav, zda má být vlastnosti deníku aplikace nebo služby, které podporují deníku (<xref:System.Windows.FrameworkPropertyMetadata.Journal%2A>). Obecné elementy deníku není ve výchozím nastavení povolené, ale je selektivně povolen pro některé uživatele, vstupní ovládací prvky. Tato vlastnost má číst deníku služeb včetně [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementace deníku a se obvykle nastavuje na uživatelské ovládací prvky, jako je výběr uživatelů v rámci seznamy, které by měl být zachován po navigační kroky. Informace o deníku najdete v tématu [navigační přehled](../../../../docs/framework/wpf/app-development/navigation-overview.md).  
  
<a name="Reading_FrameworkPropertyMetadata"></a>   
## <a name="reading-frameworkpropertymetadata"></a>Čtení FrameworkPropertyMetadata  
 Ke každé z vlastností uvedený výše jsou konkrétní vlastnosti, <xref:System.Windows.FrameworkPropertyMetadata> přidá do své okamžitou základní třídy <xref:System.Windows.UIPropertyMetadata>. Každý z těchto vlastností bude `false` ve výchozím nastavení. Žádost metadata pro vlastnost, kde je důležité zároveň budete vědět, hodnota tyto vlastnosti mají pokusit o přetypovat Vrácená metadata k <xref:System.Windows.FrameworkPropertyMetadata>a potom zkontrolujte hodnoty jednotlivé vlastnosti podle potřeby.  
  
<a name="Specifying_Metadata"></a>   
## <a name="specifying-metadata"></a>Určení metadat  
 Když vytvoříte novou instanci metadata pro účely použití metadata pro nové registrace vlastnost závislosti, máte možnost volby které třídy metadat použít: základní <xref:System.Windows.PropertyMetadata> nebo některé odvozené třídy, jako <xref:System.Windows.FrameworkPropertyMetadata>. Obecně platí, měli byste použít <xref:System.Windows.FrameworkPropertyMetadata>, zvlášť pokud vaše vlastnost má interakce s vlastností systému a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] funkce jako je například rozložení a datové vazby. Další možností pro sofistikovanější scénáře je odvozena od <xref:System.Windows.FrameworkPropertyMetadata> k vytvoření vlastních metadat generování sestav se doplňující informace provádět v její členy. Nebo můžete použít <xref:System.Windows.PropertyMetadata> nebo <xref:System.Windows.UIPropertyMetadata> komunikovat stupeň podpora pro funkce vaší implementace.  
  
 Pro existující vlastnosti (<xref:System.Windows.DependencyProperty.AddOwner%2A> nebo <xref:System.Windows.DependencyProperty.OverrideMetadata%2A> volání), byste měli vždy přepsat s typem metadat používané původní registrace.  
  
 Pokud vytváříte <xref:System.Windows.FrameworkPropertyMetadata> instance, k naplnění aby metadata s hodnotami pro konkrétní vlastnosti, které předávají charakteristiky vlastnost framework dvěma způsoby:  
  
1.  Použití <xref:System.Windows.FrameworkPropertyMetadata> podpis konstruktor, který umožňuje `flags` parametr. Tento parametr je nutné zadat všechny požadované kombinované hodnotami <xref:System.Windows.FrameworkPropertyMetadataOptions> výčet příznaků.  
  
2.  Použijte jednu z podpisy bez `flags` parametr a poté nastavte všechny zprávy o vlastnost typu Boolean <xref:System.Windows.FrameworkPropertyMetadata> k `true` pro každý požadovaných charakteristik změnu. Pokud to uděláte, musíte nastavit tyto vlastnosti předtím, než se vytvářejí všechny prvky s Tato vlastnost závislosti; Logická hodnota vlastnosti jsou pro čtení a zápis, aby bylo možné toto chování vyhnout `flags` parametr a stále naplnit metadata, ale metadata musí být efektivně zapečetěná před použitím vlastnost. Proto pokusu o nastavení vlastnosti po vyžádání metadata bude na neplatnou operaci.  
  
<a name="Framework_Property_Metadata_Merge_Behavior"></a>   
## <a name="framework-property-metadata-merge-behavior"></a>Chování metadat sloučení vlastnost Framework  
 Při přepsání metadat vlastností framework charakteristiky rozdílná metadata jsou sloučit nebo nahradit.  
  
-   <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>sloučí. Pokud přidáte nový <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>, že zpětné volání je uložená v metadatech. Pokud nezadáte <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> v hodnotě přepsání <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> se vyzval jako odkaz z nejbližším podřízeném objektu, který je zadaný v metadatech.  
  
-   Skutečné vlastnost chování systému pro <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> je, že implementace pro všechny vlastníky metadata v hierarchii se zachovají a přidat do tabulky s pořadí provádění vlastnosti systému, který probíhá zpětná volání nejvíce hluboko odvozené třídy nejdříve volána. Zděděné zpětná volání spustit jenom jednou, počítání jako probíhá vlastní třídu, která je umístěna v metadatech.  
  
-   <xref:System.Windows.PropertyMetadata.DefaultValue%2A>nahrazuje. Pokud nezadáte <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> v hodnotě přepsání <xref:System.Windows.PropertyMetadata.DefaultValue%2A> pochází z nejbližším podřízeném objektu, který je zadaný v metadatech.  
  
-   <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>implementace jsou nahrazena. Pokud přidáte nový <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>, že zpětné volání je uložená v metadatech. Pokud nezadáte <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> v hodnotě přepsání <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> se vyzval jako odkaz z nejbližším podřízeném objektu, který je zadaný v metadatech.  
  
-   Vlastnost chování systému je pouze <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> ve okamžitou metadata volat. Žádné odkazy na jiné <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> implementace v hierarchii se zachovají.  
  
-   Příznaky systému <xref:System.Windows.FrameworkPropertyMetadataOptions> výčtu slučují jako bitové operace OR.  Pokud zadáte <xref:System.Windows.FrameworkPropertyMetadataOptions>, původní možnosti se nepřepíšou.  Chcete-li změnit možnost, nastavte na odpovídající vlastnost <xref:System.Windows.FrameworkPropertyMetadata>. Například pokud původní <xref:System.Windows.FrameworkPropertyMetadata> objektu sady <xref:System.Windows.FrameworkPropertyMetadataOptions.NotDataBindable?displayProperty=nameWithType> příznak, který můžete změnit nastavením <xref:System.Windows.FrameworkPropertyMetadata.IsNotDataBindable%2A?displayProperty=nameWithType> k `false`.  
  
 Toto chování je implementováno modulem <xref:System.Windows.FrameworkPropertyMetadata.Merge%2A>a je možné přepsat na metadata odvozené třídy.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.DependencyProperty.GetMetadata%2A>  
 [Metadata vlastností závislosti](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)  
 [Přehled vlastností závislosti](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Vlastní vlastnosti závislosti](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)
