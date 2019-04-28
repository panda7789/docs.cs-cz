---
title: Hodnoty pro sloupce SQL XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d97ce4da-f09c-4d1e-85b7-a0ccedd7246a
ms.openlocfilehash: 803357f9ae97eee2cbbf5e777dbc1210ded26ab2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670128"
---
# <a name="sql-xml-column-values"></a>Hodnoty pro sloupce SQL XML
Systém SQL Server podporuje `xml` datový typ, a vývojáři mohou načítat sad výsledků dotazu, včetně tohoto typu pomocí standardní chování <xref:System.Data.SqlClient.SqlCommand> třídy. `xml` Sloupec se dá načíst stejně, jako je načten žádný sloupec (do <xref:System.Data.SqlClient.SqlDataReader>, například), ale pokud chcete pracovat s obsahem sloupci ve formátu XML, musíte použít <xref:System.Xml.XmlReader>.  
  
## <a name="example"></a>Příklad  
 Vybere dva řádky, každá obsahuje následující aplikaci konzoly `xml` sloupce, z **Sales.Store** tabulku v **AdventureWorks** do databáze <xref:System.Data.SqlClient.SqlDataReader> instance. Pro každý řádek, hodnota `xml` sloupce se načítají pomocí <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> metoda <xref:System.Data.SqlClient.SqlDataReader>. Hodnota je uložena v <xref:System.Xml.XmlReader>. Všimněte si, že je nutné použít <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> místo <xref:System.Data.IDataRecord.GetValue%2A> metodu, pokud chcete nastavit na obsah <xref:System.Data.SqlTypes.SqlXml> proměnné. <xref:System.Data.IDataRecord.GetValue%2A> vrací hodnotu `xml` sloupce jako řetězec.  
  
> [!NOTE]
>  **AdventureWorks** ukázkovou databázi není nainstalovaný ve výchozím nastavení při instalaci systému SQL Server. Můžete ho nainstalovat spuštěním instalační program systému SQL Server.  
  
 [!code-csharp[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Data.SqlTypes.SqlXml>
- [Data XML na SQL Serveru](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
