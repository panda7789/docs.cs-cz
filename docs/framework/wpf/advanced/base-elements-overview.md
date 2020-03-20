---
title: Přehled základních elementů
ms.date: 03/30/2017
helpviewer_keywords:
- base elements [WPF]
ms.assetid: 2c997092-72c6-4767-bc84-74267f4eee72
ms.openlocfilehash: 7d52d951d4fa4df83bbcca6b4cb479e18e532d2a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141625"
---
# <a name="base-elements-overview"></a>Přehled základních elementů
Vysoké procento tříd [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] v jsou odvozeny ze čtyř tříd, které jsou běžně označovány v dokumentaci sady SDK jako třídy základní prvek. Tyto třídy <xref:System.Windows.FrameworkElement> <xref:System.Windows.ContentElement>jsou <xref:System.Windows.UIElement> <xref:System.Windows.FrameworkContentElement>, , , a . Třída <xref:System.Windows.DependencyObject> je také související, protože se jedná <xref:System.Windows.UIElement> o společnou základní třídu obou<xref:System.Windows.ContentElement>  

<a name="base_apis"></a>
## <a name="base-element-apis-in-wpf-classes"></a>Rozhraní API základního prvku ve třídách WPF  
 Oba <xref:System.Windows.UIElement> <xref:System.Windows.ContentElement> a jsou <xref:System.Windows.DependencyObject>odvozeny z , prostřednictvím poněkud odlišných cest. Rozdělení na této úrovni se <xref:System.Windows.UIElement> <xref:System.Windows.ContentElement> zabývá tím, jak nebo jsou používány v uživatelském rozhraní a k jakému účelu slouží v aplikaci. <xref:System.Windows.UIElement>má <xref:System.Windows.Media.Visual> také ve své hierarchii třídy, což je třída, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]která zveřejňuje podporu grafiky nižší úrovně, která je základem . <xref:System.Windows.Media.Visual>poskytuje rozhraní vykreslování definováním nezávislých obdélníkových oblastí obrazovky. V praxi <xref:System.Windows.UIElement> je pro prvky, které budou podporovat větší objektový model, jsou určeny k vykreslení a rozložení do oblastí, které lze popsat jako obdélníkové oblasti obrazovky a kde je model obsahu záměrně otevřenější, aby různé kombinace prvků. <xref:System.Windows.ContentElement>nepochází z <xref:System.Windows.Media.Visual>; jeho model je, že <xref:System.Windows.ContentElement> by být spotřebovány něco jiného, jako je například čtenář nebo prohlížeč, který by pak interpretovat prvky a vyrábět kompletní <xref:System.Windows.Media.Visual> pro [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] konzumovat. Některé <xref:System.Windows.UIElement> třídy jsou určeny jako hostitelé obsahu: poskytují <xref:System.Windows.ContentElement> hostování<xref:System.Windows.Controls.DocumentViewer> a vykreslování pro jednu nebo více tříd (je příkladem takové třídy). <xref:System.Windows.ContentElement>se používá jako základní třída pro prvky s poněkud menšími objektovými modely a který více <xref:System.Windows.UIElement>řeší text, informace nebo obsah dokumentu, který může být hostován v rámci .  
  
### <a name="framework-level-and-core-level"></a>Úroveň rámce a základní úroveň  
 <xref:System.Windows.UIElement>slouží jako základní <xref:System.Windows.FrameworkElement>třída <xref:System.Windows.ContentElement> pro , a <xref:System.Windows.FrameworkContentElement>slouží jako základní třída pro . Důvodem pro tuto další úroveň tříd je podpora wpf základní úroveň, která je oddělena od úrovně architektury WPF, s toto rozdělení také existující v tom, jak jsou rozhraní API rozdělena mezi PresentationCore a PresentationFramework sestavení. Úroveň architektury WPF představuje úplnější řešení pro základní potřeby aplikací, včetně implementace správce rozložení pro prezentaci. WPF základní úroveň poskytuje způsob, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jak používat velkou část bez převzetí režie další sestavení. Rozdíl mezi těmito úrovněmi velmi zřídka záleží pro nejtypičtější scénáře [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vývoje aplikací a obecně byste měli myslet na rozhraní API jako celek a netýkají se sami s rozdílem mezi wpf úroveň architektury a WPF základní úrovni. Možná budete potřebovat vědět o úrovni rozdíly, pokud návrh aplikace se rozhodne nahradit značné množství wpf framework úrovni funkce, například pokud vaše celkové řešení již má své vlastní implementace [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] složení a rozložení.  
  
<a name="subclassing_elements"></a>
## <a name="choosing-which-element-to-derive-from"></a>Výběr prvku, ze kterého má být odvozen  
 Nejpraktičtější způsob, jak vytvořit vlastní [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] třídu, která se rozšiřuje, je odvození mj. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] V této části jsou uvedeny funkce, které jsou součástí tří nejdůležitějších tříd prvků, které vám pomohou rozhodnout, ze které třídy chcete dědit.  
  
 Pokud implementujete ovládací prvek, který je skutečně jedním z nejběžnějších [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] důvodů pro odvození z třídy, pravděpodobně budete chtít odvodit z <xref:System.Windows.Controls.Control> třídy, která je praktickým ovládacím prvkem, základní třídou rodiny ovládacích prvku nebo alespoň ze základní třídy. Některé pokyny a praktické příklady naleznete [v tématu Přehled vytváření ovládacích prvku](../controls/control-authoring-overview.md).  
  
 Pokud nevytváříte ovládací prvek a potřebujete odvodit z třídy, která je vyšší v hierarchii, jsou následující části určeny jako vodítko pro jaké vlastnosti jsou definovány v každé třídě základního prvku.  
  
 Pokud vytvoříte třídu, <xref:System.Windows.DependencyObject>která je odvozena z , zdědíte následující funkce:  
  
- <xref:System.Windows.DependencyObject.GetValue%2A>a <xref:System.Windows.DependencyObject.SetValue%2A> podporu a obecnou podporu majetkového systému.  
  
- Možnost používat vlastnosti závislostí a připojené vlastnosti, které jsou implementovány jako vlastnosti závislostí.  
  
 Pokud vytvoříte třídu, <xref:System.Windows.UIElement>která je odvozena z , zdědíte kromě funkcí poskytovaných <xref:System.Windows.DependencyObject>:  
  
- Základní podpora hodnot animovaných vlastností. Další informace naleznete v [tématu Přehled animace](../graphics-multimedia/animation-overview.md).  
  
- Základní podpora vstupních událostí a podpora velení. Další informace naleznete [v tématech Přehled vstupů](input-overview.md) a [Přehled příkazů](commanding-overview.md).  
  
- Virtuální metody, které mohou být přepsány poskytnout informace do systému rozložení.  
  
 Pokud vytvoříte třídu, <xref:System.Windows.FrameworkElement>která je odvozena z , zdědíte kromě funkcí poskytovaných <xref:System.Windows.UIElement>:  
  
- Podpora pro styling a scénáře. Další informace naleznete <xref:System.Windows.Style> v tématu přehled [scénářů](../graphics-multimedia/storyboards-overview.md).  
  
- Podpora datové vazby. Další informace naleznete v [tématu Přehled datových vazeb](../data/data-binding-overview.md).  
  
- Podpora pro dynamické odkazy na prostředky. Další informace naleznete v tématu [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
- Podpora dědičnosti hodnoty vlastnosti a další příznaky v metadatech, které pomáhají sestavy podmínky o vlastnostech pro rámcové služby, jako je například datové vazby, styly nebo rozhraní implementace rozložení. Další informace naleznete v [tématu Metadata vlastností rozhraní framework](framework-property-metadata.md).  
  
- Koncept logického stromu. Další informace naleznete [v tématu Stromy v WPF](trees-in-wpf.md).  
  
- Podpora pro praktickou implementaci systému rozložení na úrovni <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> architektury WPF, včetně přepsání, které dokáže rozpoznat změny vlastností, které ovlivňují rozložení.  
  
 Pokud vytvoříte třídu, <xref:System.Windows.ContentElement>která je odvozena z , zdědíte kromě funkcí poskytovaných <xref:System.Windows.DependencyObject>:  
  
- Podpora pro animace. Další informace naleznete v [tématu Přehled animace](../graphics-multimedia/animation-overview.md).  
  
- Základní podpora vstupních událostí a podpora velení. Další informace naleznete [v tématech Přehled vstupů](input-overview.md) a [Přehled příkazů](commanding-overview.md).  
  
 Pokud vytvoříte třídu, <xref:System.Windows.FrameworkContentElement>která je odvozena z , získáte následující <xref:System.Windows.ContentElement>funkce kromě funkce poskytované :  
  
- Podpora pro styling a scénáře. Další informace naleznete <xref:System.Windows.Style> v tématech a [přehled animací](../graphics-multimedia/animation-overview.md).  
  
- Podpora datové vazby. Další informace naleznete v [tématu Přehled datových vazeb](../data/data-binding-overview.md).  
  
- Podpora pro dynamické odkazy na prostředky. Další informace naleznete v tématu [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
- Podpora dědičnosti hodnoty vlastnosti a další příznaky v metadatech, které pomáhají sestavy podmínky o vlastnostech pro rámcové služby, jako je datová vazba, styly nebo rozhraní implementace rozložení. Další informace naleznete v [tématu Metadata vlastností rozhraní framework](framework-property-metadata.md).  
  
- Nedědíte přístup ke změnám systému rozložení (například). <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> Implementace systému rozložení jsou <xref:System.Windows.FrameworkElement>k dispozici pouze na . Zdědíte <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> však přepsání, které dokáže rozpoznat změny vlastností, které ovlivňují rozložení, a hlásit je všem hostitelům obsahu.  
  
 Modely obsahu jsou dokumentovány pro různé třídy. Model obsahu pro třídu je jedním z možných faktorů, které byste měli zvážit, pokud chcete najít vhodnou třídu, ze které chcete odvodit. Další informace naleznete v [tématu WPF Content Model](../controls/wpf-content-model.md).  
  
<a name="other_base_classes"></a>
## <a name="other-base-classes"></a>Ostatní základní třídy  
  
### <a name="dispatcherobject"></a>Dispatcherobject  
 <xref:System.Windows.Threading.DispatcherObject>poskytuje podporu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] modelu zřetězení a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] umožňuje všechny objekty <xref:System.Windows.Threading.Dispatcher>vytvořené pro aplikace, které mají být přidruženy k . I v případě, <xref:System.Windows.UIElement>že <xref:System.Windows.DependencyObject>není <xref:System.Windows.Media.Visual>odvozen z , , <xref:System.Windows.Threading.DispatcherObject> nebo , měli byste zvážit odvození z chcete-li získat podporu tohoto modelu podprocesu. Další informace naleznete v tématu [Threading Model](threading-model.md).  
  
### <a name="visual"></a>Vizuál  
 <xref:System.Windows.Media.Visual>implementuje koncept 2D objektu, který obecně vyžaduje vizuální prezentaci v zhruba obdélníkové oblasti. Skutečné vykreslování <xref:System.Windows.Media.Visual> se stane v jiných třídách <xref:System.Windows.Media.Visual> (není samostatný), ale třída poskytuje známý typ, který se používá vykreslování procesy na různých úrovních. <xref:System.Windows.Media.Visual>implementuje testování přístupů, ale nezveřejňuje události, které hlásí <xref:System.Windows.UIElement>pozitivní výsledky testování přístupů (ty jsou v ). Další informace naleznete [v tématu Visual Layer Programming](../graphics-multimedia/visual-layer-programming.md).  
  
### <a name="freezable"></a>Freezable  
 <xref:System.Windows.Freezable>simuluje neměnnost v proměnlivém objektu poskytnutím prostředků ke generování kopií objektu, když je neměnný objekt vyžadován nebo žádoucí z důvodů výkonu. Typ <xref:System.Windows.Freezable> poskytuje společný základ pro určité grafické prvky, jako jsou geometrie a stopy, stejně jako animace. Zejména, <xref:System.Windows.Freezable> a není <xref:System.Windows.Media.Visual>; může obsahovat vlastnosti, které <xref:System.Windows.Freezable> se stanou podvlastnostmi, když je použita k vyplnění hodnoty vlastnosti jiného objektu a tyto podvlastnosti mohou ovlivnit vykreslování. Další informace naleznete v tématu [Přehled mrazivých objektů](freezable-objects-overview.md).  
  
 <xref:System.Windows.Media.Animation.Animatable>  
  
 <xref:System.Windows.Media.Animation.Animatable>je <xref:System.Windows.Freezable> odvozená třída, která konkrétně přidává vrstvu ovládacího prvku animace a některé členy nástroje, takže aktuálně animované vlastnosti lze odlišit od neanimovaných vlastností.  
  
### <a name="control"></a>Řízení  
 <xref:System.Windows.Controls.Control>je zamýšlená základní třída pro typ objektu, který je různě označován ovládacím prvkem nebo komponentou v závislosti na technologii. Obecně kontrolní [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] třídy jsou třídy, které buď přímo představují ovládací prvek ui nebo se úzce účastní složení ovládacího prvku. Primární funkce, <xref:System.Windows.Controls.Control> která umožňuje, je ovládání šablonování.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Controls.Control>
- [Přehled vlastností závislosti](dependency-properties-overview.md)
- [Přehled vytváření ovládacích prvků](../controls/control-authoring-overview.md)
- [Architektura WPF](wpf-architecture.md)
