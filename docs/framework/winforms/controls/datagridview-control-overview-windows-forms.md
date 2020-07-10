---
title: DataGridView – přehled ovládacího prvku
description: Naučte se používat ovládací prvek DataGridView model Windows Forms k zobrazení a úpravám tabulkových dat z mnoha různých druhů zdrojů dat.
ms.date: 03/30/2017
f1_keywords:
- DataGridView
helpviewer_keywords:
- DataGridView control [Windows Forms], about DataGridView control
- grid controls [Windows Forms]
- tables [Windows Forms], displaying in DataGridView control
- tables [Windows Forms], binding to DataGridView control
- columns [Windows Forms], DataGridView control
- bound controls [Windows Forms], dataGridView control
- datasets [Windows Forms], binding to DataGridView control
- data grids [Windows Forms], about data grids
- data [Windows Forms], resorting
- data [Windows Forms], navigating
- grids [Windows Forms]
- data binding [Windows Forms], DataGridView control
- data sources [Windows Forms], binding to DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 0a45c661-89dc-4390-9cc6-c47eee501488
ms.openlocfilehash: 3e68f536853081453f6ba746d342bc016bc8ca17
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174611"
---
# <a name="datagridview-control-overview-windows-forms"></a>DataGridView – přehled ovládacího prvku (Windows Forms)
> [!NOTE]
> <xref:System.Windows.Forms.DataGridView>Ovládací prvek nahrazuje a přidává funkce <xref:System.Windows.Forms.DataGrid> ovládacímu prvku. <xref:System.Windows.Forms.DataGrid> ovládací prvek je však ponechán pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte. Další informace naleznete v tématu [rozdíly mezi ovládacími prvky model Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Pomocí <xref:System.Windows.Forms.DataGridView> ovládacího prvku můžete zobrazit a upravit tabulková data z mnoha různých druhů zdrojů dat.  
  
 Vázání dat na <xref:System.Windows.Forms.DataGridView> ovládací prvek je jednoduché a intuitivní a v mnoha případech je to jednoduché jako nastavení <xref:System.Windows.Forms.DataGridView.DataSource%2A> Vlastnosti. Při vytváření vazby ke zdroji dat, který obsahuje více seznamů nebo tabulek, nastavte <xref:System.Windows.Forms.DataGridView.DataMember%2A> vlastnost na řetězec, který určuje seznam nebo tabulku, na které se má vytvořit vazba.  
  
 <xref:System.Windows.Forms.DataGridView>Ovládací prvek podporuje model standardní model Windows Forms datové vazby, takže se vytvoří vazba na instance tříd popsané v následujícím seznamu:  
  
- Libovolná třída, která implementuje <xref:System.Collections.IList> rozhraní, včetně jednorozměrného pole.  
  
- Libovolná třída, která implementuje <xref:System.ComponentModel.IListSource> rozhraní, například <xref:System.Data.DataTable> třídy a <xref:System.Data.DataSet> .  
  
- Libovolná třída, která implementuje <xref:System.ComponentModel.IBindingList> rozhraní, jako je například <xref:System.ComponentModel.BindingList%601> Třída.  
  
- Libovolná třída, která implementuje <xref:System.ComponentModel.IBindingListView> rozhraní, jako je například <xref:System.Windows.Forms.BindingSource> Třída.  
  
 <xref:System.Windows.Forms.DataGridView>Ovládací prvek podporuje datovou vazbu na veřejné vlastnosti objektů vrácených těmito rozhraními nebo na kolekci vlastností vrácenou <xref:System.ComponentModel.ICustomTypeDescriptor> rozhraním, pokud jsou implementovány u vrácených objektů.  
  
 Obvykle budete navazovat vazby na <xref:System.Windows.Forms.BindingSource> komponentu a navazovat <xref:System.Windows.Forms.BindingSource> komponentu na jiný zdroj dat nebo ji naplnit obchodními objekty. Tato <xref:System.Windows.Forms.BindingSource> součást je preferovaným zdrojem dat, protože může vytvořit vazbu na širokou škálu zdrojů dat a může automaticky vyřešit mnoho problémů s vazbami dat. Další informace najdete v tématu [Komponenta BindingSource](bindingsource-component.md).  
  
 <xref:System.Windows.Forms.DataGridView>Ovládací prvek lze také použít v *nevázaném* režimu bez základního úložiště dat. Příklad kódu, který používá nevázaný <xref:System.Windows.Forms.DataGridView> ovládací prvek, naleznete v tématu [Návod: Vytvoření nevázaného ovládacího prvku DataGridView model Windows Forms](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).  
  
 <xref:System.Windows.Forms.DataGridView>Ovládací prvek je vysoce konfigurovatelný a rozšiřitelný a poskytuje mnoho vlastností, metod a událostí pro přizpůsobení jeho vzhledu a chování. Pokud chcete, aby aplikace model Windows Forms zobrazovala tabulková data, zvažte použití <xref:System.Windows.Forms.DataGridView> ovládacího prvku před ostatními (například <xref:System.Windows.Forms.DataGrid> ). Pokud zobrazujete malou mřížku hodnot jen pro čtení, nebo pokud pro uživatele povolíte úpravu tabulky s miliony záznamů, <xref:System.Windows.Forms.DataGridView> ovládací prvek vám poskytne snadno programovatelné řešení paměti, které je efektivní.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Souhrn technologie ovládacího prvku DataGridView](datagridview-control-technology-summary-windows-forms.md)  
 Shrnuje <xref:System.Windows.Forms.DataGridView> Koncepty řízení a použití souvisejících tříd.  
  
 [Architektura ovládacího prvku DataGridView](datagridview-control-architecture-windows-forms.md)  
 Popisuje architekturu <xref:System.Windows.Forms.DataGridView> ovládacího prvku, která vysvětluje jeho hierarchii typů a strukturu dědičnosti.  
  
 [Scénáře ovládacího prvku DataGridView](datagridview-control-scenarios-windows-forms.md)  
 V této části najdete popis nejběžnějších scénářů, ve kterých <xref:System.Windows.Forms.DataGridView> se používají ovládací prvky.  
  
 [Adresář kódu ovládacího prvku DataGridView](datagridview-control-code-directory-windows-forms.md)  
 Obsahuje odkazy na příklady kódu v dokumentaci pro různé <xref:System.Windows.Forms.DataGridView> úlohy. Tyto příklady jsou zařazeny do kategorií podle typu úkolu.  
  
## <a name="related-sections"></a>Související oddíly  
 [Typy sloupců v ovládacím prvku Windows Forms DataGridView](column-types-in-the-windows-forms-datagridview-control.md)  
 Popisuje typy sloupců v <xref:System.Windows.Forms.DataGridView> ovládacím prvku model Windows Forms, které slouží k zobrazení informací a umožňují uživatelům upravovat nebo přidávat informace.  
  
 [Zobrazení dat v ovládacím prvku Windows Forms DataGridView](displaying-data-in-the-windows-forms-datagridview-control.md)  
 Poskytuje témata, které popisují způsob naplnění ovládacího prvku daty buď ručně, nebo z externího zdroje dat.  
  
 [Přizpůsobení ovládacího prvku Windows Forms DataGridView](customizing-the-windows-forms-datagridview-control.md)  
 Poskytuje témata, které popisují vlastní vybarvení <xref:System.Windows.Forms.DataGridView> buněk a řádků a vytváření odvozených typů buněk, sloupců a řádků.  
  
 [Ladění výkonu v ovládacím prvku Windows Forms DataGridView](performance-tuning-in-the-windows-forms-datagridview-control.md)  
 Poskytuje témata, které popisují, jak efektivně používat ovládací prvek, aby se zabránilo problémům s výkonem při práci s velkým objemem dat.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [DataGridView – ovládací prvek](datagridview-control-windows-forms.md)
- [Výchozí funkce v ovládacím prvku Windows Forms DataGridView](default-functionality-in-the-windows-forms-datagridview-control.md)
- [Výchozí zpracování klávesnice a myši v ovládacím prvku Windows Forms DataGridView](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
