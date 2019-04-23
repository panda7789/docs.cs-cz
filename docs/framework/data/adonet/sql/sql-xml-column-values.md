---
title: Hodnoty pro sloupce SQL XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d97ce4da-f09c-4d1e-85b7-a0ccedd7246a
ms.openlocfilehash: 803357f9ae97eee2cbbf5e777dbc1210ded26ab2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59149705"
---
# <a name="sql-xml-column-values"></a><span data-ttu-id="ebe23-102">Hodnoty pro sloupce SQL XML</span><span class="sxs-lookup"><span data-stu-id="ebe23-102">SQL XML Column Values</span></span>
<span data-ttu-id="ebe23-103">Systém SQL Server podporuje `xml` datový typ, a vývojáři mohou načítat sad výsledků dotazu, včetně tohoto typu pomocí standardní chování <xref:System.Data.SqlClient.SqlCommand> třídy.</span><span class="sxs-lookup"><span data-stu-id="ebe23-103">SQL Server supports the `xml` data type, and developers can retrieve result sets including this type using standard behavior of the <xref:System.Data.SqlClient.SqlCommand> class.</span></span> <span data-ttu-id="ebe23-104">`xml` Sloupec se dá načíst stejně, jako je načten žádný sloupec (do <xref:System.Data.SqlClient.SqlDataReader>, například), ale pokud chcete pracovat s obsahem sloupci ve formátu XML, musíte použít <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="ebe23-104">An `xml` column can be retrieved just as any column is retrieved (into a <xref:System.Data.SqlClient.SqlDataReader>, for example) but if you want to work with the content of the column as XML, you must use an <xref:System.Xml.XmlReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ebe23-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="ebe23-105">Example</span></span>  
 <span data-ttu-id="ebe23-106">Vybere dva řádky, každá obsahuje následující aplikaci konzoly `xml` sloupce, z **Sales.Store** tabulku v **AdventureWorks** do databáze <xref:System.Data.SqlClient.SqlDataReader> instance.</span><span class="sxs-lookup"><span data-stu-id="ebe23-106">The following console application selects two rows, each containing an `xml` column, from the **Sales.Store** table in the **AdventureWorks** database to a <xref:System.Data.SqlClient.SqlDataReader> instance.</span></span> <span data-ttu-id="ebe23-107">Pro každý řádek, hodnota `xml` sloupce se načítají pomocí <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> metoda <xref:System.Data.SqlClient.SqlDataReader>.</span><span class="sxs-lookup"><span data-stu-id="ebe23-107">For each row, the value of the `xml` column is read using the <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> method of <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="ebe23-108">Hodnota je uložena v <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="ebe23-108">The value is stored in an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="ebe23-109">Všimněte si, že je nutné použít <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> místo <xref:System.Data.IDataRecord.GetValue%2A> metodu, pokud chcete nastavit na obsah <xref:System.Data.SqlTypes.SqlXml> proměnné. <xref:System.Data.IDataRecord.GetValue%2A> vrací hodnotu `xml` sloupce jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="ebe23-109">Note that you must use <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> rather than the <xref:System.Data.IDataRecord.GetValue%2A> method if you want to set the contents to a <xref:System.Data.SqlTypes.SqlXml> variable; <xref:System.Data.IDataRecord.GetValue%2A> returns the value of the `xml` column as a string.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ebe23-110">**AdventureWorks** ukázkovou databázi není nainstalovaný ve výchozím nastavení při instalaci systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ebe23-110">The **AdventureWorks** sample database is not installed by default when you install SQL Server.</span></span> <span data-ttu-id="ebe23-111">Můžete ho nainstalovat spuštěním instalační program systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ebe23-111">You can install it by running SQL Server Setup.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ebe23-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ebe23-112">See also</span></span>

- <xref:System.Data.SqlTypes.SqlXml>
- [<span data-ttu-id="ebe23-113">Data XML na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="ebe23-113">XML Data in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)
- [<span data-ttu-id="ebe23-114">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="ebe23-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
