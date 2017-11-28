---
title: "Optimalizace výkonu: Datová vazba"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- binding data [WPF], performance
- data binding [WPF], performance
ms.assetid: 1506a35d-c009-43db-9f1e-4e230ad5be73
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 36f7f1fa5aee672caea7d79fabfc0408c4186cdd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="optimizing-performance-data-binding"></a>Optimalizace výkonu: Datová vazba
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]Datová vazba poskytuje jednoduchý a konzistentní způsob pro aplikace pro práci s daty a k dispozici. Elementy lze vázat na data z různých zdrojů dat ve formě [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objekty a [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)].  
  
 Toto téma obsahuje doporučení pro optimální výkon datové vazby.  
  

  
<a name="HowDataBindingReferencesAreResolved"></a>   
## <a name="how-data-binding-references-are-resolved"></a>Způsob řešení odkazy na vazby dat  
 Před hovoříte o datové vazby problémy s výkonem, je smysl prozkoumat jak [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] stroje vazby dat přeloží odkazy na objekty pro vazbu.  
  
 Zdroj [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vázání dat může být libovolná [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objektu. Můžete vázat na vlastnosti, dílčí vlastnosti nebo indexery z [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objektu. Odkazy na vazba se přeloží pomocí buď [!INCLUDE[TLA#tla_avalonwinfx](../../../../includes/tlasharptla-avalonwinfx-md.md)] reflexe nebo <xref:System.ComponentModel.ICustomTypeDescriptor>. Tady jsou tři metody pro řešení odkazy na objekty pro vazbu.  
  
 První metoda, která pomocí reflexe. V takovém případě <xref:System.Reflection.PropertyInfo> objekt se používá ke zjišťování atributy vlastnosti a poskytuje přístup k vlastnosti metadat. Při použití <xref:System.ComponentModel.ICustomTypeDescriptor> rozhraní, modul vazby dat používá toto rozhraní pro přístup k hodnoty vlastností. <xref:System.ComponentModel.ICustomTypeDescriptor> Rozhraní je obzvláště užitečná v případech, kde objekt nemá statické sadu vlastností.  
  
 Oznámení o změnách vlastnost lze zadat buď implementací <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní nebo pomocí přidružená oznámení o změnách <xref:System.ComponentModel.TypeDescriptor>. Upřednostňované strategie pro implementaci oznámení o změnách vlastnost je však používat <xref:System.ComponentModel.INotifyPropertyChanged>.  
  
 Pokud je zdrojový objekt [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objekt a zdrojová vlastnost se [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] vlastnost, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] je modul vazby dat nejprve získat pomocí reflexe na zdrojový objekt <xref:System.ComponentModel.TypeDescriptor>a potom budete dotazovat pro <xref:System.ComponentModel.PropertyDescriptor>. Tato posloupnost operací reflexe je potenciálně velmi zdlouhavý z hlediska výkonu.  
  
 Zahrnuje druhé metody pro řešení odkazy na objekty [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] zdrojový objekt, který implementuje <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní a vlastnosti zdroje, která je [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] vlastnost. V takovém případě stroje vazby dat používá reflexe přímo na typ zdroje a získá požadovaná vlastnost. Toto není stále optimální metodu, ale že menší při práci požadavky sady než první metodu náklady.  
  
 Třetí metodu pro překlad odkazy na objekty zahrnuje zdrojový objekt, který je <xref:System.Windows.DependencyObject> a vlastnosti zdroje, která je <xref:System.Windows.DependencyProperty>. Modul vazby dat v tomto případě není potřeba pomocí reflexe. Místo toho modul vlastnost stroje vazby dat společně vyřešit a odkaz na vlastnost nezávisle. Toto je optimální metodu pro překlad odkazy na objekty, které používají pro datovou vazbu.  
  
 Následující tabulka porovnává rychlosti datová vazba <xref:System.Windows.Controls.TextBlock.Text%2A> vlastnost tisíců <xref:System.Windows.Controls.TextBlock> elementů pomocí těchto tří metod.  
  
|**Vytvoření vazby vlastnosti textu TextBlock**|**Vazba čas (ms)**|**Doba vykreslování – zahrnuje vazby (ms)**|  
|--------------------------------------------------|-----------------------------|--------------------------------------------------|  
|Do vlastnosti [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objektu|115|314|  
|Do vlastnosti [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objekt, který implementuje<xref:System.ComponentModel.INotifyPropertyChanged>|115|305|  
|K <xref:System.Windows.DependencyProperty> z <xref:System.Windows.DependencyObject>.|90|263|  
  
<a name="Binding_to_Large_CLR_Objects"></a>   
## <a name="binding-to-large-clr-objects"></a>Vytvoření vazby na objekty Large CLR  
 Nebude to mít vliv významně zvýšit výkon při data vytvoření vazby na jednu [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objekt s tisíci vlastnosti. Můžete minimalizovat tomuto vlivu vydělením jednoho objektu do více [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objekty se méně vlastností. V tabulce jsou uvedeny vazby a vykreslování časy pro datovou vazbu na jednu velké [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objekt versus více menší objektů.  
  
|**Datové vazby 1000 TextBlock objekty**|**Vazba čas (ms)**|**Doba vykreslování – zahrnuje vazby (ms)**|  
|---------------------------------------------|-----------------------------|--------------------------------------------------|  
|K [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objekt s 1 000 vlastnosti|950|1200|  
|Na 1000 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objekty s jednu vlastnost|115|314|  
  
<a name="Binding_to_an_ItemsSource"></a>   
## <a name="binding-to-an-itemssource"></a>Vytvoření vazby vlastnost ItemsSource  
 Vezměte v úvahu scénář, ve kterém máte [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601> objekt, který obsahuje seznam zaměstnanců, které chcete zobrazit v <xref:System.Windows.Controls.ListBox>. K vytvoření vztahu mezi tyto dva objekty, by vytvořit vazbu seznamu Zaměstnanci mají <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost <xref:System.Windows.Controls.ListBox>. Ale Předpokládejme, že máte nového zaměstnance připojení vaší skupině. Si myslíte, aby bylo možné vložit tento nový uživatel do vaší hranice <xref:System.Windows.Controls.ListBox> hodnoty, by jednoduše přidat do seznamu Zaměstnanec tato osoba a očekávají, že tato změna rozpoznala stroje vazby dat automaticky. Předpokládá, že byste prokázat false; ve skutečnosti, změny se neprojeví v <xref:System.Windows.Controls.ListBox> automaticky. Důvodem je, že [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601> objekt nevyvolá automaticky událostí kolekce byla změněna. Chcete-li získat <xref:System.Windows.Controls.ListBox> mohla vybrat změny, bude muset znovu vytvořit seznam zaměstnanci a znovu připojte ji k <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost <xref:System.Windows.Controls.ListBox>. Když toto řešení funguje, představuje výkonu velký dopad. Pokaždé, když přiřadíte <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> z <xref:System.Windows.Controls.ListBox> nový objekt <xref:System.Windows.Controls.ListBox> nejprve vyvolá rychle jeho předchozí položky a regeneruje jeho celý seznam. Dopad na výkon je zvětšit, pokud vaše <xref:System.Windows.Controls.ListBox> mapuje komplexní <xref:System.Windows.DataTemplate>.  
  
 Velmi efektivní řešení tohoto problému je zajistit seznamu zaměstnanců <xref:System.Collections.ObjectModel.ObservableCollection%601>. <xref:System.Collections.ObjectModel.ObservableCollection%601> Objekt vyvolá upozornění na změnu, která může přijímat stroje vazby dat. Událost přidá nebo odebere položku z <xref:System.Windows.Controls.ItemsControl> bez nutnosti znovu vygenerovat celý seznam.  
  
 V tabulce níže znázorňuje doba potřebná k aktualizaci <xref:System.Windows.Controls.ListBox> (pomocí uživatelského rozhraní virtualizace vypnutý) když jedna položka byla přidána. Toto číslo v prvním řádku představuje uplynulý čas při [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601> objekt je vázán na <xref:System.Windows.Controls.ListBox> elementu <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>. Toto číslo ve druhém řádku představuje uplynulý čas při <xref:System.Collections.ObjectModel.ObservableCollection%601> je vázána <xref:System.Windows.Controls.ListBox> elementu <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>. Poznámka: čas významné úspory pomocí <xref:System.Collections.ObjectModel.ObservableCollection%601> strategie vazby dat.  
  
|**Datové vazby položka ItemsSource**|**Aktualizujte dobu 1 položka (ms)**|  
|--------------------------------------|---------------------------------------|  
|K [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601> objektu|1656|  
|Pro<xref:System.Collections.ObjectModel.ObservableCollection%601>|20|  
  
<a name="Binding_IList_to_ItemsControl_not_IEnumerable"></a>   
## <a name="bind-ilist-to-itemscontrol-not-ienumerable"></a>ItemsControl není IEnumerable vytvořit vazbu rozhraní IList.  
 Pokud máte možnost volby mezi vazby <xref:System.Collections.Generic.IList%601> nebo <xref:System.Collections.IEnumerable> k <xref:System.Windows.Controls.ItemsControl> objektu, vyberte <xref:System.Collections.Generic.IList%601> objektu. Vazba <xref:System.Collections.IEnumerable> k <xref:System.Windows.Controls.ItemsControl> vynutí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vytvořit obálku <xref:System.Collections.Generic.IList%601> objekt, což znamená, je vliv výkon zbytečné režii druhý objekt.  
  
<a name="Do_not_Convert_CLR_objects_to_Xml_Just_For_Data_Binding"></a>   
## <a name="do-not-convert-clr-objects-to-xml-just-for-data-binding"></a>Udělat není CLR převést objekty do XML pouze pro datové vazby.  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Umožňuje vám dat vytvořit vazbu na [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] obsahu; však datová vazba na [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] obsah je nižší než datová vazba na [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objekty. Nepřevádějí [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] data do formátu XML objektu, pokud je jediným účelem pro datovou vazbu.  
  
## <a name="see-also"></a>Viz také  
 [Optimalizace výkonu aplikace WPF](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [Plánování výkonu aplikace](../../../../docs/framework/wpf/advanced/planning-for-application-performance.md)  
 [Využití výhod hardwaru](../../../../docs/framework/wpf/advanced/optimizing-performance-taking-advantage-of-hardware.md)  
 [Rozložení a návrh](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [2D grafika a vytvoření bitové kopie](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Chování objektů](../../../../docs/framework/wpf/advanced/optimizing-performance-object-behavior.md)  
 [Prostředky aplikace](../../../../docs/framework/wpf/advanced/optimizing-performance-application-resources.md)  
 [Text](../../../../docs/framework/wpf/advanced/optimizing-performance-text.md)  
 [Další doporučení výkonu](../../../../docs/framework/wpf/advanced/optimizing-performance-other-recommendations.md)  
 [Přehled vazba dat](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Návod: Ukládání dat aplikací v aplikaci WPF](../../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)
