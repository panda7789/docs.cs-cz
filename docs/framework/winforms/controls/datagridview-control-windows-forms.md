---
title: DataGridView – ovládací prvek
description: Naučte se používat `DataGridView` ovládací prvek k zobrazení zobrazení s malým množstvím dat jen pro čtení, nebo ke změně velikosti pro zobrazení upravitelných zobrazení velmi rozsáhlých datových sad.
ms.date: 03/30/2017
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
ms.openlocfilehash: f9a45e8be7975697ca5c0d019c6bc4119f562aea
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325900"
---
# <a name="datagridview-control-windows-forms"></a>DataGridView – ovládací prvek (Windows Forms)
`DataGridView`Ovládací prvek poskytuje výkonný a flexibilní způsob zobrazení dat v tabulkovém formátu. Ovládací prvek můžete použít `DataGridView` k zobrazení zobrazení s malým množstvím dat jen pro čtení, nebo můžete škálovat a zobrazit upravitelná zobrazení velmi rozsáhlých datových sad.  
  
 Ovládací prvek můžete roztáhnout `DataGridView` mnoha způsoby, abyste mohli vytvářet vlastní chování do svých aplikací. Můžete například programově zadat vlastní algoritmy řazení a můžete vytvořit vlastní typy buněk. Vzhled ovládacího prvku lze snadno přizpůsobit výběrem `DataGridView` z několika vlastností. Jako zdroj dat lze použít mnoho typů úložišť dat, nebo `DataGridView` ovládací prvek může fungovat bez vazby na zdroj dat.  
  
 Témata v této části popisují koncepty a techniky, které můžete použít k vytváření funkcí v `DataGridView` aplikacích.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [DataGridView – přehled ovládacího prvku](datagridview-control-overview-windows-forms.md)  
 Poskytuje témata, která popisují architekturu a základní koncepty `DataGridView` ovládacího prvku model Windows Forms.  
  
 [Výchozí funkce v ovládacím prvku Windows Forms DataGridView](default-functionality-in-the-windows-forms-datagridview-control.md)  
 Popisuje výchozí vzhled a chování ovládacího prvku model Windows Forms, `DataGridView` když je svázán se zdrojem dat.  
  
 [Typy sloupců v ovládacím prvku Windows Forms DataGridView](column-types-in-the-windows-forms-datagridview-control.md)  
 Popisuje typy sloupců v `DataGridView` ovládacím prvku model Windows Forms, které slouží k zobrazení dat a umožňují uživatelům upravovat nebo přidávat data.  
  
 [Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView](basic-column-row-and-cell-features-wf-datagridview-control.md)  
 Poskytuje témata, která popisují běžně používané vlastnosti buňky, řádku a sloupce.  
  
 [Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 Poskytuje témata, které popisují, jak upravit základní vzhled ovládacího prvku a formátování zobrazení dat buněk.  
  
 [Zobrazení dat v ovládacím prvku Windows Forms DataGridView](displaying-data-in-the-windows-forms-datagridview-control.md)  
 Poskytuje témata, které popisují způsob naplnění ovládacího prvku daty buď ručně, nebo z externího zdroje dat.  
  
 [Změna velikosti sloupců a řádků v ovládacím prvku Windows Forms DataGridView](resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)  
 Poskytuje témata, která popisují, jak lze velikost řádků a sloupců automaticky upravit tak, aby odpovídala obsahu buňky nebo aby odpovídala dostupné šířce ovládacího prvku.  
  
 [Řazení dat v ovládacím prvku Windows Forms DataGridView](sorting-data-in-the-windows-forms-datagridview-control.md)  
 Obsahuje témata, která popisují funkce řazení v ovládacím prvku.  
  
 [Zadávání dat v ovládacím prvku Windows Forms DataGridView](data-entry-in-the-windows-forms-datagridview-control.md)  
 Poskytuje témata, která popisují, jak změnit způsob, jakým uživatelé přidávají a upravují data v ovládacím prvku.  
  
 [Výběr a používání schránky s ovládacím prvkem Windows Forms DataGridView](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)  
 Obsahuje témata, která popisují funkce výběru buněk, řádků a sloupců v ovládacím prvku.  
  
 [Programování s buňkami, řádky a sloupci v ovládacím prvku Windows Forms DataGridView](programming-with-cells-rows-and-columns-in-the-datagrid.md)  
 Poskytuje témata, která popisují, jak programovat s objekty buňky, řádku a sloupce.  
  
 [Přizpůsobení ovládacího prvku Windows Forms DataGridView](customizing-the-windows-forms-datagridview-control.md)  
 Poskytuje témata, které popisují vlastní vybarvení `DataGridView` buněk a řádků a vytváření odvozených typů buněk, sloupců a řádků.  
  
 [Ladění výkonu v ovládacím prvku Windows Forms DataGridView](performance-tuning-in-the-windows-forms-datagridview-control.md)  
 Poskytuje témata, které popisují, jak efektivně používat ovládací prvek, aby se zabránilo problémům s výkonem při práci s velkým objemem dat.  
  
 [Výchozí zpracování klávesnice a myši v ovládacím prvku Windows Forms DataGridView](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)  
 Popisuje, jak uživatelé mohou pracovat s `DataGridView` ovládacím prvkem prostřednictvím klávesnice a myši.  
  
 [Rozdíly mezi ovládacími prvky Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)  
 Popisuje, jak se `DataGridView` ovládací prvek zlepšuje a nahrazuje <xref:System.Windows.Forms.DataGrid> ovládací prvek.  
  
 Viz také téma [použití návrháře s ovládacím prvkem model Windows Forms DataGridView](using-the-designer-with-the-windows-forms-datagridview-control.md).  
  
## <a name="reference"></a>Referenční informace  
 <xref:System.Windows.Forms.DataGridView>  
 Poskytuje referenční dokumentaci k <xref:System.Windows.Forms.DataGridView> ovládacímu prvku.  
  
 <xref:System.Windows.Forms.BindingSource>  
 Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.BindingSource> komponentu. <xref:System.Windows.Forms.DataGridView>Ovládací prvek a <xref:System.Windows.Forms.BindingSource> součást jsou navržené tak, aby úzce spolupracovaly.  
  
## <a name="see-also"></a>Viz také

- [Ovládací prvky používané ve Windows Forms](controls-to-use-on-windows-forms.md)
