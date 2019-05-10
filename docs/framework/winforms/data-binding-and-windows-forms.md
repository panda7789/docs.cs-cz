---
title: Datové vazby a rozhraní Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- master-details lists
- data [Windows Forms], data binding
- reports [Windows Forms], Windows Forms
- lookup tables [Windows Forms], data binding
- data [Windows Forms], complex data binding
- data binding [Windows Forms], Windows Forms
- data [Windows Forms], simple data binding
- Windows Forms controls, data binding
- data-bound controls [Windows Forms], Windows Forms
ms.assetid: 419aac5e-819b-4aad-88b0-73a2f8c0bd27
ms.openlocfilehash: e8a3011828fd3b3f7aaaa062e837570c86f4fd65
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626855"
---
# <a name="data-binding-and-windows-forms"></a>Datové vazby a rozhraní Windows Forms
Ve Windows Forms lze svázat jenom tradičních datových zdrojů, ale také pro téměř jakoukoli strukturu, která obsahuje data. Můžete vytvořit vazbu na pole hodnot, které vypočítat v době běhu, čtení ze souboru nebo jsou odvozeny z hodnot jiných ovládacích prvků.  
  
 Kromě toho můžete vázat nějaká vlastnost libovolný ovládací prvek na zdroj dat. V tradičních datových vazbách obvykle vazby vlastnosti zobrazení – například <xref:System.Windows.Forms.Control.Text%2A> vlastnost <xref:System.Windows.Forms.TextBox> ovládacího prvku – ke zdroji dat. S [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], máte také možnost nastavení prostřednictvím vazby také další vlastnosti. Vazby můžete použít k provádění následujících úloh:  
  
- Nastaví obrázek ovládacího prvku pro obrázek.  
  
- Nastavení barvy pozadí jeden nebo více ovládacích prvků.  
  
- Nastavení velikosti ovládacích prvků.  
  
 Datová vazba je v podstatě automatický způsob nastavení nějaká přístupné za běhu vlastnost libovolný ovládací prvek na formuláři.  
  
## <a name="types-of-data-binding"></a>Typy datových vazeb  
 Formuláře Windows můžete využít dva druhy datové vazby: komplexní vazby a jednoduché vazby. Každá nabízí různé výhody.  
  
|Typ vázání dat|Popis|  
|--------------------------|-----------------|  
|Jednoduchá vazba dat|Možnost ovládací prvek svázat jednoho datového prvku, jako je například hodnota ve sloupci v tabulce datové sady. Jedná se o typ vazby typické pro ovládací prvky, jako <xref:System.Windows.Forms.TextBox> ovládací prvek nebo <xref:System.Windows.Forms.Label> ovládacího prvku, které jsou ovládací prvky, které se obvykle zobrazuje pouze jednu hodnotu. Žádné vlastnost v ovládacím prvku ve skutečnosti může být vázána na pole v databázi. Není k dispozici rozsáhlou podporu pro tuto funkci v sadě Visual Studio.<br /><br /> Další informace naleznete v tématu:<br /><br /> -   [Rozhraní související s datovou vazbou](interfaces-related-to-data-binding.md)<br />-   [Jak: Procházení dat v modelu Windows Forms](how-to-navigate-data-in-windows-forms.md)<br />-   [Jak: Vytvoření jednoduše vázaného ovládacího prvku ve formuláři Windows](how-to-create-a-simple-bound-control-on-a-windows-form.md)|  
|Rozšířené datové vazby|Možnost ovládací prvek svázat s více než jeden prvek dat, obvykle více než jeden záznam v databázi. Komplexní vazby se také nazývá vazbu založenou na seznamu. Příklady ovládacích prvků, které podporují složité vazby <xref:System.Windows.Forms.DataGridView>, <xref:System.Windows.Forms.ListBox>, a <xref:System.Windows.Forms.ComboBox> ovládací prvky. Příklad rozšířené datové vazby, naleznete v tématu [jak: Windows Forms ComboBox nebo ListBox – ovládací prvek svázat Data](./controls/how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md).|  
  
## <a name="bindingsource-component"></a>BindingSource – komponenta  
 Windows Forms pro zjednodušení vytváření datových vazeb, umožňuje vytvoření vazby zdroje dat na <xref:System.Windows.Forms.BindingSource> komponentu a potom vazby ovládacích prvků <xref:System.Windows.Forms.BindingSource>. Můžete použít <xref:System.Windows.Forms.BindingSource> v jednoduchých nebo složitých vazby scénáře. V obou případech <xref:System.Windows.Forms.BindingSource> funguje jako prostředník mezi zdrojem dat a vázané ovládací prvky, které poskytují oznámení měny řízení změn a dalších služeb.  
  
## <a name="common-scenarios-that-employ-data-binding"></a>Běžné scénáře, které používají datová vazba  
 Téměř každá obchodní aplikace používá informace o čtení ze zdroje dat z jednoho typu nebo jiného, obvykle prostřednictvím datové vazby. Následující seznam uvádí některé z nejběžnějších scénářů, které využívají jako způsob prezentace dat a manipulace s datovou vazbu.  
  
|Scénář|Popis|  
|--------------|-----------------|  
|Generování sestav|Sestavy poskytují flexibilní způsob zobrazení a shrnujících data v tištěném dokumentu. Je velmi běžné, pokud chcete vytvořit sestavu, která vytiskne obsah vybrané zdroje dat na obrazovku nebo k tiskárně. Běžné sestavy zahrnují seznamy, faktury a souhrny. Položky jsou obvykle ve formátu do sloupce seznamů, s podřízené položky, které jsou uspořádané pod každou položku seznamu, ale měli byste zvolit na rozložení, které nejlépe vyhovuje stylu vaší data.|  
|Zadávání dat|Běžný způsob zadat velké množství souvisejících dat nebo vyzve uživatele, které informace se prostřednictvím formuláře datových záznamů. Uživatelům můžete zadat informace nebo vyberte voleb textová pole, přepínačů, rozevírací seznamy a zaškrtávací políčka. Informace jsou pak odeslání a uloženy v databázi, jejíž struktura je založená na zadané informace.|  
|Vztah záznamů master/detail|Záznamů master/detail aplikace je jeden formát pro vyhledávání na související data. Konkrétně, existují dvě tabulky data pomocí vztahu je propojí – v klasické obchodní například tabulku "Zákazníci" a tabulku "Orders" se vztahem mezi jejich propojení zákazníky a jejich příslušné objednávky. Další informace o vytvoření záznamů master/detail aplikace s dva formuláře Windows <xref:System.Windows.Forms.DataGridView> ovládacích prvků, naleznete v tématu [jak: Vytvoření hlavního/podrobného formuláře pomocí dvou prvkům Windows Forms DataGridView](./controls/create-a-master-detail-form-using-two-datagridviews.md)|  
|Vyhledávací tabulky|Další z typických data prezentace a manipulaci s možností je prohledávání tabulky. Jako součást větší zobrazení dat, často <xref:System.Windows.Forms.ComboBox> ovládací prvek se používá k zobrazení a manipulaci s daty. Klíč je, že se data zobrazí v <xref:System.Windows.Forms.ComboBox> ovládací prvek se liší od data zapsaná do databáze. Pokud máte například <xref:System.Windows.Forms.ComboBox> ovládací prvek položky zobrazení je k dispozici z úložiště blízkým, pravděpodobně chcete zobrazit názvy produktů (chléb, mléka, vajíčka). Ale usnadnění načítání informací v databázi a databázi normalizace, pravděpodobně ukládání informací pro konkrétní položky daného pořadí jako čísla položky (#501, #603 a tak dále). Proto je implicitní propojení "popisný název" blízkým položky v <xref:System.Windows.Forms.ComboBox> ovládací prvek na formuláři a číslo související položky, která je k dispozici v pořadí. Toto je podstata prohledávání tabulky. Další informace najdete v tématu [jak: Vytvoření vyhledávací tabulky s komponentou Windows Forms BindingSource](./controls/how-to-create-a-lookup-table-with-the-windows-forms-bindingsource-component.md).|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Binding>
- [Windows Forms – datová vazba](windows-forms-data-binding.md)
- [Postupy: Vytvoření vazby ovládacího prvku Windows Forms DataGrid ke zdroji dat](./controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
- [Komponenta BindingSource](./controls/bindingsource-component.md)
