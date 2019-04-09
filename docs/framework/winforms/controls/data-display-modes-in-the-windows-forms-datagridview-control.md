---
title: Režimy zobrazení dat v ovládacím prvku Windows Forms DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], display modes
- data grids [Windows Forms], display modes
- DataGridView control [Windows Forms], display modes
ms.assetid: 9755a030-3f3f-4705-a661-ba5a48a81875
ms.openlocfilehash: 673780909f6d66168548893e99d79bbfec70a0e0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079692"
---
# <a name="data-display-modes-in-the-windows-forms-datagridview-control"></a>Režimy zobrazení dat v ovládacím prvku Windows Forms DataGridView
<xref:System.Windows.Forms.DataGridView> Ovládací prvek mohl zobrazit data ve třech různých režimech: vázaný, odvázat a virtuální. Zvolte nejvhodnější režim na základě vašich požadavků.  
  
## <a name="unbound"></a>Nevázaný  
 Režim bez vazby je vhodný pro zobrazování poměrně malý objem dat, která můžete spravovat prostřednictvím kódu programu. Připojení není <xref:System.Windows.Forms.DataGridView> ovládacího prvku přímo ke zdroji dat stejně jako v režimu vázaná. Místo toho vám musí vložit ovládací prvek sami, obvykle pomocí <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> metody.  
  
 Režim bez vazby může být zvláště užitečná pro data statické a jen pro čtení, nebo když chcete poskytnout vlastní kód, který komunikuje s externím úložišti. Pokud chcete, aby vaši uživatelé povolenou interakci s externí zdroj dat, ale obvykle použijete vázané režimu.  
  
 Příklad, který se používá jen pro čtení nevázaných <xref:System.Windows.Forms.DataGridView>, naleznete v tématu [jak: Vytvoření ovládacího prvku DataGridView formuláře Windows nevázaného](how-to-create-an-unbound-windows-forms-datagridview-control.md).  
  
## <a name="bound"></a>vázaný  
 Vázané režim je vhodný pro správu dat s využitím automatického interakci s úložišti. Můžete připojit <xref:System.Windows.Forms.DataGridView> ovládacího prvku přímo ke zdroji dat tím, že nastavíte <xref:System.Windows.Forms.DataGridView.DataSource%2A> vlastnost. Když ovládací prvek je vázána na data, jsou řádky dat vloženo a dali bez nutnosti explicitního správy vaší. Když <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> vlastnost `true`, způsobí, že jednotlivé sloupce ve zdroji dat odpovídající sloupci má být vytvořen v ovládacím prvku. Pokud chcete vytvořit vlastní sloupce, můžete tuto vlastnost nastavíte `false` a použít <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A> vlastnost k vytvoření vazby každého sloupce, když ho konfigurujete. To je užitečné, pokud chcete použít typ sloupce než typy, které jsou generovány ve výchozím nastavení. Další informace najdete v tématu [typy sloupců v ovládacím prvku Windows Forms DataGridView](column-types-in-the-windows-forms-datagridview-control.md).  
  
 Příklad, který používá vazbu <xref:System.Windows.Forms.DataGridView> řídí, najdete v článku [názorný postup: Ověřování dat v Windows Forms DataGridView – ovládací prvek](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).  
  
 Můžete také přidat nevázaného sloupce, které chcete <xref:System.Windows.Forms.DataGridView> ovládací prvek v režimu vázaná. To je užitečné, pokud chcete zobrazit sloupec tlačítek nebo odkazů, které umožňují uživatelům provádět akce na konkrétní řádky. Je také užitečný k zobrazení sloupce mají hodnoty vypočítané ze svázané sloupce. Můžete naplnit mají vzít hodnoty buněk pro počítané sloupce v obslužné rutiny pro <xref:System.Windows.Forms.DataGridView.CellFormatting> událostí. Pokud používáte <xref:System.Data.DataSet> nebo <xref:System.Data.DataTable> jako zdroj dat, ale můžete chtít použít <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType> vlastnost místo toho vytvořit počítaný sloupec. V takovém případě <xref:System.Windows.Forms.DataGridView> ovládací prvek bude zacházet s stejně jako všechny ostatní sloupce ve zdroji dat počítaný sloupec.  
  
 Řazení podle nevázaných sloupců v vázaný režimu není podporováno. Pokud vytvoříte nepřipojeného sloupce v vázaný režimu, který obsahuje uživatele upravitelné hodnoty, je nutné implementovat virtuální režim zachování tyto hodnoty při ovládací prvek je seřazený podle vázaný sloupec.  
  
## <a name="virtual"></a>Virtual  
 Virtuální režim můžete implementovat vlastní operace správy data. To je nezbytné zachovat hodnoty nevázaných sloupců v režimu vázaný, když ovládací prvek je seřazený podle svázané sloupce. Primární použití virtuálním režimu, ale za účelem optimalizace výkonu při práci s velkými objemy dat je.  
  
 Připojíte <xref:System.Windows.Forms.DataGridView> ovládacího prvku do mezipaměti, která spravujete a ovládacích prvků kódu při řádky dat se doručí a načetli. Pokud chcete zachovat malé nároky na paměť, mezipaměť by měl vypadat přibližně velikost počet řádků, které jsou aktuálně zobrazeny. Uživatel posune stránku nových řádků do zobrazení, váš kód vyžaduje nová data z mezipaměti a volitelně vyprázdní stará data z paměti.  
  
 Když jsou implementace virtuálního režimu, je potřeba sledovat, kdy je nový řádek, je potřeba v datovém modelu a při přidání nového řádku vrácení zpět. Přesné implementaci této funkce závisí na implementaci datového modelu a sémantika transakce datového modelu; potvrzení obor Určuje, zda je na úrovni buněk nebo řádků.  
  
 Další informace o virtuálním režimu, najdete v části [virtuálního režimu v ovládacím prvku Windows Forms DataGridView](virtual-mode-in-the-windows-forms-datagridview-control.md). Příklad, který ukazuje, jak používat virtuální režim události, naleznete v tématu [názorný postup: Implementace virtuálního režimu v Windows Forms DataGridView – ovládací prvek](implementing-virtual-mode-wf-datagridview-control.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A?displayProperty=nameWithType>
- [Zobrazení dat v ovládacím prvku Windows Forms DataGridView](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Typy sloupců v ovládacím prvku Windows Forms DataGridView](column-types-in-the-windows-forms-datagridview-control.md)
- [Návod: Vytvoření nevázaného ovládacího prvku Windows Forms DataGridView](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)
- [Postupy: Vytvoření vazby dat k ovládacímu prvku Windows Forms DataGridView](how-to-bind-data-to-the-windows-forms-datagridview-control.md)
- [Virtuální režim v ovládacím prvku Windows Forms DataGridView](virtual-mode-in-the-windows-forms-datagridview-control.md)
- [Návod: Implementace virtuálního režimu v ovládacím prvku Windows Forms DataGridView](implementing-virtual-mode-wf-datagridview-control.md)
