---
title: DataGridView – přehled ovládacího prvku
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
ms.openlocfilehash: 74de5b449525be9ff93fcbef0ddabd041470177c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742491"
---
# <a name="datagridview-control-overview-windows-forms"></a>DataGridView – přehled ovládacího prvku (Windows Forms)
> [!NOTE]
> Ovládací prvek <xref:System.Windows.Forms.DataGridView> nahrazuje a přidává funkce do ovládacího prvku <xref:System.Windows.Forms.DataGrid>; Nicméně ovládací prvek <xref:System.Windows.Forms.DataGrid> se zachovává pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte. Další informace naleznete v tématu [rozdíly mezi ovládacími prvky model Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Pomocí ovládacího prvku <xref:System.Windows.Forms.DataGridView> můžete zobrazit a upravit tabulková data z mnoha různých druhů zdrojů dat.  
  
 Vázání dat na ovládací prvek <xref:System.Windows.Forms.DataGridView> je jednoduché a intuitivní a v mnoha případech je to jednoduché jako nastavení vlastnosti <xref:System.Windows.Forms.DataGridView.DataSource%2A>. Při vytváření vazby ke zdroji dat, který obsahuje více seznamů nebo tabulek, nastavte vlastnost <xref:System.Windows.Forms.DataGridView.DataMember%2A> na řetězec, který určuje seznam nebo tabulku, ke které se má vytvořit vazba.  
  
 Ovládací prvek <xref:System.Windows.Forms.DataGridView> podporuje model datové vazby Standard model Windows Forms, takže se vytvoří vazba na instance tříd popsané v následujícím seznamu:  
  
- Libovolná třída, která implementuje rozhraní <xref:System.Collections.IList>, včetně jednorozměrného pole.  
  
- Libovolná třída, která implementuje rozhraní <xref:System.ComponentModel.IListSource>, jako jsou <xref:System.Data.DataTable> a třídy <xref:System.Data.DataSet>.  
  
- Libovolná třída, která implementuje rozhraní <xref:System.ComponentModel.IBindingList>, jako je například třída <xref:System.ComponentModel.BindingList%601>.  
  
- Libovolná třída, která implementuje rozhraní <xref:System.ComponentModel.IBindingListView>, jako je například třída <xref:System.Windows.Forms.BindingSource>.  
  
 Ovládací prvek <xref:System.Windows.Forms.DataGridView> podporuje datovou vazbu na veřejné vlastnosti objektů vrácených těmito rozhraními nebo na kolekci vlastností vrácenou rozhraním <xref:System.ComponentModel.ICustomTypeDescriptor>, pokud jsou implementovány u vrácených objektů.  
  
 Obvykle budete navazovat vazby na komponentu <xref:System.Windows.Forms.BindingSource> a navážete komponentu <xref:System.Windows.Forms.BindingSource> na jiný zdroj dat nebo ji naplnit obchodními objekty. Součást <xref:System.Windows.Forms.BindingSource> je preferovaným zdrojem dat, protože může vytvořit vazbu na širokou škálu zdrojů dat a může automaticky vyřešit mnoho problémů s datovou vazbou. Další informace najdete v tématu [Komponenta BindingSource](bindingsource-component.md).  
  
 Ovládací prvek <xref:System.Windows.Forms.DataGridView> lze také použít v *nevázaném* režimu bez příslušného úložiště dat. Příklad kódu, který používá nevázaný ovládací prvek <xref:System.Windows.Forms.DataGridView>, naleznete v tématu [Návod: Vytvoření nevázaného ovládacího prvku DataGridView model Windows Forms](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).  
  
 <xref:System.Windows.Forms.DataGridView> ovládací prvek je vysoce konfigurovatelný a rozšiřitelný a poskytuje mnoho vlastností, metod a událostí pro přizpůsobení jeho vzhledu a chování. Pokud chcete, aby aplikace model Windows Forms zobrazovala tabulková data, zvažte použití ovládacího prvku <xref:System.Windows.Forms.DataGridView> před jinými (například <xref:System.Windows.Forms.DataGrid>). Pokud zobrazujete malou mřížku hodnot jen pro čtení, nebo pokud pro uživatele povolíte úpravu tabulky s miliony záznamů, <xref:System.Windows.Forms.DataGridView> ovládací prvek vám poskytne snadno programovatelné řešení, které je efektivní pro paměť.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Souhrn technologie ovládacího prvku DataGridView](datagridview-control-technology-summary-windows-forms.md)  
 Shrnuje <xref:System.Windows.Forms.DataGridView> koncepty řízení a použití souvisejících tříd.  
  
 [Architektura ovládacího prvku DataGridView](datagridview-control-architecture-windows-forms.md)  
 Popisuje architekturu ovládacího prvku <xref:System.Windows.Forms.DataGridView> a vysvětluje jeho hierarchii typů a strukturu dědičnosti.  
  
 [Scénáře ovládacího prvku DataGridView](datagridview-control-scenarios-windows-forms.md)  
 V této části najdete popis nejběžnějších scénářů, ve kterých se používají <xref:System.Windows.Forms.DataGridView> ovládací prvky.  
  
 [Adresář kódu ovládacího prvku DataGridView](datagridview-control-code-directory-windows-forms.md)  
 Obsahuje odkazy na příklady kódu v dokumentaci pro různé úlohy <xref:System.Windows.Forms.DataGridView>. Tyto příklady jsou zařazeny do kategorií podle typu úkolu.  
  
## <a name="related-sections"></a>Související oddíly  
 [Typy sloupců v ovládacím prvku Windows Forms DataGridView](column-types-in-the-windows-forms-datagridview-control.md)  
 Popisuje typy sloupců v ovládacím prvku model Windows Forms <xref:System.Windows.Forms.DataGridView>, který slouží k zobrazení informací a umožňuje uživatelům upravovat nebo přidávat informace.  
  
 [Zobrazení dat v ovládacím prvku Windows Forms DataGridView](displaying-data-in-the-windows-forms-datagridview-control.md)  
 Poskytuje témata, které popisují způsob naplnění ovládacího prvku daty buď ručně, nebo z externího zdroje dat.  
  
 [Přizpůsobení ovládacího prvku Windows Forms DataGridView](customizing-the-windows-forms-datagridview-control.md)  
 Poskytuje témata, která popisují vlastní Malování <xref:System.Windows.Forms.DataGridView> buňky a řádky a vytváření odvozených typů buněk, sloupců a řádků.  
  
 [Ladění výkonu v ovládacím prvku Windows Forms DataGridView](performance-tuning-in-the-windows-forms-datagridview-control.md)  
 Poskytuje témata, které popisují, jak efektivně používat ovládací prvek, aby se zabránilo problémům s výkonem při práci s velkým objemem dat.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Ovládací prvek DataGridView](datagridview-control-windows-forms.md)
- [Výchozí funkce v ovládacím prvku Windows Forms DataGridView](default-functionality-in-the-windows-forms-datagridview-control.md)
- [Výchozí zpracování klávesnice a myši v ovládacím prvku Windows Forms DataGridView](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
