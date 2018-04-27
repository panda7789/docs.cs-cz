---
title: Datové vazby a rozhraní Windows Forms
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: db0e3ad5602d7ee608299bc5b9c5c85b860cab7d
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="data-binding-and-windows-forms"></a>Datové vazby a rozhraní Windows Forms
V systému Windows Forms můžete vázat na právě tradičních datových zdrojů, ale také k téměř jakoukoli struktura, která obsahuje data. Můžete vázat na pole hodnot, které vypočítat za běhu, čtení ze souboru nebo odvozena z hodnot jiných ovládacích prvků.  
  
 Kromě toho můžete vázat žádnou vlastnost libovolný ovládací prvek na zdroj dat. V tradiční datovou vazbu, obvykle vazby vlastnosti zobrazení – například <xref:System.Windows.Forms.Control.Text%2A> vlastnost <xref:System.Windows.Forms.TextBox> ovládací prvek – ke zdroji dat. Pomocí [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], máte také možnost nastavení prostřednictvím vazby také další vlastnosti. Vazba můžete použít k provádění následujících úloh:  
  
-   Nastavení obrázek ovládacího prvku obrázek.  
  
-   Nastavení barvy pozadí jeden nebo více ovládacích prvků.  
  
-   Nastavení velikosti ovládacích prvků.  
  
 Datová vazba je v podstatě automatické způsob nastavení žádnou běhu přístupné vlastnost libovolný ovládací prvek na formuláři.  
  
## <a name="types-of-data-binding"></a>Typy datová vazba  
 Windows Forms můžete využít výhod dva typy datové vazby: jednoduché vázání a složitých vazby. Každý nabízí jiné výhody.  
  
|Typ datová vazba|Popis|  
|--------------------------|-----------------|  
|Jednoduchá datová vazba|Schopnost ovládacího prvku vazby do jednoho datového elementu, jako je například hodnotu ve sloupci v tabulce datovou sadu. Jedná se o typ vazbu typických pro ovládací prvky, jako <xref:System.Windows.Forms.TextBox> ovládací prvek nebo <xref:System.Windows.Forms.Label> řízení, které jsou ovládací prvky, které obvykle pouze zobrazí jednu hodnotu. Všechny vlastnost v ovládacím prvku ve skutečnosti může být vázána na pole v databázi. Rozsáhlá podpora pro tuto funkci v sadě Visual Studio není k dispozici.<br /><br /> Další informace naleznete v tématu:<br /><br /> -   [Rozhraní související s datovou vazbou](../../../docs/framework/winforms/interfaces-related-to-data-binding.md)<br />-   [Postupy: navigace daty v systému Windows Forms](../../../docs/framework/winforms/how-to-navigate-data-in-windows-forms.md)<br />-   [Postupy: vytvoření jednoduše připojeného ovládacího prvku ve formuláři Windows](../../../docs/framework/winforms/how-to-create-a-simple-bound-control-on-a-windows-form.md)|  
|Komplexní datová vazba|Schopnost ovládacího prvku vytvořit vazbu k více než jeden element dat, obvykle více než jeden záznam v databázi. Komplexní vazba je také označován na základě seznamu vazby. Příklady ovládacích prvků, které podporují komplexní vazby <xref:System.Windows.Forms.DataGridView>, <xref:System.Windows.Forms.ListBox>, a <xref:System.Windows.Forms.ComboBox> ovládací prvky. Příklad rozšířené datové vazby, naleznete v části [postupy: vytvoření vazby na Windows Forms ComboBox nebo ListBox – ovládací prvek k datům](../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md).|  
  
## <a name="bindingsource-component"></a>BindingSource – komponenta  
 Windows Forms ke zjednodušení datové vazby, umožňuje vytvoření vazby zdroje dat <xref:System.Windows.Forms.BindingSource> součásti a poté vazby ovládacích prvků <xref:System.Windows.Forms.BindingSource>. Můžete použít <xref:System.Windows.Forms.BindingSource> ve scénářích jednoduché nebo komplexní vazby. V obou případech <xref:System.Windows.Forms.BindingSource> jednání jako zprostředkovatel mezi zdroji dat a vázané ovládací prvky, které poskytuje oznámení měna řízení změn a dalších služeb.  
  
## <a name="common-scenarios-that-employ-data-binding"></a>Běžné scénáře, které využívají datová vazba  
 Téměř každý komerční aplikace používá informace o čtení ze zdroje dat jeden typ nebo jinou, obvykle prostřednictvím datové vazby. Následující seznam obsahuje několik nejběžnějších scénářů, které využívají datová vazba jako metodu prezentace dat a zpracování.  
  
|Scénář|Popis|  
|--------------|-----------------|  
|Generování sestav|Sestavy poskytují flexibilní způsob, jak můžete zobrazit a shrnují data v tištěné dokumentu. Je velmi běžné vytvořit sestavu, která zobrazí obsah vybrané zdroje dat na obrazovce nebo na tiskárnu. Běžné sestavy obsahují seznamy, faktury a souhrny. Položky jsou obvykle naformátovaný do sloupce seznamů, dílčí položky seřazené podle jednotlivé položky seznamu, ale měli byste vybrat rozložení, který nejlépe vyhovuje data.|  
|Vkládání dat|Prostřednictvím dat je běžným způsobem zadejte velkých objemů dat v relaci nebo Dotázat se uživatelů na informace. Uživatele můžete zadat informace nebo vyberte možnosti pomocí textová pole, možnost tlačítka, rozevírací seznamy a zaškrtávací políčka. Informace se potom odeslána a uloženy v databázi, jejíž struktura je založený na informacích zadali.|  
|Vztahu seznam podrobnosti|Aplikace a podrobností je jeden formát pro prohlížení související data. Konkrétně, existují dvě tabulky dat vztahem jejich připojením – příklad classic firmy, tabulku "Zákazníci" a tabulku "Objednávky" se vztah mezi je serveru linking zákazníků a jejich odpovídajících objednávky. Další informace o vytvoření hlavního/podrobného aplikace s dvěma Windows Forms <xref:System.Windows.Forms.DataGridView> najdete v části ovládací prvky, [postupy: vytvoření hlavního a podrobného formuláře pomocí dvou prvkům Windows Forms DataGridView](../../../docs/framework/winforms/controls/create-a-master-detail-form-using-two-datagridviews.md)|  
|Vyhledávací tabulky|Jiný běžný scénář prezentace nebo zpracování dat je tabulka vyhledávání. Jako součást větší zobrazení dat, často <xref:System.Windows.Forms.ComboBox> řízení se používá k zobrazení a pracovat s daty. Klíč je, že jsou data zobrazena v <xref:System.Windows.Forms.ComboBox> řízení se liší od data zapsána do databáze. Pokud máte například <xref:System.Windows.Forms.ComboBox> řízení zobrazení položky k dispozici z úložiště supermarketu, pravděpodobně chcete zobrazit názvy produktů (chléb, mléko, vejce). Však usnadňují načítání informací v databázi a pro normalizaci databáze, pravděpodobně uložení informací pro konkrétní položky daného pořadí položek čísla (#501, #603 a tak dále). Proto je implicitní propojení "popisný název" supermarketu položky v <xref:System.Windows.Forms.ComboBox> ovládací prvek na formuláři a související číslo, které se nachází v pořadí. Toto je podstatu prohledávání tabulky. Další informace najdete v tématu [postupy: vytváření vyhledávacích tabulek s komponentou Windows Forms BindingSource](../../../docs/framework/winforms/controls/how-to-create-a-lookup-table-with-the-windows-forms-bindingsource-component.md).|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Binding>  
 [Windows Forms – datová vazba](../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Postupy: Vázání ovládacího prvku Windows Forms DataGrid ke zdroji dat](../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)  
 [Komponenta BindingSource](../../../docs/framework/winforms/controls/bindingsource-component.md)
