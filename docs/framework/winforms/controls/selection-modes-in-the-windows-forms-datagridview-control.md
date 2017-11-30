---
title: "Režimy výběru v ovládacím prvku Windows Forms DataGridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- selection [Windows Forms], modes in DataGridView control
- DataGridView control [Windows Forms], selection mode
ms.assetid: a3ebfd3d-0525-479d-9d96-d9e017289b36
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4f6b603382382971249b08cddd482566ec6e5fa5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="selection-modes-in-the-windows-forms-datagridview-control"></a>Režimy výběru v ovládacím prvku Windows Forms DataGridView
Někdy má vaše aplikace k provádění akcí podle volby uživatele v rámci <xref:System.Windows.Forms.DataGridView> ovládacího prvku. V závislosti na akce můžete omezit druhy výběru, které jsou možné. Předpokládejme například, že vaše aplikace můžete vytisknout sestavu pro aktuálně vybraný záznam. V takovém případě můžete nakonfigurovat <xref:System.Windows.Forms.DataGridView> ovládacího prvku tak, že kliknete na libovolné místo v řádku vždy vybere celý řádek, a proto lze vybrat že pouze jeden řádek v čase.  
  
 Můžete zadat povolenou nastavení výběr <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType> vlastnost na jednu z následujících <xref:System.Windows.Forms.DataGridViewSelectionMode> hodnot výčtu.  
  
|Hodnota DataGridViewSelectionMode|Popis|  
|-------------------------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>|Klepnutím na buňku vyberete. Záhlaví řádků a sloupců nelze použít pro výběr.|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>|Klepnutím na buňku vyberete. Kliknutím na záhlaví sloupce vybere celý sloupec. Záhlaví sloupců nelze použít k řazení.|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>|Kliknutím na buňku nebo záhlaví sloupce vybere celý sloupec. Záhlaví sloupců nelze použít k řazení.|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>|Kliknutím na buňku nebo řádek záhlaví vybere celý řádek.|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>|Výchozí režim výběru. Klepnutím na buňku vyberete. Kliknutím na záhlaví řádků vybere celý řádek.|  
  
> [!NOTE]
>  Změna režimu výběru v době běhu automaticky vymaže aktuální výběr.  
  
 Ve výchozím nastavení uživatelé mohou vybrat více řádků, sloupců nebo buněk přetažením pomocí myši, stisknutím kláves CTRL nebo SHIFT při výběru rozšířit nebo změnit výběr, nebo kliknutím na tlačítko levého horního datovou buňku a vyberte všechny buňky v ovládacím prvku. Chcete-li toto chování zakázat, nastavte <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> vlastnost `false`.  
  
 <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> a <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> režimy povolit uživatelům odstranit řádky tak, že je vyberete a stisknutím klávesy DELETE. Uživatele můžete odstranit řádky jenom v případě, že aktuální buňky není v režimu úprav, <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> je nastavena na `true`, a na podkladový zdroj dat podporuje odstranění řádku řízené uživatele. Všimněte si, že tato nastavení nebudou bránit programovým řádek odstranění.  
  
## <a name="programmatic-selection"></a>Programová výběr  
 Aktuální režim výběru omezuje chování programový výběr, jakož i výběr uživatele. Aktuální výběr můžete změnit prostřednictvím kódu programu nastavením `Selected` vlastnost žádné buněk, řádků nebo sloupců, které jsou součástí <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Můžete také vybrat všechny buňky v ovládacím prvku prostřednictvím <xref:System.Windows.Forms.DataGridView.SelectAll%2A> metoda, v závislosti na režimu výběru. Chcete-li zrušte zaškrtnutí políčka, použijte <xref:System.Windows.Forms.DataGridView.ClearSelection%2A> metoda.  
  
 Pokud <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> je nastavena na `true`, můžete přidat <xref:System.Windows.Forms.DataGridView> elementů nebo je odeberte ze výběr změnou `Selected` vlastnost elementu. Jinak, nastavení `Selected` vlastnost `true` pro jeden element další prvky automaticky odebere z výběru.  
  
 Všimněte si, že změna hodnoty <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> vlastnost nezmění aktuální výběr.  
  
 Můžete načíst kolekce aktuálně vybraných buněk, řádků a sloupců v rámci <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>, a <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> vlastnosti <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Přístup k tyto vlastnosti je neefektivní, pokud je vybrána každých buňky v ovládacím prvku. Chcete-li v tomto případě se zabránilo snížení výkonu, použijte <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> metoda první. Kromě toho přistupují k těchto kolekcí k určení počtu vybraných buněk, řádků a sloupců může být neefektivní. Místo toho používejte <xref:System.Windows.Forms.DataGridView.GetCellCount%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.GetRowCount%2A>, nebo <xref:System.Windows.Forms.DataGridViewColumnCollection.GetColumnCount%2A> předávání v případě metody <xref:System.Windows.Forms.DataGridViewElementStates.Selected> hodnotu.  
  
> [!TIP]
>  Příklad kódu, která demonstruje použití programový vybraných buněk najdete v <xref:System.Windows.Forms.DataGridView> přehledu třídy.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A>  
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>  
 <xref:System.Windows.Forms.DataGridViewSelectionMode>  
 [Výběr a používání schránky s ovládacím prvkem Windows Forms DataGridView](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)  
 [Postupy: nastavení režimu výběru ovládacího prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control.md)
