---
title: Hodnoty pro sloupec SQL XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d97ce4da-f09c-4d1e-85b7-a0ccedd7246a
ms.openlocfilehash: 8aa33d2c4558c003d1424e118bdf512d4cafaea9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="sql-xml-column-values"></a>Hodnoty pro sloupec SQL XML
Systém SQL Server podporuje `xml` datový typ a vývojáři mohou získat sad výsledků dotazu, včetně tohoto typu pomocí standardní chování <xref:System.Data.SqlClient.SqlCommand> třídy. `xml` Sloupec se dá načíst stejně, jako je načíst žádný sloupec (do <xref:System.Data.SqlClient.SqlDataReader>, například), ale pokud chcete pracovat s obsahem sloupce ve formátu XML, musíte použít <xref:System.Xml.XmlReader>.  
  
## <a name="example"></a>Příklad  
 Následující aplikace konzoly vybere dva řádky, každý obsahující `xml` sloupce, z **Sales.Store** tabulky v **AdventureWorks** do databáze <xref:System.Data.SqlClient.SqlDataReader> instance. Pro každý řádek hodnotu `xml` sloupec je pro čtení, pomocí <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> metodu <xref:System.Data.SqlClient.SqlDataReader>. Hodnota je uložena v <xref:System.Xml.XmlReader>. Všimněte si, že je nutné použít <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> místo <xref:System.Data.IDataRecord.GetValue%2A> metoda, pokud chcete nastavit obsah na <xref:System.Data.SqlTypes.SqlXml> proměnné. <xref:System.Data.IDataRecord.GetValue%2A> vrací hodnotu `xml` sloupec jako řetězec.  
  
> [!NOTE]
>  **AdventureWorks** ukázkové databáze není nainstalována ve výchozím nastavení při instalaci systému SQL Server. Můžete ho nainstalovat tak, že spustíte instalační program SQL serveru.  
  
 [!code-csharp[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Data.SqlTypes.SqlXml>  
 [Data XML na SQL Serveru](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
