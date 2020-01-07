---
title: Datová vazba a LINQ to DataSet
ms.date: 03/30/2017
ms.assetid: 310bff4a-32dd-4f20-a271-6dbd82912631
ms.openlocfilehash: 2b49e2a3ff0d95dcbceff8099f51993c0f08d64e
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634869"
---
# <a name="data-binding-and-linq-to-dataset"></a>Datová vazba a LINQ to DataSet
*Datová vazba* je proces, který vytváří propojení mezi uživatelským rozhraním aplikace a obchodní logikou. Pokud má vazba správné nastavení a data poskytují správná oznámení, při změně její hodnoty prvky, které jsou vázány na data, se automaticky projeví změny. <xref:System.Data.DataSet> je reprezentace dat v paměti, která poskytuje konzistentní relační programovací model bez ohledu na zdroj dat, který obsahuje. ADO.NET 2,0 <xref:System.Data.DataView> umožňuje řadit a filtrovat data uložená v <xref:System.Data.DataTable>. Tato funkce se často používá v aplikacích pro datovou vazbu. Pomocí <xref:System.Data.DataView>můžete vystavit data v tabulce s různými objednávkami řazení a data můžete filtrovat podle stavu řádku nebo podle výrazu filtru. Další informace o objektu <xref:System.Data.DataView> naleznete v tématu [DataViews](./dataset-datatable-dataview/dataviews.md).  
  
 LINQ to DataSet umožňuje vývojářům vytvářet komplexní a výkonné dotazy přes <xref:System.Data.DataSet> pomocí LINQ (Language-Integrated Query). LINQ to DataSet dotaz však vrátí výčet objektů <xref:System.Data.DataRow>, který není možné snadno použít ve scénáři vazby. Aby bylo vytváření vazby snazší, můžete vytvořit <xref:System.Data.DataView> z dotazu LINQ to DataSet. Tato <xref:System.Data.DataView> používá filtrování a řazení zadané v dotazu, ale je vhodnější pro datovou vazbu. LINQ to DataSet rozšiřuje funkčnost <xref:System.Data.DataView> tím, že poskytuje filtrování a řazení založené na výrazu LINQ, což umožňuje mnohem složitější a výkonné filtrování a řazení operací než filtrování a řazení založené na řetězci.  
  
 Všimněte si, že <xref:System.Data.DataView> představuje samotný dotaz a není zobrazením nad dotazem. <xref:System.Data.DataView> je vázán k ovládacímu prvku uživatelského rozhraní, jako je například <xref:System.Windows.Forms.DataGrid> nebo <xref:System.Windows.Forms.DataGridView>, což poskytuje jednoduchý model vázání dat. <xref:System.Data.DataView> lze také vytvořit z <xref:System.Data.DataTable>a poskytnout tak výchozí zobrazení této tabulky.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Vytvoření objektu zobrazení dat](creating-a-dataview-object-linq-to-dataset.md)  
 Poskytuje informace o vytváření <xref:System.Data.DataView>.  
  
 [Filtrování se zobrazením dat](filtering-with-dataview-linq-to-dataset.md)  
 Popisuje, jak filtrovat pomocí <xref:System.Data.DataView>.  
  
 [Řazení se zobrazením dat](sorting-with-dataview-linq-to-dataset.md)  
 V této části najdete popis postupu při řazení pomocí <xref:System.Data.DataView>.  
  
 [Dotazování na kolekci DataRowView v zobrazení dat](querying-the-datarowview-collection-in-a-dataview.md)  
 Poskytuje informace o dotazování kolekce <xref:System.Data.DataRowView> vystavené <xref:System.Data.DataView>.  
  
 [Výkon zobrazení dat](dataview-performance.md)  
 Poskytuje informace o <xref:System.Data.DataView> a výkonu.  
  
 [Postupy: Připojení objektu DataView k ovládacímu prvku Windows Forms DataGridView](how-to-bind-a-dataview-object-to-a-winforms-datagridview-control.md)  
 Popisuje, jak vytvořit objekt <xref:System.Data.DataView> k <xref:System.Windows.Forms.DataGridView>.  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním](programming-guide-linq-to-dataset.md)
