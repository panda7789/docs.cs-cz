---
title: Přehled základních elementů
ms.date: 03/30/2017
helpviewer_keywords:
- base elements [WPF]
ms.assetid: 2c997092-72c6-4767-bc84-74267f4eee72
ms.openlocfilehash: 0cd69a4d2d6087c1ebf93bb5931511f32a4c9c5f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110055"
---
# <a name="base-elements-overview"></a>Přehled základních elementů
Vysoké procento třídy v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] jsou odvozeny z čtyři třídy, které se běžně označují v [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)] dokumentaci jako základní prvek třídy. Tyto třídy jsou <xref:System.Windows.UIElement>, <xref:System.Windows.FrameworkElement>, <xref:System.Windows.ContentElement>, a <xref:System.Windows.FrameworkContentElement>. <xref:System.Windows.DependencyObject> Třídy se také vztahuje, protože je obecná základní třída obou <xref:System.Windows.UIElement> a <xref:System.Windows.ContentElement>  

<a name="base_apis"></a>   
## <a name="base-element-apis-in-wpf-classes"></a>Base Element rozhraní API ve třídách WPF  
 Obě <xref:System.Windows.UIElement> a <xref:System.Windows.ContentElement> jsou odvozeny z <xref:System.Windows.DependencyObject>, pomocí nich do jisté míry různé přístupy. Jak se zabývá rozděleného na této úrovni <xref:System.Windows.UIElement> nebo <xref:System.Windows.ContentElement> se používají v uživatelském rozhraní a co účel slouží v aplikaci. <xref:System.Windows.UIElement> má také <xref:System.Windows.Media.Visual> v její hierarchii tříd, což je třída, která poskytuje základní podpory nižší úrovně grafiky [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. <xref:System.Windows.Media.Visual> poskytuje rozhraní vykreslování definováním oblasti obdélníkový nezávislé obrazovky. V praxi <xref:System.Windows.UIElement> je pro prvky, které budou podporovat větší objektový model, jsou určené k vykreslení a rozložení do oblastí, které lze popsat jako oblasti obdélníkový obrazovky a kde obsahový model je záměrně otevřenější, aby jiný kombinace prvků. <xref:System.Windows.ContentElement> není odvozen od <xref:System.Windows.Media.Visual>; svůj model, který je <xref:System.Windows.ContentElement> by být využívány službou něco jiného, jako je Čtenář nebo prohlížeče, který by pak interpretovat elementy a vytvářet kompletní <xref:System.Windows.Media.Visual> pro [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] využívat. Některé <xref:System.Windows.UIElement> třídy mají být obsahu hostitelů: poskytují hostování a vykreslování pro jeden nebo více <xref:System.Windows.ContentElement> třídy (<xref:System.Windows.Controls.DocumentViewer> je příkladem takové třídy). <xref:System.Windows.ContentElement> slouží jako základní třídu pro prvky se o něco menší objektové modely a více adres textové informace, nebo dokument obsah, který může být hostovaná v rámci <xref:System.Windows.UIElement>.  
  
### <a name="framework-level-and-core-level"></a>Základní úrovni a úrovni architektury  
 <xref:System.Windows.UIElement> slouží jako základní třída pro <xref:System.Windows.FrameworkElement>, a <xref:System.Windows.ContentElement> slouží jako základní třída pro <xref:System.Windows.FrameworkContentElement>. Důvod pro tuto další úroveň třídy je podpora úroveň core WPF, která je oddělená od úrovně rozhraní WPF, se můžeme také existující ve způsobu [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] dělí mezi PresentationCore a PresentationFramework sestavení. Úroveň rozhraní WPF nabízí kompletní řešení pro potřeby základní aplikaci, včetně implementace Správce rozložení pro prezentaci. Základní úroveň WPF poskytuje způsob, jak používat většinu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bez nutnosti přepínat režijní náklady na další sestavení. Rozdíl mezi těmito úrovně velmi zřídka otázky pro nejčastější scénáře vývoje aplikací a obecně byste uvažovat o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] jako celek a netýkají sami rozdíl mezi úrovní rozhraní WPF a WPF základní úroveň. Můžete potřebovat vědět o úrovni rozdíly, pokud se rozhodne návrhu aplikace k nahrazení značné množství funkční úroveň rozhraní WPF, například pokud vaše celkové řešení již má své vlastní implementace [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] složení a rozložení.  
  
<a name="subclassing_elements"></a>   
## <a name="choosing-which-element-to-derive-from"></a>Které – Element pro odvození z výběru  
 Nejvhodnější způsob, jak vytvořit vlastní třídu, která rozšiřuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] je po odvození některého ze [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] třídy, kde můžete získat co nejvíc vaše požadované funkce do existující hierarchie třídy. V této části jsou uvedeny funkce, která se dodává s třemi vám pomohou rozhodnout, které třídy dědit z nejdůležitější element třídy.  
  
 Při implementaci ovládacího prvku, který je ve skutečnosti, jedna pro odvození z běžných příčin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] třídy, budete pravděpodobně chtít jsou odvozeny z třídy, která je praktické ovládací prvek, ovládací prvek řady základní třídy nebo v nejméně z <xref:System.Windows.Controls.Control> základní třídy. Některé pokyny a praktické příklady najdete v tématu [Přehled vytváření ovládacího prvku](../controls/control-authoring-overview.md).  
  
 Pokud nejsou vytvoření ovládacího prvku a musí být odvozen od třídy, která je v hierarchii, v dalších částech slouží jako vodítko pro vlastnosti, které jsou definovány v každé třídě base element.  
  
 Pokud vytvoříte třídu, která je odvozena z <xref:System.Windows.DependencyObject>, abyste dědili následující funkce:  
  
-   <xref:System.Windows.DependencyObject.GetValue%2A> a <xref:System.Windows.DependencyObject.SetValue%2A> podporu a podporu systému obecné vlastnosti.  
  
-   Možnost používat vlastnosti závislosti a připojené vlastnosti, které jsou implementovány jako vlastnosti závislosti.  
  
 Pokud vytvoříte třídu, která je odvozena z <xref:System.Windows.UIElement>, abyste dědili kromě toho poskytuje následující funkce <xref:System.Windows.DependencyObject>:  
  
-   Podpora pro hodnoty animované vlastnosti na úrovni Basic. Další informace najdete v tématu [přehled animace](../graphics-multimedia/animation-overview.md).  
  
-   Základní událost vstupu podporu a podporu řídicího. Další informace najdete v tématu [vstup přehled](input-overview.md) a [přehled příkazů](commanding-overview.md).  
  
-   Virtuální metody, které mohou být potlačena za účelem obsahují informace, které systém rozložení.  
  
 Pokud vytvoříte třídu, která je odvozena z <xref:System.Windows.FrameworkElement>, abyste dědili kromě toho poskytuje následující funkce <xref:System.Windows.UIElement>:  
  
-   Podpora pro používání stylů pro prvky a scénáři. Další informace najdete v tématu <xref:System.Windows.Style> a [přehled scénářů](../graphics-multimedia/storyboards-overview.md).  
  
-   Podpora pro vytváření datových vazeb. Další informace najdete v tématu [přehled datových vazeb](../data/data-binding-overview.md).  
  
-   Podpora pro dynamický prostředek odkazy. Další informace najdete v tématu [prostředky XAML](xaml-resources.md).  
  
-   Podpora dědičnosti hodnotu vlastnosti a další příznaky v metadatech, které pomáhají podmínky sestavy o vlastnostech framework služeb, jako je vytváření datových vazeb, styly nebo rozložení při implementaci rozhraní. Další informace najdete v tématu [Metadata vlastnosti architektury](framework-property-metadata.md).  
  
-   Konceptu logického stromu. Další informace najdete v tématu [stromy v subsystému WPF](trees-in-wpf.md).  
  
-   Podpora pro praktické implementace úrovni rozhraní WPF rozložení systému, včetně <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> přepsání, které může zjistit změny vlastností rozložení tohoto vliv.  
  
 Pokud vytvoříte třídu, která je odvozena z <xref:System.Windows.ContentElement>, abyste dědili kromě toho poskytuje následující funkce <xref:System.Windows.DependencyObject>:  
  
-   Podpora pro animace. Další informace najdete v tématu [přehled animace](../graphics-multimedia/animation-overview.md).  
  
-   Základní událost vstupu podporu a podporu řídicího. Další informace najdete v tématu [vstup přehled](input-overview.md) a [přehled příkazů](commanding-overview.md).  
  
 Pokud vytvoříte třídu, která je odvozena z <xref:System.Windows.FrameworkContentElement>, získáte následující funkce kromě toho poskytuje <xref:System.Windows.ContentElement>:  
  
-   Podpora pro používání stylů pro prvky a scénáři. Další informace najdete v tématu <xref:System.Windows.Style> a [přehled animace](../graphics-multimedia/animation-overview.md).  
  
-   Podpora pro vytváření datových vazeb. Další informace najdete v tématu [přehled datových vazeb](../data/data-binding-overview.md).  
  
-   Podpora pro dynamický prostředek odkazy. Další informace najdete v tématu [prostředky XAML](xaml-resources.md).  
  
-   Podpora dědičnosti hodnotu vlastnosti a další příznaky v metadatech, které pomáhají podmínky sestavy o vlastnostech framework služeb, jako je vytváření datových vazeb, styly nebo rozložení při implementaci rozhraní. Další informace najdete v tématu [Metadata vlastnosti architektury](framework-property-metadata.md).  
  
-   Nedědit přístup pro úpravy rozložení systému (například <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>). Implementace systému rozložení dostupné jen na <xref:System.Windows.FrameworkElement>. Nicméně, abyste dědili <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> přepsání, které může zjistit změny vlastností, které ovlivňují rozložení a nahlaste je na všechny hostitele obsahu.  
  
 Modely obsahu jsou popsány pro různé třídy. Model obsahu pro třídu je jediný faktor možná byste měli zvážit, pokud chcete najít odpovídající třídu odvodit z. Další informace najdete v tématu [Model obsahu WPF](../controls/wpf-content-model.md).  
  
<a name="other_base_classes"></a>   
## <a name="other-base-classes"></a>Další základní třídy  
  
### <a name="dispatcherobject"></a>Dispatcherobject –  
 <xref:System.Windows.Threading.DispatcherObject> poskytuje podporu pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dělení na vlákna modelu a umožňuje všechny objekty vytvořené pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace má být spojen s <xref:System.Windows.Threading.Dispatcher>. I v případě, že není odvozen od <xref:System.Windows.UIElement>, <xref:System.Windows.DependencyObject>, nebo <xref:System.Windows.Media.Visual>, měli byste zvážit odvozený od <xref:System.Windows.Threading.DispatcherObject> zajistí tato podpora vláken modelu. Další informace najdete v tématu [Model vláken](threading-model.md).  
  
### <a name="visual"></a>Vizuál  
 <xref:System.Windows.Media.Visual> implementuje koncept 2D objekt, který obvykle vyžaduje vizuální prezentace v přibližně obdélníková oblast. Skutečné vykreslování <xref:System.Windows.Media.Visual> dochází v jiných třídách (není samostatná), ale <xref:System.Windows.Media.Visual> třída poskytuje známý typ, který se používá vykreslování procesy na různých úrovních. <xref:System.Windows.Media.Visual> implementuje testování průchodu, ale nezpřístupňuje události, které podléhají pozitivní výsledky spuštění testu (jsou v <xref:System.Windows.UIElement>). Další informace najdete v tématu [programování vizuální vrstvy](../graphics-multimedia/visual-layer-programming.md).  
  
### <a name="freezable"></a>Freezable  
 <xref:System.Windows.Freezable> simuluje neměnnosti v měnitelný objekt tím, že poskytuje způsob, jak generovat kopií objektu při neměnné objektu je vyžaduje nebo požadovaných z důvodů výkonu. <xref:System.Windows.Freezable> Typ poskytuje společný základ pro některé grafické prvky, jako je například geometrie a štětce, jakož i animace. Zejména <xref:System.Windows.Freezable> není <xref:System.Windows.Media.Visual>; může obsahovat vlastnosti, které se stanou objektu třídy subproperties při <xref:System.Windows.Freezable> se použije k vyplnění hodnotu vlastnosti jiného objektu, a tyto objektu třídy subproperties může mít vliv na vykreslování. Další informace najdete v tématu [přehled Zablokovatelných objektů](freezable-objects-overview.md).  
  
 <xref:System.Windows.Media.Animation.Animatable>  
  
 <xref:System.Windows.Media.Animation.Animatable> je <xref:System.Windows.Freezable> odvozené třídy, která konkrétně přidává vrstvu ovládacího prvku animace a některé členy nástroj tak, aby se dají rozlišovat aktuálně animované vlastnosti z nonanimated vlastností.  
  
### <a name="control"></a>Control  
 <xref:System.Windows.Controls.Control> je základní třídy určené pro typ objektu, který se nazývá různě ovládacího prvku nebo komponenty, v závislosti na technologie. Obecně platí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] třídy ovládacích prvků jsou třídy, které přímo představují ovládacího prvku uživatelského rozhraní nebo úzce součástí kompozice ovládacích prvků. Primární funkce, která <xref:System.Windows.Controls.Control> umožňuje je ukázka ovládacího prvku.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.Control>
- [Přehled vlastností závislosti](dependency-properties-overview.md)
- [Přehled řízeného vytváření](../controls/control-authoring-overview.md)
- [Architektura WPF](wpf-architecture.md)
