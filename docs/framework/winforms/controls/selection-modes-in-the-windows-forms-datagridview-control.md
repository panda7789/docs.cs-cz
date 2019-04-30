---
title: Režimy výběru v ovládacím prvku Windows Forms DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- selection [Windows Forms], modes in DataGridView control
- DataGridView control [Windows Forms], selection mode
ms.assetid: a3ebfd3d-0525-479d-9d96-d9e017289b36
ms.openlocfilehash: 79e13e65938252015e43b59a962d40f20963a5df
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61902665"
---
# <a name="selection-modes-in-the-windows-forms-datagridview-control"></a>Režimy výběru v ovládacím prvku Windows Forms DataGridView
Občas můžete chtít vaše aplikace k provádění akcí na základě výběrů uživatele v rámci <xref:System.Windows.Forms.DataGridView> ovládacího prvku. V závislosti na akce můžete omezit, které jsou možné druhy výběru. Předpokládejme například, že aplikace můžete vytisknout sestavu pro aktuálně vybraný záznam. V takovém případě můžete chtít konfigurovat <xref:System.Windows.Forms.DataGridView> ovládacího prvku tak, aby kliknutím kamkoli na řádku vždy vybere celý řádek, a proto je možné vybrat tuto pouze jeden řádek v čase.  
  
 Můžete zadat povolené nastavení voleb <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> vlastnost na jednu z následujících <xref:System.Windows.Forms.DataGridViewSelectionMode> hodnot výčtu.  
  
|DataGridViewSelectionMode value|Popis|  
|-------------------------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>|Klepnutím na buňku vybere. Záhlaví řádků a sloupců nelze použít pro výběr.|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>|Klepnutím na buňku vybere. Kliknutím na záhlaví sloupce vybere celý sloupec. Nelze zadat záhlaví sloupců pro řazení.|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>|Kliknutím na buňku nebo záhlaví sloupce vybere celý sloupec. Nelze zadat záhlaví sloupců pro řazení.|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>|Kliknutím na buňku nebo řádek záhlaví vybere celý řádek.|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>|Výchozí režim výběru. Klepnutím na buňku vybere. Kliknutím na záhlaví řádků vybere celý řádek.|  
  
> [!NOTE]
>  Změna režimu výběru za běhu automaticky zruší aktuální výběr.  
  
 Ve výchozím nastavení uživatele můžete vybrat více řádky, sloupce nebo buňky pomocí přetažení myší, stisknutí klávesy CTRL nebo SHIFT při výběru rozšířit nebo změnit výběr, nebo kliknutím na buňku záhlaví levého horního rohu a vyberte všechny buňky v ovládacím prvku. Chcete-li toto chování zakázat, nastavte <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> vlastnost `false`.  
  
 <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> a <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> režimy uživatelům odstraňte řádky tak, že je vyberete a stisknutím klávesy DELETE. Uživatelé, mohou odstranit řádky pouze v případě, že aktuální buňka není v režimu úprav <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> je nastavena na `true`, a podkladový zdroj dat podporuje odstranění řádku řízené uživatele. Všimněte si, že toto nastavení nebrání odstranění řádku prostřednictvím kódu programu.  
  
## <a name="programmatic-selection"></a>Výběr prostřednictvím kódu programu  
 Aktuální režim výběru omezuje chování výběru prostřednictvím kódu programu, stejně jako výběr uživatele. Aktuální výběr můžete změnit prostřednictvím kódu programu nastavením `Selected` vlastnosti buněk, řádků nebo sloupců v <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Můžete také vybrat všechny buňky v ovládacím prvku prostřednictvím <xref:System.Windows.Forms.DataGridView.SelectAll%2A> metoda, v závislosti na režimu výběru. Chcete-li zrušte zaškrtnutí políčka, použijte <xref:System.Windows.Forms.DataGridView.ClearSelection%2A> metody.  
  
 Pokud <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> je nastavena na `true`, můžete přidat <xref:System.Windows.Forms.DataGridView> prvků, které mají nebo je odeberte z výběru tak, že změníte `Selected` vlastnost elementu. V opačném případě nastavení `Selected` vlastnost `true` pro jeden element automaticky odstraní další elementy z výběru.  
  
 Poznámka: Změna hodnoty <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> vlastnost nedojde ke změně aktuálního výběru.  
  
 Kolekce aktuálně vybraných buněk, řádků nebo sloupců prostřednictvím můžete načíst <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>, a <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> vlastnosti <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Přístup k těmto vlastnostem je neefektivní, pokud je vybrána všechny buňky v ovládacím prvku. Chcete-li v tomto případě se zabránilo snížení výkonu, použijte <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> metoda první. Kromě toho přístup k těmto kolekcím k určení počtu vybraných buněk, řádků nebo sloupců může být neefektivní. Místo toho používejte <xref:System.Windows.Forms.DataGridView.GetCellCount%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.GetRowCount%2A>, nebo <xref:System.Windows.Forms.DataGridViewColumnCollection.GetColumnCount%2A> metodu <xref:System.Windows.Forms.DataGridViewElementStates.Selected> hodnotu.  
  
> [!TIP]
>  Příklad kódu, který ukazuje programová použití vybraných buněk najdete v <xref:System.Windows.Forms.DataGridView> přehledu třídy.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.MultiSelect%2A>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridViewSelectionMode>
- [Výběr a používání schránky s ovládacím prvkem Windows Forms DataGridView](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
- [Postupy: Nastavení režimu výběru ovládacího prvku Windows Forms DataGridView](how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control.md)
