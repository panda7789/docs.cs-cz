---
title: DataTableReaders
ms.date: 03/30/2017
ms.assetid: 97546ae2-0e42-4d26-961d-e0b244d81ded
ms.openlocfilehash: a790335a25327563e3dab6093449345b99afd048
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59213998"
---
# <a name="datatablereaders"></a>DataTableReaders
<xref:System.Data.DataTableReader> Představuje obsah <xref:System.Data.DataTable> nebo <xref:System.Data.DataSet> ve formě nejmíň jeden výsledek jen pro čtení, dopředné nastaví.  
  
 Při vytváření **třída DataTableReader** z **DataTable**, výsledná **třída DataTableReader** objekt obsahuje sadu s stejná data jako jeden výsledek  **Objekt DataTable** ze které byla vytvořena, s výjimkou všechny řádky, které jsou označené jako odstraněný. Sloupce se zobrazí ve stejném pořadí jako původní **DataTable**.  
  
 A **třída DataTableReader** může obsahovat více sad výsledků dotazu, pokud byl vytvořen voláním <xref:System.Data.DataSet.CreateDataReader%2A>. Výsledky jsou ve stejném pořadí jako **DataTables** v **datovou sadu** objektu <xref:System.Data.DataSet.Tables%2A> kolekce.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Vytvoření čtečky dat](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-datareader.md)  
 Popisuje, jak vytvořit **třída DataTableReader** objektu.  
  
 [Navigace v datových tabulkách](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datatables.md)  
 Popisuje použití **čtení** metoda procházejte obsah **třída DataTableReader**.  
  
## <a name="see-also"></a>Viz také:

- [Načítání a úpravy dat v ADO.NET](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
