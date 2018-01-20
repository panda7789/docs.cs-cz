---
title: "Mapování datového typu v technologii ADO.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4afab94-ada6-4c77-a73c-41f17bae6b5a
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a75914e032adf5b160724e17966b683a119b69a7
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="data-type-mappings-in-adonet"></a><span data-ttu-id="d1d29-102">Mapování datového typu v technologii ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d1d29-102">Data Type Mappings in ADO.NET</span></span>
<span data-ttu-id="d1d29-103">Rozhraní .NET Framework je založena na obecný systém typů, který definuje, jak jsou typy deklarovat, používat a spravovat v modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="d1d29-103">The .NET Framework is based on the common type system, which defines how types are declared, used, and managed in the runtime.</span></span> <span data-ttu-id="d1d29-104">Obsahuje typy hodnot a odkazové typy, které jsou odvozeny od <xref:System.Object> základní typ.</span><span class="sxs-lookup"><span data-stu-id="d1d29-104">It consists of both value types and reference types, which all derive from the <xref:System.Object> base type.</span></span> <span data-ttu-id="d1d29-105">Při práci se zdrojem dat, je datový typ odvodit z poskytovatele dat, pokud není explicitně zadané.</span><span class="sxs-lookup"><span data-stu-id="d1d29-105">When working with a data source, the data type is inferred from the data provider if it is not explicitly specified.</span></span> <span data-ttu-id="d1d29-106">Například <xref:System.Data.DataSet> je nezávislý na libovolný zdroj dat pro konkrétní objekt.</span><span class="sxs-lookup"><span data-stu-id="d1d29-106">For example, a <xref:System.Data.DataSet> object is independent of any specific data source.</span></span> <span data-ttu-id="d1d29-107">Data v `DataSet` se načítají ze zdroje dat a zachováním změn zpět do zdroje dat pomocí `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="d1d29-107">Data in a `DataSet` is retrieved from a data source, and changes are persisted back to the data source by using a `DataAdapter`.</span></span> <span data-ttu-id="d1d29-108">To znamená, že pokud `DataAdapter` doplní <xref:System.Data.DataTable> v `DataSet` s hodnotami ze zdroje dat, výsledné datové typy sloupce v `DataTable` jsou [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy místo typy, které jsou specifické pro [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dat Zprostředkovatel, který se používá k připojení ke zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="d1d29-108">This means that when a `DataAdapter` fills a <xref:System.Data.DataTable> in a `DataSet` with values from a data source, the resulting data types of the columns in the `DataTable` are [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] types, instead of types specific to the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data provider that is used to connect to the data source.</span></span>  
  
 <span data-ttu-id="d1d29-109">Podobně když `DataReader` vrátí hodnotu ze zdroje dat, výsledná hodnota je uložen v místní proměnné, která má [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typu.</span><span class="sxs-lookup"><span data-stu-id="d1d29-109">Likewise, when a `DataReader` returns a value from a data source, the resulting value is stored in a local variable that has a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] type.</span></span> <span data-ttu-id="d1d29-110">Pro oba `Fill` operace `DataAdapter` a `Get` metody `DataReader`, [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typ je odvozen z hodnota vrácená z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatele dat.</span><span class="sxs-lookup"><span data-stu-id="d1d29-110">For both the `Fill` operations of the `DataAdapter` and the `Get` methods of the `DataReader`, the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] type is inferred from the value returned from the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data provider.</span></span>  
  
 <span data-ttu-id="d1d29-111">Aniž byste museli spoléhat na odvozené datový typ, můžete použít metody typu přístupového objektu `DataReader` Pokud znáte konkrétní typ hodnoty nebyl vrácen.</span><span class="sxs-lookup"><span data-stu-id="d1d29-111">Instead of relying on the inferred data type, you can use the typed accessor methods of the `DataReader` when you know the specific type of the value being returned.</span></span> <span data-ttu-id="d1d29-112">Typové přístupových metod získáte lepší výkon a vrátila hodnotu jako konkrétní [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typu, který eliminuje potřebu další typ převodu.</span><span class="sxs-lookup"><span data-stu-id="d1d29-112">Typed accessor methods give you better performance by returning a value as a specific [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] type, which eliminates the need for additional type conversion.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d1d29-113">Hodnoty Null [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dat zprostředkovatele datové typy jsou reprezentované pomocí `DBNull.Value`.</span><span class="sxs-lookup"><span data-stu-id="d1d29-113">Null values for [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data provider data types are represented by `DBNull.Value`.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d1d29-114">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="d1d29-114">In This Section</span></span>  
 [<span data-ttu-id="d1d29-115">Mapování datových typů SQL Serveru</span><span class="sxs-lookup"><span data-stu-id="d1d29-115">SQL Server Data Type Mappings</span></span>](../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 <span data-ttu-id="d1d29-116">Seznamy odvodit mapování datového typu a data přístupových metod pro <xref:System.Data.SqlClient>.</span><span class="sxs-lookup"><span data-stu-id="d1d29-116">Lists inferred data type mappings and data accessor methods for <xref:System.Data.SqlClient>.</span></span>  
  
 [<span data-ttu-id="d1d29-117">Mapování datových typů OLE DB</span><span class="sxs-lookup"><span data-stu-id="d1d29-117">OLE DB Data Type Mappings</span></span>](../../../../docs/framework/data/adonet/ole-db-data-type-mappings.md)  
 <span data-ttu-id="d1d29-118">Seznamy odvodit mapování datového typu a data přístupových metod pro <xref:System.Data.OleDb>.</span><span class="sxs-lookup"><span data-stu-id="d1d29-118">Lists inferred data type mappings and data accessor methods for <xref:System.Data.OleDb>.</span></span>  
  
 [<span data-ttu-id="d1d29-119">Mapování datových typů ODBC</span><span class="sxs-lookup"><span data-stu-id="d1d29-119">ODBC Data Type Mappings</span></span>](../../../../docs/framework/data/adonet/odbc-data-type-mappings.md)  
 <span data-ttu-id="d1d29-120">Seznamy odvodit mapování datového typu a data přístupových metod pro <xref:System.Data.Odbc>.</span><span class="sxs-lookup"><span data-stu-id="d1d29-120">Lists inferred data type mappings and data accessor methods for <xref:System.Data.Odbc>.</span></span>  
  
 [<span data-ttu-id="d1d29-121">Mapování datových typů Oracle</span><span class="sxs-lookup"><span data-stu-id="d1d29-121">Oracle Data Type Mappings</span></span>](../../../../docs/framework/data/adonet/oracle-data-type-mappings.md)  
 <span data-ttu-id="d1d29-122">Seznamy odvodit mapování datového typu a data přístupových metod pro <xref:System.Data.OracleClient>.</span><span class="sxs-lookup"><span data-stu-id="d1d29-122">Lists inferred data type mappings and data accessor methods for <xref:System.Data.OracleClient>.</span></span>  
  
 [<span data-ttu-id="d1d29-123">Čísla s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="d1d29-123">Floating-Point Numbers</span></span>](../../../../docs/framework/data/adonet/floating-point-numbers.md)  
 <span data-ttu-id="d1d29-124">Popisuje problémy, které vývojáři často nastat při práci s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="d1d29-124">Describes issues that developers frequently encounter when working with floating-point numbers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1d29-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="d1d29-125">See Also</span></span>  
 [<span data-ttu-id="d1d29-126">Datové typy SQL Serveru a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d1d29-126">SQL Server Data Types and ADO.NET</span></span>](../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [<span data-ttu-id="d1d29-127">Konfigurace parametrů a datové typy parametrů</span><span class="sxs-lookup"><span data-stu-id="d1d29-127">Configuring Parameters and Parameter Data Types</span></span>](../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [<span data-ttu-id="d1d29-128">Načítání informací o databázovém schématu</span><span class="sxs-lookup"><span data-stu-id="d1d29-128">Retrieving Database Schema Information</span></span>](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [<span data-ttu-id="d1d29-129">Obecný systém typů</span><span class="sxs-lookup"><span data-stu-id="d1d29-129">Common Type System</span></span>](../../../../docs/standard/base-types/common-type-system.md)  
 [<span data-ttu-id="d1d29-130">Převádění typů</span><span class="sxs-lookup"><span data-stu-id="d1d29-130">Converting Types</span></span>](http://msdn.microsoft.com/library/6038316e-bdaf-4f55-8006-407f591ce156)  
 [<span data-ttu-id="d1d29-131">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="d1d29-131">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
