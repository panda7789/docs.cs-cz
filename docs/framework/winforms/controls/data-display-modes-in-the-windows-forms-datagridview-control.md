---
title: Režimy zobrazení dat v ovládacím prvku DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], display modes
- data grids [Windows Forms], display modes
- DataGridView control [Windows Forms], display modes
ms.assetid: 9755a030-3f3f-4705-a661-ba5a48a81875
ms.openlocfilehash: ad6be647e3a36904b055fd6771f539df28938fab
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744018"
---
# <a name="data-display-modes-in-the-windows-forms-datagridview-control"></a>Režimy zobrazení dat v ovládacím prvku Windows Forms DataGridView
Ovládací prvek <xref:System.Windows.Forms.DataGridView> může zobrazit data ve třech různých režimech: Bound, Unbounded a Virtual. Podle svých požadavků vyberte nejvhodnější režim.  
  
## <a name="unbound"></a>Nevázaný  
 Nevázaný režim je vhodný pro zobrazení relativně malých objemů dat, která spravujete prostřednictvím kódu programu. Nepřipojujte ovládací prvek <xref:System.Windows.Forms.DataGridView> přímo ke zdroji dat, jako v přivázaném režimu. Místo toho je nutné ovládací prvek naplnit sami, obvykle pomocí metody <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType>.  
  
 Nevázaný režim může být zvláště užitečný pro statická data, která jsou jen pro čtení, nebo když chcete poskytnout vlastní kód, který komunikuje s externím úložištěm dat. Pokud chcete, aby uživatelé mohli pracovat s externím zdrojem dat, budete obvykle používat vázaný režim.  
  
 Příklad, který používá nevázaný <xref:System.Windows.Forms.DataGridView>jen pro čtení, naleznete v tématu [How to: Create a unbounded model Windows Forms DataGridView Control](how-to-create-an-unbound-windows-forms-datagridview-control.md).  
  
## <a name="bound"></a>Bound  
 Vázaný režim je vhodný pro správu dat pomocí automatické interakce s úložištěm dat. Ovládací prvek <xref:System.Windows.Forms.DataGridView> lze připojit přímo ke zdroji dat nastavením vlastnosti <xref:System.Windows.Forms.DataGridView.DataSource%2A>. Když je ovládací prvek vázaný na data, jsou řádky dat vloženy a vyžádány bez nutnosti explicitní správy na vaší straně. Pokud je vlastnost <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> `true`, každý sloupec ve zdroji dat způsobí, že v ovládacím prvku bude vytvořen odpovídající sloupec. Pokud dáváte přednost vytváření vlastních sloupců, můžete tuto vlastnost nastavit na `false` a použít vlastnost <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A> k navázání každého sloupce při jeho konfiguraci. To je užitečné, pokud chcete použít jiný typ sloupce než typy, které jsou generovány ve výchozím nastavení. Další informace naleznete v tématu [typy sloupců v ovládacím prvku DataGridView model Windows Forms](column-types-in-the-windows-forms-datagridview-control.md).  
  
 Příklad, který používá ovládací prvek vázané <xref:System.Windows.Forms.DataGridView>, naleznete v tématu [Návod: ověřování dat v ovládacím prvku DataGridView model Windows Forms](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).  
  
 Do ovládacího prvku <xref:System.Windows.Forms.DataGridView> v přivázaném režimu můžete také přidat nevázané sloupce. To je užitečné, když chcete zobrazit sloupec tlačítek nebo odkazů, které uživatelům umožňují provádět akce na určitých řádcích. Je také užitečné zobrazit sloupce s hodnotami vypočítanými z vázaných sloupců. Hodnoty buněk pro počítané sloupce lze naplnit v obslužné rutině pro událost <xref:System.Windows.Forms.DataGridView.CellFormatting>. Pokud však jako zdroj dat používáte <xref:System.Data.DataSet> nebo <xref:System.Data.DataTable>, můžete místo toho použít vlastnost <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType> k vytvoření počítaného sloupce. V tomto případě bude ovládací prvek <xref:System.Windows.Forms.DataGridView> zacházet s počítaným sloupcem stejně jako s jakýmkoli jiným sloupcem ve zdroji dat.  
  
 Řazení podle nevázaných sloupců v vázaného režimu není podporováno. Vytvoříte-li nevázaný sloupec v vázaného režimu, který obsahuje hodnoty umožňující úpravy uživatelem, je nutné implementovat virtuální režim, aby byly tyto hodnoty uchovávány, když je ovládací prvek seřazen podle vázaného sloupce.  
  
## <a name="virtual"></a>VM  
 Ve virtuálním režimu můžete implementovat své vlastní operace správy dat. To je nezbytné pro zachování hodnot nevázaných sloupců v režimu vázaného v případě, že je ovládací prvek seřazen podle vázaných sloupců. Primárním použitím virtuálního režimu ale je optimalizace výkonu při interakci s velkým objemem dat.  
  
 Ovládací prvek <xref:System.Windows.Forms.DataGridView> přiřadíte do mezipaměti, kterou spravujete, a váš kód řídí, kdy jsou řádky dat vloženy a vyžádány. Aby velikost paměti byla malá, měla by velikost mezipaměti vypadat přibližně podle počtu aktuálně zobrazených řádků. Když uživatel posune nové řádky do zobrazení, váš kód si vyžádá nová data z mezipaměti a volitelně vyprázdní stará data z paměti.  
  
 Při implementaci virtuálního režimu budete muset sledovat, kdy je v datovém modelu potřeba nový řádek a kdy se má vrátit přidání nového řádku. Přesná implementace této funkce bude záviset na implementaci datového modelu a sémantikě transakce datového modelu. zda je rozsah potvrzení na úrovni buňky nebo řádku.  
  
 Další informace o virtuálním režimu najdete v tématu [virtuální režim v ovládacím prvku DataGridView model Windows Forms](virtual-mode-in-the-windows-forms-datagridview-control.md). Příklad, který ukazuje, jak použít události virtuálního režimu, naleznete v tématu [Návod: implementace virtuálního režimu v ovládacím prvku DataGridView model Windows Forms](implementing-virtual-mode-wf-datagridview-control.md).  
  
## <a name="see-also"></a>Viz také

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
