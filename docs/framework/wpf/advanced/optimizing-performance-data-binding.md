---
title: 'Optimalizace výkonu: Datová vazba'
ms.date: 03/30/2017
helpviewer_keywords:
- binding data [WPF], performance
- data binding [WPF], performance
ms.assetid: 1506a35d-c009-43db-9f1e-4e230ad5be73
ms.openlocfilehash: 3128f453378f9d74f867b571e30f2be4e8add8a4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186762"
---
# <a name="optimizing-performance-data-binding"></a>Optimalizace výkonu: Datová vazba
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]datová vazba poskytuje jednoduchý a konzistentní způsob, jak mohou aplikace prezentovat data a pracovat s nimi. Prvky mohou být vázány na data z různých zdrojů dat ve formě objektů CLR a XML.  
  
 Toto téma obsahuje doporučení pro výkon datové vazby.  

<a name="HowDataBindingReferencesAreResolved"></a>
## <a name="how-data-binding-references-are-resolved"></a>Jak jsou vyřešeny odkazy na datové vazby  
 Před diskutovat o problémy s výkonem datové [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vazby, je vhodné prozkoumat, jak modul datové vazby řeší odkazy na objekty pro vazbu.  
  
 Zdrojem [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] datové vazby může být libovolný objekt CLR. Můžete vytvořit vazbu na vlastnosti, dílčí vlastnosti nebo indexery objektu CLR. Odkazy na vazby jsou vyřešeny pomocí reflexe <xref:System.ComponentModel.ICustomTypeDescriptor>rozhraní Microsoft .NET Framework nebo . Zde jsou tři metody pro řešení odkazů na objekty pro vazbu.  
  
 První metoda zahrnuje použití reflexe. V tomto případě <xref:System.Reflection.PropertyInfo> se objekt používá ke zjištění atributů vlastnosti a poskytuje přístup k metadatům vlastnosti. Při použití <xref:System.ComponentModel.ICustomTypeDescriptor> rozhraní modul datové vazby používá toto rozhraní pro přístup k hodnotám vlastností. Rozhraní <xref:System.ComponentModel.ICustomTypeDescriptor> je užitečné zejména v případech, kdy objekt nemá statickou sadu vlastností.  
  
 Oznámení o změně vlastnosti lze poskytnout <xref:System.ComponentModel.INotifyPropertyChanged> buď implementací rozhraní, nebo <xref:System.ComponentModel.TypeDescriptor>pomocí oznámení o změně přidružených k rozhraní . Upřednostňovanou strategií pro implementaci oznámení o změně <xref:System.ComponentModel.INotifyPropertyChanged>vlastností je však použití .  
  
 Pokud je zdrojový objekt objekt CLR a vlastnost source je [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] vlastnost CLR, modul datové vazby musí <xref:System.ComponentModel.TypeDescriptor>nejprve použít <xref:System.ComponentModel.PropertyDescriptor>reflexe na zdrojový objekt získat a potom dotaz na . Tato posloupnost operací reflexe je potenciálně velmi časově náročné z hlediska výkonu.  
  
 Druhá metoda pro řešení odkazů na objekt zahrnuje zdrojový objekt <xref:System.ComponentModel.INotifyPropertyChanged> CLR, který implementuje rozhraní, a zdrojovou vlastnost, která je vlastností CLR. V tomto případě modul datové vazby používá reflexe přímo na typ zdroje a získá požadovanou vlastnost. To stále není optimální metoda, ale bude stát méně v požadavcích pracovní sady než první metoda.  
  
 Třetí metoda pro řešení odkazů na objekt zahrnuje <xref:System.Windows.DependencyObject> zdrojový objekt, který <xref:System.Windows.DependencyProperty>je a zdrojvlastnost, která je . V tomto případě modul datové vazby není nutné použít reflexe. Místo toho modul vlastností a modul datové vazby společně vyřešit odkaz na vlastnost nezávisle. Toto je optimální metoda pro řešení odkazů na objekty používané pro datové vazby.  
  
 Níže uvedená tabulka porovnává rychlost <xref:System.Windows.Controls.TextBlock.Text%2A> datové vazby <xref:System.Windows.Controls.TextBlock> vlastnost tisíc prvků pomocí těchto tří metod.  
  
|**Vazba Text vlastnost TextBlock**|**Doba vazby (ms)**|**Doba vykreslování -- zahrnuje vazbu (ms)**|  
|--------------------------------------------------|-----------------------------|--------------------------------------------------|  
|K vlastnosti objektu CLR|115|314|  
|K vlastnosti objektu CLR, který implementuje<xref:System.ComponentModel.INotifyPropertyChanged>|115|305|  
|Na <xref:System.Windows.DependencyProperty> . <xref:System.Windows.DependencyObject>|90|263|  
  
<a name="Binding_to_Large_CLR_Objects"></a>
## <a name="binding-to-large-clr-objects"></a>Vazba na velké objekty CLR  
 Při vazbě dat na jeden objekt CLR s tisíci vlastnostmi je významný dopad na výkon. Tento dopad můžete minimalizovat rozdělením jednoho objektu na více objektů CLR s menším počtem vlastností. Tabulka zobrazuje časy vazby a vykreslování pro datové vazby na jeden velký objekt CLR versus více menších objektů.  
  
|**Datové vazby 1000 TextBlock objekty**|**Doba vazby (ms)**|**Doba vykreslování -- zahrnuje vazbu (ms)**|  
|---------------------------------------------|-----------------------------|--------------------------------------------------|  
|K objektu CLR s vlastnostmi 1000|950|1200|  
|Až 1000 CLR objektů s jednou vlastností|115|314|  
  
<a name="Binding_to_an_ItemsSource"></a>
## <a name="binding-to-an-itemssource"></a>Vazba na ItemsSource  
 Zvažte scénář, ve kterém <xref:System.Collections.Generic.List%601> máte objekt CLR, který obsahuje seznam <xref:System.Windows.Controls.ListBox>zaměstnanců, které chcete zobrazit v . Chcete-li vytvořit korespondenci mezi těmito dvěma <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> objekty, <xref:System.Windows.Controls.ListBox>spojte seznam zaměstnanců s vlastností . Předpokládejme však, že máte nového zaměstnance, který se připojuje ke skupině. Možná si myslíte, že chcete-li vložit <xref:System.Windows.Controls.ListBox> tuto novou osobu do vázaných hodnot, jednoduše byste tuto osobu přidali do seznamu zaměstnanců a očekávali, že tato změna bude automaticky rozpoznána motorem datové vazby. Tento předpoklad by se ukázal jako nepravdivý; ve skutečnosti se změna automaticky neprojeví. <xref:System.Windows.Controls.ListBox> Důvodem je, <xref:System.Collections.Generic.List%601> že objekt CLR automaticky nevyvolá událost změněné kolekce. Chcete-li získat <xref:System.Windows.Controls.ListBox> vyzvednout změny, budete muset znovu vytvořit seznam zaměstnanců a znovu jej <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> připojit <xref:System.Windows.Controls.ListBox>k majetku . I když toto řešení funguje, přináší obrovský dopad na výkon. Pokaždé, když znovu <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.ListBox> přiřadíte z <xref:System.Windows.Controls.ListBox> na nový objekt, první vyhodí své předchozí položky a regeneruje celý svůj seznam. Dopad na výkon se <xref:System.Windows.Controls.ListBox> zvětší, <xref:System.Windows.DataTemplate>pokud se mapuje na komplex .  
  
 Velmi efektivní řešení tohoto problému je, aby <xref:System.Collections.ObjectModel.ObservableCollection%601>se váš seznam zaměstnanců . Objekt <xref:System.Collections.ObjectModel.ObservableCollection%601> vyvolá oznámení o změně, které může přijímat modul datové vazby. Událost přidá nebo odebere položku <xref:System.Windows.Controls.ItemsControl> z bez nutnosti regenerovat celý seznam.  
  
 V následující tabulce je uveden čas <xref:System.Windows.Controls.ListBox> potřebný k aktualizaci (s vypnutou virtualizací ui), když je přidána jedna položka. Číslo v prvním řádku představuje uplynulý čas, <xref:System.Collections.Generic.List%601> kdy je <xref:System.Windows.Controls.ListBox> objekt CLR vázán na prvek <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>. Číslo v druhém řádku představuje uplynulý čas, kdy <xref:System.Collections.ObjectModel.ObservableCollection%601> <xref:System.Windows.Controls.ListBox> je vázán <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>na prvek . Všimněte si významné <xref:System.Collections.ObjectModel.ObservableCollection%601> úspory času pomocí strategie datové vazby.  
  
|**Datová vazba ItemsSource**|**Čas aktualizace pro 1 položku (ms)**|  
|--------------------------------------|---------------------------------------|  
|K objektu <xref:System.Collections.Generic.List%601> CLR|1656|  
|Chcete-li<xref:System.Collections.ObjectModel.ObservableCollection%601>|20|  
  
<a name="Binding_IList_to_ItemsControl_not_IEnumerable"></a>
## <a name="bind-ilist-to-itemscontrol-not-ienumerable"></a>Vytvořit vazbu IList na položky: Ovládací prvek Není nelze sčetněn.  
 Pokud máte na výběr <xref:System.Collections.Generic.IList%601> mezi <xref:System.Collections.IEnumerable> vazbou <xref:System.Windows.Controls.ItemsControl> nebo objektem, zvolte <xref:System.Collections.Generic.IList%601> objekt. Vazba <xref:System.Collections.IEnumerable> <xref:System.Windows.Controls.ItemsControl> na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] síly k <xref:System.Collections.Generic.IList%601> vytvoření objektu obálky, což znamená, že výkon je ovlivněn zbytečné režie druhého objektu.  
  
<a name="Do_not_Convert_CLR_objects_to_Xml_Just_For_Data_Binding"></a>
## <a name="do-not-convert-clr-objects-to-xml-just-for-data-binding"></a>Nepřevádějí objekty CLR na XML pouze pro datová vazba.  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]umožňuje svázat data s obsahem XML; datová vazba na obsah XML je však pomalejší než datová vazba na objekty CLR. Nepřevádíte data objektu CLR do xml, pokud je jediným účelem pro datovou vazbu.  
  
## <a name="see-also"></a>Viz také

- [Optimalizace výkonu aplikace WPF](optimizing-wpf-application-performance.md)
- [Plánování výkonu aplikace](planning-for-application-performance.md)
- [Využití výhod hardwaru](optimizing-performance-taking-advantage-of-hardware.md)
- [Rozložení a návrh](optimizing-performance-layout-and-design.md)
- [2D grafika a obrázky](optimizing-performance-2d-graphics-and-imaging.md)
- [Chování objektu](optimizing-performance-object-behavior.md)
- [Prostředky aplikace](optimizing-performance-application-resources.md)
- [Text](optimizing-performance-text.md)
- [Další doporučení k optimalizaci výkonu](optimizing-performance-other-recommendations.md)
- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Návod: Ukládání aplikačních dat do mezipaměti v aplikaci WPF](walkthrough-caching-application-data-in-a-wpf-application.md)
