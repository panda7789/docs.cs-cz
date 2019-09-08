---
title: Datové sady, datové tabulky a datová zobrazení
ms.date: 03/30/2017
ms.assetid: 6d4c4b69-8919-4224-8a65-6cca1c61b48f
ms.openlocfilehash: 1744f6c6d8ea3c28a8dab30c0d201ae1dacc7ee3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786191"
---
# <a name="datasets-datatables-and-dataviews"></a>Datové sady, datové tabulky a datová zobrazení
ADO.NET <xref:System.Data.DataSet> je reprezentace dat rezidenta v paměti, která poskytuje konzistentní relační programovací model bez ohledu na zdroj dat, který obsahuje. <xref:System.Data.DataSet> Představuje kompletní sadu dat, včetně tabulek, které obsahují, vyřazení a omezení dat a také vztahů mezi tabulkami.  
  
 Existuje několik způsobů práce s a <xref:System.Data.DataSet>, které lze použít nezávisle nebo v kombinaci. Můžete:  
  
- Programové vytvoření <xref:System.Data.DataTable>, <xref:System.Data.DataRelation>a v rámci<xref:System.Data.DataSet> a naplnění tabulek daty. <xref:System.Data.Constraint>  
  
- Naplňte tabulky daty z existujícího relačního zdroje dat `DataAdapter`pomocí. <xref:System.Data.DataSet>  
  
- Načtěte a zachovejte <xref:System.Data.DataSet> obsah pomocí XML. Další informace naleznete v tématu [using XML in a DataSet](using-xml-in-a-dataset.md).  
  
 Silné typy <xref:System.Data.DataSet> lze také přenést pomocí webové služby XML. Návrh je <xref:System.Data.DataSet> ideální pro přenos dat pomocí webových služeb XML. Přehled webových služeb XML najdete v tématu [Přehled webových služeb XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w9fdtx28(v=vs.100)). Příklad použití <xref:System.Data.DataSet> webové služby XML naleznete v tématu [spotřebovávání datové sady z webové služby XML](consuming-a-dataset-from-an-xml-web-service.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Vytvoření datové sady](creating-a-dataset.md)  
 Popisuje syntaxi pro vytvoření instance <xref:System.Data.DataSet>.  
  
 [Přidání datové tabulky do datové sady](adding-a-datatable-to-a-dataset.md)  
 Popisuje, jak vytvořit a přidat tabulky a sloupce do <xref:System.Data.DataSet>.  
  
 [Přidání datových relací](adding-datarelations.md)  
 Popisuje, jak vytvořit relace mezi tabulkami v <xref:System.Data.DataSet>.  
  
 [Navigace v datových relacích](navigating-datarelations.md)  
 Popisuje, jak použít relace mezi tabulkami v <xref:System.Data.DataSet> k vrácení podřízených nebo nadřazených řádků relace typu nadřazený-podřízený.  
  
 [Slučování obsahu datové sady](merging-dataset-contents.md)  
 Popisuje, jak sloučit obsah <xref:System.Data.DataSet>jednoho, <xref:System.Data.DataTable>nebo <xref:System.Data.DataRow> pole do jiného <xref:System.Data.DataSet>.  
  
 [Kopírování obsahu datové sady](copying-dataset-contents.md)  
 Popisuje <xref:System.Data.DataSet> , jak vytvořit kopii, která může obsahovat schéma i zadaná data.  
  
 [Zpracování událostí datové sady](handling-dataset-events.md)  
 Popisuje události <xref:System.Data.DataSet> a, jak je používat.  
  
 [Typové datové sady](typed-datasets.md)  
 Popisuje, co je <xref:System.Data.DataSet> typu a jak ho vytvořit a použít.  
  
 [Datové tabulky](datatables.md)  
 Popisuje <xref:System.Data.DataTable>, jak vytvořit, definovat schéma a manipulovat s daty.  
  
 [Čtečky datových tabulek](datatablereaders.md)  
 Popisuje, jak vytvořit a použít <xref:System.Data.DataTableReader>.  
  
 [Zobrazení dat](dataviews.md)  
 Popisuje, jak vytvořit a pracovat `DataViews` s <xref:System.Data.DataView> událostmi a pracovat s nimi.  
  
 [Použití XML v datové sadě](using-xml-in-a-dataset.md)  
 Popisuje, jak <xref:System.Data.DataSet> komunikuje s XML jako zdroj dat, včetně načítání a uchování obsahu <xref:System.Data.DataSet> jako XML data.  
  
 [Spotřebování datové sady z webové služby XML](consuming-a-dataset-from-an-xml-web-service.md)  
 Popisuje, jak vytvořit webovou službu XML, která používá <xref:System.Data.DataSet> k přenosu dat.  
  
## <a name="related-sections"></a>Související oddíly  
 [Novinky v ADO.NET](../whats-new.md)  
 Přináší nové funkce, které jsou v ADO.NET novinkou.  
  
 [Přehled ADO.NET](../ado-net-overview.md)  
 Poskytuje Úvod k návrhu a součástem ADO.NET.  
  
 [Naplnění datové sady z adaptéru dat](../populating-a-dataset-from-a-dataadapter.md)  
 Popisuje, jak načíst **datovou sadu** s daty ze zdroje dat.  
  
 [Aktualizace zdrojů dat pomocí adaptérů dat](../updating-data-sources-with-dataadapters.md)  
 Popisuje, jak vyřešit změny dat v datové **sadě** zpět do zdroje dat.  
  
 [Přidání existujících omezení do datové sady](../adding-existing-constraints-to-a-dataset.md)  
 Popisuje, jak naplnit **datovou sadu** pomocí informací o primárním klíči ze zdroje dat.  
  
## <a name="see-also"></a>Viz také:

- [ADO.NET](../index.md)
- [Přehled ADO.NET](../ado-net-overview.md)
