---
title: Hodnoty pro sloupce SQL XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d97ce4da-f09c-4d1e-85b7-a0ccedd7246a
ms.openlocfilehash: 03b09d3a53c725bb0e84ba6b5d98944267bc564c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780797"
---
# <a name="sql-xml-column-values"></a>Hodnoty pro sloupce SQL XML
SQL Server podporuje `xml` datový typ a vývojáři mohou načíst sady výsledků, včetně tohoto typu, pomocí standardního chování <xref:System.Data.SqlClient.SqlCommand> třídy. Sloupec lze načíst pouze v případě <xref:System.Data.SqlClient.SqlDataReader>, že je načten libovolný sloupec (například), ale pokud chcete pracovat s obsahem sloupce ve formátu XML <xref:System.Xml.XmlReader>, je nutné použít. `xml`  
  
## <a name="example"></a>Příklad  
 Následující Konzolová aplikace vybere dva řádky, z nichž každý `xml` obsahuje sloupec, z tabulky **Sales. Store** v databázi **AdventureWorks** do <xref:System.Data.SqlClient.SqlDataReader> instance. Pro každý řádek je hodnota `xml` sloupce čtena <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> pomocí metody <xref:System.Data.SqlClient.SqlDataReader>. Hodnota je uložena v <xref:System.Xml.XmlReader>. Všimněte si, že je <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> nutné použít místo <xref:System.Data.IDataRecord.GetValue%2A> metody, pokud chcete <xref:System.Data.SqlTypes.SqlXml> nastavit obsah na proměnnou. <xref:System.Data.IDataRecord.GetValue%2A> vrátí hodnotu`xml` sloupce jako řetězec.  
  
> [!NOTE]
> Ukázková databáze **AdventureWorks** není při instalaci SQL Server standardně nainstalovaná. Můžete ji nainstalovat spuštěním SQL Server instalačního programu.  
  
 [!code-csharp[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Data.SqlTypes.SqlXml>
- [Data XML na SQL Serveru](xml-data-in-sql-server.md)
- [Přehled ADO.NET](../ado-net-overview.md)
