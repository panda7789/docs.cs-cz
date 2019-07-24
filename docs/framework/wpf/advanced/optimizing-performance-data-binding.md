---
title: 'Optimalizace výkonu: Datová vazba'
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], performance
- data binding [WPF], performance
ms.assetid: 1506a35d-c009-43db-9f1e-4e230ad5be73
ms.openlocfilehash: 25c0906e9f23948476732b10b2c5fb10fe4eb55f
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401452"
---
# <a name="optimizing-performance-data-binding"></a>Optimalizace výkonu: Datová vazba
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]datové vazby poskytují jednoduchý a konzistentní způsob, jak aplikace prezentovat a interagovat s daty. Prvky mohou být vázány na data z nejrůznějších zdrojů dat ve formě objektů CLR a [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)].  
  
 Toto téma poskytuje doporučení týkající se výkonu datových vazeb.  

<a name="HowDataBindingReferencesAreResolved"></a>   
## <a name="how-data-binding-references-are-resolved"></a>Způsob řešení odkazů na datové vazby  
 Než proberete problémy s výkonem datových vazeb, je vhodné prozkoumat, jak [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] modul vazby dat řeší odkazy na objekty pro vazbu.  
  
 Zdrojem [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] datové vazby může být libovolný objekt CLR. Můžete vytvořit vazby k vlastnostem, dílčím vlastnostem nebo indexerům objektu CLR. Odkazy na vazby jsou vyřešeny buď pomocí reflexe .NET Framework, <xref:System.ComponentModel.ICustomTypeDescriptor>nebo. Tady jsou tři metody pro překládání odkazů na objekty pro vazbu.  
  
 První metoda zahrnuje použití reflexe. V tomto případě <xref:System.Reflection.PropertyInfo> se objekt používá ke zjištění atributů vlastnosti a poskytuje přístup k metadatům vlastností. Při použití <xref:System.ComponentModel.ICustomTypeDescriptor> rozhraní používá modul vazby dat toto rozhraní pro přístup k hodnotám vlastností. <xref:System.ComponentModel.ICustomTypeDescriptor> Rozhraní je zvláště užitečné v případech, kde objekt nemá statickou sadu vlastností.  
  
 Oznámení o změnách vlastností lze zadat implementací <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní nebo pomocí oznámení změn přidružených <xref:System.ComponentModel.TypeDescriptor>k. Upřednostňovaná strategie pro implementaci oznámení o změně vlastností je ale použití <xref:System.ComponentModel.INotifyPropertyChanged>.  
  
 Pokud je zdrojový objekt objekt CLR a vlastnost source je vlastnost CLR, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] musí modul vazby dat nejprve použít reflexi na zdrojovém objektu <xref:System.ComponentModel.TypeDescriptor>, aby získal <xref:System.ComponentModel.PropertyDescriptor>a pak dotaz na. Tato sekvence operací reflexe je potenciálně velmi časově náročná z hlediska výkonu.  
  
 Druhá metoda pro překlad odkazů na objekty zahrnuje zdrojový objekt CLR, který implementuje <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní a vlastnost zdroje, která je vlastností CLR. V takovém případě modul vazby dat používá reflexi přímo na zdrojovém typu a získá požadovanou vlastnost. Nejedná se o optimální metodu, ale náklady na pracovní sadu, která je nižší než první metoda, bude levnější.  
  
 Třetí metoda pro překlad odkazů na objekty zahrnuje zdrojový objekt, který je <xref:System.Windows.DependencyObject> a zdrojovou vlastnost, která <xref:System.Windows.DependencyProperty>je. V takovém případě nemusí modul vazby dat používat reflexi. Místo toho modul vlastností a modul vazby dat společně vyřeší odkaz na vlastnost nezávisle. Toto je optimální metoda pro překládání odkazů na objekty používané pro datovou vazbu.  
  
 Následující tabulka porovnává rychlost vázání <xref:System.Windows.Controls.TextBlock.Text%2A> dat vlastností 1000 <xref:System.Windows.Controls.TextBlock> prvků pomocí těchto tří metod.  
  
|**Vytvoření vazby vlastnosti text pro TextBlock**|**Čas vazby (MS)**|**Čas vykreslování – zahrnuje vazbu (MS)**|  
|--------------------------------------------------|-----------------------------|--------------------------------------------------|  
|Na vlastnost objektu CLR|115|314|  
|Do vlastnosti objektu CLR, který implementuje<xref:System.ComponentModel.INotifyPropertyChanged>|115|305|  
|K a <xref:System.Windows.DependencyProperty> <xref:System.Windows.DependencyObject>.|90|263|  
  
<a name="Binding_to_Large_CLR_Objects"></a>   
## <a name="binding-to-large-clr-objects"></a>Vazba na velké objekty CLR  
 Existuje značný dopad na výkon při vázání dat na jeden objekt CLR s tisíci vlastností. Tento dopad můžete minimalizovat tak, že jeden objekt vydělíte na více objektů CLR s menším počtem vlastností. Tabulka ukazuje dobu vazby a vykreslování pro datovou vazbu na jeden velký objekt CLR a více menších objektů.  
  
|**Datové vazby 1000 TextBlock objekty**|**Čas vazby (MS)**|**Čas vykreslování – zahrnuje vazbu (MS)**|  
|---------------------------------------------|-----------------------------|--------------------------------------------------|  
|K objektu CLR s vlastností 1000|950|1200|  
|Na 1000 objektů CLR s jednou vlastností|115|314|  
  
<a name="Binding_to_an_ItemsSource"></a>   
## <a name="binding-to-an-itemssource"></a>Vazba na ItemsSource  
 Vezměte v úvahu scénář, ve kterém máte objekt <xref:System.Collections.Generic.List%601> CLR, který obsahuje seznam zaměstnanců, které chcete zobrazit <xref:System.Windows.Controls.ListBox>v. Chcete-li vytvořit korespondenci mezi těmito dvěma objekty, můžete vytvořit propojení seznamu zaměstnanců s <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastností. <xref:System.Windows.Controls.ListBox> Předpokládejme však, že máte nového zaměstnance, který se připojuje ke skupině. Možná si myslíte, že pokud chcete tuto novou osobu do svých vázaných <xref:System.Windows.Controls.ListBox> hodnot vložit, stačí přidat tuto osobu do seznamu zaměstnanců a očekávat tuto změnu, aby ji modul datových vazeb automaticky rozpoznal. Tento předpoklad by prokáže false; ve skutečnosti se tato změna neprojeví <xref:System.Windows.Controls.ListBox> automaticky. Důvodem je to, že <xref:System.Collections.Generic.List%601> objekt CLR nevyvolává automaticky změněné události kolekce. Aby bylo možné získat <xref:System.Windows.Controls.ListBox> změny, je nutné znovu vytvořit seznam zaměstnanců a znovu ho připojit <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> k vlastnosti <xref:System.Windows.Controls.ListBox>. I když toto řešení funguje, přináší značný dopad na výkon. Pokaždé, když znovu přiřadíte <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.ListBox> objekt k novému objektu <xref:System.Windows.Controls.ListBox> , první vyvolá předchozí položky a znovu vygeneruje celý seznam. Dopad na výkon je zvětšený, pokud <xref:System.Windows.Controls.ListBox> vaše mapy na komplexní <xref:System.Windows.DataTemplate>.  
  
 Velice efektivním řešením tohoto problému je vytvořit seznam <xref:System.Collections.ObjectModel.ObservableCollection%601>zaměstnanců. <xref:System.Collections.ObjectModel.ObservableCollection%601> Objekt vyvolá oznámení o změně, které může modul datových vazeb přijmout. Událost přidá nebo odebere položku z <xref:System.Windows.Controls.ItemsControl> , aniž by bylo nutné znovu vygenerovat celý seznam.  
  
 Následující tabulka ukazuje dobu potřebnou k aktualizaci <xref:System.Windows.Controls.ListBox> (při vypnutí virtualizace uživatelského rozhraní), když se přidá jedna položka. Číslo v prvním řádku představuje uplynulý čas, kdy je objekt CLR <xref:System.Collections.Generic.List%601> svázán s <xref:System.Windows.Controls.ListBox> prvkem <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>. Číslo ve druhém řádku představuje uplynulý čas, kdy <xref:System.Collections.ObjectModel.ObservableCollection%601> je svázána <xref:System.Windows.Controls.ListBox> s prvkem <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>. Všimněte si výrazné úspory času pomocí <xref:System.Collections.ObjectModel.ObservableCollection%601> strategie vázání dat.  
  
|**Vázání dat na ItemsSource**|**Aktualizovat čas pro 1 položku (MS)**|  
|--------------------------------------|---------------------------------------|  
|K objektu CLR <xref:System.Collections.Generic.List%601>|1656|  
|Do<xref:System.Collections.ObjectModel.ObservableCollection%601>|20|  
  
<a name="Binding_IList_to_ItemsControl_not_IEnumerable"></a>   
## <a name="bind-ilist-to-itemscontrol-not-ienumerable"></a>Vazba IList na ItemsControl, které není IEnumerable  
 Pokud máte možnost volby mezi vazbou <xref:System.Collections.Generic.IList%601> <xref:System.Collections.IEnumerable> a nebo k <xref:System.Windows.Controls.ItemsControl> objektu, vyberte <xref:System.Collections.Generic.IList%601> objekt. Vazba <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IList%601> na síly pro[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vytvoření objektu obálky, což znamená, že váš výkon je ovlivněn zbytečnými nároky na druhý objekt. <xref:System.Windows.Controls.ItemsControl>  
  
<a name="Do_not_Convert_CLR_objects_to_Xml_Just_For_Data_Binding"></a>   
## <a name="do-not-convert-clr-objects-to-xml-just-for-data-binding"></a>Neprovádějte převod objektů CLR do XML pouze pro datovou vazbu.  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]umožňuje svázat data s [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] obsahem. datová vazba k [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] obsahu je však pomalejší než datová vazba s objekty CLR. Neprovádějte převod dat objektu CLR do formátu XML, je-li jediným účelem vytváření datových vazeb.  
  
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
- [Návod: Ukládání aplikačních dat do mezipaměti v aplikaci WPF](walkthrough-caching-application-data-in-a-wpf-application.md)
