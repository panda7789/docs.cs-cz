---
title: Datové typy SQL Serveru a ADO.NET
titleSuffix: ''
ms.date: 03/30/2017
ms.assetid: 81b43550-23e8-43bb-b460-7eb8ac825c33
ms.openlocfilehash: f727c69b1dd5c23c6a89911005256de70255fd4c
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452328"
---
# <a name="sql-server-data-types-and-adonet"></a><span data-ttu-id="d13c1-102">Datové typy SQL Serveru a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d13c1-102">SQL Server Data Types and ADO.NET</span></span>
<span data-ttu-id="d13c1-103">SQL Server a rozhraní .NET Framework jsou založeny na jiný typ systémy, které může způsobit ztrátu dat.</span><span class="sxs-lookup"><span data-stu-id="d13c1-103">SQL Server and the .NET Framework are based on different type systems, which can result in potential data loss.</span></span> <span data-ttu-id="d13c1-104">Aby se zajistila integrita dat, .NET Framework Zprostředkovatel dat pro SQL Server (<xref:System.Data.SqlClient>) poskytují typové přístupové metody pro práci s SQL Server daty.</span><span class="sxs-lookup"><span data-stu-id="d13c1-104">To preserve data integrity, the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) provides typed accessor methods for working with SQL Server data.</span></span> <span data-ttu-id="d13c1-105">Výčty v třídách <xref:System.Data.SqlDbType> lze použít k určení <xref:System.Data.SqlClient.SqlParameter> datových typů.</span><span class="sxs-lookup"><span data-stu-id="d13c1-105">You can use the enumerations in the <xref:System.Data.SqlDbType> classes to specify <xref:System.Data.SqlClient.SqlParameter> data types.</span></span>  
  
 <span data-ttu-id="d13c1-106">Další informace a tabulku, která popisuje mapování datových typů mezi SQL Server a .NET Framework datových typů naleznete v tématu [SQL Server mapování datových typů](../sql-server-data-type-mappings.md).</span><span class="sxs-lookup"><span data-stu-id="d13c1-106">For more information and a table that describes the data type mappings between SQL Server and .NET Framework data types, see [SQL Server Data Type Mappings](../sql-server-data-type-mappings.md).</span></span>  
  
 <span data-ttu-id="d13c1-107">SQL Server 2008 zavádí nové datové typy, které jsou navržené tak, aby vyhovovaly obchodním potřebám pro práci s daty a časem, strukturovanými, částečně strukturovanými a nestrukturovanými daty.</span><span class="sxs-lookup"><span data-stu-id="d13c1-107">SQL Server 2008 introduces new data types that are designed to meet business needs to work with date and time, structured, semi-structured, and unstructured data.</span></span> <span data-ttu-id="d13c1-108">Ty jsou popsány v SQL Server 2008 Knihy online.</span><span class="sxs-lookup"><span data-stu-id="d13c1-108">These are documented in SQL Server 2008 Books Online.</span></span>  
  
 <span data-ttu-id="d13c1-109">SQL Server datové typy, které jsou k dispozici pro použití ve vaší aplikaci, závisí na verzi SQL Server, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="d13c1-109">The SQL Server data types that are available for use in your application depends on the version of SQL Server that you are using.</span></span> <span data-ttu-id="d13c1-110">Další informace najdete v příslušné verzi SQL Server Knihy online v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="d13c1-110">For more information, see the relevant version of SQL Server Books Online in the following table.</span></span>  
  
 <span data-ttu-id="d13c1-111">**Dokumentace SQL Serveru**</span><span class="sxs-lookup"><span data-stu-id="d13c1-111">**SQL Server documentation**</span></span>  
  
1. [<span data-ttu-id="d13c1-112">Datové typy (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="d13c1-112">Data Types (Transact-SQL)</span></span>](/sql/t-sql/data-types/data-types-transact-sql)  
  
## <a name="in-this-section"></a><span data-ttu-id="d13c1-113">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="d13c1-113">In This Section</span></span>  
 [<span data-ttu-id="d13c1-114">SqlTypes a datová sada</span><span class="sxs-lookup"><span data-stu-id="d13c1-114">SqlTypes and the DataSet</span></span>](sqltypes-and-the-dataset.md)  
 <span data-ttu-id="d13c1-115">Popisuje podporu typu pro `SqlTypes` v `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="d13c1-115">Describes type support for `SqlTypes` in the `DataSet`.</span></span>  
  
 [<span data-ttu-id="d13c1-116">Zpracování hodnot null</span><span class="sxs-lookup"><span data-stu-id="d13c1-116">Handling Null Values</span></span>](handling-null-values.md)  
 <span data-ttu-id="d13c1-117">Ukazuje, jak pracovat s hodnotami null a s logikou se třemi hodnotami.</span><span class="sxs-lookup"><span data-stu-id="d13c1-117">Demonstrates how to work with null values and three-valued logic.</span></span>  
  
 [<span data-ttu-id="d13c1-118">Porovnání hodnoty GUID a uniqueidentifier</span><span class="sxs-lookup"><span data-stu-id="d13c1-118">Comparing GUID and uniqueidentifier Values</span></span>](comparing-guid-and-uniqueidentifier-values.md)  
 <span data-ttu-id="d13c1-119">Ukazuje, jak pracovat s hodnotami GUID a uniqueidentifier v SQL Server a .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d13c1-119">Demonstrates how to work with GUID and uniqueidentifier values in SQL Server and the .NET Framework.</span></span>  
  
 [<span data-ttu-id="d13c1-120">Kalendářní a časová data</span><span class="sxs-lookup"><span data-stu-id="d13c1-120">Date and Time Data</span></span>](date-and-time-data.md)  
 <span data-ttu-id="d13c1-121">Popisuje způsob použití nových datových typů data a času zavedených v SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="d13c1-121">Describes how to use the new date and time data types introduced in SQL Server 2008.</span></span>  
  
 [<span data-ttu-id="d13c1-122">Velké uživatelsky definované typy</span><span class="sxs-lookup"><span data-stu-id="d13c1-122">Large UDTs</span></span>](large-udts.md)  
 <span data-ttu-id="d13c1-123">Ukazuje, jak načíst data z velké hodnoty UDT představené v SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="d13c1-123">Demonstrates how to retrieve data from large value UDTs introduced in SQL Server 2008.</span></span>  
  
 [<span data-ttu-id="d13c1-124">Data XML na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="d13c1-124">XML Data in SQL Server</span></span>](xml-data-in-sql-server.md)  
 <span data-ttu-id="d13c1-125">Popisuje, jak pracovat s daty XML načtenými z SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d13c1-125">Describes how to work with XML data retrieved from SQL Server.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d13c1-126">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="d13c1-126">Reference</span></span>  
 <xref:System.Data.DataSet>  
 <span data-ttu-id="d13c1-127">Popisuje třídu `DataSet` a všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="d13c1-127">Describes the `DataSet` class and all of its members.</span></span>  
  
 <xref:System.Data.SqlTypes>  
 <span data-ttu-id="d13c1-128">Popisuje obor názvů `SqlTypes` a všechny jeho členy.</span><span class="sxs-lookup"><span data-stu-id="d13c1-128">Describes the `SqlTypes` namespace and all of its members.</span></span>  
  
 <xref:System.Data.SqlDbType>  
 <span data-ttu-id="d13c1-129">Popisuje výčet `SqlDbType` a všechny jeho členy.</span><span class="sxs-lookup"><span data-stu-id="d13c1-129">Describes the `SqlDbType` enumeration and all of its members.</span></span>  
  
 <xref:System.Data.DbType>  
 <span data-ttu-id="d13c1-130">Popisuje výčet `DbType` a všechny jeho členy.</span><span class="sxs-lookup"><span data-stu-id="d13c1-130">Describes the `DbType` enumeration and all of its members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d13c1-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="d13c1-131">See also</span></span>

- [<span data-ttu-id="d13c1-132">Mapování datových typů SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="d13c1-132">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="d13c1-133">Konfigurace parametrů a datové typy parametrů</span><span class="sxs-lookup"><span data-stu-id="d13c1-133">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="d13c1-134">Parametry s hodnotami v tabulkách</span><span class="sxs-lookup"><span data-stu-id="d13c1-134">Table-Valued Parameters</span></span>](table-valued-parameters.md)
- [<span data-ttu-id="d13c1-135">Binární a vysoké hodnoty na SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="d13c1-135">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)
- [<span data-ttu-id="d13c1-136">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d13c1-136">ADO.NET Overview</span></span>](../ado-net-overview.md)
