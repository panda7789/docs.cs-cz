---
title: Použití řádku pro nové záznamy v ovládacím prvku Windows Forms DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], adding rows for new records
- rows [Windows Forms], new records
- DataGridView control [Windows Forms], data entry
ms.assetid: 6110f1ea-9794-442c-a98a-f104a1feeaf4
ms.openlocfilehash: 86e61afd0882fea9015cdfe3b40e6d3cd329391b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54734954"
---
# <a name="using-the-row-for-new-records-in-the-windows-forms-datagridview-control"></a>Použití řádku pro nové záznamy v ovládacím prvku Windows Forms DataGridView
Při použití <xref:System.Windows.Forms.DataGridView> pro úpravy dat v aplikaci, bude často chcete dát uživatelům možnost přidávat nové řádky dat do úložiště. <xref:System.Windows.Forms.DataGridView> Ovládací prvek podporuje tuto funkci poskytnutím řádek pro nové záznamy, které je vždy zobrazen jako poslední řádek. Je označené atributem symbol hvězdičky (*) v záhlaví řádku. Následující části popisují některé z akcí, byste měli zvážit, když program s řádkem pro nové záznamy povoleno.  
  
## <a name="displaying-the-row-for-new-records"></a>Zobrazení řádku pro nové záznamy  
 Použití <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> vlastnost umožňující označit, zda se zobrazí řádek pro nové záznamy. Výchozí hodnota této vlastnosti je `true`.  
  
 Pro data vázat případu, zobrazí se řádek pro nové záznamy Pokud <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> vlastnost ovládacího prvku a <xref:System.ComponentModel.IBindingList.AllowNew%2A?displayProperty=nameWithType> vlastnost zdroje dat jsou obě `true`. Pokud platí některá `false` pak řádku se nezobrazí.  
  
## <a name="populating-the-row-for-new-records-with-default-data"></a>Naplnění řádku pro nové záznamy s výchozími daty  
 Když uživatel vybere řádek pro nové záznamy jako aktuální řádek <xref:System.Windows.Forms.DataGridView> vyvolá ovládací prvek <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> událostí.  
  
 Tato událost poskytuje přístup k novému <xref:System.Windows.Forms.DataGridViewRow> a umožňuje naplnit nový řádek s výchozími daty. Další informace najdete v tématu [jak: Určení výchozích hodnot pro nové řádky v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/specify-default-values-for-new-rows-in-the-datagrid.md)  
  
## <a name="the-rows-collection"></a>Kolekce řádků  
 Je součástí řádku pro nové záznamy <xref:System.Windows.Forms.DataGridView> ovládacího prvku <xref:System.Windows.Forms.DataGridView.Rows%2A> kolekce ale chová odlišně ve dvou směrech:  
  
-   Nelze odebrat řádek pro nové záznamy <xref:System.Windows.Forms.DataGridView.Rows%2A> kolekce prostřednictvím kódu programu. <xref:System.InvalidOperationException> Je vyvolána, pokud to dojde k pokusu o. Uživatel také nelze odstranit řádek pro nové záznamy. <xref:System.Windows.Forms.DataGridViewRowCollection.Clear%2A?displayProperty=nameWithType> Metoda neodebere tento řádek z <xref:System.Windows.Forms.DataGridView.Rows%2A> kolekce.  
  
-   Je možné přidat žádný řádek po řádku pro nové záznamy. <xref:System.InvalidOperationException> Dojde při pokusu o to. V důsledku toho řádku pro nové záznamy se vždycky poslední řádek v <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Metody <xref:System.Windows.Forms.DataGridViewRowCollection> přidá řádků –<xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopy%2A>, a <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopies%2A>– všechny interně volání metod vložení při řádku pro nové záznamy je k dispozici.  
  
## <a name="visual-customization-of-the-row-for-new-records"></a>Vizuální přizpůsobení řádku pro nové záznamy  
 Při vytvoření řádku pro nové záznamy, je založena na určeném řádku <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> vlastnost. Všechny styly buňky, které nejsou zadané pro tento řádek se dědí z dalších vlastností. Další informace o dědičnosti styl buňky, naleznete v tématu [styly buňky v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).  
  
 Počáteční hodnoty pro nové záznamy se načítají z každé buňce zobrazí buňkami v řádku <xref:System.Windows.Forms.DataGridViewCell.DefaultNewRowValue%2A> vlastnost. Pro buňky ovládacího prvku typu <xref:System.Windows.Forms.DataGridViewImageCell>, vrátí tato vlastnost zástupné obrázky. V opačném případě vrátí tato vlastnost `null`. Tato vlastnost se vraťte na vlastní hodnotu lze přepsat. Ale tyto počáteční hodnoty mohou být nahrazeny <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> obslužné rutiny události při fokusu zadá řádek pro nové záznamy.  
  
 Standardní ikony pro tento řádek záhlaví, které se šipkou nebo hvězdičku, nejsou zveřejněné veřejně. Pokud chcete přizpůsobit ikony, budete muset vytvořit vlastní <xref:System.Windows.Forms.DataGridViewRowHeaderCell> třídy.  
  
 Použití standardních ikon <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> vlastnost <xref:System.Windows.Forms.DataGridViewCellStyle> používá buňky záhlaví řádku. Standardní ikony nevykreslují, pokud není k dispozici dostatek místa pro úplné zobrazení.  
  
 Pokud buňky záhlaví řádku má řetězec hodnotu nastavení a pokud není k dispozici dostatek volného místa pro text a ikona, je nejprve vyřadit, na ikonu.  
  
## <a name="sorting"></a>Řazení  
 V režim bez vazby, se nové záznamy vždy přidána na konec objektu <xref:System.Windows.Forms.DataGridView> i v případě, že uživatel má Seřadit obsah <xref:System.Windows.Forms.DataGridView>. Uživatel bude muset nevztahují řazení znovu řadit řádek do správného umístění; Toto chování je podobné <xref:System.Windows.Forms.ListView> ovládacího prvku.  
  
 V datech budou provázaná a virtuální režimů vložení chování při použití řazení závislé na implementaci datového modelu. Pro [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)], řádek jsou okamžitě rozděleny na správné pozice.  
  
## <a name="other-notes-on-the-row-for-new-records"></a>Další poznámky na řádku pro nové záznamy  
 Nelze nastavit <xref:System.Windows.Forms.DataGridViewRow.Visible%2A> vlastnosti tohoto řádku na `false`. <xref:System.InvalidOperationException> Dojde při pokusu o to.  
  
 Řádek pro nové záznamy se vždy vytvoří v nevybraném stavu.  
  
## <a name="virtual-mode"></a>Virtuální režim  
 Pokud jsou implementace virtuálního režimu, je potřeba sledovat, kdy je potřeba řádek pro nové záznamy v datovém modelu a kdy se mají vrátit zpět přidání řádku. Přesné implementaci této funkce závisí na implementaci datového modelu a jeho transakce sémantiku, například, zda je obor potvrzení změn na úrovni buněk nebo řádků. Další informace najdete v tématu [virtuálního režimu v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>
- [Zadávání dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)
- [Postupy: Určení výchozích hodnot pro nové řádky v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/specify-default-values-for-new-rows-in-the-datagrid.md)
