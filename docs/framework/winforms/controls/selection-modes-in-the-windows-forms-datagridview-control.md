---
title: Režimy výběru v ovládacím prvku DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- selection [Windows Forms], modes in DataGridView control
- DataGridView control [Windows Forms], selection mode
ms.assetid: a3ebfd3d-0525-479d-9d96-d9e017289b36
ms.openlocfilehash: e20bf6307d77bf189b698e847c6b855c249dc3c1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743038"
---
# <a name="selection-modes-in-the-windows-forms-datagridview-control"></a>Režimy výběru v ovládacím prvku Windows Forms DataGridView

Někdy budete chtít, aby aplikace prováděla akce na základě výběrů uživatele v rámci ovládacího prvku <xref:System.Windows.Forms.DataGridView>. V závislosti na akcích můžete chtít omezit druhy výběru, které jsou možné. Předpokládejme například, že vaše aplikace může vytisknout sestavu pro aktuálně vybraný záznam. V takovém případě můžete chtít nakonfigurovat <xref:System.Windows.Forms.DataGridView> ovládací prvek tak, aby při kliknutí kamkoli v rámci řádku vždy vybral celý řádek, a tak, aby bylo možné vybrat pouze jeden řádek najednou.

Můžete určit výběr povolený nastavením vlastnosti <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> na jednu z následujících <xref:System.Windows.Forms.DataGridViewSelectionMode> hodnot výčtu.

|Hodnota DataGridViewSelectionMode|Popis|
|-------------------------------------|-----------------|
|<xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>|Kliknutím na buňku ji vyberete. Záhlaví řádků a sloupců nelze použít pro výběr.|
|<xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>|Kliknutím na buňku ji vyberete. Kliknutím na záhlaví sloupce vyberete celý sloupec. Záhlaví sloupců nelze použít pro řazení.|
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>|Kliknutím na buňku nebo záhlaví sloupce vyberete celý sloupec. Záhlaví sloupců nelze použít pro řazení.|
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>|Kliknutím na buňku nebo záhlaví řádku vyberete celý řádek.|
|<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>|Výchozí režim výběru. Kliknutím na buňku ji vyberete. Kliknutím na záhlaví řádku vyberete celý řádek.|

> [!NOTE]
> Změna režimu výběru v době běhu automaticky vymaže aktuální výběr.

Ve výchozím nastavení mohou uživatelé vybrat více řádků, sloupců nebo buněk přetažením pomocí myši, stisknutím klávesy CTRL nebo SHIFT při výběru rozšíří nebo upravit výběr, nebo kliknutím na buňku v levém horním rohu vybrat všechny buňky v ovládacím prvku. Chcete-li tomuto chování zabránit, nastavte vlastnost <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> na hodnotu `false`.

Režimy <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> a <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> umožňují uživatelům odstraňovat řádky jejich výběrem a stisknutím klávesy DELETE. Uživatelé mohou odstraňovat řádky pouze v případě, že aktuální buňka není v režimu úprav, vlastnost <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> je nastavena na hodnotu `true`a podkladový zdroj dat podporuje odstranění řádků řízené uživatelem. Všimněte si, že tato nastavení nebrání programovému odstranění řádků.

## <a name="programmatic-selection"></a>Programový výběr

Aktuální režim výběru omezuje chování programového výběru i výběr uživatele. Aktuální výběr můžete změnit programově nastavením vlastnosti `Selected` všech buněk, řádků nebo sloupců přítomných v ovládacím prvku <xref:System.Windows.Forms.DataGridView>. Můžete také vybrat všechny buňky v ovládacím prvku pomocí metody <xref:System.Windows.Forms.DataGridView.SelectAll%2A> v závislosti na režimu výběru. Chcete-li výběr zrušit, použijte metodu <xref:System.Windows.Forms.DataGridView.ClearSelection%2A>.

Je-li vlastnost <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> nastavena na hodnotu `true`, lze přidat <xref:System.Windows.Forms.DataGridView> prvky nebo je z výběru odebrat změnou vlastnosti `Selected` prvku. V opačném případě nastavení vlastnosti `Selected` na `true` pro jeden prvek automaticky odstraní další prvky z výběru.

Všimněte si, že změna hodnoty vlastnosti <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> nemění aktuální výběr.

Kolekci aktuálně vybraných buněk, řádků nebo sloupců můžete načíst prostřednictvím vlastností <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>a <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> ovládacího prvku <xref:System.Windows.Forms.DataGridView>. Přístup k těmto vlastnostem je neefektivní, pokud je vybrána každá buňka v ovládacím prvku. Aby se zabránilo snížení výkonu v tomto případě, použijte nejprve metodu <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>. K určení počtu vybraných buněk, řádků nebo sloupců může být také neefektivní přístup k těmto kolekcím. Místo toho byste měli použít metodu <xref:System.Windows.Forms.DataGridView.GetCellCount%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.GetRowCount%2A>nebo <xref:System.Windows.Forms.DataGridViewColumnCollection.GetColumnCount%2A>, která předává hodnotu <xref:System.Windows.Forms.DataGridViewElementStates.Selected>.

> [!TIP]
> Příklad kódu, který ukazuje programové použití vybraných buněk, najdete v přehledu třídy <xref:System.Windows.Forms.DataGridView>.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.MultiSelect%2A>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridViewSelectionMode>
- [Výběr a používání schránky s ovládacím prvkem Windows Forms DataGridView](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
- [Postupy: Nastavení režimu výběru ovládacího prvku Windows Forms DataGridView](how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control.md)
