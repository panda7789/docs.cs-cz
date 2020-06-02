---
title: Datové sady, datové tabulky a datová zobrazení
description: Seznamte se s různými způsoby, jak pracovat s datovou sadou ADO.NET, což je reprezentace dat rezidentních v paměti, která poskytuje konzistentní relační programovací model.
ms.date: 03/30/2017
ms.assetid: 6d4c4b69-8919-4224-8a65-6cca1c61b48f
ms.openlocfilehash: f6562452261cbc1f7ee36fb264b858646a42e4f5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286893"
---
# <a name="datasets-datatables-and-dataviews"></a>Datové sady, datové tabulky a datová zobrazení
ADO.NET <xref:System.Data.DataSet> je reprezentace dat rezidenta v paměti, která poskytuje konzistentní relační programovací model bez ohledu na zdroj dat, který obsahuje. <xref:System.Data.DataSet>Představuje kompletní sadu dat, včetně tabulek, které obsahují, vyřazení a omezení dat a také vztahů mezi tabulkami.  
  
 Existuje několik způsobů práce s a <xref:System.Data.DataSet> , které lze použít nezávisle nebo v kombinaci. Další možnosti:  
  
- Programové vytvoření <xref:System.Data.DataTable> , a <xref:System.Data.DataRelation> <xref:System.Data.Constraint> v rámci <xref:System.Data.DataSet> a naplnění tabulek daty.  
  
- Naplňte <xref:System.Data.DataSet> tabulky daty z existujícího relačního zdroje dat pomocí `DataAdapter` .  
  
- Načtěte a zachovejte <xref:System.Data.DataSet> obsah pomocí XML. Další informace naleznete v tématu [using XML in a DataSet](using-xml-in-a-dataset.md).  
  
 Silné typy <xref:System.Data.DataSet> lze také přenést pomocí webové služby XML. Návrh je <xref:System.Data.DataSet> ideální pro přenos dat pomocí webových služeb XML. Přehled webových služeb XML najdete v tématu [Přehled webových služeb XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w9fdtx28(v=vs.100)). Příklad použití <xref:System.Data.DataSet> webové služby XML naleznete v tématu [spotřebovávání datové sady z webové služby XML](consuming-a-dataset-from-an-xml-web-service.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Vytvoření datové sady](creating-a-dataset.md)  
 Popisuje syntaxi pro vytvoření instance <xref:System.Data.DataSet> .  
  
 [Přidání datové tabulky do datové sady](adding-a-datatable-to-a-dataset.md)  
 Popisuje, jak vytvořit a přidat tabulky a sloupce do <xref:System.Data.DataSet> .  
  
 [Přidání datových relací](adding-datarelations.md)  
 Popisuje, jak vytvořit relace mezi tabulkami v <xref:System.Data.DataSet> .  
  
 [Navigace v datových relacích](navigating-datarelations.md)  
 Popisuje, jak použít relace mezi tabulkami v <xref:System.Data.DataSet> k vrácení podřízených nebo nadřazených řádků relace typu nadřazený-podřízený.  
  
 [Slučování obsahu datové sady](merging-dataset-contents.md)  
 Popisuje, jak sloučit obsah jednoho <xref:System.Data.DataSet> , <xref:System.Data.DataTable> nebo <xref:System.Data.DataRow> pole do jiného <xref:System.Data.DataSet> .  
  
 [Kopírování obsahu datové sady](copying-dataset-contents.md)  
 Popisuje, jak vytvořit kopii <xref:System.Data.DataSet> , která může obsahovat schéma i zadaná data.  
  
 [Zpracování událostí datové sady](handling-dataset-events.md)  
 Popisuje události <xref:System.Data.DataSet> a, jak je používat.  
  
 [Typové datové sady](typed-datasets.md)  
 Popisuje <xref:System.Data.DataSet> , co je typu a jak ho vytvořit a použít.  
  
 [Datové tabulky](datatables.md)  
 Popisuje, jak vytvořit <xref:System.Data.DataTable> , definovat schéma a manipulovat s daty.  
  
 [Čtečky datových tabulek](datatablereaders.md)  
 Popisuje, jak vytvořit a použít <xref:System.Data.DataTableReader> .  
  
 [Zobrazení dat](dataviews.md)  
 Popisuje, jak vytvořit a pracovat s `DataViews` událostmi a pracovat s nimi <xref:System.Data.DataView> .  
  
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
  
## <a name="see-also"></a>Viz také

- [ADO.NET](../index.md)
- [Přehled ADO.NET](../ado-net-overview.md)
