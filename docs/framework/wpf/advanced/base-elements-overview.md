---
title: Přehled základních elementů
ms.date: 03/30/2017
helpviewer_keywords:
- base elements [WPF]
ms.assetid: 2c997092-72c6-4767-bc84-74267f4eee72
ms.openlocfilehash: bcfcb87d0ddf5181a47d459e821bacd9b9f6b61c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="base-elements-overview"></a>Přehled základních elementů
Vysoké procento třídy v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] jsou odvozeny od čtyři třídy, které se běžně označují v [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)] dokumentace jako element základní třídy. Tyto třídy jsou <xref:System.Windows.UIElement>, <xref:System.Windows.FrameworkElement>, <xref:System.Windows.ContentElement>, a <xref:System.Windows.FrameworkContentElement>. <xref:System.Windows.DependencyObject> Třída rovněž souvisí, protože je obecná základní třída i <xref:System.Windows.UIElement> a <xref:System.Windows.ContentElement>  
 
  
<a name="base_apis"></a>   
## <a name="base-element-apis-in-wpf-classes"></a>Base Element rozhraní API v třídy grafického subsystému WPF  
 Obě <xref:System.Windows.UIElement> a <xref:System.Windows.ContentElement> jsou odvozeny od <xref:System.Windows.DependencyObject>, prostřednictvím poněkud různých způsobů. Rozdělení na této úrovni, na které se zabývá postupy <xref:System.Windows.UIElement> nebo <xref:System.Windows.ContentElement> se používají v uživatelském rozhraní a co účel slouží v aplikaci. <xref:System.Windows.UIElement> má také <xref:System.Windows.Media.Visual> v hierarchii třídy, což je třída, která zveřejňuje, základní podpora nižší úrovně grafiky [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. <xref:System.Windows.Media.Visual> poskytuje rozhraní vykreslování definováním oblasti nezávislé obdélníková obrazovky. V praxi <xref:System.Windows.UIElement> je pro elementy, které budou podporovat větší objektový model, jsou určené k vykreslení a rozložení do oblasti, která lze popsat jako oblasti obdélníková obrazovky a kde je úmyslně více otevřený, a povolit jiný model obsahu kombinace elementů. <xref:System.Windows.ContentElement> není odvozena od <xref:System.Windows.Media.Visual>; svůj model je, že <xref:System.Windows.ContentElement> by být využívány službou něco jiného, například čtečky nebo prohlížeče, která by pak interpretovat elementy a vytvoří kompletní <xref:System.Windows.Media.Visual> pro [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] využívat. Některé <xref:System.Windows.UIElement> třídy by měla být obsahu hostitelů: poskytují hostování a vykreslování pro jeden nebo více <xref:System.Windows.ContentElement> třídy (<xref:System.Windows.Controls.DocumentViewer> je příklad této třídy). <xref:System.Windows.ContentElement> slouží jako základní třída pro prvky s něco menší objektové modely a že více adresy text, informace, nebo obsahu dokumentu, který může být hostovaným v rámci <xref:System.Windows.UIElement>.  
  
### <a name="framework-level-and-core-level"></a>Úroveň Framework a jader  
 <xref:System.Windows.UIElement> slouží jako základní třída pro <xref:System.Windows.FrameworkElement>, a <xref:System.Windows.ContentElement> slouží jako základní třída pro <xref:System.Windows.FrameworkContentElement>. Z důvodu pro tuto další úroveň třídy se na podporu úrovně WPF jádra, která je oddělená od úrovní framework WPF s Tento oddíl také existující v tom, jak [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] dělí mezi PresentationCore a PresentationFramework sestavení. Úroveň framework WPF uvede víc kompletního řešení pro základní aplikaci, včetně implementace Správce rozložení pro prezentaci. Základní úroveň WPF poskytuje způsob, jak používat většinu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bez nutnosti převádět nároky na další sestavení. Rozdíl mezi tyto úrovně velmi zřídka záleží pro některé běžné scénáře vývoj aplikací a obecně by měl úvahách o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] jako celek a není sami se týkají s rozdíl mezi úroveň framework WPF a WPF základní úrovni. Potřebujete vědět o úrovni rozdíly, pokud se rozhodne návrhu aplikace nahradit významné množství WPF framework úrovně funkčnosti, například pokud celkového řešení již má své vlastní implementace [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] složení a rozložení.  
  
<a name="subclassing_elements"></a>   
## <a name="choosing-which-element-to-derive-from"></a>Výběr který Element k odvozování z  
 Nejvhodnější způsob, jak vytvořit vlastní třídu, která rozšiřuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je odvození některého ze [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] třídy, kde můžete získat co nejvíce z vaší požadované funkce prostřednictvím existující třídy hierarchie. Tato část uvádí funkci, která se dodává s třemi nejdůležitější třídy element vám pomohou rozhodnout, které třídy dědí.  
  
 Při implementaci ovládacího prvku který je ve skutečnosti, jeden z běžných příčin pro odvozování z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] třída, budete pravděpodobně chtít odvozena ze třídy, která je praktické ovládací prvek, řízení rodiny základní třídu nebo v minimálně z <xref:System.Windows.Controls.Control> základní třídy. Některé pokyny a příklady praktické najdete v tématu [vytváření – Přehled ovládacího prvku](../../../../docs/framework/wpf/controls/control-authoring-overview.md).  
  
 Pokud nejsou vytvoření ovládacího prvku a musí být odvozen od třídy, který je v hierarchii, v následujících částech jsou určeny jako vodítko, pro jaké vlastnosti jsou definovány v každé třídě base element.  
  
 Pokud vytvoříte třídu odvozenou z <xref:System.Windows.DependencyObject>, dědí následující funkce:  
  
-   <xref:System.Windows.DependencyObject.GetValue%2A> a <xref:System.Windows.DependencyObject.SetValue%2A> podporu a podporu systému obecné vlastnosti.  
  
-   Možnost používat vlastností závislostí a přidružené vlastnosti, které jsou implementovány jako vlastnosti závislosti.  
  
 Pokud vytvoříte třídu odvozenou z <xref:System.Windows.UIElement>, dědí k těm, které poskytuje následující funkce <xref:System.Windows.DependencyObject>:  
  
-   Základní podpora hodnoty animovaný vlastností. Další informace najdete v tématu [animace přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
-   Základní vstupní událost podporu a řídicího podporu. Další informace najdete v tématu [vstup přehled](../../../../docs/framework/wpf/advanced/input-overview.md) a [tvorba příkazů přehled](../../../../docs/framework/wpf/advanced/commanding-overview.md).  
  
-   Virtuální metody, které může být potlačena za účelem zadejte informace k systému rozložení.  
  
 Pokud vytvoříte třídu odvozenou z <xref:System.Windows.FrameworkElement>, dědí k těm, které poskytuje následující funkce <xref:System.Windows.UIElement>:  
  
-   Podpora stylů a scénářů. Další informace najdete v tématu <xref:System.Windows.Style> a [přehled scénářů](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md).  
  
-   Podpora pro datovou vazbu. Další informace najdete v tématu [přehled vazby dat](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
-   Podpora dynamického prostředku odkazy. Další informace najdete v tématu [XAML prostředky](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
-   Podpora dědičnosti hodnotu vlastnosti a další příznaky v metadatech, které pomáhají podmínky sestavy o vlastnostech Services framework například datové vazby, styly nebo implementace rozhraní framework rozložení. Další informace najdete v tématu [metadat vlastností Framework](../../../../docs/framework/wpf/advanced/framework-property-metadata.md).  
  
-   Koncept logickém stromu. Další informace najdete v tématu [stromy v grafickém subsystému WPF](../../../../docs/framework/wpf/advanced/trees-in-wpf.md).  
  
-   Podpora pro praktické implementace úrovni rozhraní WPF rozložení systému, včetně <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> přepsání, které může zjistit změny vlastnosti tohoto rozložení vliv.  
  
 Pokud vytvoříte třídu odvozenou z <xref:System.Windows.ContentElement>, dědí k těm, které poskytuje následující funkce <xref:System.Windows.DependencyObject>:  
  
-   Podpora pro animace. Další informace najdete v tématu [animace přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
-   Základní vstupní událost podporu a řídicího podporu. Další informace najdete v tématu [vstup přehled](../../../../docs/framework/wpf/advanced/input-overview.md) a [tvorba příkazů přehled](../../../../docs/framework/wpf/advanced/commanding-overview.md).  
  
 Pokud vytvoříte třídu odvozenou z <xref:System.Windows.FrameworkContentElement>, dojde k těm, které poskytuje následující funkce <xref:System.Windows.ContentElement>:  
  
-   Podpora stylů a scénářů. Další informace najdete v tématu <xref:System.Windows.Style> a [animace přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
-   Podpora pro datovou vazbu. Další informace najdete v tématu [přehled vazby dat](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
-   Podpora dynamického prostředku odkazy. Další informace najdete v tématu [XAML prostředky](../../../../docs/framework/wpf/advanced/xaml-resources.md).  
  
-   Podpora dědičnosti hodnotu vlastnosti a další příznaky v metadatech, které pomáhají podmínky sestavy o vlastnostech framework služeb, třeba vazby dat, styly nebo implementace rozhraní framework rozložení. Další informace najdete v tématu [metadat vlastností Framework](../../../../docs/framework/wpf/advanced/framework-property-metadata.md).  
  
-   Nedědí přístup k rozložení systému úpravy (například <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>). Implementace systému rozložení jsou dostupné jenom na <xref:System.Windows.FrameworkElement>. Ale dědění <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> přepsání, které může zjistit změny vlastností, které ovlivňují rozložení a zobrazit zprávu do všech hostitelích, u obsahu.  
  
 Obsahu modely jsou popsané pro různé třídy. Model obsahu pro třídu je jediný faktor možná byste měli zvážit, pokud chcete najít odpovídající třídu k odvozování z. Další informace najdete v tématu [modelu obsahu WPF](../../../../docs/framework/wpf/controls/wpf-content-model.md).  
  
<a name="other_base_classes"></a>   
## <a name="other-base-classes"></a>Ostatní třídy Base  
  
### <a name="dispatcherobject"></a>DispatcherObject  
 <xref:System.Windows.Threading.DispatcherObject> poskytuje podporu pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dělení na vlákna model a umožňuje všechny objekty vytvářené pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace má být spojen s <xref:System.Windows.Threading.Dispatcher>. I když není odvozena od <xref:System.Windows.UIElement>, <xref:System.Windows.DependencyObject>, nebo <xref:System.Windows.Media.Visual>, měli byste zvážit odvozování z <xref:System.Windows.Threading.DispatcherObject> zajistí, že tato podpora vláken modelu. Další informace najdete v tématu [Model podprocesů](../../../../docs/framework/wpf/advanced/threading-model.md).  
  
### <a name="visual"></a>Visual  
 <xref:System.Windows.Media.Visual> implementuje koncept 2D objekt, který obvykle vyžaduje vizuální prezentaci v zhruba obdélníkovou oblast. Skutečné vykreslování <xref:System.Windows.Media.Visual> probíhá jiné třídy (není úplný a samostatný), ale <xref:System.Windows.Media.Visual> třída poskytuje známému typu, který se používá vykreslování procesy na různých úrovních. <xref:System.Windows.Media.Visual> testování průchodu implementuje, ale nevystavuje události, které sestav přístupů k testování přijetí (jedná se v <xref:System.Windows.UIElement>). Další informace najdete v tématu [programování Visual vrstvy](../../../../docs/framework/wpf/graphics-multimedia/visual-layer-programming.md).  
  
### <a name="freezable"></a>Zablokovatelné  
 <xref:System.Windows.Freezable> tím, že poskytuje způsob, jak vygenerovat kopie objektu, když je objekt neměnné požadované nebo požadovaných z důvodů výkonu simuluje neměnitelnosti v měnitelný objekt. <xref:System.Windows.Freezable> Typ poskytuje společný základ pro některé grafické prvky, jako jsou například geometrie a štětce, jakož i animace. Zejména <xref:System.Windows.Freezable> není <xref:System.Windows.Media.Visual>; může uchovávat vlastnosti, které se stanou podvlastnosti při <xref:System.Windows.Freezable> je použita k vyplnění hodnotu vlastnosti jiného objektu, a tyto podvlastnosti mohou ovlivnit vykreslování. Další informace najdete v tématu [zmrazitelné objekty – přehled](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
 <xref:System.Windows.Media.Animation.Animatable>  
  
 <xref:System.Windows.Media.Animation.Animatable> je <xref:System.Windows.Freezable> odvozené třídy, která konkrétně přidává vrstvu ovládacího prvku animace a některé členy nástroj tak, aby se dají rozlišovat aktuálně animovaný vlastnosti z nonanimated vlastností.  
  
### <a name="control"></a>Ovládací prvek  
 <xref:System.Windows.Controls.Control> je určený základní třídu pro typ objektu, který se říká různě na ovládací prvek nebo součást, v závislosti na technologie. Obecně platí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] – třídy ovládacích prvků jsou třídy, které buď přímo, představují ovládacího prvku uživatelského rozhraní nebo úzce účastnit řízení složení. Primární funkce který <xref:System.Windows.Controls.Control> umožňuje je ukázka ovládacího prvku.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.Control>  
 [Přehled vlastností závislosti](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Přehled vytváření ovládacích prvků](../../../../docs/framework/wpf/controls/control-authoring-overview.md)  
 [Architektura WPF](../../../../docs/framework/wpf/advanced/wpf-architecture.md)
