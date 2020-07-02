---
title: Datová vazba
description: Naučte se vytvořit vazby k poli hodnot, které vypočítáte za běhu, jak číst ze souboru nebo odvozovat z hodnot jiných ovládacích prvků v model Windows Forms.
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
ms.openlocfilehash: 78e8a3287c565cfa7dae56b68c0eb57f48c30ea2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619660"
---
# <a name="data-binding-and-windows-forms"></a>Datové vazby a rozhraní Windows Forms
V model Windows Forms se můžete připojit k not pouze k tradičním zdrojům dat, ale také k téměř libovolné struktuře, která obsahuje data. Můžete vytvořit propojení s polem hodnot, který počítáte za běhu, číst ze souboru nebo odvozovat z hodnot jiných ovládacích prvků.  
  
 Kromě toho můžete vytvořit vázání libovolné vlastnosti libovolného ovládacího prvku na zdroj dat. V tradiční datové vazbě je obvykle navázána vlastnost zobrazení – například <xref:System.Windows.Forms.Control.Text%2A> vlastnost <xref:System.Windows.Forms.TextBox> ovládacího prvku na zdroj dat. U .NET Framework máte také možnost nastavit další vlastnosti i prostřednictvím vazby. Pomocí vazby můžete provádět následující úlohy:  
  
- Nastavení grafiky ovládacího prvku obrázek.  
  
- Nastavení barvy pozadí jednoho nebo více ovládacích prvků.  
  
- Nastavení velikosti ovládacích prvků.  
  
 Datová vazba je v podstatě automatickým způsobem nastavení jakékoli vlastnosti přístupné pro libovolný ovládací prvek na formuláři.  
  
## <a name="types-of-data-binding"></a>Typy datových vazeb  
 Model Windows Forms může využít výhod dvou typů datové vazby: jednoduchá vazba a složitá vazba. Každá z nich nabízí různé výhody.  
  
|Typ datové vazby|Popis|  
|--------------------------|-----------------|  
|Jednoduchá datová vazba|Možnost ovládacího prvku pro svázání s jedním datovým prvkem, jako je například hodnota ve sloupci v tabulce DataSet. Toto je typ vazby typický pro ovládací prvky, jako je například <xref:System.Windows.Forms.TextBox> ovládací prvek nebo <xref:System.Windows.Forms.Label> ovládací prvek, což jsou ovládací prvky, které obvykle zobrazují pouze jednu hodnotu. Ve skutečnosti může být jakákoliv vlastnost v ovládacím prvku svázána s polem v databázi. Existuje Rozsáhlá podpora pro tuto funkci v aplikaci Visual Studio.<br /><br /> Další informace naleznete v tématech:<br /><br /> -   [Rozhraní související s datovou vazbou](interfaces-related-to-data-binding.md)<br />-   [Postupy: navigace mezi daty v model Windows Forms](how-to-navigate-data-in-windows-forms.md)<br />-   [Postupy: vytvoření jednoduchého ovládacího prvku vázaného na formulář Windows](how-to-create-a-simple-bound-control-on-a-windows-form.md)|  
|Složitá datová vazba|Schopnost ovládacího prvku vytvořit svázání s více než jedním datovým prvkem, obvykle více než jedním záznamem v databázi. Komplexní vazba se také nazývá vazba založená na seznamu. Příklady ovládacích prvků, které podporují komplexní vazby <xref:System.Windows.Forms.DataGridView> , jsou <xref:System.Windows.Forms.ListBox> <xref:System.Windows.Forms.ComboBox> ovládací prvky, a. Příklad komplexní datové vazby naleznete v tématu [How to: bind a model Windows Forms ComboBox nebo ListBox Control to data](./controls/how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md).|  
  
## <a name="bindingsource-component"></a>BindingSource – komponenta  
 Pro zjednodušení datových vazeb model Windows Forms umožňuje svázat zdroj dat s <xref:System.Windows.Forms.BindingSource> komponentou a potom svázat ovládací prvky s <xref:System.Windows.Forms.BindingSource> . <xref:System.Windows.Forms.BindingSource>V jednoduchých nebo složitých scénářích vazeb můžete použít. V obou případech <xref:System.Windows.Forms.BindingSource> funguje jako prostředník mezi zdrojem dat a vázanými ovládacími prvky, které poskytují správu měny oznámení změn a další služby.  
  
## <a name="common-scenarios-that-employ-data-binding"></a>Běžné scénáře, které využívají datovou vazbu  
 Skoro každá komerční aplikace používá informace čtené ze zdrojů dat jednoho nebo druhého typu, obvykle prostřednictvím datové vazby. Následující seznam obsahuje několik nejběžnějších scénářů, které využívají datovou vazbu jako metodu pro úpravu a manipulaci s daty.  
  
|Scénář|Popis|  
|--------------|-----------------|  
|Vytváření sestav|Sestavy poskytují flexibilní způsob zobrazení a sumarizace dat ve vytištěném dokumentu. Je velmi běžné vytvořit sestavu, která vytiskne vybraný obsah zdroje dat na obrazovku nebo na tiskárnu. Mezi běžné sestavy patří seznamy, faktury a souhrny. Položky jsou obvykle formátovány do sloupců seznamů, jejichž podřízené položky jsou uspořádány pod každou položkou seznamu, ale měli byste zvolit rozložení, které nejlépe odpovídá datům.|  
|Zadávání dat|Běžný způsob, jak zadat velké objemy souvisejících dat nebo vyzvat uživatele k zadání informací, je prostřednictvím formuláře pro zadávání dat. Uživatelé mohou zadávat informace nebo vybírat volby pomocí textových polí, přepínačů, rozevíracích seznamů a zaškrtávacích políček. Informace jsou následně odeslány a uloženy v databázi, jejíž struktura je založena na zadaných informacích.|  
|Vztah hlavního/podrobného vztahu|Hlavní a podrobná aplikace je jedním z formátů pro prohlížení souvisejících dat. Konkrétně existují dvě tabulky dat s relací, které je spojují – v klasickém podnikovém příkladu tabulka Customers (zákazníci) a tabulka Orders (objednávky) se vztahem mezi nimi propojující zákazníky a jejich příslušnými objednávkami. Další informace o vytvoření hlavní a podrobné aplikace se dvěma model Windows Formsmi <xref:System.Windows.Forms.DataGridView> ovládacími prvky naleznete v tématu [How to: Create a Master/Detail Form using a dva ovládací prvky DataGridView model Windows Forms](./controls/create-a-master-detail-form-using-two-datagridviews.md)|  
|Vyhledávací tabulka|Dalším běžným scénářem prezentace nebo manipulace s daty je hledání v tabulce. V rámci většího zobrazení dat se často <xref:System.Windows.Forms.ComboBox> používá ovládací prvek k zobrazení a manipulaci s daty. Klíčem je, že data zobrazená v <xref:System.Windows.Forms.ComboBox> ovládacím prvku se liší od dat zapsaných do databáze. Například pokud máte ovládací prvek, který <xref:System.Windows.Forms.ComboBox> zobrazuje položky, které jsou k dispozici z prodejny obchodu, pravděpodobně chcete zobrazit názvy produktů (pečivo, mléko, vejce). Pro usnadnění načítání informací v rámci databáze a pro normalizaci databází byste ale pravděpodobně uložili informace o konkrétních položkách v daném pořadí jako čísla položek (#501, #603 atd.). Proto existuje implicitní propojení mezi "popisným názvem" nákupní položky v <xref:System.Windows.Forms.ComboBox> ovládacím prvku formuláře a číslem související položky, které se nachází v objednávce. Toto je podstata vyhledávání tabulky. Další informace najdete v tématu [Postup: Vytvoření vyhledávací tabulky pomocí model Windows Forms komponenty BindingSource](./controls/how-to-create-a-lookup-table-with-the-windows-forms-bindingsource-component.md).|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Binding>
- [Windows Forms – datová vazba](windows-forms-data-binding.md)
- [Postupy: Vázání ovládacího prvku Windows Forms DataGrid ke zdroji dat](./controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
- [Komponenta BindingSource](./controls/bindingsource-component.md)
