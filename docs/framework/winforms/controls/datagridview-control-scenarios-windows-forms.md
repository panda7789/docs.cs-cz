---
title: "Scénáře ovládacího prvku DataGridView (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [Windows Forms], displaying in tabular format
- data grids [Windows Forms], about data grids
- DataGridView control [Windows Forms], scenarios
ms.assetid: 09a5fd05-3447-47ec-a4ec-6082a2b7f0dd
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 38e5337f775d98f8729c62b3481c3e839bff2252
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="datagridview-control-scenarios-windows-forms"></a>Scénáře ovládacího prvku DataGridView (Windows Forms)
S <xref:System.Windows.Forms.DataGridView> řízení, můžete zobrazit tabulková data z různých datových zdrojů. Pro jednoduché používá, můžete ručně naplnění <xref:System.Windows.Forms.DataGridView> a manipulovat s daty přímo prostřednictvím ovládacího prvku. Obvykle se však budete ukládat data do externího zdroje dat a vytvořit vazbu ovládacího prvku na přes <xref:System.Windows.Forms.BindingSource> součásti.  
  
 Toto téma popisuje některé běžné scénáře, které zahrnují <xref:System.Windows.Forms.DataGridView> ovládacího prvku.  
  
## <a name="scenario-1-displaying-small-amounts-of-data"></a>Scénář 1: Zobrazení malé množství dat  
 Není nutné ukládat data do externího zdroje dat pro zobrazení v <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Pokud pracujete s malé množství dat, můžete naplnit ovládací prvek sami a pracovat s daty pomocí ovládacího prvku. To se označuje jako *nevázaný režimu*. Další informace najdete v tématu [postupy: vytvoření nevázaný ovládací prvek Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Klíčové body scénáře  
  
-   V nevázaný režimu můžete naplnit ovládací prvek ručně.  
  
-   Nevázaný režim je obzvláště vhodný pro malé množství dat jen pro čtení.  
  
-   Nevázaný režimu je také vhodné pro tabulkovém nebo řídce vyplněná tabulek.  
  
## <a name="scenario-2-viewing-and-updating-data-stored-in-an-external-data-source"></a>Scénář 2: Zobrazení a aktualizace dat uložených v externího zdroje dat  
 Můžete použít <xref:System.Windows.Forms.DataGridView> řízení jako uživatelské rozhraní (UI), přes které uživatelé přístup k datům zachovány ve zdroji dat, například databázové tabulky nebo kolekce objektů firmy. Další informace najdete v tématu [postupy: vytvoření vazby dat ovládacího prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Klíčové body scénáře  
  
-   Vázané režim umožňuje připojení ke zdroji dat, automatické generování sloupců na základě vlastnosti zdroje dat nebo sloupců databáze a automaticky naplnit ovládací prvek.  
  
-   Vázané režimu je vhodné pro interakci s velkou uživatelem s daty. Data mohou být formátována pro zobrazení a zadat uživatele data můžete analyzovat do formátu očekávaném zdroj dat. Vkládání dat formátování chyby a omezení chyby databáze lze zjistit tak, aby uživatele může být upozorněn a může být vyřešen chybné buněk.  
  
-   Další funkce jako je například řazení sloupců či zmrazení a změna povolit uživatelům zobrazení dat způsobem nejvhodnější pro jejich pracovní postup.  
  
-   Podpora schránky umožňuje uživatelům kopírovat data z vaší aplikace do jiných aplikací.  
  
## <a name="scenario-3-advanced-data"></a>Scénář 3: Pokročilé dat  
 Pokud máte speciální požadavky standardní datový model vazby neřeší, můžete spravovat interakce mezi ovládacího prvku a vašich dat tím, že implementujete *virtuální režim*. Implementace virtuálního režimu znamená implementace jeden nebo více obslužných rutin událostí tak informace o žádosti o řízení o buněk jako informace, je potřeba.  
  
 Pokud pracujete s velkými objemy dat, můžete chtít implementace virtuálního režimu zajistit optimální efektivitu. Virtuální režim je také užitečné pro zachování hodnot nevázaných sloupců, které zobrazují společně s sloupce načíst z jiného zdroje dat.  
  
 Další informace o virtuální režim najdete v tématu [návod: Implementace virtuálního režimu v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Klíčové body scénáře  
  
-   Virtuální režim je vhodný pro zobrazení velmi velké objemy dat, když potřebujete optimalizovat výkon.  
  
## <a name="scenario-4-automatically-resizing-rows-and-columns"></a>Scénář 4: Automatická změna velikosti řádků a sloupců  
 Při zobrazení data, která se pravidelně aktualizují, můžete nastavit automaticky velikost řádků a sloupců zajistit, že veškerý obsah je viditelná. <xref:System.Windows.Forms.DataGridView> Řízení poskytuje několik možností, které vám umožní povolit nebo zakázat ruční změna velikosti, přizpůsobit prostřednictvím kódu programu v určitých časech nebo změny velikosti automaticky vždy, když obsah změny. Další informace najdete v tématu [možnosti pro změnu velikosti v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Klíčové body scénáře  
  
-   Ruční změna velikosti umožňuje uživatelům upravit buňky výšky a šířky.  
  
-   Automatická změna velikosti umožňuje udržovat velikosti buněk tak, aby buňky obsah je oříznut nikdy.  
  
-   Programová změna velikosti umožňuje v určitých časech, aby se zabránilo snížení výkonu systému průběžné Automatická změna velikosti Změna velikosti buněk.  
  
## <a name="scenario-5-simple-customization"></a>Scénář 5: Přizpůsobení jednoduchý  
 <xref:System.Windows.Forms.DataGridView> Řízení poskytuje mnoho způsobů, změnit jeho základní vzhled a chování. Další informace najdete v tématu [styly buňky v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Klíčové body scénáře  
  
-   <xref:System.Windows.Forms.DataGridViewCellStyle>objekty umožňují poskytovat barvy, písma, formátování a umístění informace na více úrovních a pro jednotlivé elementy ovládacího prvku.  
  
-   Styly buňky můžete vrstvu a sdílí několik elementů, takže můžete opakovaně použít kód.  
  
## <a name="scenario-6-advanced-customization"></a>Scénář 6: Rozšířené přizpůsobení  
 <xref:System.Windows.Forms.DataGridView> Řízení nabízí mnoha způsoby, jak můžete přizpůsobit vzhled a chování.  
  
### <a name="scenario-key-points"></a>Klíčové body scénáře  
  
-   Můžete zadat vlastní kód Malování buňky. Další informace najdete v tématu [postupy: přizpůsobení vzhledu buněk v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md).  
  
-   Můžete zadat vlastní Malování řádek. To je užitečné, například k vytvoření řádků s obsahem, který zahrnuje několik sloupců. Další informace najdete v tématu [postupy: přizpůsobení vzhledu řádků v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/customize-the-appearance-of-rows-in-the-datagrid.md).  
  
-   Můžete implementovat vaše vlastní třídy buňky a ve sloupci k přizpůsobení vzhledu buněk. Další informace najdete v tématu [postupy: přizpůsobení buněk a sloupců v ovládacím prvku Windows Forms DataGridView pomocí rozšíření jejich chování a vzhledu](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md).  
  
-   Můžete implementovat vaše vlastní třídy buněk a sloupců do hostitelské ovládací prvky než ty, které jsou poskytované typy integrované sloupce. Další informace najdete v tématu [postup: hostitelské ovládací prvky v systému Windows Forms DataGridView buněk](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 [Přehled ovládacího prvku DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)
