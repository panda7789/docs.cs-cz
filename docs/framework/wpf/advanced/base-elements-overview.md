---
title: Přehled základních elementů
ms.date: 03/30/2017
helpviewer_keywords:
- base elements [WPF]
ms.assetid: 2c997092-72c6-4767-bc84-74267f4eee72
ms.openlocfilehash: 823c81bf6b21b88d719503387a68ce6e7d643d61
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740913"
---
# <a name="base-elements-overview"></a>Přehled základních elementů
Vysoké procento tříd v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] jsou odvozeny ze čtyř tříd, které se běžně označují v dokumentaci k sadě SDK jako základní třídy prvků. Tyto třídy jsou <xref:System.Windows.UIElement>, <xref:System.Windows.FrameworkElement>, <xref:System.Windows.ContentElement>a <xref:System.Windows.FrameworkContentElement>. Třída <xref:System.Windows.DependencyObject> také souvisí, protože se jedná o společnou základní třídu obou <xref:System.Windows.UIElement> a <xref:System.Windows.ContentElement>  

<a name="base_apis"></a>   
## <a name="base-element-apis-in-wpf-classes"></a>Rozhraní API základních prvků v třídách WPF  
 <xref:System.Windows.UIElement> i <xref:System.Windows.ContentElement> jsou odvozeny z <xref:System.Windows.DependencyObject>, a to prostřednictvím trochu odlišných cest. Rozdělení na této úrovni se zabývá tím, jak se v uživatelském rozhraní používá <xref:System.Windows.UIElement> nebo <xref:System.Windows.ContentElement> a jaký účel obsluhuje aplikace. <xref:System.Windows.UIElement> má také <xref:System.Windows.Media.Visual> ve své hierarchii tříd, což je třída, která zpřístupňuje podporu grafiky nižší úrovně na základě [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]. <xref:System.Windows.Media.Visual> poskytuje rozhraní pro vykreslování definováním nezávislých oblastí obdélníkové obrazovky. V praxi je <xref:System.Windows.UIElement> pro prvky, které podporují větší objektový model, určeny k vykreslování a rozložení oblastí, které mohou být popsány jako obdélníkové oblasti obrazovky a kde je model obsahu záměrně otevřen, aby bylo možné použít různé kombinace. prvků. <xref:System.Windows.ContentElement> neodvozuje z <xref:System.Windows.Media.Visual>; jeho model je, že by <xref:System.Windows.ContentElement> mohl spotřebovat jiný objekt, jako je čtenář nebo prohlížeč, který by pak interpretoval prvky a vytvořil kompletní <xref:System.Windows.Media.Visual> pro [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] pro využití. Některé <xref:System.Windows.UIElement> třídy jsou určeny jako hostitelé obsahu: poskytují hostování a vykreslování pro jednu nebo více tříd <xref:System.Windows.ContentElement> (<xref:System.Windows.Controls.DocumentViewer> je příkladem takové třídy). <xref:System.Windows.ContentElement> se používá jako základní třída pro prvky s poněkud menšími objektovými modely a je více adresovat text, informace nebo obsah dokumentu, které mohou být hostovány v rámci <xref:System.Windows.UIElement>.  
  
### <a name="framework-level-and-core-level"></a>Úrovni rozhraní a úrovně Core  
 <xref:System.Windows.UIElement> slouží jako základní třída pro <xref:System.Windows.FrameworkElement>a <xref:System.Windows.ContentElement> slouží jako základní třída pro <xref:System.Windows.FrameworkContentElement>. Důvodem pro tuto další úroveň tříd je podpora základní úrovně WPF, která je oddělená od úrovně rozhraní WPF, s tímto oddílem také existuje ve způsobu, jakým jsou rozhraní API rozdělena mezi sestavení PresentationCore a PresentationFramework. Úroveň rozhraní WPF Framework prezentuje úplnější řešení pro potřeby základních aplikací, včetně implementace Správce rozložení pro prezentaci. Základní úroveň WPF poskytuje způsob, jak použít mnohem [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] bez nutnosti přebírat nároky na další sestavení. Rozdíl mezi těmito úrovněmi je velmi zřídka pro většinu typických scénářů vývoje aplikací a obecně byste si měli představit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozhraní API jako celek a nezáleží na tom, jestli se jedná o rozdíl mezi úrovní architektury WPF a platformou WPF Core. Je možné, že budete potřebovat znát odlišnosti na úrovni, pokud se návrh aplikace rozhodne, že nahradí podstatné množství funkcí na úrovni rozhraní WPF, například pokud vaše celkové řešení již má vlastní implementace [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]ho složení a rozložení.  
  
<a name="subclassing_elements"></a>   
## <a name="choosing-which-element-to-derive-from"></a>Výběr prvku, ze kterého se mají odvozovat  
 Nejpohodlnější způsob, jak vytvořit vlastní třídu, která rozšiřuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], je odvozování z jedné z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] tříd, kde co nejvíc dosáhnete požadovaných funkcí prostřednictvím existující hierarchie tříd. Tato část obsahuje seznam funkcí, které jsou dodávány se třemi nejdůležitějšími třídami prvků, které vám pomůžou rozhodnout, ze které třídy dědí.  
  
 Pokud implementujete ovládací prvek, který je skutečně jedním z nejběžnějších důvodů odvození od [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] třídy, pravděpodobně budete chtít odvozovat od třídy, která je praktického ovládacího prvku, základní třídy řady nebo alespoň <xref:System.Windows.Controls.Control> základní třídy. Některé doprovodné materiály a praktické příklady najdete v tématu [Přehled vytváření ovládacích prvků](../controls/control-authoring-overview.md).  
  
 Pokud nevytváříte ovládací prvek a potřebujete odvozovat z třídy, která je vyšší v hierarchii, jsou následující oddíly určeny jako vodítko pro to, jaké charakteristiky jsou definovány v každé třídě základního elementu.  
  
 Pokud vytvoříte třídu, která je odvozena z <xref:System.Windows.DependencyObject>, zdědíte následující funkce:  
  
- Podpora <xref:System.Windows.DependencyObject.GetValue%2A> a <xref:System.Windows.DependencyObject.SetValue%2A> a obecná podpora systému vlastností.  
  
- Možnost používat vlastnosti závislosti a připojené vlastnosti, které jsou implementovány jako vlastnosti závislosti.  
  
 Pokud vytvoříte třídu, která je odvozena z <xref:System.Windows.UIElement>, kromě toho, který poskytuje <xref:System.Windows.DependencyObject>, převezmete následující funkce:  
  
- Podpora Basic pro animované hodnoty vlastností. Další informace najdete v tématu [Přehled animací](../graphics-multimedia/animation-overview.md).  
  
- Základní podpora událostí vstupu a podpora příkazů. Další informace najdete v tématech [Přehled vstupu](input-overview.md) a [Přehled příkazů](commanding-overview.md).  
  
- Virtuální metody, které mohou být přepsány, aby poskytovaly informace systému rozložení.  
  
 Pokud vytvoříte třídu, která je odvozena z <xref:System.Windows.FrameworkElement>, kromě toho, který poskytuje <xref:System.Windows.UIElement>, převezmete následující funkce:  
  
- Podpora stylů a scénářů. Další informace najdete v tématu Přehled <xref:System.Windows.Style> a [scénářů](../graphics-multimedia/storyboards-overview.md).  
  
- Podpora datových vazeb. Další informace najdete v tématu [Přehled datových vazeb](../data/data-binding-overview.md).  
  
- Podpora dynamických odkazů na prostředky. Další informace naleznete v tématu [prostředky XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
- Podpora dědičnosti hodnot vlastností a dalších příznaků v metadatech, které vám pomůžou hlásit podmínky týkající se vlastností pro služby architektury, jako jsou datové vazby, styly nebo implementace architektury rozložení. Další informace najdete v tématu [Metadata vlastností rozhraní](framework-property-metadata.md).  
  
- Koncept logického stromu. Další informace najdete v tématu [stromy v](trees-in-wpf.md)subsystému WPF.  
  
- Podpora praktické implementace systému rozložení na úrovni WPF Frameworku, včetně přepsání <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A>, která může detekovat změny vlastností, které mají vliv na rozložení.  
  
 Pokud vytvoříte třídu, která je odvozena z <xref:System.Windows.ContentElement>, kromě toho, který poskytuje <xref:System.Windows.DependencyObject>, převezmete následující funkce:  
  
- Podpora animací. Další informace najdete v tématu [Přehled animací](../graphics-multimedia/animation-overview.md).  
  
- Základní podpora událostí vstupu a podpora příkazů. Další informace najdete v tématech [Přehled vstupu](input-overview.md) a [Přehled příkazů](commanding-overview.md).  
  
 Pokud vytvoříte třídu, která je odvozena od <xref:System.Windows.FrameworkContentElement>, získáte kromě funkcí poskytovaných <xref:System.Windows.ContentElement>následující funkce:  
  
- Podpora stylů a scénářů. Další informace najdete v tématu Přehled <xref:System.Windows.Style> a [animace](../graphics-multimedia/animation-overview.md).  
  
- Podpora datových vazeb. Další informace najdete v tématu [Přehled datových vazeb](../data/data-binding-overview.md).  
  
- Podpora dynamických odkazů na prostředky. Další informace naleznete v tématu [prostředky XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md).  
  
- Podpora dědičnosti hodnot vlastností a dalších příznaků v metadatech, které vám pomůžou hlásit podmínky týkající se vlastností pro služby architektury, jako jsou datové vazby, styly nebo implementace architektury rozložení. Další informace najdete v tématu [Metadata vlastností rozhraní](framework-property-metadata.md).  
  
- Nezdědíte přístup k změnám v systému rozložení (například <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>). Implementace systému rozložení jsou k dispozici pouze na <xref:System.Windows.FrameworkElement>. Nicméně převezmete přepsání <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A>, které může detekovat změny vlastností, které ovlivňují rozložení a nastavovat je pro všechny hostitele obsahu.  
  
 Modely obsahu jsou zdokumentovány pro nejrůznější třídy. Model obsahu pro třídu je jedním z možných faktorů, které byste měli zvážit, pokud chcete najít vhodnou třídu, ze které se má odvozovat. Další informace najdete v tématu [model obsahu WPF](../controls/wpf-content-model.md).  
  
<a name="other_base_classes"></a>   
## <a name="other-base-classes"></a>Další základní třídy  
  
### <a name="dispatcherobject"></a>DispatcherObject –  
 <xref:System.Windows.Threading.DispatcherObject> poskytuje podporu pro model vláken [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a umožňuje všem objektům vytvořeným pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace přidružit k <xref:System.Windows.Threading.Dispatcher>. I v případě, že nebudete odvozovat z <xref:System.Windows.UIElement>, <xref:System.Windows.DependencyObject>nebo <xref:System.Windows.Media.Visual>, měli byste zvážit odvození od <xref:System.Windows.Threading.DispatcherObject>, aby bylo možné tuto podporu modelu vláken získat. Další informace najdete v tématu [model vláken](threading-model.md).  
  
### <a name="visual"></a>Vizuál  
 <xref:System.Windows.Media.Visual> implementuje koncept 2D objektu, který obvykle vyžaduje vizuální prezentaci ve zhruba obdélníkové oblasti. Skutečné vykreslování <xref:System.Windows.Media.Visual> dochází v jiných třídách (není samo), ale třída <xref:System.Windows.Media.Visual> poskytuje známý typ, který je používán vykreslovacími procesy na různých úrovních. <xref:System.Windows.Media.Visual> implementuje testování přístupů, ale nevystavuje události, které hlásí pozitivní výsledky testování přístupů (jsou v <xref:System.Windows.UIElement>). Další informace naleznete v tématu [programování vizuální vrstvy](../graphics-multimedia/visual-layer-programming.md).  
  
### <a name="freezable"></a>Freezable  
 <xref:System.Windows.Freezable> simuluje neměnnosti v proměnlivém objektu poskytnutím prostředků pro generování kopií objektu, je-li vyžadován neproměnlivý objekt nebo je požadován z důvodů výkonu. Typ <xref:System.Windows.Freezable> poskytuje společný základ pro určité grafické prvky, jako jsou geometrií a štětce, a také animace. Zejména <xref:System.Windows.Freezable> není <xref:System.Windows.Media.Visual>; může uchovávat vlastnosti, které se stanou podvlastnostmi, pokud je <xref:System.Windows.Freezable> použito pro vyplnění hodnoty vlastnosti jiného objektu a tyto podvlastnosti mohou ovlivnit vykreslování. Další informace najdete v tématu [Přehled objektů Freezable](freezable-objects-overview.md).  
  
 <xref:System.Windows.Media.Animation.Animatable>  
  
 <xref:System.Windows.Media.Animation.Animatable> je <xref:System.Windows.Freezable> odvozená třída, která specificky přidá vrstvu ovládacího prvku animace a některé členy nástrojů, aby se aktuálně animované vlastnosti mohly odlišit od neanimovaných vlastností.  
  
### <a name="control"></a>Control  
 <xref:System.Windows.Controls.Control> je zamýšlená základní třída pro typ objektu, který je v závislosti na technologii v závislosti na technologii označován jako ovládací prvek nebo komponenta. Obecně jsou třídy ovládacího prvku [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] třídy, které buď přímo představují ovládací prvek uživatelského rozhraní, nebo jsou úzce zapojeny do kompozice ovládacích prvků. Hlavní funkčnost, kterou <xref:System.Windows.Controls.Control> umožňuje, je ovládací prvek šablonování.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.Control>
- [Přehled vlastností závislosti](dependency-properties-overview.md)
- [Přehled vytváření ovládacích prvků](../controls/control-authoring-overview.md)
- [Architektura WPF](wpf-architecture.md)
