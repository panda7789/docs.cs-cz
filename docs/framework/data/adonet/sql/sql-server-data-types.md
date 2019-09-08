---
title: Datové typy SQL Serveru a ADO.NET
ms.date: 03/30/2017
ms.assetid: 81b43550-23e8-43bb-b460-7eb8ac825c33
ms.openlocfilehash: 642fe0d541aca01d6ffb2d9279c4d0fa91eadb63
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780849"
---
# <a name="sql-server-data-types-and-adonet"></a><span data-ttu-id="8c904-102">Datové typy SQL Serveru a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8c904-102">SQL Server Data Types and ADO.NET</span></span>
<span data-ttu-id="8c904-103">SQL Server a rozhraní .NET Framework jsou založeny na jiný typ systémy, které může způsobit ztrátu dat.</span><span class="sxs-lookup"><span data-stu-id="8c904-103">SQL Server and the .NET Framework are based on different type systems, which can result in potential data loss.</span></span> <span data-ttu-id="8c904-104">Aby se zajistila integrita dat, poskytuje .NET Framework Zprostředkovatel dat<xref:System.Data.SqlClient>pro SQL Server () typové přístupové metody pro práci s SQL Servermi daty.</span><span class="sxs-lookup"><span data-stu-id="8c904-104">To preserve data integrity, the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) provides typed accessor methods for working with SQL Server data.</span></span> <span data-ttu-id="8c904-105">Můžete použít výčty ve <xref:System.Data.SqlDbType> třídách k určení <xref:System.Data.SqlClient.SqlParameter> datových typů.</span><span class="sxs-lookup"><span data-stu-id="8c904-105">You can use the enumerations in the <xref:System.Data.SqlDbType> classes to specify <xref:System.Data.SqlClient.SqlParameter> data types.</span></span>  
  
 <span data-ttu-id="8c904-106">Další informace a tabulku, která popisuje mapování datových typů mezi SQL Server a .NET Framework datových typů naleznete v tématu [SQL Server mapování datových typů](../sql-server-data-type-mappings.md).</span><span class="sxs-lookup"><span data-stu-id="8c904-106">For more information and a table that describes the data type mappings between SQL Server and .NET Framework data types, see [SQL Server Data Type Mappings](../sql-server-data-type-mappings.md).</span></span>  
  
 <span data-ttu-id="8c904-107">SQL Server 2008 zavádí nové datové typy, které jsou navržené tak, aby vyhovovaly obchodním potřebám pro práci s daty a časem, strukturovanými, částečně strukturovanými a nestrukturovanými daty.</span><span class="sxs-lookup"><span data-stu-id="8c904-107">SQL Server 2008 introduces new data types that are designed to meet business needs to work with date and time, structured, semi-structured, and unstructured data.</span></span> <span data-ttu-id="8c904-108">Ty jsou popsány v SQL Server 2008 Knihy online.</span><span class="sxs-lookup"><span data-stu-id="8c904-108">These are documented in SQL Server 2008 Books Online.</span></span>  
  
 <span data-ttu-id="8c904-109">SQL Server datové typy, které jsou k dispozici pro použití ve vaší aplikaci, závisí na verzi SQL Server, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="8c904-109">The SQL Server data types that are available for use in your application depends on the version of SQL Server that you are using.</span></span> <span data-ttu-id="8c904-110">Další informace najdete v příslušné verzi SQL Server Knihy online v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="8c904-110">For more information, see the relevant version of SQL Server Books Online in the following table.</span></span>  
  
 <span data-ttu-id="8c904-111">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="8c904-111">**SQL Server Books Online**</span></span>  
  
1. [<span data-ttu-id="8c904-112">Datové typy (databázový stroj)</span><span class="sxs-lookup"><span data-stu-id="8c904-112">Data Types (Database Engine)</span></span>](https://go.microsoft.com/fwlink/?LinkID=107468)  
  
## <a name="in-this-section"></a><span data-ttu-id="8c904-113">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="8c904-113">In This Section</span></span>  
 [<span data-ttu-id="8c904-114">SqlTypes a datová sada</span><span class="sxs-lookup"><span data-stu-id="8c904-114">SqlTypes and the DataSet</span></span>](sqltypes-and-the-dataset.md)  
 <span data-ttu-id="8c904-115">Popisuje podporu typu pro `SqlTypes` `DataSet`v.</span><span class="sxs-lookup"><span data-stu-id="8c904-115">Describes type support for `SqlTypes` in the `DataSet`.</span></span>  
  
 [<span data-ttu-id="8c904-116">Zpracování hodnot null</span><span class="sxs-lookup"><span data-stu-id="8c904-116">Handling Null Values</span></span>](handling-null-values.md)  
 <span data-ttu-id="8c904-117">Ukazuje, jak pracovat s hodnotami null a s logikou se třemi hodnotami.</span><span class="sxs-lookup"><span data-stu-id="8c904-117">Demonstrates how to work with null values and three-valued logic.</span></span>  
  
 [<span data-ttu-id="8c904-118">Porovnání hodnoty GUID a uniqueidentifier</span><span class="sxs-lookup"><span data-stu-id="8c904-118">Comparing GUID and uniqueidentifier Values</span></span>](comparing-guid-and-uniqueidentifier-values.md)  
 <span data-ttu-id="8c904-119">Ukazuje, jak pracovat s hodnotami GUID a uniqueidentifier v SQL Server a .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8c904-119">Demonstrates how to work with GUID and uniqueidentifier values in SQL Server and the .NET Framework.</span></span>  
  
 [<span data-ttu-id="8c904-120">Kalendářní a časová data</span><span class="sxs-lookup"><span data-stu-id="8c904-120">Date and Time Data</span></span>](date-and-time-data.md)  
 <span data-ttu-id="8c904-121">Popisuje způsob použití nových datových typů data a času zavedených v SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="8c904-121">Describes how to use the new date and time data types introduced in SQL Server 2008.</span></span>  
  
 [<span data-ttu-id="8c904-122">Velké uživatelsky definované typy</span><span class="sxs-lookup"><span data-stu-id="8c904-122">Large UDTs</span></span>](large-udts.md)  
 <span data-ttu-id="8c904-123">Ukazuje, jak načíst data z velké hodnoty UDT představené v SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="8c904-123">Demonstrates how to retrieve data from large value UDTs introduced in SQL Server 2008.</span></span>  
  
 [<span data-ttu-id="8c904-124">Data XML na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="8c904-124">XML Data in SQL Server</span></span>](xml-data-in-sql-server.md)  
 <span data-ttu-id="8c904-125">Popisuje, jak pracovat s daty XML načtenými z SQL Server.</span><span class="sxs-lookup"><span data-stu-id="8c904-125">Describes how to work with XML data retrieved from SQL Server.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="8c904-126">Reference</span><span class="sxs-lookup"><span data-stu-id="8c904-126">Reference</span></span>  
 <xref:System.Data.DataSet>  
 <span data-ttu-id="8c904-127">`DataSet` Popisuje třídu a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="8c904-127">Describes the `DataSet` class and all of its members.</span></span>  
  
 <xref:System.Data.SqlTypes>  
 <span data-ttu-id="8c904-128">`SqlTypes` Popisuje obor názvů a všechny jeho členy.</span><span class="sxs-lookup"><span data-stu-id="8c904-128">Describes the `SqlTypes` namespace and all of its members.</span></span>  
  
 <xref:System.Data.SqlDbType>  
 <span data-ttu-id="8c904-129">`SqlDbType` Popisuje výčet a všechny jeho členy.</span><span class="sxs-lookup"><span data-stu-id="8c904-129">Describes the `SqlDbType` enumeration and all of its members.</span></span>  
  
 <xref:System.Data.DbType>  
 <span data-ttu-id="8c904-130">`DbType` Popisuje výčet a všechny jeho členy.</span><span class="sxs-lookup"><span data-stu-id="8c904-130">Describes the `DbType` enumeration and all of its members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c904-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8c904-131">See also</span></span>

- [<span data-ttu-id="8c904-132">Mapování datových typů SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="8c904-132">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="8c904-133">Konfigurace parametrů a datové typy parametrů</span><span class="sxs-lookup"><span data-stu-id="8c904-133">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="8c904-134">Parametry s hodnotami v tabulkách</span><span class="sxs-lookup"><span data-stu-id="8c904-134">Table-Valued Parameters</span></span>](table-valued-parameters.md)
- [<span data-ttu-id="8c904-135">Binární a vysoké hodnoty na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="8c904-135">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="8c904-136">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8c904-136">ADO.NET Overview</span></span>](../ado-net-overview.md)
