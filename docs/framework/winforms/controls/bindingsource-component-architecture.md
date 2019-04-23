---
title: Architektura součásti BindingSource
ms.date: 03/30/2017
helpviewer_keywords:
- BindingSource component [Windows Forms], architecture
- Windows Forms, data binding
- BindingSource component [Windows Forms], about BindingSource component
- data binding [Windows Forms], BindingSource component
ms.assetid: 7bc69c90-8a11-48b1-9336-3adab5b41591
ms.openlocfilehash: 81559444b6e3da2861e48bdc637ae01d246c0758
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59165344"
---
# <a name="bindingsource-component-architecture"></a>Architektura součásti BindingSource
S <xref:System.Windows.Forms.BindingSource> komponentu, můžete ke zdrojům dat univerzálně svázat všechny ovládací prvky Windows Forms.  
  
 <xref:System.Windows.Forms.BindingSource> Komponenty zjednodušuje proces vytvoření vazby ovládacích prvků ke zdroji dat a poskytuje následující výhody oproti tradičním datové vazby:  
  
-   Umožňuje vytvořit vazbu doby návrhu pro obchodní objekty.  
  
-   Zapouzdřuje <xref:System.Windows.Forms.CurrencyManager> funkce a zpřístupňuje <xref:System.Windows.Forms.CurrencyManager> událostí v době návrhu.  
  
-   Zjednodušuje vytváření seznam, který podporuje <xref:System.ComponentModel.IBindingList> rozhraní tím, že poskytuje seznam oznámení o změně pro oznámení o změně zdroje dat, které nativně nepodporují seznamu.  
  
-   Představuje rozšíření pro bod <xref:System.ComponentModel.IBindingList.AddNew%2A?displayProperty=nameWithType> metody.  
  
-   Poskytuje určitou úroveň dereference mezi zdrojem dat a ovládacího prvku. Tuto indirekci je důležité, pokud zdroj dat se může změnit v době běhu.  
  
-   Spolupracuje s jinými ovládacími prvky související s daty Windows Forms konkrétně <xref:System.Windows.Forms.BindingNavigator> a <xref:System.Windows.Forms.DataGridView> ovládací prvky.  
  
 Z těchto důvodů <xref:System.Windows.Forms.BindingSource> komponenta je upřednostňovaný způsob vazby ovládacích prvků Windows Forms ke zdrojům dat.  
  
## <a name="bindingsource-features"></a>BindingSource – funkce  
 <xref:System.Windows.Forms.BindingSource> Součást poskytuje několik funkcí pro vytvoření vazby ovládacích prvků na data. S těmito funkcemi můžete tedy implementovat scénáře většina datové vazby téměř bez kódování z vaší strany.  
  
 <xref:System.Windows.Forms.BindingSource> Součástí toho dosahuje tím, že poskytuje jednotné rozhraní pro přístup k mnoha různých druhů zdrojů dat. To znamená, použijte stejný postup pro vytvoření vazby na libovolný typ. Například můžete připojit <xref:System.Windows.Forms.BindingSource.DataSource%2A> vlastnost <xref:System.Data.DataSet> nebo obchodní objekt a v obou případech použijete stejnou sadu vlastností, metody a události pro manipulaci s zdroj dat.  
  
 Konzistentní rozhraní, poskytuje <xref:System.Windows.Forms.BindingSource> komponenty výrazně zjednodušuje proces vazba dat k ovládacím prvkům. Pro typy zdrojů dat, které poskytují oznámení, změn <xref:System.Windows.Forms.BindingSource> komponenty automaticky komunikuje mezi ovládacím prvkem a zdroj dat změny. Pro typy zdrojů dat, které neposkytují oznámení o změně události jsou k dispozici, které umožňují vytváření oznámení o změnách. Následující seznam obsahuje nepodporované funkce <xref:System.Windows.Forms.BindingSource> komponenty:  
  
-   Indirekce.  
  
-   Správa měny.  
  
-   Zdroj dat jako seznam.  
  
-   <xref:System.Windows.Forms.BindingSource> jako <xref:System.ComponentModel.IBindingList>.  
  
-   Vytvoření vlastní položky.  
  
-   Vytvoření transakční položky.  
  
-   <xref:System.Collections.IEnumerable> podpora.  
  
-   Podpory během návrhu.  
  
-   Statické <xref:System.Windows.Forms.ListBindingHelper> metody.  
  
-   Řazení a filtrování se <xref:System.ComponentModel.IBindingListView> rozhraní.  
  
-   Integrace s <xref:System.Windows.Forms.BindingNavigator>.  
  
### <a name="indirection"></a>Dereference  
 <xref:System.Windows.Forms.BindingSource> Součást poskytuje určitou úroveň dereference mezi ovládacího prvku a zdroji dat. Místo vytvoření vazby ovládacího prvku přímo ke zdroji dat, můžete svázat ovládací prvek <xref:System.Windows.Forms.BindingSource>, a připojení zdroje dat <xref:System.Windows.Forms.BindingSource> komponenty <xref:System.Windows.Forms.BindingSource.DataSource%2A> vlastnost.  
  
 S touto úrovní dereference můžete změnit zdroj dat bez resetování vazbu ovládacího prvku. To vám následující funkce:  
  
-   Můžete připojit <xref:System.Windows.Forms.BindingSource> k různým zdrojům dat. při zachování aktuální vazby ovládacího prvku.  
  
-   Můžete změnit položky ve zdroji dat a upozornit vázané ovládací prvky. Další informace najdete v tématu [jak: Uplatňování aktualizací zdroje dat v ovládacím prvku Windows Forms pomocí BindingSource](reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md).  
  
-   Lze svázat <xref:System.Type> místo objektu v paměti. Další informace najdete v tématu [jak: Vytvoření vazby ovládacího prvku Windows Forms k typu](how-to-bind-a-windows-forms-control-to-a-type.md). Můžete pak vytvoříte vazbu k objektu v době běhu.  
  
### <a name="currency-management"></a>Správa měn  
 <xref:System.Windows.Forms.BindingSource> Komponenta implementuje <xref:System.Windows.Forms.ICurrencyManagerProvider> rozhraní pro zpracování správy měny. S <xref:System.Windows.Forms.ICurrencyManagerProvider> rozhraní, se dá dostat taky pro správce měny pro <xref:System.Windows.Forms.BindingSource>, kromě správce měny pro jiné <xref:System.Windows.Forms.BindingSource> vázána na stejný <xref:System.Windows.Forms.BindingSource.DataMember%2A>.  
  
 <xref:System.Windows.Forms.BindingSource> Komponenty zapouzdřuje <xref:System.Windows.Forms.CurrencyManager> funkce a vystavuje nejčastěji používaných <xref:System.Windows.Forms.CurrencyManager> vlastnosti a události. Následující tabulka popisuje některé členy související se správou měny.  
  
 <xref:System.Windows.Forms.ICurrencyManagerProvider.CurrencyManager%2A> Vlastnost  
 Získá správce měny přidružené <xref:System.Windows.Forms.BindingSource>.  
  
 <xref:System.Windows.Forms.ICurrencyManagerProvider.GetRelatedCurrencyManager%2A> – Metoda  
 Pokud je jiný <xref:System.Windows.Forms.BindingSource> vázán na zadaný datový člen, načte její správce měny.  
  
 <xref:System.Windows.Forms.BindingSource.Current%2A> Vlastnost  
 Získá aktuální položku datového zdroje.  
  
 <xref:System.Windows.Forms.BindingSource.Position%2A> Vlastnost  
 Získá nebo nastaví aktuální pozici v nadřízeném seznamu.  
  
 <xref:System.Windows.Forms.BindingSource.EndEdit%2A> – Metoda  
 Podkladový zdroj dat se týká čekající změny.  
  
 <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> – Metoda  
 Zruší aktuální operaci úprav.  
  
### <a name="data-source-as-a-list"></a>Zdroj dat jako seznam  
 <xref:System.Windows.Forms.BindingSource> Komponenta implementuje <xref:System.ComponentModel.IBindingListView> a <xref:System.ComponentModel.ITypedList> rozhraní. V této implementaci můžete použít <xref:System.Windows.Forms.BindingSource> komponentu jako zdroj dat, bez jakékoli externího úložiště.  
  
 Když <xref:System.Windows.Forms.BindingSource> komponenta je připojen ke zdroji dat, poskytuje zdroj dat jako seznam.  
  
 <xref:System.Windows.Forms.BindingSource.DataSource%2A> Vlastnost lze nastavit k několika zdrojům dat. Patří mezi ně typy objektů a typy seznamů. Výsledný zdroj dat se zveřejní jako seznam. V následující tabulce jsou uvedeny některé běžné zdroje dat a výsledný seznam vyhodnocení.  
  
|Vlastnost DataSource|Seznam výsledků|  
|-------------------------|------------------|  
|Odkaz s hodnotou null (`Nothing` v jazyce Visual Basic)|Prázdná <xref:System.ComponentModel.IBindingList> objektů. Přidání položky nastaví seznam typu přidanou položku.|  
|Odkaz s hodnotou null (`Nothing` v jazyce Visual Basic) s <xref:System.Windows.Forms.BindingSource.DataMember%2A> nastavení|Nejsou podporovány. Vyvolá <xref:System.ArgumentException>.|  
|Typ bez seznamu nebo objekt typu "T"|Prázdná <xref:System.ComponentModel.IBindingList> typu "T".|  
|Pole instance|<xref:System.ComponentModel.IBindingList> Obsahující prvky pole.|  
|<xref:System.Collections.IEnumerable> instance|<xref:System.ComponentModel.IBindingList> Obsahující <xref:System.Collections.IEnumerable> položky|  
|Seznam obsahující typ instance "T"|<xref:System.ComponentModel.IBindingList> Instance obsahující typ "T".|  
  
 Kromě toho <xref:System.Windows.Forms.BindingSource.DataSource%2A> lze nastavit na jiné typy seznamu, jako například <xref:System.ComponentModel.IListSource> a <xref:System.ComponentModel.ITypedList>a <xref:System.Windows.Forms.BindingSource> jejich zpracování odpovídajícím způsobem. Typ, který je obsažen v seznamu v tomto případě by měl mít výchozí konstruktor.  
  
### <a name="bindingsource-as-an-ibindinglist"></a>Objekt BindingSource jako rozhraní IBindingList  
 <xref:System.Windows.Forms.BindingSource> Součást poskytuje členy pro přístup k a manipulaci se podkladových dat jako <xref:System.ComponentModel.IBindingList>. Následující tabulka popisuje některé z těchto členů.  
  
|Člen|Popis|  
|------------|-----------------|  
|<xref:System.Windows.Forms.BindingSource.List%2A> Vlastnost|Získá seznam, který je výsledkem vyhodnocení <xref:System.Windows.Forms.BindingSource.DataSource%2A> nebo <xref:System.Windows.Forms.BindingSource.DataMember%2A> vlastnosti.|  
|<xref:System.Windows.Forms.BindingSource.AddNew%2A> – Metoda|Přidá novou položku do seznamu základní. Platí pro zdroje dat, které implementují <xref:System.ComponentModel.IBindingList> rozhraní a povolit přidávání položek (to znamená <xref:System.Windows.Forms.BindingSource.AllowNew%2A> je nastavena na `true`).|  
  
### <a name="custom-item-creation"></a>Vytvoření vlastní položky  
 Dokáže zpracovat <xref:System.Windows.Forms.BindingSource.AddingNew> události poskytnout vlastní logiku vytvoření položky. <xref:System.Windows.Forms.BindingSource.AddingNew> Před přidáním nového objektu do dojde k události <xref:System.Windows.Forms.BindingSource>. Tato událost je aktivována po <xref:System.Windows.Forms.BindingSource.AddNew%2A> metoda je volána, ale předtím, než je na nadřízeném seznamu přidá nová položka. Díky zpracování této události, můžete zadat chování vytvoření vlastní položky bez odvozený od <xref:System.Windows.Forms.BindingSource> třídy. Další informace najdete v tématu [jak: Přizpůsobení přidávání položek pomocí Windows Forms BindingSource](how-to-customize-item-addition-with-the-windows-forms-bindingsource.md).  
  
### <a name="transactional-item-creation"></a>Vytvoření transakční položky  
 <xref:System.Windows.Forms.BindingSource> Komponenta implementuje <xref:System.ComponentModel.ICancelAddNew> rozhraní, které umožňuje vytvoření transakční položky. Po vytvoření nové položky dočasně pomocí volání <xref:System.Windows.Forms.BindingSource.AddNew%2A>, přidání mohou být potvrzena nebo vrácena zpět následujícími způsoby:  
  
-   <xref:System.ComponentModel.ICancelAddNew.EndNew%2A> Metoda explicitně potvrzení změn přidání čekajícího na zpracování.  
  
-   Probíhá jiná operace kolekce, například vložení, odebrání nebo přesunutí, budou implicitně potvrzení přidání čekajícího na zpracování.  
  
-   <xref:System.ComponentModel.ICancelAddNew.CancelNew%2A> Metoda se vrátit zpět, přidání čekajícího na zpracování Pokud metody již nebyla potvrzena.  
  
### <a name="ienumerable-support"></a>Podpora IEnumerable  
 <xref:System.Windows.Forms.BindingSource> Komponenta povoluje vazba ovládacích prvků s <xref:System.Collections.IEnumerable> zdrojů. Tato součást je možné svázat ke zdroji dat, jako <xref:System.Data.SqlClient.SqlDataReader?displayProperty=nameWithType>.  
  
 Při <xref:System.Collections.IEnumerable> zdroj dat je přiřazený k <xref:System.Windows.Forms.BindingSource> komponenty, <xref:System.Windows.Forms.BindingSource> vytvoří <xref:System.ComponentModel.IBindingList> a přidá obsah <xref:System.Collections.IEnumerable> zdroj dat do seznamu.  
  
### <a name="design-time-support"></a>Podpory během návrhu  
 Některé typy objektů nelze vytvořit v době návrhu, jako jsou objekty vytvořené z třídu objektů factory nebo objekty vrácené webové služby. V některých případech možná k vytvoření vazby ovládacích prvků pro tyto typy v době návrhu, i když není žádný objekt v paměti, ke kterému můžete svázat ovládací prvky. Například může potřebovat k popisu záhlaví sloupců z <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvy vlastností vlastního typu public.  
  
 Pro podporu tohoto scénáře <xref:System.Windows.Forms.BindingSource> komponenta podporuje vazbu <xref:System.Type>. Když přiřadíte <xref:System.Type> k <xref:System.Windows.Forms.BindingSource.DataSource%2A> vlastnost, <xref:System.Windows.Forms.BindingSource> komponenta vytvoří prázdnou <xref:System.ComponentModel.BindingList%601> z <xref:System.Type> položky. Následně svázat ovládací prvky <xref:System.Windows.Forms.BindingSource> komponenty upozorněni na přítomnost vlastnosti nebo schématu typu v době návrhu nebo v době běhu. Další informace najdete v tématu [jak: Vytvoření vazby ovládacího prvku Windows Forms k typu](how-to-bind-a-windows-forms-control-to-a-type.md).  
  
### <a name="static-listbindinghelper-methods"></a>Statické ListBindingHelper metody  
 <xref:System.Windows.Forms.BindingContext?displayProperty=nameWithType>, <xref:System.Windows.Forms.CurrencyManager?displayProperty=nameWithType>, A <xref:System.Windows.Forms.BindingSource> veškerou logiku běžné sdílené složky pro vygenerování seznamu z typů `DataSource` / `DataMember` pár. Kromě toho tato běžné logika je veřejně zpřístupnit pro použití autoři ovládacího prvku a jiných třetích stran v následujícím `static` metody:  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetListItemProperties%2A>  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetList%2A>.  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetListName%2A>  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetListItemType%2A>  
  
### <a name="sorting-and-filtering-with-the-ibindinglistview-interface"></a>Řazení a filtrování pomocí rozhraní IBindingListView  
 <xref:System.Windows.Forms.BindingSource> Komponenta implementuje <xref:System.ComponentModel.IBindingListView> rozhraní, která rozšiřuje <xref:System.ComponentModel.IBindingList> rozhraní. <xref:System.ComponentModel.IBindingList> Nabízí řazení jednoho sloupce a <xref:System.ComponentModel.IBindingListView> nabízí rozšířené řazení a filtrování. S <xref:System.ComponentModel.IBindingListView>, můžete seřadit a filtrovat položky ve zdroji dat, pokud zdroj dat také implementuje jednu z těchto rozhraní. <xref:System.Windows.Forms.BindingSource> Součást neposkytuje referenční implementace těchto členů. Místo toho volání jsou předány podkladový seznam.  
  
 Následující tabulka popisuje vlastnosti, které se použijí k řazení a filtrování.  
  
|Člen|Popis|  
|------------|-----------------|  
|<xref:System.Windows.Forms.BindingSource.Filter%2A> Vlastnost|Pokud je zdroj dat <xref:System.ComponentModel.IBindingListView>, získá nebo nastaví výraz určený k filtrování, které řádky jsou zobrazeny.|  
|<xref:System.Windows.Forms.BindingSource.Sort%2A> Vlastnost|Pokud je zdroj dat <xref:System.ComponentModel.IBindingList>, získá nebo nastaví název sloupce pro řazení a informace o pořadí řazení.<br /><br /> -nebo-<br /><br /> Pokud je zdroj dat <xref:System.ComponentModel.IBindingListView> a podporuje rozšířené řazení, získá více názvů sloupců použité pro řazení a pořadí řazení|  
  
### <a name="integration-with-bindingnavigator"></a>Integrace s BindingNavigator  
 Můžete použít <xref:System.Windows.Forms.BindingSource> součásti pro vytvoření vazby libovolný ovládací prvek Windows Forms ke zdroji dat, ale <xref:System.Windows.Forms.BindingNavigator> ovládacího prvku je určený konkrétně pro práci s <xref:System.Windows.Forms.BindingSource> komponenty. <xref:System.Windows.Forms.BindingNavigator> Ovládacího prvku poskytuje uživatelské rozhraní pro řízení <xref:System.Windows.Forms.BindingSource> komponenty aktuální položky. Ve výchozím nastavení <xref:System.Windows.Forms.BindingNavigator> poskytuje ovládací prvek tlačítka, která odpovídají na metody navigace na <xref:System.Windows.Forms.BindingSource> komponenty. Další informace najdete v tématu [jak: Navigace daty pomocí ovládacího prvku Windows Forms BindingNavigator](how-to-navigate-data-with-the-windows-forms-bindingnavigator-control.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.BindingNavigator>
- [Přehled komponenty BindingSource](bindingsource-component-overview.md)
- [Ovládací prvek BindingNavigator](bindingnavigator-control-windows-forms.md)
- [Windows Forms – datová vazba](../windows-forms-data-binding.md)
- [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)
- [Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu](how-to-bind-a-windows-forms-control-to-a-type.md)
- [Postupy: Uplatňování aktualizací zdroje dat v ovládacím prvku Windows Forms pomocí BindingSource](reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)
