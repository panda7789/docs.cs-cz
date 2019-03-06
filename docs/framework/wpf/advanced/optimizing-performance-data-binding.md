---
title: 'Optimalizace výkonu: Datová vazba'
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], performance
- data binding [WPF], performance
ms.assetid: 1506a35d-c009-43db-9f1e-4e230ad5be73
ms.openlocfilehash: dfc58036bc39879009b31d29dc41247a914bcd59
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352019"
---
# <a name="optimizing-performance-data-binding"></a>Optimalizace výkonu: Datová vazba
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vytváření datových vazeb nabízí jednoduchý a konzistentní způsob pro aplikace k zobrazení a interakci s daty. Elementy mohou být vázány na data z různých zdrojů dat ve formě [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objekty a [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)].  
  
 Toto téma obsahuje doporučení ohledně výkonu pro datové vazby.  
  

  
<a name="HowDataBindingReferencesAreResolved"></a>   
## <a name="how-data-binding-references-are-resolved"></a>Jak vyřešit odkazy vazby dat  
 Před diskuze o datové vazbě problémy s výkonem, je vhodné prozkoumat jak [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] modul vazby překládá odkazy na objekty pro vazbu.  
  
 Zdroj [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] datová vazba může být kterýkoli [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objektu. Můžete vytvořit vazbu na vlastnosti, dílčí vlastnosti nebo indexerů z [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objektu. Vazební odkazy se přeloží pomocí buď odraz rozhraní Microsoft .NET Framework nebo <xref:System.ComponentModel.ICustomTypeDescriptor>. Tady jsou tři metody pro vyřešení odkazy na objekty pro vazbu.  
  
 První metoda, která využívá reflexe. V takovém případě <xref:System.Reflection.PropertyInfo> objektu se používá ke zjišťování atributy vlastnosti a poskytuje přístup k vlastnosti metadat. Při použití <xref:System.ComponentModel.ICustomTypeDescriptor> rozhraní, modul vazby dat použije toto rozhraní pro přístup k hodnoty vlastností. <xref:System.ComponentModel.ICustomTypeDescriptor> Rozhraní je zvláště užitečná v případech, kde objekt nemá statickou sadu vlastností.  
  
 Oznámení změn vlastností lze zadat buď implementací <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní nebo pomocí přidružené k oznámení o změnách <xref:System.ComponentModel.TypeDescriptor>. Upřednostňované strategie implementace oznámení změn vlastností je však použít <xref:System.ComponentModel.INotifyPropertyChanged>.  
  
 Pokud je zdrojový objekt [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objektů a vlastností zdroje je [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] vlastnost, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] modul vazby musí nejprve získat pomocí reflexe ve zdrojovém objektu <xref:System.ComponentModel.TypeDescriptor>a potom zadejte dotaz pro <xref:System.ComponentModel.PropertyDescriptor>. Tahle posloupnost reflexe operace je potenciálně velmi časově náročné z hlediska výkonu.  
  
 Druhá metoda k vyřešení odkazů na objekty zahrnuje [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] zdrojový objekt, který implementuje <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní a vlastnosti zdroje, který je [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] vlastnost. V tomto případě modul vazby dat používá reflexi přímo na typ zdroje a získá požadovanou vlastnost. Toto není stále optimální způsob, ale stojí méně v požadavky sady než první způsob práce.  
  
 Třetí metoda k vyřešení odkazů na objekty zahrnuje zdrojový objekt, který je <xref:System.Windows.DependencyObject> a vlastnosti zdroje, který je <xref:System.Windows.DependencyProperty>. V takovém případě modul vazby dat není nutné používat reflexi. Místo toho modul vlastnost a modul vazby dat společně přeložit odkaz na vlastnost nezávisle na sobě. Toto je optimální metodu pro překlad odkazy na objekty pro vytváření datových vazeb.  
  
 Následující tabulka porovnává rychlost vytváření datových vazeb <xref:System.Windows.Controls.TextBlock.Text%2A> vlastnost tisíc <xref:System.Windows.Controls.TextBlock> prvky pomocí těchto tří metod.  
  
|**Vytvoření vazby vlastnosti Text v objektech TextBlock**|**Vytvoření vazby. čas (ms)**|**Doba vykreslování – obsahuje vazbu (ms)**|  
|--------------------------------------------------|-----------------------------|--------------------------------------------------|  
|Na vlastnost [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objektu|115|314|  
|Na vlastnost [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objekt, který implementuje <xref:System.ComponentModel.INotifyPropertyChanged>|115|305|  
|K <xref:System.Windows.DependencyProperty> z <xref:System.Windows.DependencyObject>.|90|263|  
  
<a name="Binding_to_Large_CLR_Objects"></a>   
## <a name="binding-to-large-clr-objects"></a>Vytvoření vazby na objekty Large CLR  
 Se dopad výkonu, pokud vaše data svázat jediného [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objektu s tisíci vlastnosti. Minimalizujete tohoto dopadu vydělením jeden objekt do několika [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objekty se méně vlastností. V tabulce jsou uvedeny vazby a vykreslování časů pro vytváření datových vazeb do jediné velké [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objekt oproti více menší objektů.  
  
|**Datové vazby 1000 TextBlock – objekty**|**Vytvoření vazby. čas (ms)**|**Doba vykreslování – obsahuje vazbu (ms)**|  
|---------------------------------------------|-----------------------------|--------------------------------------------------|  
|K [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objekt s vlastnostmi 1000|950|1200|  
|Až 1000 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objekty s jednou vlastností|115|314|  
  
<a name="Binding_to_an_ItemsSource"></a>   
## <a name="binding-to-an-itemssource"></a>Vytvoření vazby vlastnost ItemsSource.  
 Představte si třeba situaci, ve které máte [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601> objekt, který obsahuje seznam zaměstnanců, které chcete zobrazit v <xref:System.Windows.Controls.ListBox>. K vytvoření vztahu mezi těmito dvěma objekty, by vazby seznam zaměstnanců <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost <xref:System.Windows.Controls.ListBox>. Nicméně Předpokládejme, že máte nového zaměstnance propojení vaší skupiny. Můžete uvažovat, aby bylo možné vložit tohoto nového uživatele do vaší mez <xref:System.Windows.Controls.ListBox> hodnoty, bude jednoduše přidat tohoto uživatele do seznamu zaměstnance a očekávat tuto změnu Chcete-li rozpoznán modulem vazby dat automaticky. Tento předpoklad by prokázat false; ve skutečnosti, změny se neprojeví v <xref:System.Windows.Controls.ListBox> automaticky. Je to proto, [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601> objekt nevyvolává automaticky změnit kolekci událostí. Pokud chcete získat <xref:System.Windows.Controls.ListBox> ke sbírání změny, bude muset znovu vytvořit seznam zaměstnanců a připojí ho k <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost <xref:System.Windows.Controls.ListBox>. Když toto řešení funguje, představuje velký výkon vliv. Pokaždé, když znovu přiřadíte <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> z <xref:System.Windows.Controls.ListBox> nový objekt, <xref:System.Windows.Controls.ListBox> nejprve vyvolá okamžitě jeho předchozí položky a znovu vygeneruje jeho celý seznam. Zvětšená dopad na výkon, pokud vaše <xref:System.Windows.Controls.ListBox> mapuje na komplexní <xref:System.Windows.DataTemplate>.  
  
 Velmi efektivní řešení tohoto problému je, aby seznam vašich zaměstnanců <xref:System.Collections.ObjectModel.ObservableCollection%601>. <xref:System.Collections.ObjectModel.ObservableCollection%601> Oznámení o změně, která může přijímat modul vazby dat, vyvolá objekt. Událost přidá nebo odebere položky ze <xref:System.Windows.Controls.ItemsControl> bez nutnosti znovu vygenerovat úplný seznam.  
  
 V tabulce níže ukazuje čas potřebný k aktualizaci <xref:System.Windows.Controls.ListBox> (pomocí uživatelského rozhraní virtualizace vypnutý) při přidání jedné položky. Číslo v prvním řádku představuje uplynulý čas při [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601> je objekt vázán na <xref:System.Windows.Controls.ListBox> elementu <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>. Číslo ve druhém řádku představuje uplynulý čas při <xref:System.Collections.ObjectModel.ObservableCollection%601> je vázán <xref:System.Windows.Controls.ListBox> elementu <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>. Poznámka: pomocí úspory spoustu času <xref:System.Collections.ObjectModel.ObservableCollection%601> strategie datové vazby.  
  
|**Datové vazby vlastnost ItemsSource.**|**Aktualizovat dobu 1 položek (ms)**|  
|--------------------------------------|---------------------------------------|  
|K [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] <xref:System.Collections.Generic.List%601> objektu|1656|  
|Do <xref:System.Collections.ObjectModel.ObservableCollection%601>|20|  
  
<a name="Binding_IList_to_ItemsControl_not_IEnumerable"></a>   
## <a name="bind-ilist-to-itemscontrol-not-ienumerable"></a>Svázat IList ItemsControl není typu IEnumerable  
 Pokud máte možnost volby mezi vazby <xref:System.Collections.Generic.IList%601> nebo <xref:System.Collections.IEnumerable> do <xref:System.Windows.Controls.ItemsControl> objektu, zvolte <xref:System.Collections.Generic.IList%601> objektu. Vazby <xref:System.Collections.IEnumerable> do <xref:System.Windows.Controls.ItemsControl> vynutí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vytvoření obálku <xref:System.Collections.Generic.IList%601> objekt, což znamená, že výkon má vliv zbytečnou režii druhého objektu.  
  
<a name="Do_not_Convert_CLR_objects_to_Xml_Just_For_Data_Binding"></a>   
## <a name="do-not-convert-clr-objects-to-xml-just-for-data-binding"></a>Jak ne CLR převést objekty XML jenom pro datové vazby.  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Umožňuje vám data svázat [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] obsahu; však vazba dat na [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] obsah je pomalejší než datové vazby k [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objekty. Nelze převést [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] objekt dat do formátu XML, pokud jediným účelem je určený pro vytváření datových vazeb.  
  
## <a name="see-also"></a>Viz také:
- [Optimalizace výkonu aplikace WPF](optimizing-wpf-application-performance.md)
- [Plánování výkonu aplikace](planning-for-application-performance.md)
- [Využití výhod hardwaru](optimizing-performance-taking-advantage-of-hardware.md)
- [Rozložení a návrh](optimizing-performance-layout-and-design.md)
- [2D grafika a obrázky](optimizing-performance-2d-graphics-and-imaging.md)
- [Chování objektu](optimizing-performance-object-behavior.md)
- [Prostředky aplikace](optimizing-performance-application-resources.md)
- [Text](optimizing-performance-text.md)
- [Další výkonnostní doporučení](optimizing-performance-other-recommendations.md)
- [Přehled datových vazeb](../data/data-binding-overview.md)
- [Návod: Ukládání dat aplikací v aplikaci WPF](walkthrough-caching-application-data-in-a-wpf-application.md)
