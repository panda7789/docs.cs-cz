---
title: "Datové sady, datové tabulky a datová zobrazení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d4c4b69-8919-4224-8a65-6cca1c61b48f
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 5106454e3f515d671060bf00cdd2cdb859e0a047
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="datasets-datatables-and-dataviews"></a>Datové sady, datové tabulky a datová zobrazení
Technologie ADO.NET <xref:System.Data.DataSet> je rezidentní reprezentace data, která zajišťuje konzistentní relační programovací model bez ohledu na zdroj dat obsahuje. A <xref:System.Data.DataSet> představuje kompletní sadu dat včetně tabulek, které obsahují, řazení a omezit data, jakož i relace mezi tabulkami.  
  
 Práce s několika způsoby <xref:System.Data.DataSet>, který je možné použít samostatně nebo v kombinaci. Můžeš:  
  
-   Vytváření prostřednictvím kódu programu <xref:System.Data.DataTable>, <xref:System.Data.DataRelation>, a <xref:System.Data.Constraint> v rámci <xref:System.Data.DataSet> a naplnění tabulky s daty.  
  
-   Naplnění <xref:System.Data.DataSet> s tabulkami dat z existujícího zdroje relačních dat systémem `DataAdapter`.  
  
-   Načtení a zachovat <xref:System.Data.DataSet> obsah pomocí XML. Další informace najdete v tématu [pomocí XML v datové sadě](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).  
  
 Silného typu <xref:System.Data.DataSet> můžete také přenosu pomocí webové služby XML. Návrh <xref:System.Data.DataSet> je ideální pro přenos dat pomocí webové služby XML. Přehled webové služby XML, najdete v části [Přehled webové služby XML](http://msdn.microsoft.com/en-us/9db0c7b8-bca6-462b-9be5-f5f9a7f05a4d). Příklad použití <xref:System.Data.DataSet> z webové služby XML, najdete na stránce [využívání datové sady z webové služby XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/consuming-a-dataset-from-an-xml-web-service.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Vytvoření datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset.md)  
 Popisuje syntaxi pro vytvoření instance <xref:System.Data.DataSet>.  
  
 [Přidání datové tabulky do datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-a-datatable-to-a-dataset.md)  
 Popisuje postup vytvoření a přidání tabulek a sloupců <xref:System.Data.DataSet>.  
  
 [Přidání datových relací](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md)  
 Popisuje postup vytvoření relace mezi tabulkami <xref:System.Data.DataSet>.  
  
 [Navigace v datových relacích](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations.md)  
 Popisuje, jak použít vztahy mezi tabulkami <xref:System.Data.DataSet> vrátit nadřazená nebo podřízená řádky relaci nadřazený podřízený.  
  
 [Slučování obsahu datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md)  
 Popisuje, jak sloučit obsah jedné <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, nebo <xref:System.Data.DataRow> pole do jiné <xref:System.Data.DataSet>.  
  
 [Kopírování obsahu datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/copying-dataset-contents.md)  
 Popisuje, jak vytvořit kopii <xref:System.Data.DataSet> obsahující schématu, jakož i zadaná data.  
  
 [Zpracování událostí datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md)  
 Popisuje události z <xref:System.Data.DataSet> a jejich použití.  
  
 [Typové datové sady](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 Popisuje, co představuje zadaný <xref:System.Data.DataSet> je a o tom, jak vytvořit a používat ho.  
  
 [Datové tabulky](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 Popisuje postup vytvoření <xref:System.Data.DataTable>, definovat schéma a pracovat s daty.  
  
 [Čtečky datových tabulek](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)  
 Popisuje, jak vytvořit a použít <xref:System.Data.DataTableReader>.  
  
 [Zobrazení dat](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 Popisuje postup vytváření a práci s `DataViews` a pracovat s <xref:System.Data.DataView> události.  
  
 [Použití XML v datové sadě](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 Popisuje, jak <xref:System.Data.DataSet> komunikuje s XML jako zdroj dat, včetně načítání a zachování obsahu <xref:System.Data.DataSet> jako XML data.  
  
 [Spotřebování datové sady z webové služby XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/consuming-a-dataset-from-an-xml-web-service.md)  
 Popisuje postup vytvoření XML webové služby, který používá <xref:System.Data.DataSet> k přenosu dat.  
  
## <a name="related-sections"></a>Související oddíly  
 [Novinky v ADO.NET](../../../../../docs/framework/data/adonet/whats-new.md)  
 Nabízí funkce, které nově jsou v technologii ADO.NET.  
  
 [Přehled ADO.NET](../../../../../docs/framework/data/adonet/ado-net-overview.md)  
 Poskytuje úvod do návrhu a součástí ADO.NET.  
  
 [Naplnění datové sady z adaptéru dat](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 Popisuje, jak načíst **datovou sadu** s daty ze zdroje dat.  
  
 [Aktualizace zdrojů dat pomocí adaptérů dat](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 Popisuje, jak vyřešit změny k datům ve **datovou sadu** zpět do zdroje dat.  
  
 [Přidání existujících omezení do datové sady](../../../../../docs/framework/data/adonet/adding-existing-constraints-to-a-dataset.md)  
 Popisuje, jak k naplnění **datovou sadu** s primární klíče informace ze zdroje dat.  
  
## <a name="see-also"></a>Viz také  
 [ADO.NET](../../../../../docs/framework/data/adonet/index.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
