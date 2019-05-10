---
title: Scénáře ovládacího prvku DataGridView (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], displaying in tabular format
- data grids [Windows Forms], about data grids
- DataGridView control [Windows Forms], scenarios
ms.assetid: 09a5fd05-3447-47ec-a4ec-6082a2b7f0dd
ms.openlocfilehash: 7350b0da19650b99bcfd456f93e994492a56d7e3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648098"
---
# <a name="datagridview-control-scenarios-windows-forms"></a>Scénáře ovládacího prvku DataGridView (Windows Forms)
S <xref:System.Windows.Forms.DataGridView> ovládacího prvku, lze zobrazit tabulková data z různých datových zdrojů. Pro jednoduché použití, můžete ručně naplnit <xref:System.Windows.Forms.DataGridView> a manipulaci s daty přímo prostřednictvím ovládacího prvku. Obvykle, ale bude ukládat data v externí zdroj dat a vazbu ovládacího prvku k němu prostřednictvím <xref:System.Windows.Forms.BindingSource> komponenty.  
  
 Toto téma popisuje některé běžné scénáře, které se týkají <xref:System.Windows.Forms.DataGridView> ovládacího prvku.  
  
## <a name="scenario-1-displaying-small-amounts-of-data"></a>Scénář 1: Zobrazení malý objem dat.  
 Není nutné ukládat data do externího zdroje dat pro její zobrazení v <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Pokud pracujete s menším objemem dat, kterou můžete naplnit ovládací prvek sami a manipulaci s daty pomocí ovládacího prvku. Tento postup se nazývá *režim bez vazby*. Další informace najdete v tématu [jak: Vytvoření ovládacího prvku DataGridView formuláře Windows nevázaného](how-to-create-an-unbound-windows-forms-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Klíčové body scénáře  
  
- V režim bez vazby vyplníte ovládací prvek ručně.  
  
- Režim bez vazby je obzvláště vhodný pro malé množství dat jen pro čtení.  
  
- Režim bez vazby je také vhodné pro tabulkovém nebo řídce naplněných tabulek.  
  
## <a name="scenario-2-viewing-and-updating-data-stored-in-an-external-data-source"></a>Scénář 2: Zobrazení a aktualizace dat uložených v externí zdroj dat.  
 Můžete použít <xref:System.Windows.Forms.DataGridView> ovládací prvek jako uživatelské rozhraní (UI), přes které uživatelé můžou k datům v zdroj dat, například databázové tabulce nebo kolekci objektů firmy. Další informace najdete v tématu [jak: Vytvoření vazby dat k Windows Forms DataGridView – ovládací prvek](how-to-bind-data-to-the-windows-forms-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Klíčové body scénáře  
  
- Vázané režim umožňuje připojení ke zdroji dat, automaticky generovat sloupce podle vlastnosti zdroje dat nebo sloupců databáze a automaticky vyplní ovládací prvek.  
  
- Vázané režim je vhodný pro náročné uživatelské interakce s daty. Data mohou být formátována pro zobrazení a formátu očekávaném zdrojem dat je možné získat uživatelská data. Zadávání dat formátování chyb a chyb omezení databáze lze zjistit tak, aby se uživatelům může být upozornění a chybné buňky je možné odstranit.  
  
- Další funkce, jako je například řazení sloupců, zamrzá a změna uspořádání chcete uživatelům umožnit prohlížení dat tak, jak nejlépe vyhovuje jejich pracovního postupu.  
  
- Podpora schránky umožňuje uživatelům ke kopírování dat z vaší aplikace do jiných aplikací.  
  
## <a name="scenario-3-advanced-data"></a>Scénář 3: Pokročilé dat  
 Pokud máte zvláštní požadavky, které standardní datový model vazby neřeší, můžete spravovat interakce mezi ovládacím prvkem a vaše data implementací *virtuální režim*. Implementace virtuálního režimu znamená, že implementace jeden nebo více obslužných rutin událostí, které umožní ovládací prvek žádost o informace o buňky jako informace je potřeba.  
  
 Například pokud pracujete s velkými objemy dat, můžete implementovat virtuální režim k zajištění optimální efektivity. Virtuální režim je také užitečné pro zachování hodnot nevázaných sloupců, které zobrazují společně s načíst z jiného zdroje dat sloupce.  
  
 Další informace o virtuálním režimu, najdete v části [názorný postup: Implementace virtuálního režimu v Windows Forms DataGridView – ovládací prvek](implementing-virtual-mode-wf-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Klíčové body scénáře  
  
- Virtuální režim je vhodný pro zobrazení velmi velké objemy dat, když je potřeba optimalizovat výkon.  
  
## <a name="scenario-4-automatically-resizing-rows-and-columns"></a>Scénář 4: Automatická změna velikosti řádků a sloupců  
 Když zobrazíte data, která se pravidelně aktualizují, můžete automaticky změnit velikost řádků a sloupců tak, aby byl veškerý obsah viditelný. <xref:System.Windows.Forms.DataGridView> Ovládacího prvku poskytuje několik možností, které vám umožní povolit nebo zakázat ruční změna velikosti, změna velikosti programově v určitých časech nebo změny velikosti automaticky pokaždé, když obsah změny. Další informace najdete v tématu [možnosti nastavení velikosti v ovládacím prvku Windows Forms DataGridView](sizing-options-in-the-windows-forms-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Klíčové body scénáře  
  
- Ruční změna velikosti umožňuje uživatelům upravit buňku výšky a šířky.  
  
- Automatická změna velikosti umožňuje spravovat velikost buněk tak, aby obsah buňky je nikdy oříznut.  
  
- Programová změna velikosti umožňuje změnit velikost buněk v určitých časech, aby se zabránilo snížení výkonu v důsledku průběžné automatickou změnu velikosti.  
  
## <a name="scenario-5-simple-customization"></a>Scénář 5: Jednoduché přizpůsobení  
 <xref:System.Windows.Forms.DataGridView> Ovládací prvek nabízí mnoho způsobů, jak si můžete změnit jeho základního vzhledu a chování. Další informace najdete v tématu [styly buňky v ovládacím prvku Windows Forms DataGridView](cell-styles-in-the-windows-forms-datagridview-control.md).  
  
### <a name="scenario-key-points"></a>Klíčové body scénáře  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle> objekty umožňují poskytovat barvy, písma, formátování a umístění informace na různých úrovních a k jednotlivým prvkům ovládacího prvku.  
  
- Styly buňky můžete na základě úrovní a sdílí několik elementů, takže můžete opakovaně používat kód.  
  
## <a name="scenario-6-advanced-customization"></a>Scénář 6: Upravit vlastní nastavení  
 <xref:System.Windows.Forms.DataGridView> Ovládací prvek nabízí mnoho způsobů, jak můžete přizpůsobit její vzhled a chování.  
  
### <a name="scenario-key-points"></a>Klíčové body scénáře  
  
- Můžete zadat vlastní kód vykreslení obsahu buňky. Další informace najdete v tématu [jak: Přizpůsobení vzhledu buněk v ovládacím prvku Windows Forms DataGridView](customize-the-appearance-of-cells-in-the-datagrid.md).  
  
- Můžete zadat vlastní Malování řádek. To je užitečné, například k vytvoření řádky s obsahem, který zahrnuje několik sloupců. Další informace najdete v tématu [jak: Přizpůsobení vzhledu řádků v ovládacím prvku Windows Forms DataGridView](customize-the-appearance-of-rows-in-the-datagrid.md).  
  
- Můžete implementovat vlastní třídy buňky ve sloupci pro přizpůsobení vzhledu buněk. Další informace najdete v tématu [jak: Přizpůsobení buněk a sloupců v Windows Forms DataGridView rozšířením jejich chování a vzhledu](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md).  
  
- Můžete implementovat vlastní třídy buněk a sloupců do hostitelské ovládací prvky, kromě těch, které jsou poskytované typy integrované sloupců. Další informace najdete v tématu [jak: Hostování ovládacích prvků ve Windows Forms DataGridView buňky](how-to-host-controls-in-windows-forms-datagridview-cells.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- [Přehled ovládacího prvku DataGridView](datagridview-control-overview-windows-forms.md)
