---
title: Virtuální režim v ovládacím prvku DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], virtual mode
ms.assetid: feae5d43-2848-4b1a-8ea7-77085dc415b5
ms.openlocfilehash: 0d82f0fc9946e5b61ea171f2f5d2ab5690db0c71
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745442"
---
# <a name="virtual-mode-in-the-windows-forms-datagridview-control"></a>Virtuální režim v ovládacím prvku Windows Forms DataGridView
Ve virtuálním režimu můžete spravovat interakci mezi ovládacími prvky <xref:System.Windows.Forms.DataGridView> a vlastní datovou mezipamětí. Chcete-li implementovat virtuální režim, nastavte vlastnost <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> na `true` a zpracujte jednu nebo více událostí popsaných v tomto tématu. Obvykle budete zpracovávat aspoň `CellValueNeeded` událost, která umožňuje ovládacímu prvku vyhledat hodnoty v mezipaměti dat.  
  
## <a name="bound-mode-and-virtual-mode"></a>Vázaný režim a virtuální režim  
 Virtuální režim je nutný jenom v případě, že je potřeba doplnit nebo nahradit vázaný režim. V vázaném režimu nastavíte vlastnost <xref:System.Windows.Forms.DataGridView.DataSource%2A> a ovládací prvek automaticky načte data ze zadaného zdroje a odešlete do něj změny uživatele. Můžete určit, které z vázaných sloupců se zobrazí, a samotný zdroj dat obvykle zpracovává operace, jako je například řazení.  
  
## <a name="supplementing-bound-mode"></a>Doplňování vázaného režimu  
 Můžete doplnit vázaný režim zobrazením nevázaných sloupců spolu s vázanými sloupci. To se někdy označuje jako "smíšený režim" a je užitečné pro zobrazení podobných hodnot nebo ovládacích prvků uživatelského rozhraní (UI).  
  
 Vzhledem k tomu, že nevázané sloupce jsou mimo zdroj dat, jsou ignorovány operacemi řazení zdroje dat. Proto pokud povolíte řazení ve smíšeném režimu, je nutné spravovat nevázaná data v místní mezipaměti a implementovat virtuální režim, aby mohl ovládací prvek <xref:System.Windows.Forms.DataGridView> pracovat s ním.  
  
 Další informace o použití virtuálního režimu k údržbě hodnot v nevázaných sloupcích naleznete v příkladech v tématech <xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A?displayProperty=nameWithType> vlastností a <xref:System.Windows.Forms.DataGridViewComboBoxColumn?displayProperty=nameWithType> třídy odkazu.  
  
## <a name="replacing-bound-mode"></a>Výměna vázaného režimu  
 Pokud vázaný režim nevyhovuje vašim požadavkům na výkon, můžete spravovat všechna vaše data ve vlastní mezipaměti prostřednictvím obslužných rutin událostí ve virtuálním režimu. Můžete například použít virtuální režim k implementaci mechanismu načítání dat za běhu, který načte jenom tolik dat z databáze v síti, který je nutný k zajištění optimálního výkonu. Tento scénář je zvláště užitečný, když pracujete s velkým objemem dat v případě pomalého síťového připojení nebo s klientskými počítači, které mají omezené množství paměti RAM nebo úložného prostoru.  
  
 Další informace o použití virtuálního režimu v rámci scénáře za běhu naleznete [v tématu Implementace virtuálního režimu s načítáním dat za běhu v ovládacím prvku DataGridView model Windows Forms](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md).  
  
## <a name="virtual-mode-events"></a>Události ve virtuálním režimu  
 Pokud jsou vaše data jen pro čtení, může být událost `CellValueNeeded` jedinou událostí, kterou budete muset zpracovat. Další události ve virtuálním režimu umožňují povolit konkrétní funkce, jako jsou uživatelské úpravy, přidávání a odstraňování řádků a transakce na úrovni řádků.  
  
 Některé standardní <xref:System.Windows.Forms.DataGridView> události (například události, ke kterým dochází, když uživatelé přidají nebo odstraňují řádky nebo když se upraví, analyzují, ověří nebo naformátují), jsou užitečné i ve virtuálním režimu. Můžete také zpracovávat události, které umožňují udržovat hodnoty, které nejsou obvykle uloženy ve vázaném zdroji dat, jako je text popisku buňky, text chyby buňky a řádku, data nabídky pro místní a řádek a data výšky řádku.  
  
 Další informace o implementaci virtuálního režimu pro správu dat pro čtení a zápis s rozsahem potvrzení na úrovni řádku naleznete v tématu [Návod: implementace virtuálního režimu v ovládacím prvku DataGridView model Windows Forms](implementing-virtual-mode-wf-datagridview-control.md).  
  
 Příklad, který implementuje virtuální režim s rozsahem potvrzení na úrovni buňky, najdete v tématu informace o vlastnosti <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>.  
  
 K následujícím událostem dojde pouze v případě, že je vlastnost <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> nastavena na hodnotu `true`.  
  
|Událost|Popis|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.DataGridView.CellValueNeeded>|Používá se ovládacím prvkem k načtení hodnoty buňky z datové mezipaměti pro zobrazení. Tato událost se vyskytuje pouze u buněk v nevázaných sloupcích.|  
|<xref:System.Windows.Forms.DataGridView.CellValuePushed>|Používá se v ovládacím prvku k potvrzení vstupu uživatele pro buňku do mezipaměti dat. Tato událost se vyskytuje pouze u buněk v nevázaných sloupcích.<br /><br /> Zavolejte metodu <xref:System.Windows.Forms.DataGridView.UpdateCellValue%2A> při změně hodnoty uložené v mezipaměti mimo obslužnou rutinu události <xref:System.Windows.Forms.DataGridView.CellValuePushed>, aby se zajistilo, že se aktuální hodnota zobrazuje v ovládacím prvku a aby se použily všechny režimy automatického přizpůsobení velikosti, které jsou aktuálně platné.|  
|<xref:System.Windows.Forms.DataGridView.NewRowNeeded>|Používá se ovládacím prvkem k označení potřeby nového řádku v mezipaměti dat.|  
|<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>|Používáno ovládacím prvkem k určení, zda řádek obsahuje nějaké nepotvrzené změny.|  
|<xref:System.Windows.Forms.DataGridView.CancelRowEdit>|Používá se ovládacím prvkem k označení toho, že by se měl řádek vrátit do hodnot uložených v mezipaměti.|  
  
 Ve virtuálním režimu jsou užitečné následující události, ale dají se použít bez ohledu na nastavení vlastnosti <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>.  
  
|Události|Popis|  
|------------|-----------------|  
|<xref:System.Windows.Forms.DataGridView.UserDeletingRow><br /><br /> <xref:System.Windows.Forms.DataGridView.UserDeletedRow><br /><br /> <xref:System.Windows.Forms.DataGridView.RowsRemoved><br /><br /> <xref:System.Windows.Forms.DataGridView.RowsAdded>|Používá se ovládacím prvkem k označení, kdy se mají odstranit nebo přidat řádky, a umožní vám aktualizovat datovou mezipaměť odpovídajícím způsobem.|  
|<xref:System.Windows.Forms.DataGridView.CellFormatting><br /><br /> <xref:System.Windows.Forms.DataGridView.CellParsing><br /><br /> <xref:System.Windows.Forms.DataGridView.CellValidating><br /><br /> <xref:System.Windows.Forms.DataGridView.CellValidated><br /><br /> <xref:System.Windows.Forms.DataGridView.RowValidating><br /><br /> <xref:System.Windows.Forms.DataGridView.RowValidated>|Používá se ovládacím prvkem k formátování hodnot buněk pro zobrazení a k analýze a ověření vstupu uživatele.|  
|<xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded>|Používá se ovládacím prvkem k načtení textu popisku buňky, když je nastavená vlastnost <xref:System.Windows.Forms.DataGridView.DataSource%2A> nebo vlastnost <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> `true`.<br /><br /> Popisky buněk jsou zobrazeny pouze v případě, že je hodnota vlastnosti <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> `true`.|  
|<xref:System.Windows.Forms.DataGridView.CellErrorTextNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowErrorTextNeeded>|Používá se ovládacím prvkem k načtení textu chyby buňky nebo řádku, pokud je nastavena vlastnost <xref:System.Windows.Forms.DataGridView.DataSource%2A> nebo vlastnost <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> `true`.<br /><br /> Když změníte text chyby buňky nebo řádku, zavolejte metodu <xref:System.Windows.Forms.DataGridView.UpdateCellErrorText%2A> nebo metodu <xref:System.Windows.Forms.DataGridView.UpdateRowErrorText%2A>, aby se zajistilo, že se v ovládacím prvku zobrazí aktuální hodnota.<br /><br /> Glyfy chyb buňky a řádku se zobrazí, když jsou `true`hodnoty vlastností <xref:System.Windows.Forms.DataGridView.ShowCellErrors%2A> a <xref:System.Windows.Forms.DataGridView.ShowRowErrors%2A>.|  
|<xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowContextMenuStripNeeded>|Používá se ovládacím prvkem k načtení buňky nebo řádku <xref:System.Windows.Forms.ContextMenuStrip>, když je nastavena vlastnost <xref:System.Windows.Forms.DataGridView.DataSource%2A> ovládacího prvku nebo vlastnost <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> `true`.|  
|<xref:System.Windows.Forms.DataGridView.RowHeightInfoNeeded><br /><br /> <xref:System.Windows.Forms.DataGridView.RowHeightInfoPushed>|Používá se ovládacím prvkem k načtení nebo uložení informací o výšce řádku v mezipaměti dat. Zavolejte metodu <xref:System.Windows.Forms.DataGridView.UpdateRowHeightInfo%2A> při změně informací o výšce řádku v mezipaměti mimo obslužnou rutinu události <xref:System.Windows.Forms.DataGridView.RowHeightInfoPushed>, aby se zajistilo, že se aktuální hodnota používá při zobrazení ovládacího prvku.|  
  
## <a name="best-practices-in-virtual-mode"></a>Osvědčené postupy ve virtuálním režimu  
 Pokud implementujete virtuální režim, aby bylo možné efektivně pracovat s velkým objemem dat, budete mít také jistotu, že budete efektivně pracovat s <xref:System.Windows.Forms.DataGridView> sám. Další informace o efektivním použití stylů buněk, automatické velikosti, výběrech a sdílení řádků naleznete v tématu [osvědčené postupy pro škálování ovládacího prvku model Windows Forms DataGridView](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- [Ladění výkonu v ovládacím prvku Windows Forms DataGridView](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [Doporučené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [Návod: Implementace virtuálního režimu v ovládacím prvku Windows Forms DataGridView](implementing-virtual-mode-wf-datagridview-control.md)
- [Implementace virtuálního režimu s načítáním dat za běhu v ovládacím prvku Windows Forms DataGridView](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)
