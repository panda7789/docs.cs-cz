---
title: "Vlastní vlastnosti závislosti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f1ee7c7b4e21d147bad1cd8e4b854c0ff4fe13aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="custom-dependency-properties"></a>Vlastní vlastnosti závislosti
Toto téma popisuje důvody, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vývojáři aplikací a součástí autoři může být potřeba vytvořit vlastnost vlastní závislosti a popisuje kroky implementace, jakož i některé možnosti implementace, které může zlepšit výkon, použitelnost, nebo všestrannost vlastnost.  
  

  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 Toto téma předpokládá, že rozumíte vlastností závislostí z perspektivy příjemce existující vlastností závislostí na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] třídy a mít ke čtení [přehled vlastností závislostí](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md) tématu. Chcete-li v následujících příkladech v tomto tématu byste měli také porozumět [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] a vědět, jak napsat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.  
  
<a name="whatis"></a>   
## <a name="what-is-a-dependency-property"></a>Co je vlastnost závislosti?  
 Můžete povolit, co by se jinak mohly [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] vlastnost pro podporu stylů, vazby dat, dědičnosti, animace a výchozí hodnoty implementací jako vlastnost závislosti. Vlastnosti závislosti jsou vlastnosti, které jsou registrovány [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnost systému voláním <xref:System.Windows.DependencyProperty.Register%2A> – metoda (nebo <xref:System.Windows.DependencyProperty.RegisterReadOnly%2A>), a které jsou zajišťované <xref:System.Windows.DependencyProperty> identifikátor pole. Vlastnosti závislosti lze použít pouze systémem <xref:System.Windows.DependencyObject> typy, ale <xref:System.Windows.DependencyObject> poměrně vysokou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] třídy hierarchie, takže většina třídy k dispozici v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] může podporovat vlastností závislostí. Další informace o vlastnosti závislosti a některé terminologie a pravidla týkající se používá k popisu je v tomto [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)], najdete v části [přehled vlastností závislostí](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
<a name="example_dp"></a>   
## <a name="examples-of-dependency-properties"></a>Příklady vlastností závislostí  
 Příklady vlastností závislostí, které jsou implementovány na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] třídy zahrnují <xref:System.Windows.Controls.Control.Background%2A> vlastnost, <xref:System.Windows.FrameworkElement.Width%2A> vlastnost a <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost mezi mnoha jinými. Každá vlastnost závislosti vystavené třídu má odpovídající veřejné statické pole typu <xref:System.Windows.DependencyProperty> zveřejněné na stejné třídy. Toto je identifikátor pro vlastnost závislosti. Identifikátor je s názvem použitím: název vlastnosti závislosti řetězcem `Property` přidá se k němu. Například odpovídající <xref:System.Windows.DependencyProperty> identifikátor pole <xref:System.Windows.Controls.Control.Background%2A> vlastnost je <xref:System.Windows.Controls.Control.BackgroundProperty>. Identifikátor ukládá informace o vlastnosti závislosti, jako byl zaregistrován a identifikátor je pak později použít pro jiné operace zahrnující vlastnost závislosti, jako je například volání <xref:System.Windows.DependencyObject.SetValue%2A>.  
  
 Jak je uvedeno v [přehled vlastností závislostí](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md), všech vlastností závislostí v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (s výjimkou nejvíce přidružené vlastnosti) jsou taky [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] vlastnosti z důvodu implementace "obálku". Proto z kódu, můžete získat nebo nastavit vlastnosti závislosti voláním [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] přístupové objekty, které definují obálky stejným způsobem, že použijete jiné [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] vlastnosti. Jako příjemce vlastnosti zavedených závislostí, nepoužívejte obvykle <xref:System.Windows.DependencyObject> metody <xref:System.Windows.DependencyObject.GetValue%2A> a <xref:System.Windows.DependencyObject.SetValue%2A>, které jsou bod připojení ke podkladový systém vlastnost. Místo toho existující implementace [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] vlastnosti bude mít již volána <xref:System.Windows.DependencyObject.GetValue%2A> a <xref:System.Windows.DependencyObject.SetValue%2A> v rámci `get` a `set` obálku implementace vlastnost pomocí pole identifikátor správně . Při implementaci vlastnost vlastní závislosti sami, pak je bude možné definování obálku podobným způsobem.  
  
<a name="backing_with_dp"></a>   
## <a name="when-should-you-implement-a-dependency-property"></a>Pokud budete implementovat vlastnost závislosti?  
 Pokud implementujete vlastnost třídy, tak dlouho, dokud vaše třída odvozena z <xref:System.Windows.DependencyObject>, máte možnost zálohovat vaše vlastnost s <xref:System.Windows.DependencyProperty> identifikátor proto chcete-li vlastnost závislosti. S vaší vlastnost být vlastnost závislosti není vždy nutné nebo vhodné a bude záviset na vašich potřebách scénář. V některých případech typické technika zálohování vaší vlastnost s soukromé pole je dostačující. Ale měli byste implementovat vaše vlastnost jako vlastnost závislosti vždy, když chcete, aby vaše vlastnost pro podporu jeden nebo více z následujících [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] možnosti:  
  
-   Chcete, aby vaše vlastnost, která má být nastavit ve stylu. Další informace najdete v tématu [stylů a ukázka](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
-   Chcete, aby vaše vlastnost pro podporu datové vazby. Další informace o vlastnosti závislosti datové vazby v tématu [vazby vlastnosti dva prvky](../../../../docs/framework/wpf/data/how-to-bind-the-properties-of-two-controls.md).  
  
-   Chcete, aby vaše vlastnost, která má být nastavit s odkazem na dynamické prostředků. Další informace najdete v tématu [XAML prostředky](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
-   Chcete automaticky dědí nadřazený element ve stromové struktuře element hodnotu vlastnosti. V takovém případě zaregistrovat <xref:System.Windows.DependencyProperty.RegisterAttached%2A> metoda, i když můžete také vytvořit vlastnost obálku pro [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] přístup. Další informace najdete v tématu [dědičnost hodnotu vlastnosti](../../../../docs/framework/wpf/advanced/property-value-inheritance.md).  
  
-   Chcete, aby vaše vlastnost, která má být animatable. Další informace najdete v tématu [animace přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
-   Chcete vlastnost systému sestavy, když byla změněna předchozí hodnotu vlastnosti akce prováděné vlastnosti systému, prostředí nebo uživatele, nebo čtení a používání stylů. Pomocí metadat vlastností můžete zadat vaše vlastnost metoda zpětného volání, která bude volána pokaždé, když vlastnost systém zjišťuje, že hodnota vlastnosti platností změnila. Pojmem je převod hodnotu vlastnosti. Další informace najdete v tématu [závislostí vlastnost zpětná volání a ověření](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md).  
  
-   Chcete použít konvence zavedených metadat, které jsou také používány [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] procesů, jako je vytváření sestav, zda změna hodnotu vlastnosti měli vyžadovat rozložení systému znovu zalomit vizuální prvky pro daný element. Nebo chcete být schopni pomocí přepsání metadata tak, aby odvozené třídy můžete změnit na základě metadat charakteristiky jako výchozí hodnota.  
  
-   Chcete vlastnosti vlastního ovládacího prvku pro příjem [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)] [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] podporují, jako například **vlastnosti** okno úpravy. Další informace najdete v tématu [vytváření – Přehled ovládacího prvku](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
 Při kontrole tyto scénáře měli také zvážit, zda váš scénář můžete dosáhnout pomocí přepsání metadata existující vlastnost závislosti, nikoli implementace úplně novou vlastnost. Jestli je praktické metadata přepsání závisí na váš scénář a jak blízko tento scénář vypadá zhruba v implementaci v existující [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] třídy a vlastnosti závislosti. Další informace o přepsání metadat u stávajících vlastností najdete v tématu [metadat vlastností závislostí](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md).  
  
<a name="checklist"></a>   
## <a name="checklist-for-defining-a-dependency-property"></a>Kontrolní seznam pro definování vlastnosti závislosti  
 Definování vlastnosti závislosti se skládá ze čtyř různých koncepty. Tyto koncepty nejsou nutně striktní příklady kroků, protože některé z těchto skončili kombinováním jako jeden řádků kódu implementace:  
  
-   (Volitelné) Vytvořte vlastnost metadata pro vlastnost závislosti.  
  
-   Registraci název vlastnosti v systému vlastnosti, typ vlastníka a typ hodnoty vlastnosti. Pokud se používá také určete metadata vlastnosti.  
  
-   Definování <xref:System.Windows.DependencyProperty> identifikátor jako `public` `static` `readonly` pole pro typ vlastníka.  
  
-   Definování [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] vlastnost "obálky", jejíž název odpovídá názvu vlastnosti závislosti. Implementace [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] "obálky" vlastnost `get` a `set` přístupových objektů pro připojení s vlastností závislost, která zálohuje ho.  
  
<a name="registering"></a>   
### <a name="registering-the-property-with-the-property-system"></a>Registrace vlastnost systémem vlastnost  
 Aby vaše vlastnost jako vlastnost závislosti musíte zaregistrovat tuto vlastnost do tabulky udržované vlastnost systému a poskytněte jedinečný identifikátor, který se používá jako kvalifikátor pro pozdější operace systému vlastnost. Tyto operace může být interní operace, nebo vlastní kód volání vlastnost systému [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]. Chcete-li zaregistrovat vlastnost, zavolejte <xref:System.Windows.DependencyProperty.Register%2A> metoda v rámci tělo třídě (uvnitř třídy, ale mimo všechny definice člen). Pole identifikátoru také poskytuje <xref:System.Windows.DependencyProperty.Register%2A> volání metody, jako návratová hodnota. Z důvodu, <xref:System.Windows.DependencyProperty.Register%2A> se provádí volání mimo jiné člen definice je použití této návratová hodnota pro přiřazení a vytváření `public` `static` `readonly` pole typu <xref:System.Windows.DependencyProperty> v rámci vaší třídy. V tomto poli se změní na identifikátor pro vaše vlastnost závislosti.  
  
 [!code-csharp[WPFAquariumSln#RegisterAG](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerag)]
 [!code-vb[WPFAquariumSln#RegisterAG](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerag)]  
  
<a name="nameconventions"></a>   
### <a name="dependency-property-name-conventions"></a>Konvence název vlastnosti závislosti  
 Existují zavedené zásady vytváření názvů týkající se vlastností závislostí, které je třeba provést ve všech ale výjimečných případech.  
  
 Samotné vlastnosti závislosti bude mít základní název, "AquariumGraphic" jako v tomto příkladu je zadána jako první parametr <xref:System.Windows.DependencyProperty.Register%2A>. Tento název musí být jedinečný v rámci každé registraci typu. Zděděná prostřednictvím základní typy vlastností závislostí se považují za již součást registrace typu; názvy zděděné vlastnosti nelze znovu zaregistrovat. Existuje však postup pro přidání třídy jako vlastník vlastnosti závislosti, i když tuto vlastnost závislosti není zděděna; Podrobnosti najdete v tématu [metadat vlastností závislostí](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md).  
  
 Při vytváření pole identifikátor názvů toto pole název vlastnosti as registrované plus přípona `Property`. Toto pole, je identifikátor pro vlastnost závislosti, a bude se používat novější jako vstup pro <xref:System.Windows.DependencyObject.SetValue%2A> a <xref:System.Windows.DependencyObject.GetValue%2A> volání, které provedete v obálky, všechny ostatní kód přístup pro vlastnost pomocí vlastního kódu, všechny externí kód přístup můžete povolit , vlastnosti systému a potenciálně tím [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] procesory.  
  
> [!NOTE]
>  Definování vlastnosti závislosti v těle třídy je typické implementace, ale je také možné definovat vlastnost závislosti v konstruktoru statické třídy. Tento přístup může být vhodné, pokud potřebujete více než jeden řádek kódu k chybě při inicializaci vlastnost závislosti.  
  
<a name="wrapper1"></a>   
### <a name="implementing-the-wrapper"></a>Implementace "Obálky"  
 Implementace obálku by měly volat <xref:System.Windows.DependencyObject.GetValue%2A> v `get` implementace a <xref:System.Windows.DependencyObject.SetValue%2A> v `set` implementace (původní volání registrace a pole zde se zobrazují příliš pro přehlednost).  
  
 Všechny kromě výjimečných případů vaší implementace obálku proveďte pouze <xref:System.Windows.DependencyObject.GetValue%2A> a <xref:System.Windows.DependencyObject.SetValue%2A> akce, v uvedeném pořadí. Důvodem je popsané v tématu [načítání XAML a vlastností závislostí](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md).  
  
 Všechny existující vlastnosti veřejné závislosti, které jsou dostupné na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] třídy pomocí tohoto jednoduchého obálku implementace modelu; je buď ze své podstaty chování systému vlastnost většinu složitosti fungování vlastností závislostí nebo implementují se prostřednictvím dalších konceptech, jako je převod nebo vlastnost změnit zpětná volání prostřednictvím metadat vlastností.  
  
 [!code-csharp[WPFAquariumSln#AGWithWrapper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
 [!code-vb[WPFAquariumSln#AGWithWrapper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]  
  
 Opakujte podle konvence, název vlastnosti obálku musí být stejný jako název vybrali a zadané jako první parametr <xref:System.Windows.DependencyProperty.Register%2A> volání, které registrované vlastnost. Pokud vaše vlastnost nedodrží konvence, to není zakázána nutně všechny možné používá, ale můžete narazit několik významné problémy:  
  
-   Některé aspekty styly a šablony nebude fungovat.  
  
-   Většina nástrojů a návrháři musíte spoléhat na zásady vytváření názvů k serializaci správně [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], nebo k poskytování pomoci návrháře prostředí na úrovni pro vlastnosti.  
  
-   Aktuální implementace [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] zavaděč zcela obchází obálky a spoléhá na zásady vytváření názvů při zpracování hodnot atributů. Další informace najdete v tématu [načítání XAML a vlastností závislostí](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md).  
  
<a name="metadata"></a>   
### <a name="property-metadata-for-a-new-dependency-property"></a>Vlastnost metadat pro novou vlastnost závislosti  
 Při registraci vlastnost závislosti registrace prostřednictvím systému vlastnost vytvoří objekt metadat, který ukládá vlastnost charakteristiky. Mnoho z těchto vlastností mají výchozí hodnoty, které jsou nastaveny, pokud vlastnost není zaregistrována jednoduché signatur <xref:System.Windows.DependencyProperty.Register%2A>. Další signatury <xref:System.Windows.DependencyProperty.Register%2A> umožňují určit metadata, která chcete při registraci vlastnost. Nejběžnější metadata pro vlastnosti závislosti zadané je jim poskytnout výchozí hodnotu, která se použije na nové instance, které používají vlastnost.  
  
 Pokud vytváříte vlastnosti závislost, která existuje v odvozené třídě z <xref:System.Windows.FrameworkElement>, můžete použít více specializované třídu metadat <xref:System.Windows.FrameworkPropertyMetadata> místo základní <xref:System.Windows.PropertyMetadata> třídy. V konstruktoru pro <xref:System.Windows.FrameworkPropertyMetadata> třída obsahuje několik podpisy, kde můžete určit různé vlastnosti metadat v kombinaci. Pokud chcete zadat jenom výchozí hodnotu, použijte podpisu, který přebírá jediný parametr typu <xref:System.Object>. Předejte parametr objekt jako hodnotu výchozí specifický pro vaše vlastnost (výchozí hodnota zadaná musí být typ zadaný jako `propertyType` parametr ve <xref:System.Windows.DependencyProperty.Register%2A> volání).  
  
 Pro <xref:System.Windows.FrameworkPropertyMetadata>, můžete také zadat příznaky možnost metadat pro váš vlastnost. Tyto příznaky se převedou na diskrétní vlastnosti metadata vlastnosti po registraci a se používají ke komunikaci určité podmíněné příkazy k jinými procesy, například modul rozložení.  
  
#### <a name="setting-appropriate-metadata-flags"></a>Nastavení příslušná Metadata příznaků  
  
-   Pokud vlastnost (nebo změny v jeho hodnota) má vliv [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)], a na konkrétní ovlivňuje způsob rozložení systému by měla velikost nebo vykreslení vaší element na stránce, nastavte jeden nebo více z následujících příznaků: <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure>, <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange>, <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender>.  
  
    -   <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsMeasure>Udává, že ke změně této vlastnosti vyžaduje změnu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vykreslování, kde objekt obsahující může vyžadovat více nebo méně místa v rámci nadřazené. Například vlastnost "Šířka" by měly mít tento příznak nastaven.  
  
    -   <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsArrange>Udává, že ke změně této vlastnosti vyžaduje změnu [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vykreslení, který obvykle nevyžaduje změnu vyhrazené místo, ale znamenat, že se změnila umístění v prostoru. Například ve vlastnosti "Zarovnání" by měly mít tento příznak nastaven.  
  
    -   <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsRender>Určuje, že některých dalších změn došlo, nebude mít vliv na rozložení a míru, ale nevyžaduje další vykreslení. Příkladem může být vlastnost, která změní barvu existujícího elementu, jako je například "Pozadí".  
  
    -   Tyto příznaky jsou často používá jako protokol v metadatech pro implementace vlastního přepsat vlastnost systém nebo rozložení zpětných volání. Například můžete mít <xref:System.Windows.DependencyObject.OnPropertyChanged%2A> zpětné volání, které bude volat <xref:System.Windows.UIElement.InvalidateArrange%2A> Pokud žádnou vlastnost instance sestavy změnu hodnota a má <xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A> jako `true` ve svých metadatech.  
  
-   Některé vlastnosti mohou ovlivnit charakteristiky vykreslování obsahující nadřazeného elementu, způsoby vedle změny v požadovaná velikost uvedených výše. Příkladem je <xref:System.Windows.Documents.Paragraph.MinOrphanLines%2A> vlastnost použít v modelu dokument toku, kde změny této vlastnosti můžete změnit celkové vykreslování toku dokumentu, který obsahuje odstavce. Použití <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentArrange> nebo <xref:System.Windows.FrameworkPropertyMetadataOptions.AffectsParentMeasure> k identifikaci případů podobně jako v vlastní vlastnosti.  
  
-   Ve výchozím nastavení podporují závislostí vlastnosti datové vazby. Datová vazba pro případy, můžete zakázat úmyslně neexistuje žádné realistické scénář pro datovou vazbu nebo výkonu v datové vazbě pro velký objekt rozpoznán jako problém.  
  
-   Ve výchozím nastavení, datové vazby <xref:System.Windows.Data.Binding.Mode%2A> pro výchozí nastavení vlastnosti závislost na <xref:System.Windows.Data.BindingMode.OneWay>. Můžete kdykoli změnit vazby být <xref:System.Windows.Data.BindingMode.TwoWay> na instanci vazby; podrobnosti najdete v části [určení směru vazby](../../../../docs/framework/wpf/data/how-to-specify-the-direction-of-the-binding.md). Jako autor vlastnost závislosti, můžete vytvořit vlastnost použít, ale <xref:System.Windows.Data.BindingMode.TwoWay> režimu vazby ve výchozím nastavení. Příklad existující vlastnost závislosti je <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A?displayProperty=nameWithType>; tento scénář pro tuto vlastnost je, že <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> nastavení logiku a skládání z <xref:System.Windows.Controls.MenuItem> interakci s výchozí styl motivu. <xref:System.Windows.Controls.MenuItem.IsSubmenuOpen%2A> Datová vazba vlastnost logiku nativně používá pro uchování stavu vlastnosti v souladu na jiné vlastnosti stavu a volání metod. Další příklad vlastnost, která sváže <xref:System.Windows.Data.BindingMode.TwoWay> ve výchozím nastavení je <xref:System.Windows.Controls.TextBox.Text%2A?displayProperty=nameWithType>.  
  
-   Můžete také povolit dědičnost vlastnosti v vlastnost vlastní závislosti nastavením <xref:System.Windows.FrameworkPropertyMetadataOptions.Inherits> příznak. Dědičnost vlastnosti je užitečné pro scénář, kde prvky nadřazené a podřízené elementy mají vlastnost společné, a má smysl pro podřízené elementy tak, aby měl tento konkrétní hodnota vlastnosti nastavena na stejnou hodnotu jako nadřazený ho nastavit. Ve vlastnosti zděditelné příklad je <xref:System.Windows.FrameworkElement.DataContext%2A>, který se používá pro operace povolující důležité scénář seznam podrobnosti pro prezentaci dat vazby. Tím, že <xref:System.Windows.FrameworkElement.DataContext%2A> zděditelné, všechny podřízené elementy dědění tohoto kontextu dat také. Z důvodu dědičnost hodnotu vlastnosti můžete určit kontext dat v kořenovém adresáři stránky nebo aplikace a není potřeba respecify pro vazby do ve všech možných podřízené elementy. <xref:System.Windows.FrameworkElement.DataContext%2A>je také dobrým příkladem pro ilustraci dědičnosti přepíše výchozí hodnotu, že ho může být vždy nastavená místně na žádné konkrétní podřízený element; Podrobnosti najdete v tématu [použití vzoru seznam-podrobnosti s hierarchické Data](../../../../docs/framework/wpf/data/how-to-use-the-master-detail-pattern-with-hierarchical-data.md). Dědičnost vlastnosti hodnota nemá možný výkon a proto měli šetřit; Podrobnosti najdete v tématu [dědičnost hodnotu vlastnosti](../../../../docs/framework/wpf/advanced/property-value-inheritance.md).  
  
-   Nastavte <xref:System.Windows.FrameworkPropertyMetadataOptions.Journal> příznak indikující, pokud by měla být zjištěna nebo v navigačním deníku služeb vaší vlastnost závislosti. Příkladem je <xref:System.Windows.Controls.Primitives.Selector.SelectedIndex%2A> vlastnost; jakékoli položky vybrané ve výběru ovládacího prvku by měl nastavit jako trvalý, když je navigaci historie deníku.  
  
<a name="RODP"></a>   
## <a name="read-only-dependency-properties"></a>Vlastnosti závislosti jen pro čtení  
 Můžete definovat závislosti vlastnosti, která je jen pro čtení. Scénáře pro proč můžete definovat vaše vlastnost jen pro čtení se ale poněkud liší, jako je postup pro registraci je vlastnost systému a vystavení identifikátor. Další informace najdete v tématu [jen pro čtení vlastností závislostí](../../../../docs/framework/wpf/advanced/read-only-dependency-properties.md).  
  
<a name="CTDP"></a>   
## <a name="collection-type-dependency-properties"></a>Vlastnosti závislostí typu kolekce  
 Typ kolekce závislost vlastnosti mají některé další implementace problémy vzít v úvahu. Podrobnosti najdete v tématu [typ kolekce vlastností závislostí](../../../../docs/framework/wpf/advanced/collection-type-dependency-properties.md).  
  
<a name="SecurityC"></a>   
## <a name="dependency-property-security-considerations"></a>Aspekty zabezpečení vlastnost závislosti  
 Vlastnosti závislosti měli deklarované jako veřejné vlastnosti. Pole identifikátoru vlastnosti závislosti by měl být deklarován jako veřejné statické pole. I když se pokusíte deklarovat jiné úrovně přístupu (například chráněné), vlastnost závislosti je vždy přístupná přes identifikátor v kombinaci s vlastností systému [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]. Z důvodu stanovení vytváření sestav, nebo hodnota metadat potenciálně přístupný i pole chráněné identifikátoru [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] které jsou součástí vlastnosti systému, jako například <xref:System.Windows.LocalValueEnumerator>. Další informace najdete v tématu [zabezpečení vlastnost závislosti](../../../../docs/framework/wpf/advanced/dependency-property-security.md).  
  
<a name="DPCtor"></a>   
## <a name="dependency-properties-and-class-constructors"></a>Vlastnosti závislosti a konstruktory – třída  
 Je zásadně ve spravovaném kódu programování (často vynucuje nástrojů pro analýzu kódu například FxCop), které třídy konstruktory by neměl volat virtuální metody. Je to proto může být konstruktory volána jako základní inicializace konstruktoru odvozené třídy a zadáním virtuální metody prostřednictvím konstruktoru může dojít ve stavu neúplná inicializace vytvářen instance objektu. Pokud odvozujete od všechny třídy, která již je odvozena z <xref:System.Windows.DependencyObject>, je třeba si uvědomit, že systém vlastnost samotné volá a zpřístupní virtuální metody interně. Tyto virtuální metody jsou součástí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vlastnost systémových služeb. Přepsání metody umožňuje odvozených tříd se účastnit hodnota rozhodnutí. Chcete-li předejít problémům s inicializace modulu runtime, by neměl nastavíte závislostí hodnoty vlastností v rámci konstruktory tříd, pokud podle vzoru velmi konkrétní konstruktor. Podrobnosti najdete v tématu [bezpečné konstruktor vzory pro DependencyObjects](../../../../docs/framework/wpf/advanced/safe-constructor-patterns-for-dependencyobjects.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled vlastností závislostí](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Metadata vlastnosti závislosti](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)  
 [Vytváření – Přehled ovládacího prvku](../../../../docs/framework/wpf/controls/control-authoring-overview.md)  
 [Typ kolekce vlastností závislostí](../../../../docs/framework/wpf/advanced/collection-type-dependency-properties.md)  
 [Závislost vlastnost zabezpečení](../../../../docs/framework/wpf/advanced/dependency-property-security.md)  
 [Načítání XAML a vlastností závislostí](../../../../docs/framework/wpf/advanced/xaml-loading-and-dependency-properties.md)  
 [Bezpečné konstruktor vzory pro DependencyObjects](../../../../docs/framework/wpf/advanced/safe-constructor-patterns-for-dependencyobjects.md)
