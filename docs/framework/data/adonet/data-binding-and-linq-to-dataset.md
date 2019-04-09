---
title: Datová vazba a LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: 310bff4a-32dd-4f20-a271-6dbd82912631
ms.openlocfilehash: b081a648023aa21eea3a20ec409600d3bcbe9878
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59073556"
---
# <a name="data-binding-and-linq-to-dataset"></a>Datová vazba a LINQ to DataSet
*Vytváření datových vazeb* je proces, který vytvoří připojení mezi uživatelského rozhraní aplikace a obchodní logiky. Pokud data poskytuje správné oznámení, když se data změní jeho hodnotu vazbu se správným nastavením, elementy, které jsou vázány na data automaticky odrážejí změny. <xref:System.Data.DataSet> Je v paměti reprezentace dat, která poskytuje konzistentní relační programovací model, bez ohledu na zdroj dat obsahuje. ADO.NET 2.0 <xref:System.Data.DataView> umožňuje řazení a filtrování dat uložených v <xref:System.Data.DataTable>. Tato funkce se často používá v aplikacích datové vazby. Pomocí <xref:System.Data.DataView>, můžete zpřístupnit data v tabulce s jiné pořadí řazení a data lze filtrovat podle stavu nebo podle výraz filtru řádků. Další informace o <xref:System.Data.DataView> objektu, najdete v článku [zobrazení dat](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md).  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] umožňuje vývojářům vytvářet složité a výkonné dotazy nad <xref:System.Data.DataSet> pomocí [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]. Nicméně [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotaz vrátí výčet <xref:System.Data.DataRow> objekty, které se snadno použít ve scénáři vazby. Abychom usnadnili vazby, můžete vytvořit <xref:System.Data.DataView> z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazu. To <xref:System.Data.DataView> používá filtrování a řazení, zadaný v dotazu, ale je vhodnější pro vytváření datových vazeb. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] rozšiřuje funkce <xref:System.Data.DataView> poskytnutím [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] založené na výrazu filtrování a řazení, což umožňuje mnohem komplexnější a výkonné operace filtrování a řazení než založené na řetězci filtrování a řazení.  
  
 Všimněte si, <xref:System.Data.DataView> představuje samotný dotaz a není zobrazení nad dotaz. <xref:System.Data.DataView> , Jako je vázán na ovládací prvek uživatelského rozhraní <xref:System.Windows.Forms.DataGrid> nebo <xref:System.Windows.Forms.DataGridView>, poskytuje jednoduché datové vazby modelu. A <xref:System.Data.DataView> lze také vytvořit z <xref:System.Data.DataTable>, poskytuje výchozí zobrazení tabulky.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Vytvoření objektu zobrazení dat](../../../../docs/framework/data/adonet/creating-a-dataview-object-linq-to-dataset.md)  
 Poskytuje informace o vytváření <xref:System.Data.DataView>.  
  
 [Filtrování se zobrazením dat](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md)  
 Popisuje, jak filtrovat pomocí <xref:System.Data.DataView>.  
  
 [Řazení se zobrazením dat](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md)  
 Popisuje, jak řadit <xref:System.Data.DataView>.  
  
 [Dotazování na kolekci DataRowView v zobrazení dat](../../../../docs/framework/data/adonet/querying-the-datarowview-collection-in-a-dataview.md)  
 Poskytuje informace o vytváření dotazů <xref:System.Data.DataRowView> kolekce vystavené <xref:System.Data.DataView>.  
  
 [Výkon zobrazení dat](../../../../docs/framework/data/adonet/dataview-performance.md)  
 Poskytuje informace o <xref:System.Data.DataView> a výkonu.  
  
 [Postupy: Připojení objektu DataView k ovládacímu prvku Windows Forms DataGridView](../../../../docs/framework/data/adonet/how-to-bind-a-dataview-object-to-a-winforms-datagridview-control.md)  
 Popisuje, jak vytvořit vazbu <xref:System.Data.DataView> do objektu <xref:System.Windows.Forms.DataGridView>.  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
