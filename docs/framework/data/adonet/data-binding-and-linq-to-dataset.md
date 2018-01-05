---
title: "Datové vazby a LINQ na DataSet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 310bff4a-32dd-4f20-a271-6dbd82912631
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: efaa9f3e72af6f5ed948b974920564188ae42b44
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="data-binding-and-linq-to-dataset"></a>Datové vazby a LINQ na DataSet
*Datová vazba* je proces, který naváže připojení mezi aplikací uživatelského rozhraní a obchodní logiku. Pokud vazby má správná nastavení a data poskytuje správné oznámení, když její hodnota se mění data, projeví elementy, které jsou vázané na data změny automaticky. <xref:System.Data.DataSet> Je reprezentací v paměti data, která zajišťuje konzistentní relační programovací model, bez ohledu na zdroj dat obsahuje. ADO.NET 2.0 <xref:System.Data.DataView> umožňuje řazení a filtrování dat uložených v <xref:System.Data.DataTable>. Tato funkce se často používá v aplikacích datové vazby. Pomocí <xref:System.Data.DataView>, můžou zpřístupnit data v tabulce s různým řazením a data lze filtrovat podle řádku stavu nebo podle výraz filtru. Další informace o <xref:System.Data.DataView> objektu, najdete v části [DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md).  
  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]umožňuje vývojářům vytvářet výkonné, komplexní dotazy přes <xref:System.Data.DataSet> pomocí [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]. Ale [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotaz vrátí výčet <xref:System.Data.DataRow> objekty, které se snadno používá v případě vazby. Pro usnadnění vazby můžete vytvořit <xref:System.Data.DataView> z [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] dotazu. To <xref:System.Data.DataView> používá filtrování a řazení zadaný v dotazu, ale je vhodnější pro datovou vazbu. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]rozšiřuje funkce <xref:System.Data.DataView> tím, že poskytuje [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] založené na výrazu filtrování a řazení, což umožňuje mnohem složitější a výkonné filtrování a řazení než založené na řetězcích Filtrování a řazení.  
  
 Všimněte si, že <xref:System.Data.DataView> představuje samotný dotaz a není zobrazení nad dotazu. <xref:System.Data.DataView> , Jako je vázána k ovládacímu prvku uživatelského rozhraní <xref:System.Windows.Forms.DataGrid> nebo <xref:System.Windows.Forms.DataGridView>, poskytuje jednoduché datové vazby modelu. A <xref:System.Data.DataView> můžete také vytvořit z <xref:System.Data.DataTable>, že poskytuje výchozí zobrazení této tabulky.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Vytvoření objektu zobrazení dat](../../../../docs/framework/data/adonet/creating-a-dataview-object-linq-to-dataset.md)  
 Poskytuje informace o vytváření <xref:System.Data.DataView>.  
  
 [Filtrování se zobrazením dat](../../../../docs/framework/data/adonet/filtering-with-dataview-linq-to-dataset.md)  
 Popisuje, jak filtrovat, u kterých <xref:System.Data.DataView>.  
  
 [Řazení se zobrazením dat](../../../../docs/framework/data/adonet/sorting-with-dataview-linq-to-dataset.md)  
 Popisuje, jak řadit s <xref:System.Data.DataView>.  
  
 [Dotazování na kolekci DataRowView v zobrazení dat](../../../../docs/framework/data/adonet/querying-the-datarowview-collection-in-a-dataview.md)  
 Poskytuje informace o vytváření dotazů <xref:System.Data.DataRowView> kolekce vystavené <xref:System.Data.DataView>.  
  
 [Výkon zobrazení dat](../../../../docs/framework/data/adonet/dataview-performance.md)  
 Poskytuje informace o <xref:System.Data.DataView> a výkonu.  
  
 [Postupy: Připojení objektu DataView k ovládacímu prvku Windows Forms DataGridView](../../../../docs/framework/data/adonet/how-to-bind-a-dataview-object-to-a-winforms-datagridview-control.md)  
 Popisuje, jak vytvořit vazbu <xref:System.Data.DataView> do objektu <xref:System.Windows.Forms.DataGridView>.  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
