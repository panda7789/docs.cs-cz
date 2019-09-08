---
title: Datová vazba a LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: 310bff4a-32dd-4f20-a271-6dbd82912631
ms.openlocfilehash: 563d57249daa3aa720da1d9654866727f770afb3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786698"
---
# <a name="data-binding-and-linq-to-dataset"></a>Datová vazba a LINQ to DataSet
*Datová vazba* je proces, který vytváří propojení mezi uživatelským rozhraním aplikace a obchodní logikou. Pokud má vazba správné nastavení a data poskytují správná oznámení, při změně její hodnoty prvky, které jsou vázány na data, se automaticky projeví změny. <xref:System.Data.DataSet> Je reprezentace dat v paměti, která poskytuje konzistentní relační programovací model bez ohledu na zdroj dat, který obsahuje. ADO.NET 2,0 <xref:System.Data.DataView> umožňuje řadit a filtrovat data uložená <xref:System.Data.DataTable>v. Tato funkce se často používá v aplikacích pro datovou vazbu. Pomocí <xref:System.Data.DataView>můžete vystavit data v tabulce s různými objednávkami řazení a data můžete filtrovat podle stavu řádku nebo podle výrazu filtru. Další informace o <xref:System.Data.DataView> objektu naleznete v tématu [DataViews](./dataset-datatable-dataview/dataviews.md).  
  
 LINQ to DataSet umožňuje vývojářům vytvářet komplexní a výkonné dotazy přes <xref:System.Data.DataSet> pomocí. [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] LINQ to DataSet dotaz však vrátí výčet <xref:System.Data.DataRow> objektů, které nelze snadno použít ve scénáři vazby. Aby bylo vytváření vazby snazší, můžete vytvořit <xref:System.Data.DataView> z LINQ to DataSetho dotazu. Používá <xref:System.Data.DataView> se k tomu filtrování a řazení zadané v dotazu, ale je vhodnější pro datovou vazbu. LINQ to DataSet rozšiřuje funkčnost <xref:System.Data.DataView> služby tím, že poskytuje [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] filtrování a řazení založené na výrazech, což umožňuje mnohem složitější a výkonné operace filtrování a řazení než filtrování a řazení založené na řetězci.  
  
 Všimněte si, <xref:System.Data.DataView> že představuje samotný dotaz a není zobrazením nad dotazem. Je vázán k ovládacímu prvku uživatelského rozhraní, jako <xref:System.Windows.Forms.DataGrid> je například nebo <xref:System.Windows.Forms.DataGridView>, a poskytuje jednoduchý model vázání dat. <xref:System.Data.DataView> Lze také vytvořit z a <xref:System.Data.DataTable>a poskytnout tak výchozí zobrazení této tabulky. <xref:System.Data.DataView>  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Vytvoření objektu zobrazení dat](creating-a-dataview-object-linq-to-dataset.md)  
 Poskytuje informace o vytvoření <xref:System.Data.DataView>.  
  
 [Filtrování se zobrazením dat](filtering-with-dataview-linq-to-dataset.md)  
 Popisuje, jak filtrovat pomocí <xref:System.Data.DataView>.  
  
 [Řazení se zobrazením dat](sorting-with-dataview-linq-to-dataset.md)  
 V této části <xref:System.Data.DataView>najdete popis postupu při řazení pomocí.  
  
 [Dotazování na kolekci DataRowView v zobrazení dat](querying-the-datarowview-collection-in-a-dataview.md)  
 Poskytuje informace o dotazování <xref:System.Data.DataRowView> kolekce vystavené nástrojem. <xref:System.Data.DataView>  
  
 [Výkon zobrazení dat](dataview-performance.md)  
 Poskytuje informace o <xref:System.Data.DataView> výkonu a.  
  
 [Postupy: Vytvoření vazby objektu DataView k ovládacímu prvku DataGridView model Windows Forms](how-to-bind-a-dataview-object-to-a-winforms-datagridview-control.md)  
 Popisuje, jak vytvořit vazby <xref:System.Data.DataView> objektu <xref:System.Windows.Forms.DataGridView>k.  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním](programming-guide-linq-to-dataset.md)
