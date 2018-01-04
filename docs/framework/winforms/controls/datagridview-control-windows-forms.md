---
title: "DataGridView – ovládací prvek (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tables [Windows Forms]
- data grids [Windows Forms
- data [Windows Forms], displaying in tabular format
- grid controls [Windows Forms]
- datasets [Windows Forms], user interface
- Windows Forms, displaying data
- data presentation
- tabular data [Windows Forms], displaying on Windows Forms
- datasets [Windows Forms], displaying in DataGridView control
- DataGridView control [Windows Forms]
ms.assetid: dbee73f2-bba6-4874-9389-cd21d44309be
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 51f6765e5960ddadd27a476f7229a76fbfe985e4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="datagridview-control-windows-forms"></a>DataGridView – ovládací prvek (Windows Forms)
`DataGridView` Řízení poskytuje výkonný a flexibilní způsob, jak zobrazit data ve formátu tabulky. Můžete použít `DataGridView` řízení zobrazíte jen pro čtení zobrazení malé množství dat nebo je možné škálovat, aby bylo zřejmé, upravitelných zobrazeních velmi rozsáhlých datových sad.  
  
 Můžete rozšířit `DataGridView` řízení různými způsoby, jak vytvořit vlastní chování do svých aplikací. Například můžete programově zadat vlastní řazení algoritmy a můžete vytvořit vlastní typy buněk. Můžete snadno přizpůsobit vzhled `DataGridView` řízení můžete volit mezi několik vlastností. Mnoho typů úložišť dat lze použít jako zdroj dat nebo `DataGridView` řízení můžete pracovat s žádný zdroj dat, který je vázaný na ni.  
  
 Témata v této části popisují koncepty a techniky, které můžete použít k vytvoření `DataGridView` funkce do svých aplikací.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Přehled ovládacího prvku DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)  
 Obsahuje témata, která popisují architekturu a základní koncepty Windows Forms `DataGridView` ovládacího prvku.  
  
 [Výchozí funkce v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/default-functionality-in-the-windows-forms-datagridview-control.md)  
 Popisuje výchozí vzhled a chování Windows Forms `DataGridView` řídit, kdy je vázán na zdroj dat.  
  
 [Typy sloupců v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  
 Popisuje typy sloupců v modelu Windows Forms `DataGridView` ovládací prvek použitý k zobrazení dat a povolit uživatelům změnit nebo přidat data.  
  
 [Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 Obsahuje témata, která popisují běžně používané vlastnosti buněk, řádků a sloupců.  
  
 [Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 Obsahuje témata, která popisují, jak upravit základní vzhled ovládacího prvku a formátování zobrazení dat v buňce.  
  
 [Zobrazení dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 Obsahuje témata, která popisují, jak buď ručně, nebo z externího zdroje dat naplnit ovládací prvek s daty.  
  
 [Změna velikosti sloupců a řádků v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)  
 Obsahuje témata, která popisují, jak velikosti řádků a sloupců lze upravit automaticky podle obsahu buňky nebo podle dostupné šířky ovládacího prvku.  
  
 [Řazení dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)  
 Obsahuje témata, která popisují řazení funkce v ovládacím prvku.  
  
 [Zadávání dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 Obsahuje témata, která popisují, jak změnit způsob uživatele, přidání a změna dat v ovládacím prvku.  
  
 [Výběr a používání schránky s ovládacím prvkem Windows Forms DataGridView](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)  
 Obsahuje témata, která popisují funkce Výběr buněk, řádků a sloupců v ovládacím prvku.  
  
 [Programování s buňkami, řádky a sloupci v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)  
 Obsahuje témata, která popisují, jak programovat s buněk, řádků a sloupec objekty.  
  
 [Přizpůsobení ovládacího prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 Obsahuje témata, která popisují vlastní Malování `DataGridView` buněk a řádků a vytváření odvozené buňky, sloupce a typy řádků.  
  
 [Ladění výkonu v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 Obsahuje témata, která popisují, jak efektivně používat ovládací prvek, aby se zabránilo problémům s výkonem při práci s velkými objemy dat.  
  
 [Výchozí zpracování klávesnice a myši v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)  
 Popisuje, jak mohou uživatelé komunikovat s `DataGridView` řízení prostřednictvím klávesnici a myš.  
  
 [Rozdíly mezi ovládacími prvky Windows Forms DataGridView a DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)  
 Popisuje, jak `DataGridView` řízení zlepšuje při a nahradí <xref:System.Windows.Forms.DataGrid> ovládacího prvku.  
  
 Viz také [s ovládacím prvkem Windows Forms DataGridView pomocí návrháře](http://msdn.microsoft.com/library/ms171593\(v=vs.110\)).  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Windows.Forms.DataGridView>  
 Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView> ovládacího prvku.  
  
 <xref:System.Windows.Forms.BindingSource>  
 Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.BindingSource> součásti. <xref:System.Windows.Forms.DataGridView> Řízení a <xref:System.Windows.Forms.BindingSource> součást jsou navrženy pro práci úzce spolupracují.  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvky používané ve Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
