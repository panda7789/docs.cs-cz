---
title: Scénáře ovládacího prvku DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], displaying in tabular format
- data grids [Windows Forms], about data grids
- DataGridView control [Windows Forms], scenarios
ms.assetid: 09a5fd05-3447-47ec-a4ec-6082a2b7f0dd
ms.openlocfilehash: 160d967c6445fb753cb6c73babfb02a734a07e28
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742471"
---
# <a name="datagridview-control-scenarios-windows-forms"></a>Scénáře ovládacího prvku DataGridView (Windows Forms)
Pomocí ovládacího prvku <xref:System.Windows.Forms.DataGridView> můžete zobrazit tabulková data z nejrůznějších zdrojů dat. Pro jednoduché použití můžete ručně naplnit <xref:System.Windows.Forms.DataGridView> a manipulovat s daty přímo prostřednictvím ovládacího prvku. Obvykle ale budete ukládat data do externího zdroje dat a navážete na ni ovládací prvek prostřednictvím komponenty <xref:System.Windows.Forms.BindingSource>.  
  
 Toto téma popisuje některé z běžných scénářů, které zahrnují ovládací prvek <xref:System.Windows.Forms.DataGridView>.  
  
## <a name="scenario-1-displaying-small-amounts-of-data"></a>Scénář 1: zobrazení malých objemů dat  
 Data nemusíte ukládat do externího zdroje dat, aby je bylo možné zobrazit v ovládacím prvku <xref:System.Windows.Forms.DataGridView>. Pokud pracujete s malým množstvím dat, můžete naplnit ovládací prvek sami a manipulovat s daty prostřednictvím ovládacího prvku. Tato metoda se nazývá *nevázaný režim*. Další informace naleznete v tématu [How to: Create a unbounded model Windows Forms DataGridView Control](how-to-create-an-unbound-windows-forms-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Klíčové body scénáře  
  
- V nevázaném režimu naplníte ovládací prvek ručně.  
  
- Nevázaný režim je zvláště vhodný pro malé objemy dat jen pro čtení.  
  
- Nevázaný režim je také vhodný pro tabulky, které jsou vyplněny tabulkou nebo zhuštěně.  
  
## <a name="scenario-2-viewing-and-updating-data-stored-in-an-external-data-source"></a>Scénář 2: zobrazení a aktualizace dat uložených v externím zdroji dat  
 Ovládací prvek <xref:System.Windows.Forms.DataGridView> můžete použít jako uživatelské rozhraní (UI), přes které uživatelé budou mít přístup k datům uchovávaným ve zdroji dat, jako je databázová tabulka nebo kolekce obchodních objektů. Další informace najdete v tématu [Postup: vytvoření vazby dat k ovládacímu prvku DataGridView model Windows Forms](how-to-bind-data-to-the-windows-forms-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Klíčové body scénáře  
  
- Vázaný režim umožňuje připojit se ke zdroji dat, automaticky generovat sloupce na základě vlastností zdroje dat nebo databázových sloupců a automaticky naplnit ovládací prvek.  
  
- Vázaný režim je vhodný pro náročné uživatelské interakce s daty. Data je možné formátovat pro zobrazení a uživatelsky zadaná data lze analyzovat ve formátu očekávaném zdrojem dat. Je možné zjistit chyby formátování datových záznamů a omezení databáze, aby uživatelé mohli být varováni a mohli opravit chybné buňky.  
  
- Další funkce, jako je řazení sloupců, zamrznutí a změna pořadí, umožňují uživatelům zobrazovat data způsobem vhodným pro jejich pracovní postup.  
  
- Podpora schránky umožňuje uživatelům kopírovat data z aplikace do jiných aplikací.  
  
## <a name="scenario-3-advanced-data"></a>Scénář 3: Rozšířená data  
 Pokud máte speciální požadavky, které model standardní datové vazby neřeší, můžete spravovat interakci mezi ovládacím prvkem a daty pomocí implementace *virtuálního režimu*. Implementace virtuálního režimu znamená implementaci jedné nebo více obslužných rutin událostí, které umožňují ovládacímu prvku požadovat informace o buňkách, když jsou potřebné informace.  
  
 Například pokud pracujete s velkými objemy dat, možná budete chtít implementovat virtuální režim, abyste zajistili optimální efektivitu. Virtuální režim je také užitečný pro zachování hodnot nevázaných sloupců, které se zobrazují spolu se sloupci získanými z jiného zdroje dat.  
  
 Další informace o virtuálním režimu naleznete v tématu [Návod: implementace virtuálního režimu v ovládacím prvku DataGridView model Windows Forms](implementing-virtual-mode-wf-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Klíčové body scénáře  
  
- Virtuální režim je vhodný pro zobrazování velmi velkých objemů dat, když potřebujete vyladit výkon.  
  
## <a name="scenario-4-automatically-resizing-rows-and-columns"></a>Scénář 4: automatické změny velikosti řádků a sloupců  
 Když zobrazujete data, která se pravidelně aktualizují, můžete automaticky měnit velikost řádků a sloupců, aby se zajistilo, že se zobrazí veškerý obsah. Ovládací prvek <xref:System.Windows.Forms.DataGridView> poskytuje několik možností, které vám umožní povolit nebo zakázat ruční změnu velikosti, změnit velikost programově v určitých časech nebo změnit velikost automaticky pokaždé, když se změní obsah. Další informace najdete v tématu [Možnosti změny velikosti v ovládacím prvku DataGridView model Windows Forms](sizing-options-in-the-windows-forms-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Klíčové body scénáře  
  
- Ruční změna velikosti umožňuje uživatelům upravit výšky a šířky buněk.  
  
- Automatická změna velikosti umožňuje zachovat velikost buněk, takže obsah buňky nebude nikdy oříznut.  
  
- Programová změna velikosti umožňuje změnit velikost buněk v určitých časech, aby nedocházelo ke snížení výkonu průběžné automatické změny velikosti.  
  
## <a name="scenario-5-simple-customization"></a>Scénář 5: jednoduché přizpůsobení  
 Ovládací prvek <xref:System.Windows.Forms.DataGridView> poskytuje mnoho způsobů, jak změnit základní vzhled a chování. Další informace naleznete v tématu [styly buněk v ovládacím prvku DataGridView model Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Klíčové body scénáře  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle> objekty umožňují poskytovat informace o barvách, písmu, formátování a umístění na více úrovních a pro jednotlivé prvky ovládacího prvku.  
  
- Styly buněk lze vrstvit a sdílet více prvky, takže můžete znovu použít kód.  
  
## <a name="scenario-6-advanced-customization"></a>Scénář 6: pokročilé přizpůsobení  
 Ovládací prvek <xref:System.Windows.Forms.DataGridView> poskytuje mnoho způsobů, jak přizpůsobit jeho vzhled a chování.  
  
### <a name="scenario-key-points"></a>Klíčové body scénáře  
  
- Můžete zadat vlastní kód pro malování na buňky. Další informace naleznete v tématu [How to: Customize a vzhled buněk v ovládacím prvku DataGridView model Windows Forms](customize-the-appearance-of-cells-in-the-datagrid.md).  
  
- Můžete zadat vlastní malování na řádek. To je užitečné, když například chcete vytvořit řádky s obsahem, který pokrývá více sloupců. Další informace naleznete v tématu [Postupy: přizpůsobení vzhledu řádků v ovládacím prvku DataGridView model Windows Forms](customize-the-appearance-of-rows-in-the-datagrid.md).  
  
- Můžete implementovat vlastní třídy buňky a sloupce pro přizpůsobení vzhledu buňky. Další informace najdete v tématu [Postup: přizpůsobení buněk a sloupců v ovládacím prvku DataGridView model Windows Forms rozšířením jejich chování a vzhledu](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md).  
  
- Můžete implementovat vlastní třídy buněk a sloupců pro jiné hostitelské ovládací prvky než ty, které jsou k dispozici v předdefinovaných typech sloupců. Další informace naleznete v tématu [How to: Host Controls in model Windows Forms DataGridView Cells](how-to-host-controls-in-windows-forms-datagridview-cells.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.DataGridView>
- [Přehled ovládacího prvku DataGridView](datagridview-control-overview-windows-forms.md)
