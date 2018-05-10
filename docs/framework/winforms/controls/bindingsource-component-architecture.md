---
title: Architektura součásti BindingSource
ms.date: 03/30/2017
helpviewer_keywords:
- BindingSource component [Windows Forms], architecture
- Windows Forms, data binding
- BindingSource component [Windows Forms], about BindingSource component
- data binding [Windows Forms], BindingSource component
ms.assetid: 7bc69c90-8a11-48b1-9336-3adab5b41591
ms.openlocfilehash: b0334bd7a0bc5ff46c43fd7ee549422d98c35efe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="bindingsource-component-architecture"></a>Architektura součásti BindingSource
Pomocí <xref:System.Windows.Forms.BindingSource> součásti, všechny ovládací prvky Windows Forms všeobecně můžete vázat na datové zdroje.  
  
 <xref:System.Windows.Forms.BindingSource> Součást zjednodušuje proces vytvoření vazby ovládacích prvků ke zdroji dat a nabízí následující výhody přes tradiční datové vazby:  
  
-   Umožňuje návrhu vazby na objekty firmy.  
  
-   Zapouzdří <xref:System.Windows.Forms.CurrencyManager> funkce a zpřístupňuje <xref:System.Windows.Forms.CurrencyManager> události v době návrhu.  
  
-   Zjednodušuje vytváření seznamu, který podporuje <xref:System.ComponentModel.IBindingList> rozhraní tím, že poskytuje seznam oznámení o změně pro oznámení o změně zdroje dat, které nativně nepodporují seznamu.  
  
-   Poskytuje bod rozšiřitelnosti pro <xref:System.ComponentModel.IBindingList.AddNew%2A?displayProperty=nameWithType> metoda.  
  
-   Poskytuje úroveň dereference mezi zdroji dat a ovládacího prvku. Tento indirection je důležité, pokud zdroj dat může změnit za běhu.  
  
-   Umožňuje spolupráci s další data související s Windows Forms – ovládací prvky, konkrétně <xref:System.Windows.Forms.BindingNavigator> a <xref:System.Windows.Forms.DataGridView> ovládací prvky.  
  
 Z těchto důvodů <xref:System.Windows.Forms.BindingSource> součást je upřednostňovaný způsob, jak vytvoření vazby ovládacích prvků Windows Forms ke zdrojům dat.  
  
## <a name="bindingsource-features"></a>Funkce BindingSource  
 <xref:System.Windows.Forms.BindingSource> Součást poskytuje několik funkcí pro vytvoření vazby ovládacích prvků k datům. S těmito funkcemi můžete implementovat Většina scénářů vazby dat s téměř žádné kódování z vaší strany.  
  
 <xref:System.Windows.Forms.BindingSource> Součástí toho dosahuje tím, že poskytuje jednotné rozhraní pro přístup k mnoha různých druhů zdrojů dat. To znamená, že používáte stejný postup pro vazbu k libovolnému typu. Například můžete připojit <xref:System.Windows.Forms.BindingSource.DataSource%2A> vlastnosti <xref:System.Data.DataSet> nebo k objektu firmy a v obou případech použijete stejnou sadu událostí, vlastnosti a metody k manipulaci se zdroji dat.  
  
 Konzistentní rozhraní služby <xref:System.Windows.Forms.BindingSource> součást výrazně se zjednodušuje proces svázání dat s ovládacími prvky. Pro typy zdrojů dat, které poskytují změnit oznámení, <xref:System.Windows.Forms.BindingSource> součást automaticky změny mezi ovládacího prvku a zdroje dat komunikuje. Pro typy zdrojů dat, které neposkytuje oznámení o změně události jsou k dispozici, které umožňují vytváření oznámení o změnách. V následujícím seznamu jsou funkcí podporovaných <xref:System.Windows.Forms.BindingSource> součásti:  
  
-   Indirection.  
  
-   Správa měny.  
  
-   Zdroj dat jako seznam.  
  
-   <xref:System.Windows.Forms.BindingSource> jako <xref:System.ComponentModel.IBindingList>.  
  
-   Vytvoření vlastní položky.  
  
-   Vytvoření položky transakcí.  
  
-   <xref:System.Collections.IEnumerable> podpora.  
  
-   Podpora návrhu.  
  
-   Statické <xref:System.Windows.Forms.ListBindingHelper> metody.  
  
-   Řazení a filtrování pomocí <xref:System.ComponentModel.IBindingListView> rozhraní.  
  
-   Integrace s <xref:System.Windows.Forms.BindingNavigator>.  
  
### <a name="indirection"></a>Dereference  
 <xref:System.Windows.Forms.BindingSource> Součást poskytuje úroveň dereference mezi ovládacího prvku a zdroj dat. Místo vytvoření vazby ovládacího prvku přímo na zdroj dat, svázat ovládací prvek <xref:System.Windows.Forms.BindingSource>, a připojte zdroje dat pro <xref:System.Windows.Forms.BindingSource> součásti <xref:System.Windows.Forms.BindingSource.DataSource%2A> vlastnost.  
  
 Při této úrovni dereference můžete změnit zdroj dat bez resetování Vazba ovládacího prvku. To vám poskytuje následující možnosti:  
  
-   Můžete připojit <xref:System.Windows.Forms.BindingSource> pro různé datové zdroje a přitom zachovat aktuální vazby ovládacího prvku.  
  
-   Můžete změnit položky ve zdroji dat a oznámit vázané ovládací prvky. Další informace najdete v tématu [postup: odráží aktualizací zdroje dat v ovládacím prvku Windows Forms pomocí BindingSource](../../../../docs/framework/winforms/controls/reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md).  
  
-   Můžete vázat na <xref:System.Type> namísto objektu v paměti. Další informace najdete v tématu [postupy: vytvoření vazby ovládacího prvku Windows Forms k typu](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md). Potom můžete vázat na objekt v době běhu.  
  
### <a name="currency-management"></a>Měna správy  
 <xref:System.Windows.Forms.BindingSource> Součást implementuje <xref:System.Windows.Forms.ICurrencyManagerProvider> rozhraní pro správu měna pro vás. S <xref:System.Windows.Forms.ICurrencyManagerProvider> rozhraní, můžete taky přejít do správce měna pro <xref:System.Windows.Forms.BindingSource>, kromě manager měna pro jinou <xref:System.Windows.Forms.BindingSource> vázána na stejné <xref:System.Windows.Forms.BindingSource.DataMember%2A>.  
  
 <xref:System.Windows.Forms.BindingSource> Součást zapouzdří <xref:System.Windows.Forms.CurrencyManager> funkce a zpřístupňuje nejobvyklejší <xref:System.Windows.Forms.CurrencyManager> vlastností a událostí. Následující tabulka popisuje některé členy související se správou měny.  
  
 <xref:System.Windows.Forms.ICurrencyManagerProvider.CurrencyManager%2A> Vlastnost  
 Získá správce měna přidružené <xref:System.Windows.Forms.BindingSource>.  
  
 <xref:System.Windows.Forms.ICurrencyManagerProvider.GetRelatedCurrencyManager%2A> – Metoda  
 Pokud je jiné <xref:System.Windows.Forms.BindingSource> vázané na zadaný datový člen, získá jeho správce měny.  
  
 <xref:System.Windows.Forms.BindingSource.Current%2A> Vlastnost  
 Získá aktuální položku datového zdroje.  
  
 <xref:System.Windows.Forms.BindingSource.Position%2A> Vlastnost  
 Získá nebo nastaví aktuální pozici v podkladový seznam.  
  
 <xref:System.Windows.Forms.BindingSource.EndEdit%2A> – Metoda  
 Platí pro daný zdroj dat. změny čekající na zpracování.  
  
 <xref:System.Windows.Forms.BindingSource.CancelEdit%2A> – Metoda  
 Zruší aktuální operace upravit.  
  
### <a name="data-source-as-a-list"></a>Zdroj dat jako seznam  
 <xref:System.Windows.Forms.BindingSource> Součást implementuje <xref:System.ComponentModel.IBindingListView> a <xref:System.ComponentModel.ITypedList> rozhraní. S touto implementací, můžete použít <xref:System.Windows.Forms.BindingSource> součást sám sebe jako zdroj dat, bez jakékoli externí úložiště.  
  
 Když <xref:System.Windows.Forms.BindingSource> součást je připojený ke zdroji dat, zpřístupňuje zdroji dat jako seznam.  
  
 <xref:System.Windows.Forms.BindingSource.DataSource%2A> Vlastnost lze nastavit pro několik zdrojů dat. Mezi ně patří typy objektů a typy seznamů. Výsledný zdroj dat k dispozici jako seznam. Následující tabulka uvádí některé běžné zdroje dat a výsledný seznam vyhodnocení.  
  
|Vlastnost DataSource|Seznam výsledků|  
|-------------------------|------------------|  
|Odkaz s hodnotou null (`Nothing` v jazyce Visual Basic)|Prázdná <xref:System.ComponentModel.IBindingList> objektů. Přidání položky seznamu nastaví typ přidané položky.|  
|Odkaz s hodnotou null (`Nothing` v jazyce Visual Basic) s <xref:System.Windows.Forms.BindingSource.DataMember%2A> nastavit|Nepodporuje; Vyvolá <xref:System.ArgumentException>.|  
|Typ non-list nebo objektu typu "T"|Prázdná <xref:System.ComponentModel.IBindingList> typu "T".|  
|Pole instance|<xref:System.ComponentModel.IBindingList> Obsahující elementy pole.|  
|<xref:System.Collections.IEnumerable> Instance|<xref:System.ComponentModel.IBindingList> Obsahující <xref:System.Collections.IEnumerable> položky|  
|Seznam obsahující typ instance "T"|<xref:System.ComponentModel.IBindingList> Instance obsahující typ "T".|  
  
 Kromě toho <xref:System.Windows.Forms.BindingSource.DataSource%2A> lze nastavit na jiné typy seznamu, jako například <xref:System.ComponentModel.IListSource> a <xref:System.ComponentModel.ITypedList>a <xref:System.Windows.Forms.BindingSource> je zpracování správně. Typ, který se nachází v seznamu v takovém případě by měl mít výchozí konstruktor.  
  
### <a name="bindingsource-as-an-ibindinglist"></a>BindingSource jako IBindingList  
 <xref:System.Windows.Forms.BindingSource> Součást poskytuje členy pro přístup k informacím a manipulaci s daty základní jako <xref:System.ComponentModel.IBindingList>. Následující tabulka popisuje některé z těchto členů.  
  
|Člen|Popis|  
|------------|-----------------|  
|<xref:System.Windows.Forms.BindingSource.List%2A> Vlastnost|Získá seznam, který je výsledkem vyhodnocení <xref:System.Windows.Forms.BindingSource.DataSource%2A> nebo <xref:System.Windows.Forms.BindingSource.DataMember%2A> vlastnosti.|  
|<xref:System.Windows.Forms.BindingSource.AddNew%2A> – Metoda|Přidá novou položku do podkladový seznam. Platí pro zdroje dat, které implementují <xref:System.ComponentModel.IBindingList> rozhraní a povolit přidávání položek (který je <xref:System.Windows.Forms.BindingSource.AllowNew%2A> je nastavena na `true`).|  
  
### <a name="custom-item-creation"></a>Vytvoření vlastní položky  
 Může zpracovat <xref:System.Windows.Forms.BindingSource.AddingNew> událost a poskytuje logika vytvoření položky. <xref:System.Windows.Forms.BindingSource.AddingNew> Události dojde před přidáním nového objektu do <xref:System.Windows.Forms.BindingSource>. Tato událost se vyvolá po <xref:System.Windows.Forms.BindingSource.AddNew%2A> metoda je volána, ale předtím, než je do seznamu základní přidat novou položku. Při zpracování této událost, můžete zadat chování vytvoření vlastní položky bez odvozování z <xref:System.Windows.Forms.BindingSource> třídy. Další informace najdete v tématu [postupy: přizpůsobení přidávání položek pomocí Windows Forms BindingSource](../../../../docs/framework/winforms/controls/how-to-customize-item-addition-with-the-windows-forms-bindingsource.md).  
  
### <a name="transactional-item-creation"></a>Vytvoření položky transakcí  
 <xref:System.Windows.Forms.BindingSource> Součást implementuje <xref:System.ComponentModel.ICancelAddNew> rozhraní, což umožňuje vytvoření transakční položky. Po vytvoření nové položky podmíněně pomocí volání <xref:System.Windows.Forms.BindingSource.AddNew%2A>, přidání může být potvrzena nebo vrácena zpět následujícími způsoby:  
  
-   <xref:System.ComponentModel.ICancelAddNew.EndNew%2A> Metoda bude explicitně Potvrdit přidání čeká na zpracování.  
  
-   Provádění operace kolekce, například vložení, odebrání nebo přesunutí, budou implicitně potvrdit čekající přidání.  
  
-   <xref:System.ComponentModel.ICancelAddNew.CancelNew%2A> Metoda se vrátit zpět, čekající přidání Pokud metoda nebyla již byla potvrzena.  
  
### <a name="ienumerable-support"></a>Podpora rozhraní IEnumerable  
 <xref:System.Windows.Forms.BindingSource> Součást umožňuje vazba ovládacích prvků na <xref:System.Collections.IEnumerable> datové zdroje. Tato součást je možné svázat se zdrojem dat, jako <xref:System.Data.SqlClient.SqlDataReader?displayProperty=nameWithType>.  
  
 Když <xref:System.Collections.IEnumerable> zdroj dat je přiřazena k <xref:System.Windows.Forms.BindingSource> součást, <xref:System.Windows.Forms.BindingSource> vytvoří <xref:System.ComponentModel.IBindingList> a přidá obsah <xref:System.Collections.IEnumerable> zdroje dat do seznamu.  
  
### <a name="design-time-support"></a>Podpora návrh  
 Některé typy objektů nelze vytvořit v době návrhu, jako je například objekty vytvořené z třídy objektu pro vytváření nebo objektů vrácený webové služby. Může někdy nutné k vytvoření vazby ovládacích prvků těchto typů v době návrhu, i když se žádný objekt v paměti, ke kterému lze vázat vaše ovládací prvky. Můžete například potřebovat pro označení záhlaví sloupců z <xref:System.Windows.Forms.DataGridView> ovládacího prvku s názvy veřejných vlastností vlastního typu.  
  
 Pro podporu tohoto scénáře <xref:System.Windows.Forms.BindingSource> součást podporuje vazby ke <xref:System.Type>. Přiřadíte-li <xref:System.Type> k <xref:System.Windows.Forms.BindingSource.DataSource%2A> vlastnost, <xref:System.Windows.Forms.BindingSource> součást vytvoří prázdnou <xref:System.ComponentModel.BindingList%601> z <xref:System.Type> položky. Všechny ovládací prvky můžete následně vytvořit vazbu k <xref:System.Windows.Forms.BindingSource> součást upozorněni na přítomnost vlastnosti nebo schéma vašeho typu v době návrhu nebo za běhu. Další informace najdete v tématu [postupy: vytvoření vazby ovládacího prvku Windows Forms k typu](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md).  
  
### <a name="static-listbindinghelper-methods"></a>Statické ListBindingHelper metody  
 <xref:System.Windows.Forms.BindingContext?displayProperty=nameWithType>, <xref:System.Windows.Forms.CurrencyManager?displayProperty=nameWithType>, A <xref:System.Windows.Forms.BindingSource> typy veškerou logiku běžné sdílené složky a vygenerujte seznam z `DataSource` / `DataMember` pár. Kromě toho tato běžné logika je veřejně vystavené pro použití řízení autoři a jiných třetích stran v následujícím `static` metody:  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetListItemProperties%2A>  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetList%2A>.  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetListName%2A>  
  
-   <xref:System.Windows.Forms.ListBindingHelper.GetListItemType%2A>  
  
### <a name="sorting-and-filtering-with-the-ibindinglistview-interface"></a>Řazení a filtrování s IBindingListView – rozhraní  
 <xref:System.Windows.Forms.BindingSource> Součást implementuje <xref:System.ComponentModel.IBindingListView> rozhraní, které rozšiřuje <xref:System.ComponentModel.IBindingList> rozhraní. <xref:System.ComponentModel.IBindingList> Nabízí jeden sloupec řazení a <xref:System.ComponentModel.IBindingListView> nabízí pokročilé řazení a filtrování. S <xref:System.ComponentModel.IBindingListView>, lze řadit a filtrovat položky ve zdroji dat, pokud zdroj dat, také jeden z těchto rozhraní implementuje. <xref:System.Windows.Forms.BindingSource> Součást neposkytuje odkaz na implementaci těchto členů. Místo toho volání předávány na podkladový seznam.  
  
 Následující tabulka popisuje vlastnosti, které můžete použít pro filtrování a řazení.  
  
|Člen|Popis|  
|------------|-----------------|  
|<xref:System.Windows.Forms.BindingSource.Filter%2A> Vlastnost|Pokud je zdroj dat <xref:System.ComponentModel.IBindingListView>, získá nebo nastaví výraz použitý pro filtrování, jsou-li zobrazit řádky.|  
|<xref:System.Windows.Forms.BindingSource.Sort%2A> Vlastnost|Pokud je zdroj dat <xref:System.ComponentModel.IBindingList>, získá nebo nastaví název sloupce sloužící k řazení a informace o pořadí řazení.<br /><br /> -nebo-<br /><br /> Pokud je zdroj dat <xref:System.ComponentModel.IBindingListView> a podporuje rozšířené, řazení, získá více názvů sloupců použít pro řazení a pořadí řazení|  
  
### <a name="integration-with-bindingnavigator"></a>Integrace s BindingNavigator  
 Můžete použít <xref:System.Windows.Forms.BindingSource> součásti pro vazbu libovolný ovládací prvek Windows Forms ke zdroji dat, ale <xref:System.Windows.Forms.BindingNavigator> ovládací prvek je určený speciálně pro práci s <xref:System.Windows.Forms.BindingSource> součásti. <xref:System.Windows.Forms.BindingNavigator> Řízení poskytuje uživatelské rozhraní pro řízení <xref:System.Windows.Forms.BindingSource> aktuální položky součásti. Ve výchozím nastavení <xref:System.Windows.Forms.BindingNavigator> řízení poskytuje tlačítka odpovídající navigační metody na <xref:System.Windows.Forms.BindingSource> součásti. Další informace najdete v tématu [postup: přejděte dat pomocí ovládacího prvku Windows Forms BindingNavigator](../../../../docs/framework/winforms/controls/how-to-navigate-data-with-the-windows-forms-bindingnavigator-control.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.BindingNavigator>  
 [Přehled komponenty BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component-overview.md)  
 [Ovládací prvek BindingNavigator](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)  
 [Windows Forms – datová vazba](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Ovládací prvky používané ve Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)  
 [Postupy: Uplatňování aktualizací zdroje dat v ovládacím prvku Windows Forms pomocí BindingSource](../../../../docs/framework/winforms/controls/reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)
