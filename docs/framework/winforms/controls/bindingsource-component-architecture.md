---
title: Architektura součásti BindingSource
ms.date: 03/30/2017
helpviewer_keywords:
- BindingSource component [Windows Forms], architecture
- Windows Forms, data binding
- BindingSource component [Windows Forms], about BindingSource component
- data binding [Windows Forms], BindingSource component
ms.assetid: 7bc69c90-8a11-48b1-9336-3adab5b41591
ms.openlocfilehash: 54a23ba899ceb05701fe3580aefbb723c6b3f0fd
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364415"
---
# <a name="bindingsource-component-architecture"></a>Architektura součásti BindingSource
<xref:System.Windows.Forms.BindingSource> Pomocí komponenty můžete univerzálně navazovat všechny model Windows Forms ovládací prvky na zdroje dat.  
  
 <xref:System.Windows.Forms.BindingSource> Komponenta zjednodušuje proces vázání ovládacích prvků na zdroj dat a poskytuje následující výhody oproti tradiční datové vazbě:  
  
- Umožňuje vytváření vazeb pro obchodní objekty v době návrhu.  
  
- Zapouzdřuje <xref:System.Windows.Forms.CurrencyManager>funkcea zpřístupňuje události v době návrhu. <xref:System.Windows.Forms.CurrencyManager>  
  
- Zjednodušuje vytváření seznamu, který podporuje <xref:System.ComponentModel.IBindingList> rozhraní, zadáním oznámení o změně seznamu pro zdroje dat, které nativně nepodporují oznámení o změně seznamu.  
  
- Poskytuje bod rozšiřitelnosti pro <xref:System.ComponentModel.IBindingList.AddNew%2A?displayProperty=nameWithType> metodu.  
  
- Poskytuje úroveň nepřímých odkazů mezi zdrojem dat a ovládacím prvkem. Tento nepřímý odkaz je důležitý, když se zdroj dat může v době běhu změnit.  
  
- Spolupracuje s dalšími ovládacími prvky model Windows Forms souvisejících s daty, konkrétně <xref:System.Windows.Forms.BindingNavigator> s <xref:System.Windows.Forms.DataGridView> ovládacími prvky a.  
  
 Z těchto důvodů je tato <xref:System.Windows.Forms.BindingSource> součást preferovaným způsobem, jak navazovat ovládací prvky model Windows Forms do zdrojů dat.  
  
## <a name="bindingsource-features"></a>Funkce BindingSource  
 <xref:System.Windows.Forms.BindingSource> Komponenta poskytuje několik funkcí pro vázání ovládacích prvků na data. Pomocí těchto funkcí můžete implementovat většinu scénářů datové vazby s téměř bez kódování na vaši část.  
  
 Tato <xref:System.Windows.Forms.BindingSource> součást to dosahuje tím, že poskytuje konzistentní rozhraní pro přístup k mnoha různým druhům zdrojů dat. To znamená, že použijete stejný postup pro vytvoření vazby na libovolný typ. Můžete například připojit <xref:System.Windows.Forms.BindingSource.DataSource%2A> vlastnost <xref:System.Data.DataSet> k obchodnímu objektu nebo a v obou případech použít stejnou sadu vlastností, metod a událostí pro manipulaci se zdrojem dat.  
  
 Konzistentní rozhraní poskytované <xref:System.Windows.Forms.BindingSource> komponentou významně zjednodušuje proces vázání dat na ovládací prvky. U typů zdrojů dat, které poskytují oznámení o změně, <xref:System.Windows.Forms.BindingSource> komponenta automaticky komunikuje změny mezi ovládacím prvkem a zdrojem dat. U typů zdrojů dat, které neposkytují oznámení o změně, jsou k dispozici události, které umožňují vyvolávat oznámení o změně. Následující seznam obsahuje funkce podporované <xref:System.Windows.Forms.BindingSource> součástí:  
  
- Dereference.  
  
- Správa měn.  
  
- Zdroj dat jako seznam.  
  
- <xref:System.Windows.Forms.BindingSource><xref:System.ComponentModel.IBindingList>jako.  
  
- Vytvoření vlastní položky.  
  
- Vytváření transakční položky  
  
- <xref:System.Collections.IEnumerable>pracovníky.  
  
- Podpora při návrhu.  
  
- Statické <xref:System.Windows.Forms.ListBindingHelper> metody.  
  
- Řazení a filtrování s <xref:System.ComponentModel.IBindingListView> rozhraním.  
  
- Integrace s <xref:System.Windows.Forms.BindingNavigator>.  
  
### <a name="indirection"></a>Dereference  
 <xref:System.Windows.Forms.BindingSource> Komponenta poskytuje úroveň nepřímých odkazů mezi ovládacím prvkem a zdrojem dat. Namísto svázání ovládacího prvku přímo se zdrojem dat svážete ovládací prvek s objektem <xref:System.Windows.Forms.BindingSource>a připojíte zdroj dat <xref:System.Windows.Forms.BindingSource> k <xref:System.Windows.Forms.BindingSource.DataSource%2A> vlastnosti komponenty.  
  
 U této úrovně dereference můžete změnit zdroj dat bez resetování vazby ovládacího prvku. Tato funkce poskytuje následující možnosti:  
  
- Můžete připojit <xref:System.Windows.Forms.BindingSource> k různým zdrojům dat a zachovat aktuální vazby ovládacího prvku.  
  
- Můžete změnit položky ve zdroji dat a upozorní na svázané ovládací prvky. Další informace najdete v tématu [jak: Odrážet aktualizace zdroje dat v ovládacím prvku model Windows Forms s objektem BindingSource](reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md).  
  
- Můžete vytvořit vazby na <xref:System.Type> místo objektu v paměti. Další informace najdete v tématu [jak: Navázání ovládacího prvku model Windows Forms na](how-to-bind-a-windows-forms-control-to-a-type.md)typ. Pak můžete vytvořit navázání na objekt v době běhu.  
  
### <a name="currency-management"></a>Správa měn  
 <xref:System.Windows.Forms.BindingSource> Komponenta<xref:System.Windows.Forms.ICurrencyManagerProvider> implementuje rozhraní pro zpracování správy měn za vás. S rozhraním můžete mít také přístup ke Správci měn <xref:System.Windows.Forms.BindingSource>pro kromě správce měny pro jiný <xref:System.Windows.Forms.BindingSource> vázaný na stejný <xref:System.Windows.Forms.BindingSource.DataMember%2A>. <xref:System.Windows.Forms.ICurrencyManagerProvider>  
  
 Komponenta zapouzdřuje funkce a zpřístupňuje nejběžnější <xref:System.Windows.Forms.CurrencyManager> vlastnosti a události. <xref:System.Windows.Forms.CurrencyManager> <xref:System.Windows.Forms.BindingSource> Následující tabulka popisuje některé členy související se správou měny.  
  
 <xref:System.Windows.Forms.ICurrencyManagerProvider.CurrencyManager%2A>majetek  
 Získá správce měny přidružený <xref:System.Windows.Forms.BindingSource>k.  
  
 <xref:System.Windows.Forms.ICurrencyManagerProvider.GetRelatedCurrencyManager%2A>Metoda  
 Pokud je k zadanému datovému členu vázán jiný <xref:System.Windows.Forms.BindingSource> , získá správce měny.  
  
 <xref:System.Windows.Forms.BindingSource.Current%2A>majetek  
 Načte aktuální položku zdroje dat.  
  
 <xref:System.Windows.Forms.BindingSource.Position%2A>majetek  
 Získá nebo nastaví aktuální pozici v podkladovém seznamu.  
  
 <xref:System.Windows.Forms.BindingSource.EndEdit%2A>Metoda  
 Použije nedokončené změny v podkladovém zdroji dat.  
  
 <xref:System.Windows.Forms.BindingSource.CancelEdit%2A>Metoda  
 Zruší aktuální operaci úprav.  
  
### <a name="data-source-as-a-list"></a>Zdroj dat jako seznam  
 Komponenta implementuje rozhraní<xref:System.ComponentModel.ITypedList> a <xref:System.ComponentModel.IBindingListView>. <xref:System.Windows.Forms.BindingSource> V této implementaci můžete použít <xref:System.Windows.Forms.BindingSource> samotnou součást jako zdroj dat bez jakéhokoli externího úložiště.  
  
 Když je <xref:System.Windows.Forms.BindingSource> komponenta připojena ke zdroji dat, zpřístupňuje zdroj dat jako seznam.  
  
 <xref:System.Windows.Forms.BindingSource.DataSource%2A> Vlastnost může být nastavena na několik zdrojů dat. Mezi ně patří typy, objekty a seznamy typů. Výsledný zdroj dat bude vystaven jako seznam. V následující tabulce jsou uvedeny některé běžné zdroje dat a výsledné hodnocení seznamu.  
  
|Vlastnost DataSource|Výsledky seznamu|  
|-------------------------|------------------|  
|Odkaz s hodnotou null`Nothing` (v Visual Basic)|Prázdné <xref:System.ComponentModel.IBindingList> objekty. Přidáním položky se seznam nastaví do typu přidané položky.|  
|Odkaz s hodnotou null`Nothing` (v Visual Basic) <xref:System.Windows.Forms.BindingSource.DataMember%2A> s nastavením|Nepodporováno; vyvolá <xref:System.ArgumentException>.|  
|Typ nebo objekt typu "T", který není typu list|Prázdná <xref:System.ComponentModel.IBindingList> položka typu "T".|  
|Instance pole|<xref:System.ComponentModel.IBindingList> Obsahující prvky pole.|  
|<xref:System.Collections.IEnumerable>případě|<xref:System.ComponentModel.IBindingList> Obsahující položky<xref:System.Collections.IEnumerable>|  
|Instance seznamu obsahující typ T|<xref:System.ComponentModel.IBindingList> Instance obsahující typ "T".|  
  
 Kromě toho <xref:System.Windows.Forms.BindingSource.DataSource%2A> je možné nastavit na jiné typy seznamů, <xref:System.ComponentModel.IListSource> například a <xref:System.ComponentModel.ITypedList>, a <xref:System.Windows.Forms.BindingSource> odpovídajícím způsobem je zpracuje. V tomto případě by měl mít typ, který je obsažen v seznamu, konstruktor bez parametrů.  
  
### <a name="bindingsource-as-an-ibindinglist"></a>BindingSource jako IBindingList  
 Komponenta poskytuje členům přístup k podkladovým datům <xref:System.ComponentModel.IBindingList>a manipulaci s nimi. <xref:System.Windows.Forms.BindingSource> Některé z těchto členů jsou popsány v následující tabulce.  
  
|Člen|Popis|  
|------------|-----------------|  
|<xref:System.Windows.Forms.BindingSource.List%2A>majetek|Získá seznam, který je výsledkem vyhodnocení <xref:System.Windows.Forms.BindingSource.DataSource%2A> vlastností nebo. <xref:System.Windows.Forms.BindingSource.DataMember%2A>|  
|<xref:System.Windows.Forms.BindingSource.AddNew%2A>Metoda|Přidá novou položku do základního seznamu. Platí pro zdroje dat, které implementují <xref:System.ComponentModel.IBindingList> rozhraní a umožňují přidat položky (to znamená <xref:System.Windows.Forms.BindingSource.AllowNew%2A> , že vlastnost je nastavena `true`na hodnotu).|  
  
### <a name="custom-item-creation"></a>Vytvoření vlastní položky  
 <xref:System.Windows.Forms.BindingSource.AddingNew> Událost můžete zpracovat tak, aby poskytovala vlastní logiku vytváření položek. K události dojde před přidáním nového objektu <xref:System.Windows.Forms.BindingSource>do. <xref:System.Windows.Forms.BindingSource.AddingNew> Tato událost je aktivována po <xref:System.Windows.Forms.BindingSource.AddNew%2A> volání metody, ale před přidáním nové položky do podkladového seznamu. Zpracováním této události můžete zajistit chování při vytváření vlastních položek bez odvozování od <xref:System.Windows.Forms.BindingSource> třídy. Další informace najdete v tématu [jak: Přizpůsobte přidávání položek pomocí model Windows Forms](how-to-customize-item-addition-with-the-windows-forms-bindingsource.md)BindingSource.  
  
### <a name="transactional-item-creation"></a>Vytvoření transakční položky  
 <xref:System.Windows.Forms.BindingSource> Komponenta<xref:System.ComponentModel.ICancelAddNew> implementuje rozhraní, které umožňuje vytvoření transakční položky. Po zřízení nové položky pomocí volání <xref:System.Windows.Forms.BindingSource.AddNew%2A>nástroje může být přidání potvrzeno nebo vráceno zpět následujícími způsoby:  
  
- <xref:System.ComponentModel.ICancelAddNew.EndNew%2A> Metoda explicitně potvrdí nedokončené přidání.  
  
- Provedení jiné operace shromažďování, jako je vložení, odebrání nebo přesunutí, bude implicitně potvrzovat nedokončené přidání.  
  
- <xref:System.ComponentModel.ICancelAddNew.CancelNew%2A> Metoda vrátí nedokončené přidání, pokud metoda ještě není potvrzená.  
  
### <a name="ienumerable-support"></a>Podpora IEnumerable  
 Komponenta umožňuje svázat ovládací prvky se <xref:System.Collections.IEnumerable> zdroji dat. <xref:System.Windows.Forms.BindingSource> Pomocí této součásti můžete vytvořit propojení se zdrojem dat, jako je <xref:System.Data.SqlClient.SqlDataReader?displayProperty=nameWithType>.  
  
 <xref:System.Windows.Forms.BindingSource> <xref:System.Windows.Forms.BindingSource> Když je <xref:System.Collections.IEnumerable> zdroj <xref:System.Collections.IEnumerable> dat přiřazen ke<xref:System.ComponentModel.IBindingList> komponentě, vytvoří a přidá obsah zdroje dat do seznamu.  
  
### <a name="design-time-support"></a>Podpora při návrhu  
 Některé typy objektů nelze vytvořit v době návrhu, jako například objekty vytvořené z třídy objektu pro vytváření nebo objekty vrácené webovou službou. Někdy může být nutné navazovat ovládací prvky na tyto typy v době návrhu, i když v paměti není objekt, ke kterému lze ovládací prvky navazovat. Může být například nutné označit záhlaví <xref:System.Windows.Forms.DataGridView> sloupců ovládacího prvku názvy vlastností veřejné vlastnosti vlastního typu.  
  
 Pro podporu tohoto scénáře <xref:System.Windows.Forms.BindingSource> komponenta podporuje vazbu <xref:System.Type>na. Když přiřadíte <xref:System.Type> <xref:System.Windows.Forms.BindingSource.DataSource%2A> k vlastnosti, <xref:System.Windows.Forms.BindingSource> komponenta vytvoří prázdné <xref:System.ComponentModel.BindingList%601> <xref:System.Type> položky. Jakékoli ovládací prvky, které následně svážete s <xref:System.Windows.Forms.BindingSource> komponentou, budou upozorněny na přítomnost vlastností nebo schématu vašeho typu v době návrhu nebo v době běhu. Další informace najdete v tématu [jak: Navázání ovládacího prvku model Windows Forms na](how-to-bind-a-windows-forms-control-to-a-type.md)typ.  
  
### <a name="static-listbindinghelper-methods"></a>Statické metody ListBindingHelper  
 <xref:System.Windows.Forms.BindingContext?displayProperty=nameWithType>Typy, <xref:System.Windows.Forms.CurrencyManager?displayProperty=nameWithType>a sdílejí<xref:System.Windows.Forms.BindingSource> společnou`DataSource`logiku , aby vygenerovala seznam z páru.`DataMember` / Kromě toho je tato společná logika veřejně vystavena pro použití autory ovládacích prvků a dalších třetích stran v `static` následujících metodách:  
  
- <xref:System.Windows.Forms.ListBindingHelper.GetListItemProperties%2A>  
  
- <xref:System.Windows.Forms.ListBindingHelper.GetList%2A>.  
  
- <xref:System.Windows.Forms.ListBindingHelper.GetListName%2A>  
  
- <xref:System.Windows.Forms.ListBindingHelper.GetListItemType%2A>  
  
### <a name="sorting-and-filtering-with-the-ibindinglistview-interface"></a>Řazení a filtrování pomocí rozhraní IBindingListView  
 <xref:System.Windows.Forms.BindingSource> Komponenta implementuje<xref:System.ComponentModel.IBindingList> rozhraní, které rozšiřuje rozhraní. <xref:System.ComponentModel.IBindingListView> Nabízí řazení jediného sloupce <xref:System.ComponentModel.IBindingListView> a nabízí rozšířené řazení a filtrování. <xref:System.ComponentModel.IBindingList> Pomocí <xref:System.ComponentModel.IBindingListView>můžete položky řadit a filtrovat ve zdroji dat, pokud zdroj dat také implementuje jedno z těchto rozhraní. <xref:System.Windows.Forms.BindingSource> Komponenta neposkytuje referenční implementaci těchto členů. Místo toho jsou volání předána do podkladového seznamu.  
  
 Následující tabulka popisuje vlastnosti, které používáte pro řazení a filtrování.  
  
|Člen|Popis|  
|------------|-----------------|  
|<xref:System.Windows.Forms.BindingSource.Filter%2A>majetek|Pokud je zdrojem dat objekt <xref:System.ComponentModel.IBindingListView>, získá nebo nastaví výraz použitý k filtrování zobrazených řádků.|  
|<xref:System.Windows.Forms.BindingSource.Sort%2A>majetek|Pokud je zdrojem dat objekt <xref:System.ComponentModel.IBindingList>, získá nebo nastaví název sloupce, který se používá k řazení a řazení informací o objednávkách.<br /><br /> -nebo-<br /><br /> Pokud je <xref:System.ComponentModel.IBindingListView> zdrojem dat a podporuje pokročilé řazení, získá více názvů sloupců používaných pro řazení a řazení.|  
  
### <a name="integration-with-bindingnavigator"></a>Integrace s BindingNavigator  
 <xref:System.Windows.Forms.BindingSource> Komponentu lze použít pro svázání libovolného ovládacího prvku model Windows Forms se zdrojem dat, <xref:System.Windows.Forms.BindingNavigator> ale ovládací prvek je navržen <xref:System.Windows.Forms.BindingSource> specificky pro práci s komponentou. Ovládací prvek poskytuje uživatelské rozhraní pro <xref:System.Windows.Forms.BindingSource> řízení aktuální položky součásti. <xref:System.Windows.Forms.BindingNavigator> Ve výchozím nastavení <xref:System.Windows.Forms.BindingNavigator> ovládací prvek poskytuje tlačítka, která odpovídají metodám navigace <xref:System.Windows.Forms.BindingSource> na komponentě. Další informace najdete v tématu [jak: Navigace v datech pomocí ovládacího prvku](how-to-navigate-data-with-the-windows-forms-bindingnavigator-control.md)BindingNavigator model Windows Forms.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.BindingNavigator>
- [Přehled komponenty BindingSource](bindingsource-component-overview.md)
- [Ovládací prvek BindingNavigator](bindingnavigator-control-windows-forms.md)
- [Windows Forms – datová vazba](../windows-forms-data-binding.md)
- [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)
- [Postupy: Svázání ovládacího prvku model Windows Forms s typem](how-to-bind-a-windows-forms-control-to-a-type.md)
- [Postupy: Odrážet aktualizace zdroje dat v ovládacím prvku model Windows Forms s objektem BindingSource](reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)
