---
title: Použití řádku pro nové záznamy v ovládacím prvku Windows Forms DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], adding rows for new records
- rows [Windows Forms], new records
- DataGridView control [Windows Forms], data entry
ms.assetid: 6110f1ea-9794-442c-a98a-f104a1feeaf4
ms.openlocfilehash: abf62cc9165d74f6bf183e3df30d9a768c0c537f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33540656"
---
# <a name="using-the-row-for-new-records-in-the-windows-forms-datagridview-control"></a>Použití řádku pro nové záznamy v ovládacím prvku Windows Forms DataGridView
Při použití <xref:System.Windows.Forms.DataGridView> pro úpravy dat v aplikaci, bude často chcete umožnit uživatelům možnost přidávat nové řádky dat do úložiště dat. <xref:System.Windows.Forms.DataGridView> Řízení podporuje tato funkce tím, že poskytuje řádek pro nové záznamy, které se vždy zobrazí jako poslední řádek. Je označený s symbol hvězdičky (*) v řádku záhlaví. Následující části popisují některé z věcí, měli byste zvážit, když program s řádkem pro nové záznamy povoleno.  
  
## <a name="displaying-the-row-for-new-records"></a>Zobrazení řádek pro nové záznamy  
 Použití <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> vlastnost označující, zda se zobrazí řádek pro nové záznamy. Výchozí hodnota této vlastnosti je `true`.  
  
 Pro data vázaná případ řádek pro nové záznamy se zobrazí-li <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> vlastností ovládacího prvku a <xref:System.ComponentModel.IBindingList.AllowNew%2A?displayProperty=nameWithType> vlastnosti zdroje dat jsou obě `true`. Pokud některá `false` pak řádek se nezobrazí.  
  
## <a name="populating-the-row-for-new-records-with-default-data"></a>Naplnění řádek pro nové záznamy s výchozími daty  
 Když uživatel vybere řádek pro nové záznamy jako aktuální řádek <xref:System.Windows.Forms.DataGridView> vyvolá ovládací prvek <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> událostí.  
  
 Tato událost poskytuje přístup k novému <xref:System.Windows.Forms.DataGridViewRow> a umožňuje naplnit nový řádek s výchozími daty. Další informace najdete v tématu [postup: Zadejte výchozí hodnoty pro nové řádky v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/specify-default-values-for-new-rows-in-the-datagrid.md)  
  
## <a name="the-rows-collection"></a>Kolekce řádků  
 Je součástí řádek pro nové záznamy <xref:System.Windows.Forms.DataGridView> ovládacího prvku <xref:System.Windows.Forms.DataGridView.Rows%2A> kolekce ale odlišné chování dvě ohledech:  
  
-   Řádek pro nové záznamy nelze odebrat z <xref:System.Windows.Forms.DataGridView.Rows%2A> kolekce prostřednictvím kódu programu. <xref:System.InvalidOperationException> Je vyvolána, pokud je tento pokus. Uživatel také nelze odstranit řádek pro nové záznamy. <xref:System.Windows.Forms.DataGridViewRowCollection.Clear%2A?displayProperty=nameWithType> Metoda neodebere tento řádek z <xref:System.Windows.Forms.DataGridView.Rows%2A> kolekce.  
  
-   Mohou být přidány žádný řádek po řádku pro nové záznamy. <xref:System.InvalidOperationException> Se vyvolá, pokud je tento pokus. V důsledku toho je řádek pro nové záznamy vždy poslední řádek v <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Metody pro <xref:System.Windows.Forms.DataGridViewRowCollection> přidá řádků –<xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A>, <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopy%2A>, a <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopies%2A>– všechny interně volat metody vložení při řádek pro nové záznamy se nachází.  
  
## <a name="visual-customization-of-the-row-for-new-records"></a>Visual přizpůsobení řádků pro nové záznamy  
 Když je vytvořen řádek pro nové záznamy, je založená na řádek určeného <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> vlastnost. Všechny styly buňky, které nejsou určené pro tento řádek dědí od dalších vlastností. Další informace o dědičnosti styl buněk najdete v tématu [styly buňky v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).  
  
 Počáteční hodnoty zobrazuje buňky v řádku pro nové záznamy se načítají z jednotlivých buněk <xref:System.Windows.Forms.DataGridViewCell.DefaultNewRowValue%2A> vlastnost. Pro buněk typu <xref:System.Windows.Forms.DataGridViewImageCell>, tato vlastnost vrací bitovou kopii zástupný symbol. Jinak, vrátí tato vlastnost `null`. Vrátí vlastní hodnotu této vlastnosti můžete přepsat. Ale tyto počáteční hodnoty lze nahradit <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> obslužné rutiny události při fokus zadá řádek pro nové záznamy.  
  
 Standardní ikony pro tento řádek záhlaví, které se šipka nebo hvězdičku, nejsou veřejně přístupné. Pokud chcete přizpůsobit ikony, budete muset vytvořit vlastní <xref:System.Windows.Forms.DataGridViewRowHeaderCell> třídy.  
  
 Použijte standardní ikony <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> vlastnost <xref:System.Windows.Forms.DataGridViewCellStyle> používán řádek záhlaví buňky. Standardní ikony se nevykreslí, pokud není k dispozici dostatek místa pro úplné zobrazení.  
  
 Pokud řádek záhlaví buňky má řetězec hodnotu nastavit, a pokud není k dispozici dostatek místa pro text a ikona, je nejprve vyřadit ikonu.  
  
## <a name="sorting"></a>Řazení  
 V režimu nevázaný nové záznamy vždy přidá na konec <xref:System.Windows.Forms.DataGridView> i v případě, že uživatel má Seřadit obsah <xref:System.Windows.Forms.DataGridView>. Uživatel bude muset znovu použít řazení Chcete-li řadit řádek do správné polohy; Toto chování je podobné jako <xref:System.Windows.Forms.ListView> ovládacího prvku.  
  
 V datech bude vázané a virtuální režimů vložení chování při použití řazení závisí na implementaci datového modelu. Pro [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)], řádek je okamžitě rozděleny na správném místě.  
  
## <a name="other-notes-on-the-row-for-new-records"></a>Další poznámky na řádek pro nové záznamy  
 Nelze nastavit <xref:System.Windows.Forms.DataGridViewRow.Visible%2A> vlastnost pro tento řádek `false`. <xref:System.InvalidOperationException> Se vyvolá, pokud je tento pokus.  
  
 Řádek pro nové záznamy se vždy vytvoří ve stavu nezaškrtnuté.  
  
## <a name="virtual-mode"></a>Virtuální režim  
 Pokud jsou implementace virtuálního režimu, musíte sledovat, kdy je potřeba řádek pro nové záznamy v datovém modelu a kdy se mají vrátit přidání řádku. Přesný implementace tato funkce závisí na provádění datový model a jeho transakce sémantikou, například zda potvrzení obor je na úrovni buněk nebo řádek. Další informace najdete v tématu [virtuálního režimu v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>  
 [Zadávání dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 [Postupy: Určení výchozích hodnot pro nové řádky v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/specify-default-values-for-new-rows-in-the-datagrid.md)
