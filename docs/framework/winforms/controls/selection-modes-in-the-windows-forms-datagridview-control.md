---
title: Režimy výběru v ovládacím prvku Windows Forms DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- selection [Windows Forms], modes in DataGridView control
- DataGridView control [Windows Forms], selection mode
ms.assetid: a3ebfd3d-0525-479d-9d96-d9e017289b36
ms.openlocfilehash: cfe80d5ccb73208f1c61a2ac6c9963343d398bcb
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046421"
---
# <a name="selection-modes-in-the-windows-forms-datagridview-control"></a>Režimy výběru v ovládacím prvku Windows Forms DataGridView

Někdy budete chtít, aby aplikace prováděla akce na základě výběrů uživatelů <xref:System.Windows.Forms.DataGridView> v rámci ovládacího prvku. V závislosti na akcích můžete chtít omezit druhy výběru, které jsou možné. Předpokládejme například, že vaše aplikace může vytisknout sestavu pro aktuálně vybraný záznam. V takovém případě můžete chtít nakonfigurovat <xref:System.Windows.Forms.DataGridView> ovládací prvek tak, aby při kliknutí kamkoli v rámci řádku vždy vybral celý řádek a aby bylo možné vybrat pouze jeden řádek najednou.

Můžete určit výběr povolený nastavením <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> vlastnosti na jednu z následujících <xref:System.Windows.Forms.DataGridViewSelectionMode> hodnot výčtu.

|Hodnota DataGridViewSelectionMode|Popis|
|-------------------------------------|-----------------|
|<xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>|Kliknutím na buňku ji vyberete. Záhlaví řádků a sloupců nelze použít pro výběr.|
|<xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>|Kliknutím na buňku ji vyberete. Kliknutím na záhlaví sloupce vyberete celý sloupec. Záhlaví sloupců nelze použít pro řazení.|
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>|Kliknutím na buňku nebo záhlaví sloupce vyberete celý sloupec. Záhlaví sloupců nelze použít pro řazení.|
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>|Kliknutím na buňku nebo záhlaví řádku vyberete celý řádek.|
|<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>|Výchozí režim výběru. Kliknutím na buňku ji vyberete. Kliknutím na záhlaví řádku vyberete celý řádek.|

> [!NOTE]
> Změna režimu výběru v době běhu automaticky vymaže aktuální výběr.

Ve výchozím nastavení mohou uživatelé vybrat více řádků, sloupců nebo buněk přetažením pomocí myši, stisknutím klávesy CTRL nebo SHIFT při výběru rozšíří nebo upravit výběr, nebo kliknutím na buňku v levém horním rohu vybrat všechny buňky v ovládacím prvku. Chcete-li tomuto chování zabránit, <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> nastavte vlastnost `false`na hodnotu.

Režimy <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> a<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> umožňují uživatelům odstraňovat řádky jejich výběrem a stisknutím klávesy DELETE. Uživatelé mohou odstraňovat řádky pouze v případě, že aktuální buňka není v režimu úprav, <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> vlastnost je nastavena na `true`hodnotu a podkladový zdroj dat podporuje odstranění řádků řízené uživatelem. Všimněte si, že tato nastavení nebrání programovému odstranění řádků.

## <a name="programmatic-selection"></a>Programový výběr

Aktuální režim výběru omezuje chování programového výběru i výběr uživatele. Aktuální výběr můžete změnit programově `Selected` nastavením vlastnosti všech buněk, řádků nebo sloupců přítomných <xref:System.Windows.Forms.DataGridView> v ovládacím prvku. Můžete také vybrat všechny buňky v ovládacím prvku prostřednictvím <xref:System.Windows.Forms.DataGridView.SelectAll%2A> metody v závislosti na režimu výběru. Chcete-li výběr zrušit, použijte <xref:System.Windows.Forms.DataGridView.ClearSelection%2A> metodu.

Pokud je `true` <xref:System.Windows.Forms.DataGridView> vlastnost nastavena na, můžete přidat prvky nebo je z výběru `Selected` odebrat změnou vlastnosti prvku. <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> V opačném případě `Selected` nastavení `true` vlastnosti pro jeden prvek automaticky odstraní další prvky z výběru.

Všimněte si, že změna hodnoty <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> vlastnosti nemění aktuální výběr.

Kolekci aktuálně vybraných buněk, řádků nebo sloupců můžete <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>načíst pomocí vlastností <xref:System.Windows.Forms.DataGridView> , <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>a <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> ovládacího prvku. Přístup k těmto vlastnostem je neefektivní, pokud je vybrána každá buňka v ovládacím prvku. Aby se zabránilo snížení výkonu v tomto případě, použijte <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> nejprve metodu. K určení počtu vybraných buněk, řádků nebo sloupců může být také neefektivní přístup k těmto kolekcím. Místo toho <xref:System.Windows.Forms.DataGridView.GetCellCount%2A>byste měli použít metodu, <xref:System.Windows.Forms.DataGridViewRowCollection.GetRowCount%2A>nebo <xref:System.Windows.Forms.DataGridViewColumnCollection.GetColumnCount%2A> , která <xref:System.Windows.Forms.DataGridViewElementStates.Selected> předává hodnotu.

> [!TIP]
> Příklad kódu, který ukazuje programové použití vybraných buněk, najdete v <xref:System.Windows.Forms.DataGridView> přehledu třídy.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.MultiSelect%2A>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridViewSelectionMode>
- [Výběr a používání schránky s ovládacím prvkem Windows Forms DataGridView](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
- [Postupy: Nastavení režimu výběru ovládacího prvku DataGridView model Windows Forms](how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control.md)
