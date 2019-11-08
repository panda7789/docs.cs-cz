---
title: 'Optimalizace výkonu: Datová vazba'
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], performance
- data binding [WPF], performance
ms.assetid: 1506a35d-c009-43db-9f1e-4e230ad5be73
ms.openlocfilehash: 9b302be3ed9f01ccd27470063f49966dc7d74708
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740795"
---
# <a name="optimizing-performance-data-binding"></a>Optimalizace výkonu: Datová vazba
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] datové vazby poskytují jednoduchý a konzistentní způsob, jak aplikace prezentovat a interagovat s daty. Prvky mohou být vázány na data z nejrůznějších zdrojů dat ve formě objektů CLR a XML.  
  
 Toto téma poskytuje doporučení týkající se výkonu datových vazeb.  

<a name="HowDataBindingReferencesAreResolved"></a>   
## <a name="how-data-binding-references-are-resolved"></a>Způsob řešení odkazů na datové vazby  
 Než proberete problémy s výkonem datových vazeb, je vhodné prozkoumat, jak modul datových vazeb [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] řeší odkazy na objekty pro vazbu.  
  
 Zdrojem [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] datové vazby může být jakýkoli objekt CLR. Můžete vytvořit vazby k vlastnostem, dílčím vlastnostem nebo indexerům objektu CLR. Odkazy na vazby jsou vyřešeny buď pomocí .NET Framework reflexe, nebo <xref:System.ComponentModel.ICustomTypeDescriptor>. Tady jsou tři metody pro překládání odkazů na objekty pro vazbu.  
  
 První metoda zahrnuje použití reflexe. V tomto případě se <xref:System.Reflection.PropertyInfo> objekt používá ke zjištění atributů vlastnosti a poskytuje přístup k metadatům vlastností. Při použití <xref:System.ComponentModel.ICustomTypeDescriptor> rozhraní používá modul vazby dat toto rozhraní pro přístup k hodnotám vlastností. Rozhraní <xref:System.ComponentModel.ICustomTypeDescriptor> je zvlášť užitečné v případech, kde objekt nemá statickou sadu vlastností.  
  
 Oznámení o změnách vlastností lze zadat implementací rozhraní <xref:System.ComponentModel.INotifyPropertyChanged> nebo pomocí oznámení změn přidružených k <xref:System.ComponentModel.TypeDescriptor>. Upřednostňovaná strategie pro implementaci oznámení o změně vlastností je však použití <xref:System.ComponentModel.INotifyPropertyChanged>.  
  
 Pokud je zdrojový objekt objekt CLR a vlastnost source je vlastnost CLR, musí modul vazby dat [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] nejprve použít reflexi zdrojového objektu pro získání <xref:System.ComponentModel.TypeDescriptor>a pak dotaz na <xref:System.ComponentModel.PropertyDescriptor>. Tato sekvence operací reflexe je potenciálně velmi časově náročná z hlediska výkonu.  
  
 Druhá metoda pro překlad odkazů na objekty zahrnuje zdrojový objekt CLR, který implementuje rozhraní <xref:System.ComponentModel.INotifyPropertyChanged> a vlastnost zdroje, která je vlastností CLR. V takovém případě modul vazby dat používá reflexi přímo na zdrojovém typu a získá požadovanou vlastnost. Nejedná se o optimální metodu, ale náklady na pracovní sadu, která je nižší než první metoda, bude levnější.  
  
 Třetí metoda pro překlad odkazů na objekty zahrnuje zdrojový objekt, který je <xref:System.Windows.DependencyObject> a zdrojovou vlastnost, která je <xref:System.Windows.DependencyProperty>. V takovém případě nemusí modul vazby dat používat reflexi. Místo toho modul vlastností a modul vazby dat společně vyřeší odkaz na vlastnost nezávisle. Toto je optimální metoda pro překládání odkazů na objekty používané pro datovou vazbu.  
  
 Následující tabulka porovnává rychlost vázání dat <xref:System.Windows.Controls.TextBlock.Text%2A> vlastností 1000 <xref:System.Windows.Controls.TextBlock> prvků pomocí těchto tří metod.  
  
|**Vytvoření vazby vlastnosti text pro TextBlock**|**Čas vazby (MS)**|**Čas vykreslování – zahrnuje vazbu (MS)**|  
|--------------------------------------------------|-----------------------------|--------------------------------------------------|  
|Na vlastnost objektu CLR|115|314|  
|Do vlastnosti objektu CLR, který implementuje <xref:System.ComponentModel.INotifyPropertyChanged>|115|305|  
|Na <xref:System.Windows.DependencyProperty> <xref:System.Windows.DependencyObject>.|90|263|  
  
<a name="Binding_to_Large_CLR_Objects"></a>   
## <a name="binding-to-large-clr-objects"></a>Vazba na velké objekty CLR  
 Existuje značný dopad na výkon při vázání dat na jeden objekt CLR s tisíci vlastností. Tento dopad můžete minimalizovat tak, že jeden objekt vydělíte na více objektů CLR s menším počtem vlastností. Tabulka ukazuje dobu vazby a vykreslování pro datovou vazbu na jeden velký objekt CLR a více menších objektů.  
  
|**Datové vazby 1000 TextBlock objekty**|**Čas vazby (MS)**|**Čas vykreslování – zahrnuje vazbu (MS)**|  
|---------------------------------------------|-----------------------------|--------------------------------------------------|  
|K objektu CLR s vlastností 1000|950|1200|  
|Na 1000 objektů CLR s jednou vlastností|115|314|  
  
<a name="Binding_to_an_ItemsSource"></a>   
## <a name="binding-to-an-itemssource"></a>Vazba na ItemsSource  
 Vezměte v úvahu scénář, ve kterém máte <xref:System.Collections.Generic.List%601> objekt CLR, který obsahuje seznam zaměstnanců, které chcete zobrazit v <xref:System.Windows.Controls.ListBox>. Chcete-li vytvořit korespondenci mezi těmito dvěma objekty, můžete vytvořit propojení seznamu zaměstnanců s vlastností <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.ListBox>. Předpokládejme však, že máte nového zaměstnance, který se připojuje ke skupině. Možná si myslíte, že abyste tuto novou osobu mohli vložit do svých vázaných <xref:System.Windows.Controls.ListBox> hodnot, jednoduše přidáte tuto osobu do svého seznamu zaměstnanců a očekáváte, že tuto změnu budou automaticky rozpoznat modulem vazby dat. Tento předpoklad by prokáže false; ve skutečnosti se změna v <xref:System.Windows.Controls.ListBox> neprojeví automaticky. Důvodem je, že objekt CLR <xref:System.Collections.Generic.List%601> automaticky nevyvolává událost změněné kolekce. Chcete-li získat <xref:System.Windows.Controls.ListBox> pro výběr změn, je nutné znovu vytvořit seznam zaměstnanců a znovu ho připojit k vlastnosti <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.ListBox>. I když toto řešení funguje, přináší značný dopad na výkon. Pokaždé, když znovu přiřadíte <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.ListBox> k novému objektu, <xref:System.Windows.Controls.ListBox> nejprve vyvolá předchozí položky a znovu vygeneruje celý seznam. Dopad na výkon se zvětší, pokud se <xref:System.Windows.Controls.ListBox> mapuje na komplexní <xref:System.Windows.DataTemplate>.  
  
 Velice efektivním řešením tohoto problému je, aby se seznam zaměstnanců <xref:System.Collections.ObjectModel.ObservableCollection%601>. Objekt <xref:System.Collections.ObjectModel.ObservableCollection%601> vyvolá oznámení o změně, které může modul datových vazeb přijmout. Událost přidá nebo odebere položku z <xref:System.Windows.Controls.ItemsControl>, aniž by bylo nutné znovu vygenerovat celý seznam.  
  
 Následující tabulka ukazuje dobu potřebnou k aktualizaci <xref:System.Windows.Controls.ListBox> (s vypnutou virtualizací uživatelského rozhraní), když se přidá jedna položka. Číslo v prvním řádku představuje uplynulý čas, kdy je objekt CLR <xref:System.Collections.Generic.List%601> vázaný na <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A><xref:System.Windows.Controls.ListBox> elementu. Číslo ve druhém řádku představuje uplynulý čas, kdy je <xref:System.Collections.ObjectModel.ObservableCollection%601> svázán s <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>elementu <xref:System.Windows.Controls.ListBox>. Všimněte si výrazné úspory času pomocí <xref:System.Collections.ObjectModel.ObservableCollection%601> strategie vázání dat.  
  
|**Vázání dat na ItemsSource**|**Aktualizovat čas pro 1 položku (MS)**|  
|--------------------------------------|---------------------------------------|  
|Do objektu CLR <xref:System.Collections.Generic.List%601>|1656|  
|Na <xref:System.Collections.ObjectModel.ObservableCollection%601>|20o|  
  
<a name="Binding_IList_to_ItemsControl_not_IEnumerable"></a>   
## <a name="bind-ilist-to-itemscontrol-not-ienumerable"></a>Vazba IList na ItemsControl, které není IEnumerable  
 Pokud máte možnost volby mezi vazbou <xref:System.Collections.Generic.IList%601> nebo <xref:System.Collections.IEnumerable> objektu <xref:System.Windows.Controls.ItemsControl>, zvolte Objekt <xref:System.Collections.Generic.IList%601>. Vazba <xref:System.Collections.IEnumerable> na <xref:System.Windows.Controls.ItemsControl> vynutí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vytvořit Obálkový <xref:System.Collections.Generic.IList%601> objekt, což znamená, že váš výkon bude ovlivněn zbytečnými nároky na druhý objekt.  
  
<a name="Do_not_Convert_CLR_objects_to_Xml_Just_For_Data_Binding"></a>   
## <a name="do-not-convert-clr-objects-to-xml-just-for-data-binding"></a>Neprovádějte převod objektů CLR do XML pouze pro datovou vazbu.  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] umožňuje vytvořit datovou vazby k obsahu XML; vazba dat na obsah XML je však pomalejší než vázání dat na objekty CLR. Neprovádějte převod dat objektu CLR do formátu XML, je-li jediným účelem vytváření datových vazeb.  
  
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
- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Návod: Ukládání aplikačních dat do mezipaměti v aplikaci WPF](walkthrough-caching-application-data-in-a-wpf-application.md)
