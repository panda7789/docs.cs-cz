---
title: Použití řádku pro nové záznamy v ovládacím prvku DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], adding rows for new records
- rows [Windows Forms], new records
- DataGridView control [Windows Forms], data entry
ms.assetid: 6110f1ea-9794-442c-a98a-f104a1feeaf4
ms.openlocfilehash: 2fcd35f8c4d04909cdbc26f6a4293fdd570385b8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728336"
---
# <a name="using-the-row-for-new-records-in-the-windows-forms-datagridview-control"></a>Použití řádku pro nové záznamy v ovládacím prvku Windows Forms DataGridView
Když použijete <xref:System.Windows.Forms.DataGridView> pro úpravu dat v aplikaci, často budete chtít uživatelům poskytnout možnost přidávat do úložiště dat nové řádky dat. Ovládací prvek <xref:System.Windows.Forms.DataGridView> tuto funkci podporuje tím, že poskytuje řádek pro nové záznamy, které se vždycky zobrazují jako poslední řádek. Je označený symbolem hvězdičky (*) v záhlaví řádku. Následující části popisují některé z věcí, které byste měli vzít v úvahu při programovém řádku pro nové záznamy, které jsou povolené.  
  
## <a name="displaying-the-row-for-new-records"></a>Zobrazení řádku pro nové záznamy  
 Vlastnost <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> použijte k označení, zda se zobrazí řádek pro nové záznamy. Výchozí hodnota této vlastnosti je `true`.  
  
 V případě, že dojde k tomu, že se vlastnost <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> ovládacího prvku a vlastnost <xref:System.ComponentModel.IBindingList.AllowNew%2A?displayProperty=nameWithType> zdroje dat `true`, zobrazí se řádek pro nové záznamy. Pokud je některá z `false`, řádek nebude zobrazen.  
  
## <a name="populating-the-row-for-new-records-with-default-data"></a>Naplnění řádku pro nové záznamy s výchozími daty  
 Když uživatel vybere řádek pro nové záznamy jako aktuální řádek, ovládací prvek <xref:System.Windows.Forms.DataGridView> vyvolá událost <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded>.  
  
 Tato událost poskytuje přístup k novým <xref:System.Windows.Forms.DataGridViewRow> a umožňuje naplnit nový řádek výchozími daty. Další informace naleznete v tématu [How to: určení výchozích hodnot pro nové řádky v ovládacím prvku DataGridView model Windows Forms.](specify-default-values-for-new-rows-in-the-datagrid.md)  
  
## <a name="the-rows-collection"></a>Kolekce řádků  
 Řádek pro nové záznamy je obsažen v kolekci <xref:System.Windows.Forms.DataGridView.Rows%2A> ovládacího prvku <xref:System.Windows.Forms.DataGridView>, ale chová se odlišně ve dvou ohledech:  
  
- Řádek pro nové záznamy nelze z kolekce <xref:System.Windows.Forms.DataGridView.Rows%2A> programově odebrat. Je-li proveden pokus, je vyvolána <xref:System.InvalidOperationException>. Uživatel také nemůže odstranit řádek pro nové záznamy. Metoda <xref:System.Windows.Forms.DataGridViewRowCollection.Clear%2A?displayProperty=nameWithType> neodebere tento řádek z kolekce <xref:System.Windows.Forms.DataGridView.Rows%2A>.  
  
- Po řádku pro nové záznamy nelze přidat žádný řádek. V případě, že se to pokusí, je vyvolána <xref:System.InvalidOperationException>. V důsledku toho je řádek pro nové záznamy vždy posledním řádkem v ovládacím prvku <xref:System.Windows.Forms.DataGridView>. Metody pro <xref:System.Windows.Forms.DataGridViewRowCollection>, které přidávají řádky –<xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopy%2A>a <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopies%2A>– všechny metody vkládání volání interně, pokud je k dispozici řádek pro nové záznamy.  
  
## <a name="visual-customization-of-the-row-for-new-records"></a>Vizuální přizpůsobení řádku pro nové záznamy  
 Když je vytvořen řádek pro nové záznamy, je založen na řádku určeném vlastností <xref:System.Windows.Forms.DataGridView.RowTemplate%2A>. Žádné styly buněk, které nejsou zadány pro tento řádek, jsou zděděny z jiných vlastností. Další informace o dědičnosti stylu buňky naleznete v tématu [styly buněk v ovládacím prvku DataGridView model Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).  
  
 Počáteční hodnoty zobrazené buňkami v řádku pro nové záznamy se načítají z vlastnosti <xref:System.Windows.Forms.DataGridViewCell.DefaultNewRowValue%2A> každé buňky. Pro buňky typu <xref:System.Windows.Forms.DataGridViewImageCell>Tato vlastnost vrátí zástupný obrázek. V opačném případě vrátí tato vlastnost `null`. Tuto vlastnost můžete přepsat tak, aby vracela vlastní hodnotu. Tyto počáteční hodnoty však mohou být nahrazeny <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> obslužnou rutinou události, když se fokus zadá do řádku pro nové záznamy.  
  
 Standardní ikony pro záhlaví tohoto řádku, což jsou šipky nebo hvězdička, nejsou veřejně vystaveny. Pokud chcete ikony přizpůsobit, bude nutné vytvořit vlastní třídu <xref:System.Windows.Forms.DataGridViewRowHeaderCell>.  
  
 Standardní ikony používají vlastnost <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> <xref:System.Windows.Forms.DataGridViewCellStyle> používané v buňce záhlaví řádku. Pokud není dostatek místa k úplnému zobrazení, standardní ikony se nevykreslují.  
  
 Pokud má buňka záhlaví řádku nastavenou hodnotu řetězce a pokud není dostatek místa pro text i ikonu, ikona se vynechá jako první.  
  
## <a name="sorting"></a>Řazení  
 V nevázaném režimu budou nové záznamy vždy přidány na konec <xref:System.Windows.Forms.DataGridView> i v případě, že uživatel seřadil obsah <xref:System.Windows.Forms.DataGridView>. Uživatel bude muset znovu použít řazení, aby bylo možné řádek seřadit do správné pozice. Toto chování je podobné ovládacímu prvku <xref:System.Windows.Forms.ListView>.  
  
 V režimech vázaných a virtuálních dat se chování vložení při použití řazení bude závislé na implementaci datového modelu. V případě ADO.NET je řádek okamžitě řazen do správné pozice.  
  
## <a name="other-notes-on-the-row-for-new-records"></a>Další poznámky na řádku pro nové záznamy  
 Vlastnost <xref:System.Windows.Forms.DataGridViewRow.Visible%2A> tohoto řádku nelze nastavit na hodnotu `false`. V případě, že se to pokusí, je vyvolána <xref:System.InvalidOperationException>.  
  
 Řádek pro nové záznamy je vždy vytvořen v nevybraném stavu.  
  
## <a name="virtual-mode"></a>Virtuální režim  
 Pokud implementujete virtuální režim, budete muset sledovat, kdy je v datovém modelu potřeba řádek pro nové záznamy a kdy se má vrátit zpět přidání řádku. Přesná implementace této funkce závisí na implementaci datového modelu a jeho sémantikě transakce, například zda je rozsah potvrzení na úrovni buňky nebo řádku. Další informace naleznete v tématu [virtuální režim v ovládacím prvku DataGridView model Windows Forms](virtual-mode-in-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>
- [Zadávání dat v ovládacím prvku Windows Forms DataGridView](data-entry-in-the-windows-forms-datagridview-control.md)
- [Postupy: Určení výchozích hodnot pro nové řádky v ovládacím prvku Windows Forms DataGridView](specify-default-values-for-new-rows-in-the-datagrid.md)
