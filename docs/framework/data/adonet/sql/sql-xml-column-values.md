---
title: Hodnoty pro sloupec SQL XML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d97ce4da-f09c-4d1e-85b7-a0ccedd7246a
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c974749ee84bf64d1912ed71ea0817227b1ea514
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="sql-xml-column-values"></a><span data-ttu-id="9cd15-102">Hodnoty pro sloupec SQL XML</span><span class="sxs-lookup"><span data-stu-id="9cd15-102">SQL XML Column Values</span></span>
[!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)]<span data-ttu-id="9cd15-103">podporuje `xml` datový typ a vývojáři mohou získat sad výsledků dotazu, včetně tohoto typu pomocí standardní chování <xref:System.Data.SqlClient.SqlCommand> třídy.</span><span class="sxs-lookup"><span data-stu-id="9cd15-103"> supports the `xml` data type, and developers can retrieve result sets including this type using standard behavior of the <xref:System.Data.SqlClient.SqlCommand> class.</span></span> <span data-ttu-id="9cd15-104">`xml` Sloupec se dá načíst stejně, jako je načíst žádný sloupec (do <xref:System.Data.SqlClient.SqlDataReader>, například), ale pokud chcete pracovat s obsahem sloupce ve formátu XML, musíte použít <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="9cd15-104">An `xml` column can be retrieved just as any column is retrieved (into a <xref:System.Data.SqlClient.SqlDataReader>, for example) but if you want to work with the content of the column as XML, you must use an <xref:System.Xml.XmlReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9cd15-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="9cd15-105">Example</span></span>  
 <span data-ttu-id="9cd15-106">Následující aplikace konzoly vybere dva řádky, každý obsahující `xml` sloupce, z **Sales.Store** tabulky v **AdventureWorks** do databáze <xref:System.Data.SqlClient.SqlDataReader> instance.</span><span class="sxs-lookup"><span data-stu-id="9cd15-106">The following console application selects two rows, each containing an `xml` column, from the **Sales.Store** table in the **AdventureWorks** database to a <xref:System.Data.SqlClient.SqlDataReader> instance.</span></span> <span data-ttu-id="9cd15-107">Pro každý řádek hodnotu `xml` sloupec je pro čtení, pomocí <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> metodu <xref:System.Data.SqlClient.SqlDataReader>.</span><span class="sxs-lookup"><span data-stu-id="9cd15-107">For each row, the value of the `xml` column is read using the <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> method of <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="9cd15-108">Hodnota je uložena v <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="9cd15-108">The value is stored in an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="9cd15-109">Všimněte si, že je nutné použít <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> místo <xref:System.Data.IDataRecord.GetValue%2A> metoda, pokud chcete nastavit obsah na <xref:System.Data.SqlTypes.SqlXml> proměnné. <xref:System.Data.IDataRecord.GetValue%2A> vrací hodnotu `xml` sloupec jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="9cd15-109">Note that you must use <xref:System.Data.SqlClient.SqlDataReader.GetSqlXml%2A> rather than the <xref:System.Data.IDataRecord.GetValue%2A> method if you want to set the contents to a <xref:System.Data.SqlTypes.SqlXml> variable; <xref:System.Data.IDataRecord.GetValue%2A> returns the value of the `xml` column as a string.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9cd15-110">**AdventureWorks** ukázkové databáze není nainstalována ve výchozím nastavení při instalaci [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9cd15-110">The **AdventureWorks** sample database is not installed by default when you install [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9cd15-111">Můžete ho nainstalovat spuštěním [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] instalační program.</span><span class="sxs-lookup"><span data-stu-id="9cd15-111">You can install it by running [!INCLUDE[ssNoVersion](../../../../../includes/ssnoversion-md.md)] Setup.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetXmlDataReader#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetXmlDataReader/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="9cd15-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="9cd15-112">See Also</span></span>  
 <xref:System.Data.SqlTypes.SqlXml>  
 [<span data-ttu-id="9cd15-113">Data XML v systému SQL Server</span><span class="sxs-lookup"><span data-stu-id="9cd15-113">XML Data in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)  
 [<span data-ttu-id="9cd15-114">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="9cd15-114">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
