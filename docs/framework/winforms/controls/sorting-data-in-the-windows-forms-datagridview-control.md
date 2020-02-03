---
title: Řazení dat v ovládacím prvku DataGridView
ms.date: 02/13/2018
helpviewer_keywords:
- data [Windows Forms], sorting in grids
- data grids [Windows Forms], sorting data
- DataGridView control [Windows Forms], sorting data
ms.assetid: c1d4f24c-d961-4181-809d-5a5caa6122e4
ms.openlocfilehash: 1fcd5a5f5c6d690c573c4c2c5fa7c32aa0292441
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742942"
---
# <a name="sorting-data-in-the-windows-forms-datagridview-control"></a>Řazení dat v ovládacím prvku DataGridView model Windows Forms

Ve výchozím nastavení mohou uživatelé řadit data v ovládacím prvku <xref:System.Windows.Forms.DataGridView> kliknutím na záhlaví sloupce textového pole (nebo stisknutím klávesy F3, když se buňka textového pole zaměřuje na .NET Framework 4.7.2 a novějších verzích). Můžete upravit vlastnost <xref:System.Windows.Forms.DataGridViewColumn.SortMode> určitých sloupců a umožnit tak uživatelům řazení podle jiných typů sloupců, když to bude mít smysl. Data můžete také seřadit programově pomocí libovolného sloupce nebo více sloupců.

## <a name="in-this-section"></a>V tomto oddílu

[Režimy řazení sloupce v ovládacím prvku Windows Forms DataGridView](column-sort-modes-in-the-windows-forms-datagridview-control.md)  
Popisuje možnosti pro řazení dat v ovládacím prvku.

[Postupy: Nastavení režimů řazení pro sloupce v ovládacím prvku Windows Forms DataGridView](set-the-sort-modes-for-columns-wf-datagridview-control.md)  
Popisuje, jak uživatelům umožnit řazení podle sloupců, které ve výchozím nastavení neodpovídají.

[Postupy: Přizpůsobení řazení v ovládacím prvku Windows Forms DataGridView](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)  
Popisuje, jak řadit data programově a jak přizpůsobit řazení pomocí události <xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType> nebo implementací rozhraní <xref:System.Collections.IComparer>.

## <a name="reference"></a>Referenční informace

<xref:System.Windows.Forms.DataGridView>  
Poskytuje referenční dokumentaci pro ovládací prvek <xref:System.Windows.Forms.DataGridView>.  

<xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>  
Poskytuje referenční dokumentaci pro metodu <xref:System.Windows.Forms.DataGridView.Sort%2A>.

<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>  
Poskytuje referenční dokumentaci pro vlastnost <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>.

<xref:System.Windows.Forms.DataGridViewColumnSortMode>  
Poskytuje referenční dokumentaci pro výčet <xref:System.Windows.Forms.DataGridViewColumnSortMode>.

## <a name="see-also"></a>Viz také

- [Ovládací prvek DataGridView](datagridview-control-windows-forms.md)
- [Typy sloupců v ovládacím prvku Windows Forms DataGridView](column-types-in-the-windows-forms-datagridview-control.md)
