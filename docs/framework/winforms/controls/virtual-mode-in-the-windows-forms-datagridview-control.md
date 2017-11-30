---
title: "Virtuální režim v ovládacím prvku Windows Forms DataGridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: DataGridView control [Windows Forms], virtual mode
ms.assetid: feae5d43-2848-4b1a-8ea7-77085dc415b5
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 10c6afbcde22a82e6227ce1d95d57749bee1a88c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="virtual-mode-in-the-windows-forms-datagridview-control"></a>Virtuální režim v ovládacím prvku Windows Forms DataGridView
Virtuální režim, můžete spravovat interakce mezi <xref:System.Windows.Forms.DataGridView> řízení a vlastní datové mezipaměti. Chcete-li implementovat virtuální režim, nastavte <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> vlastnost `true` a zpracovat jeden nebo více událostí, které jsou popsané v tomto tématu. Obvykle bude zpracovávat alespoň `CellValueNeeded` událost, která umožňuje vzhledu ovládacího prvku hodnot v datové mezipaměti.  
  
## <a name="bound-mode-and-virtual-mode"></a>Vázané režim a virtuální režim  
 Virtuální režim je nutné pouze v případě potřeby k doplnění nebo nahrazení vázané režimu. V vázané režimu, můžete nastavit <xref:System.Windows.Forms.DataGridView.DataSource%2A> vlastnost a ovládací prvek automaticky načte data ze zadaného zdroje a odešle uživatel změní na jiné místo. Můžete řídit, které vázaných sloupců se zobrazují a zdroji dat, samotné obvykle zpracovává operace, jako je například řazení.  
  
## <a name="supplementing-bound-mode"></a>Dodávání vázané režimu  
 Vázané režimu lze rozšířit pomocí zobrazení nevázaných sloupců společně s vázané sloupce. To se někdy označuje jako "smíšený režim" a jsou užitečné pro zobrazení akce, jako je počítaných hodnot nebo uživatelského rozhraní (UI) ovládací prvky.  
  
 Protože nevázaných sloupců je mimo zdroj dat, jsou ignorovány ve zdroji dat operace řazení. Proto když povolíte řazení ve smíšeném režimu, musí spravovat nepřipojená data v místní mezipaměti a implementace virtuálního režimu umožníte <xref:System.Windows.Forms.DataGridView> řízení pracovat s ním.  
  
 Další informace o používání virtuálních režimu zachování hodnoty v nevázaných sloupců, podívejte se na příklady v <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A?displayProperty=nameWithType> vlastnost a <xref:System.Windows.Forms.DataGridViewComboBoxColumn?displayProperty=nameWithType> třídy referenční témata.  
  
## <a name="replacing-bound-mode"></a>Nahrazení vázané režimu  
 Pokud vázané režim nesplňuje vašim požadavkům na výkon, můžete spravovat všechna vaše data v vlastní mezipaměti prostřednictvím obslužné rutiny událostí Virtuální režim. Můžete například použít virtuální režim k implementaci dat za běhu načítání mechanismus, který načte jenom tolik dat z databáze síťových, jako je nezbytné k zajištění optimálního výkonu. Tento scénář je zvláště užitečná při práci s velkými objemy dat přes pomalé připojení k síti nebo se klientské počítače, které mají omezené množství paměti RAM nebo úložný prostor.  
  
 Další informace o používání virtuální režim ve scénáři za běhu, najdete v části [implementace virtuálního režimu s JIT načítání dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md).  
  
## <a name="virtual-mode-events"></a>Virtuální režim události  
 Pokud vaše data jsou jen pro čtení, `CellValueNeeded` události může být pouze událost, budete muset zpracovat. Další virtuální režim události umožňují povolit určitých funkcí jako uživatelské úpravy, řádek přidání a odstranění a transakce na úrovni řádků.  
  
 Některé standardní <xref:System.Windows.Forms.DataGridView> události (například události, které dojít, když uživatelé přidat nebo odstranit řádky nebo pokud buňka hodnoty jsou úpravy, analyzovat, ověřit nebo naformátovaný) jsou užitečné v virtuální režim také. Můžete také zpracovat události, které umožňují udržovat hodnoty, které obvykle nejsou uložené v vázaný datový zdroj, například buňky text popisku, buňky a text chyby řádek, buňky a řádek místní nabídky dat a dat výšku řádku.  
  
 Další informace o implementace virtuálního režimu ke správě pro čtení a zápis dat v rozsahu, potvrdit nízkoúrovňové najdete v tématu [návod: Implementace virtuálního režimu v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).  
  
 Příklad, který implementuje virtuálního režimu s obor potvrzení úrovni buněk, naleznete v části <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> vlastnost referenční téma.  
  
 Proběhne pouze když <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> je nastavena na `true`.  
  
|Událost|Popis|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.DataGridView.CellValueNeeded>|Používá k načtení hodnoty buňky z mezipaměť dat pro zobrazení ovládacího prvku. K této události dochází pouze pro buněk v nevázaných sloupců.|  
|<xref:System.Windows.Forms.DataGridView.CellValuePushed>|Potvrzení uživatelský vstup pro buňku mezipaměť dat používá ovládacího prvku. K této události dochází pouze pro buněk v nevázaných sloupců.<br /><br /> Volání <xref:System.Windows.Forms.DataGridView.UpdateCellValue%2A> metoda při změně hodnotu uloženou v mezipaměti mimo <xref:System.Windows.Forms.DataGridView.CellValuePushed> obslužné rutiny události, ujistěte se, že je aktuální hodnota nezobrazí v ovládacím prvku a použít všechny režimy Automatická změna velikosti aktuálně v platnost.|  
|<xref:System.Windows.Forms.DataGridView.NewRowNeeded>|Pomocí ovládacího prvku je třeba nový řádek v datové mezipaměti.|  
|<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>|Ovládací prvek používá k určení, zda má řádek všechny nepotvrzené změny.|  
|<xref:System.Windows.Forms.DataGridView.CancelRowEdit>|Používá k označení, že řádek by měl vrátit se do své mezipaměti hodnoty ovládacího prvku.|  
  
 Tyto události jsou užitečné v virtuální režim, ale je možné bez ohledu na to <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> nastavení vlastnosti.  
  
|Události|Popis|  
|------------|-----------------|  
|<xref:System.Windows.Forms.DataGridView.UserDeletingRow><br /><br /> <xref:System.Windows.Forms.DataGridView.UserDeletedRow><br /><br /> <xref:System.Windows.Forms.DataGridView.RowsRemoved><br /><br /> <xref:System.Windows.Forms.DataGridView.RowsAdded>|Používá ovládacího prvku označíte, když jsou odstraněných řádků nebo přidané, když necháte aktualizovat mezipaměť dat odpovídajícím způsobem.|  
|<xref:System.Windows.Forms.DataGridView.CellFormatting><br /><br /> <xref:System.Windows.Forms.DataGridView.CellParsing><br /><br /> <xref:System.Windows.Forms.DataGridView.CellValidating><br /><br /> <xref:System.Windows.Forms.DataGridView.CellValidated><br /><br /> <xref:System.Windows.Forms.DataGridView.RowValidating><br /><br /> <xref:System.Windows.Forms.DataGridView.RowValidated>|Používá k zobrazení a k analýze a ověření vstupu uživatele do formátu hodnot v buňkách ovládacího prvku.|  
|<xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded>|Ovládací prvek používají k načítání text popisu tlačítka buňky při <xref:System.Windows.Forms.DataGridView.DataSource%2A> je nastavena nebo <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> vlastnost je `true`.<br /><br /> Popisy tlačítek buněk se zobrazí pouze tehdy, když <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> hodnota vlastnosti je `true`.|  
|<xref:System.Windows.Forms.DataGridView.CellErrorTextNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowErrorTextNeeded>|Ovládací prvek používají k načítání buňku nebo řádek text chyby při <xref:System.Windows.Forms.DataGridView.DataSource%2A> je nastavena nebo <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> vlastnost je `true`.<br /><br /> Volání <xref:System.Windows.Forms.DataGridView.UpdateCellErrorText%2A> metoda nebo <xref:System.Windows.Forms.DataGridView.UpdateRowErrorText%2A> metoda při změně buňku nebo řádek text chyby zajistit, že je aktuální hodnota zobrazena v ovládacím prvku.<br /><br /> Buňky a řádek glyfů chyba se zobrazí při <xref:System.Windows.Forms.DataGridView.ShowCellErrors%2A> a <xref:System.Windows.Forms.DataGridView.ShowRowErrors%2A> jsou hodnoty vlastností `true`.|  
|<xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowContextMenuStripNeeded>|Ovládací prvek používají k načítání buňku nebo řádek <xref:System.Windows.Forms.ContextMenuStrip> při ovládacího prvku <xref:System.Windows.Forms.DataGridView.DataSource%2A> je nastavena nebo <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> vlastnost je `true`.|  
|<xref:System.Windows.Forms.DataGridView.RowHeightInfoNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowHeightInfoPushed>|Ovládací prvek používá k načtení nebo ukládání informací výšky řádku v datové mezipaměti. Volání <xref:System.Windows.Forms.DataGridView.UpdateRowHeightInfo%2A> metoda při změně informace uložené v mezipaměti řádek výška mimo <xref:System.Windows.Forms.DataGridView.RowHeightInfoPushed> obslužné rutiny události pro zajištění, že aktuální hodnota se používá v zobrazení ovládacího prvku.|  
  
## <a name="best-practices-in-virtual-mode"></a>Osvědčené postupy v virtuální režim  
 Pokud jsou implementace virtuálního režimu, aby bylo možné efektivně pracovat s velkými objemy dat, budete také chtít Ujistěte se, že pracujete efektivně <xref:System.Windows.Forms.DataGridView> ovládací prvek. Další informace o efektivní využití styly buňky, automatická změna velikosti, výběr a sdílení řádků najdete v tématu [osvědčené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 [Ladění výkonu v systému Windows Forms DataGridView – ovládací prvek](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 [Osvědčené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 [Návod: Implementace virtuálního režimu v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)  
 [Implementace virtuálního režimu s načítáním v ovládacím prvku Windows Forms DataGridView dat za běhu](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)
