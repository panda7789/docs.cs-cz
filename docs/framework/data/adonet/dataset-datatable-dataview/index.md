---
title: Datové sady, datové tabulky a datová zobrazení
ms.date: 03/30/2017
ms.assetid: 6d4c4b69-8919-4224-8a65-6cca1c61b48f
ms.openlocfilehash: 9c57f75dd94f3fbda74c13a5d5773825051fe416
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59105726"
---
# <a name="datasets-datatables-and-dataviews"></a>Datové sady, datové tabulky a datová zobrazení
ADO.NET <xref:System.Data.DataSet> je rezidentní reprezentace dat, která poskytuje relační konzistentní programovací model bez ohledu na zdroj dat obsahuje. A <xref:System.Data.DataSet> představuje ucelenou sadu dat včetně tabulek, které obsahují, pořadí a omezit data, jakož i relace mezi tabulkami.  
  
 Práce s několika způsoby <xref:System.Data.DataSet>, který je možné použít samostatně nebo v kombinaci. Můžete:  
  
-   Prostřednictvím kódu programu vytvořit <xref:System.Data.DataTable>, <xref:System.Data.DataRelation>, a <xref:System.Data.Constraint> v rámci <xref:System.Data.DataSet> a naplnění tabulek daty.  
  
-   Naplnění <xref:System.Data.DataSet> s tabulkami dat z existujícího zdroje relačních dat pomocí `DataAdapter`.  
  
-   Načtení a uložení <xref:System.Data.DataSet> obsah pomocí XML. Další informace najdete v tématu [použití XML v datové sadě](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).  
  
 Silného typu <xref:System.Data.DataSet> může taky přenášet pomocí webové služby XML. Návrh <xref:System.Data.DataSet> je ideální pro přenos dat pomocí webové služby XML. Přehled webových služeb XML, naleznete v tématu [přehled webových služeb XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w9fdtx28(v=vs.100)). Příklad použití <xref:System.Data.DataSet> z webové služby XML, naleznete v tématu [spotřebování datové sady z webové služby XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/consuming-a-dataset-from-an-xml-web-service.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Vytvoření datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset.md)  
 Popisuje syntaxi pro vytvoření instance <xref:System.Data.DataSet>.  
  
 [Přidání datové tabulky do datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-a-datatable-to-a-dataset.md)  
 Popisuje, jak vytvořit a přidat tabulky a sloupce, které chcete <xref:System.Data.DataSet>.  
  
 [Přidání datových relací](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md)  
 Popisuje postup vytvoření vztahů mezi tabulkami <xref:System.Data.DataSet>.  
  
 [Navigace v datových relacích](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations.md)  
 Popisuje způsob použití vztahy mezi tabulkami <xref:System.Data.DataSet> vrátit podřízeného nebo nadřazeného řádky v relaci nadřazený podřízený.  
  
 [Slučování obsahu datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md)  
 Popisuje, jak sloučit obsah jednoho <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, nebo <xref:System.Data.DataRow> pole do jiného <xref:System.Data.DataSet>.  
  
 [Kopírování obsahu datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/copying-dataset-contents.md)  
 Popisuje, jak vytvořit kopii <xref:System.Data.DataSet> , který může obsahovat schéma, jakož i zadaná data.  
  
 [Zpracování událostí datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md)  
 Popisuje událostí <xref:System.Data.DataSet> a způsob jejich použití.  
  
 [Typové datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 Popisuje, jaké typovaného <xref:System.Data.DataSet> je a jak vytvořit a používat ho.  
  
 [Datové tabulky](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 Popisuje, jak vytvořit <xref:System.Data.DataTable>, definovat schéma a manipulaci s daty.  
  
 [Čtečky datových tabulek](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)  
 Popisuje, jak vytvořit a používat <xref:System.Data.DataTableReader>.  
  
 [Zobrazení dat](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 Popisuje, jak vytvořit a pracovat s `DataViews` a pracovat s <xref:System.Data.DataView> události.  
  
 [Použití XML v datové sadě](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 Popisuje, jak <xref:System.Data.DataSet> komunikuje s XML jako zdroj dat, včetně načítání a při zachování obsahu <xref:System.Data.DataSet> jako XML data.  
  
 [Spotřebování datové sady z webové služby XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/consuming-a-dataset-from-an-xml-web-service.md)  
 Popisuje, jak vytvořit webové služby XML, který používá <xref:System.Data.DataSet> k přenosu dat.  
  
## <a name="related-sections"></a>Související oddíly  
 [Novinky v ADO.NET](../../../../../docs/framework/data/adonet/whats-new.md)  
 Představuje funkce, které jsou nové v rozhraní ADO.NET.  
  
 [Přehled ADO.NET](../../../../../docs/framework/data/adonet/ado-net-overview.md)  
 Poskytuje úvod do navrhování a komponenty rozhraní ADO.NET.  
  
 [Naplnění datové sady z adaptéru dat](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 Popisuje, jak načíst **datovou sadu** s daty z datového zdroje.  
  
 [Aktualizace zdrojů dat pomocí adaptérů dat](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 Popisuje, jak vyřešit změny dat v **datovou sadu** zpět do zdroje dat.  
  
 [Přidání existujících omezení do datové sady](../../../../../docs/framework/data/adonet/adding-existing-constraints-to-a-dataset.md)  
 Popisuje, jak naplnit **datovou sadu** s informacemi o primárním klíči ze zdroje dat.  
  
## <a name="see-also"></a>Viz také:

- [ADO.NET](../../../../../docs/framework/data/adonet/index.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
