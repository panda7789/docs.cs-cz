---
title: "Režimy zobrazení dat v ovládacím prvku Windows Forms DataGridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [Windows Forms], display modes
- data grids [Windows Forms], display modes
- DataGridView control [Windows Forms], display modes
ms.assetid: 9755a030-3f3f-4705-a661-ba5a48a81875
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dc7fd3d3012053d8c40edf5fdce8af45c62c98c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="data-display-modes-in-the-windows-forms-datagridview-control"></a>Režimy zobrazení dat v ovládacím prvku Windows Forms DataGridView
<xref:System.Windows.Forms.DataGridView> Řízení můžete zobrazit data ve třech různých režimech: vázaných, nevázaných a virtuální. Zvolte nejvhodnější režim podle svých požadavků.  
  
## <a name="unbound"></a>Nevázaný  
 Nevázaný režim je vhodný pro zobrazení relativně malé množství dat, které můžete spravovat prostřednictvím kódu programu. Připojení není <xref:System.Windows.Forms.DataGridView> řízení přímo ke zdroji dat jako vázané režimu. Místo toho je nutné zaplnit ovládacího prvku sami, obvykle pomocí <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> metoda.  
  
 Nevázaný režim může být obzvláště užitečné pro statické, jen pro čtení dat, nebo pokud chcete zadat vlastní kód, který komunikuje s externím úložišti. Když chcete uživatelům interakci s externího zdroje dat, ale obvykle použijete vázané režimu.  
  
 Pro příklad, který používá jen pro čtení nevázaných <xref:System.Windows.Forms.DataGridView>, najdete v části [postupy: vytvoření nevázaný ovládací prvek Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md).  
  
## <a name="bound"></a>Vázaný  
 Vázané režim je vhodný pro správu dat pomocí automatické interakci s úložištěm dat. Můžete připojit <xref:System.Windows.Forms.DataGridView> řízení přímo na zdroj dat nastavením <xref:System.Windows.Forms.DataGridView.DataSource%2A> vlastnost. Data vázaná po ovládacího prvku jsou řádky dat nabídnutých a vyžádat bez nutnosti explicitní správy z vaší strany. Když <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> vlastnost je `true`, způsobí, že každý sloupec ve zdroji dat odpovídající sloupec má být vytvořen v ovládacím prvku. Pokud ale chcete vytvořit vlastní sloupce, tuto vlastnost lze nastavit `false` a použít <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A> vlastnost pro vazbu každý sloupec při jeho konfiguraci. To je užitečné, pokud chcete použít typ sloupce než typy, které se generují ve výchozím nastavení. Další informace najdete v tématu [typy sloupců v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md).  
  
 Pro příklad, který používá hranice <xref:System.Windows.Forms.DataGridView> řízení najdete v tématu [návod: ověřování dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).  
  
 Můžete také přidat nevázaných sloupců <xref:System.Windows.Forms.DataGridView> ovládacího prvku vázané režimu. To je užitečné, pokud chcete zobrazit sloupce tlačítka nebo odkazy, které umožní uživatelům provádět akce na konkrétní řádky. Je také užitečné, pokud chcete zobrazit sloupce s hodnotami vypočítanou ze sloupce vázané. Jej můžete naplnit hodnoty buněk pro počítané sloupce v obslužnou rutinu pro <xref:System.Windows.Forms.DataGridView.CellFormatting> událostí. Pokud používáte <xref:System.Data.DataSet> nebo <xref:System.Data.DataTable> jako zdroj dat, ale můžete chtít použít <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType> vlastnosti tak, aby místo vytvoření počítaného sloupce. V takovém případě <xref:System.Windows.Forms.DataGridView> ovládací prvek bude považovat počítaný sloupec stejně jako jakýkoli jiný sloupec v datovém zdroji.  
  
 Řazení podle nevázaných sloupců v vázané režimu není podporována. Pokud vytvoříte nepřipojeného sloupce v vázané režimu, který obsahuje hodnoty, nelze upravit uživatele, je nutné implementovat virtuální režim udržovat tyto hodnoty, když ovládací prvek je seřazen podle vázané sloupce.  
  
## <a name="virtual"></a>Virtuální  
 Virtuální režim můžete implementovat vlastní data operace správy. Toto je nutné udržovat hodnoty nevázaných sloupců v vázané režimu, když ovládací prvek je seřazen podle vázané sloupců. Primárním použitím virtuální režim, ale je za účelem optimalizace výkonu při interakci s velkými objemy dat.  
  
 Připojení <xref:System.Windows.Forms.DataGridView> ovládacího prvku do mezipaměti, která spravujete a váš kód ovládacích prvků při řádky dat se instaluje a vyžádat. Chcete-li zachovat malé nároky na paměť, by měl vypadat přibližně velikost počet řádků, které jsou aktuálně zobrazený mezipaměti. Potom, co uživatel posune nové řádky do zobrazení, kódu požadavky nová data z mezipaměti a volitelně vyprázdnění stará data z paměti.  
  
 Když jsou implementace virtuálního režimu, musíte sledovat, kdy je nový řádek je potřeba v datovém modelu a při přidání nového řádku vrácení zpět. Přesný implementace tato funkce bude záviset na implementaci datového modelu a transakce sémantiku datového modelu; jestli potvrzení rozsah je na úrovni buněk nebo řádku.  
  
 Další informace o virtuální režim najdete v tématu [virtuálního režimu v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md). Příklad, který ukazuje, jak používat virtuální režim události, naleznete v části [návod: Implementace virtuálního režimu v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A?displayProperty=nameWithType>  
 [Zobrazení dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [Typy sloupců v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  
 [Návod: Vytvoření ovládacího prvku nevázaný Windows Forms DataGridView](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)  
 [Postupy: vytvoření vazby dat do ovládacího prvku Windows Forms DataGridView – ovládací prvek](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md)  
 [Virtuální režim v systému Windows Forms DataGridView – ovládací prvek](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)  
 [Návod: Implementace virtuálního režimu v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)
