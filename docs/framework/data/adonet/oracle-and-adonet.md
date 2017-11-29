---
title: Oracle a ADO.NET
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
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c615c985f885734800b471ee31451cfb8a4c8500
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="oracle-and-adonet"></a><span data-ttu-id="a2a03-102">Oracle a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a2a03-102">Oracle and ADO.NET</span></span>
> [!NOTE]
>  <span data-ttu-id="a2a03-103">Typy v <xref:System.Data.OracleClient> jsou zastaralé.</span><span class="sxs-lookup"><span data-stu-id="a2a03-103">The types in <xref:System.Data.OracleClient> are deprecated.</span></span> <span data-ttu-id="a2a03-104">Typy zůstanou podporované v aktuální verzi of.NET Framework, ale bude v budoucí verzi odebrána.</span><span class="sxs-lookup"><span data-stu-id="a2a03-104">The types remain supported in the current version of.NET Framework but will be removed in a future release.</span></span> <span data-ttu-id="a2a03-105">Společnost Microsoft doporučuje používat zprostředkovatele Oracle třetí strany.</span><span class="sxs-lookup"><span data-stu-id="a2a03-105">Microsoft recommends that you use a third-party Oracle provider.</span></span>  
  
 <span data-ttu-id="a2a03-106">Tato část popisuje funkce a chování, které jsou specifické pro [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatele dat pro databázi Oracle.</span><span class="sxs-lookup"><span data-stu-id="a2a03-106">This section describes features and behaviors that are specific to the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle.</span></span>  
  
 <span data-ttu-id="a2a03-107">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Zprostředkovatele dat pro databázi Oracle poskytuje přístup k databázi Oracle pomocí Oracle volání rozhraní (OCI) podle softwarem klienta Oracle.</span><span class="sxs-lookup"><span data-stu-id="a2a03-107">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle provides access to an Oracle database using the Oracle Call Interface (OCI) as provided by Oracle Client software.</span></span> <span data-ttu-id="a2a03-108">Funkce zprostředkovatele dat je navržený jako podobná [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatelé dat pro [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)], technologie OLE DB a rozhraní ODBC.</span><span class="sxs-lookup"><span data-stu-id="a2a03-108">The functionality of the data provider is designed to be similar to that of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data providers for [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)], OLE DB, and ODBC.</span></span>  
  
 <span data-ttu-id="a2a03-109">Použít [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatele dat pro databázi Oracle, aplikace musí odkazovat <xref:System.Data.OracleClient> oboru názvů následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="a2a03-109">To use the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle, an application must reference the <xref:System.Data.OracleClient> namespace as follows:</span></span>  
  
```vb  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data.OracleClient;  
```  
  
 <span data-ttu-id="a2a03-110">Můžete také musí obsahovat odkaz na knihovnu DLL při kompilaci kódu.</span><span class="sxs-lookup"><span data-stu-id="a2a03-110">You also must include a reference to the DLL when you compile your code.</span></span> <span data-ttu-id="a2a03-111">Například pokud jsou kompilace programu v C#, by měla obsahovat příkazového řádku:</span><span class="sxs-lookup"><span data-stu-id="a2a03-111">For example, if you are compiling a C# program, your command line should include:</span></span>  
  
```  
csc /r:System.Data.OracleClient.dll  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="a2a03-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="a2a03-112">In This Section</span></span>  
 [<span data-ttu-id="a2a03-113">Požadavky na systém</span><span class="sxs-lookup"><span data-stu-id="a2a03-113">System Requirements</span></span>](../../../../docs/framework/data/adonet/system-requirements-for-the-dotnet-data-provider-for-oracle.md)  
 <span data-ttu-id="a2a03-114">Popisuje požadavky pro použití [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatele dat pro databázi Oracle a popisuje řadu problémů znát při používání.</span><span class="sxs-lookup"><span data-stu-id="a2a03-114">Describes requirements for using the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle, and describes a number of issues to be aware when using it.</span></span>  
  
 [<span data-ttu-id="a2a03-115">Oracle BFILEs</span><span class="sxs-lookup"><span data-stu-id="a2a03-115">Oracle BFILEs</span></span>](../../../../docs/framework/data/adonet/oracle-bfiles.md)  
 <span data-ttu-id="a2a03-116">Popisuje <xref:System.Data.OracleClient.OracleBFile> třídy, která se používá pro práci s datovým typem Oracle BFILE.</span><span class="sxs-lookup"><span data-stu-id="a2a03-116">Describes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle BFILE data type.</span></span>  
  
 [<span data-ttu-id="a2a03-117">Objekty LOBs Oracle</span><span class="sxs-lookup"><span data-stu-id="a2a03-117">Oracle LOBs</span></span>](../../../../docs/framework/data/adonet/oracle-lobs.md)  
 <span data-ttu-id="a2a03-118">Popisuje <xref:System.Data.OracleClient.OracleLob> třídy, která se používá pro práci s datovými typy obchodní Oracle.</span><span class="sxs-lookup"><span data-stu-id="a2a03-118">Describes the <xref:System.Data.OracleClient.OracleLob> class, which is used to work with Oracle LOB data types.</span></span>  
  
 [<span data-ttu-id="a2a03-119">Kurzory REF Oracle</span><span class="sxs-lookup"><span data-stu-id="a2a03-119">Oracle REF CURSORs</span></span>](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)  
 <span data-ttu-id="a2a03-120">Popisuje podporu pro datový typ KURZORU REF Oracle.</span><span class="sxs-lookup"><span data-stu-id="a2a03-120">Describes support for the Oracle REF CURSOR data type.</span></span>  
  
 [<span data-ttu-id="a2a03-121">OracleTypes</span><span class="sxs-lookup"><span data-stu-id="a2a03-121">OracleTypes</span></span>](../../../../docs/framework/data/adonet/oracletypes.md)  
 <span data-ttu-id="a2a03-122">Popisuje struktury můžete použít pro práci s datovými typy Oracle, včetně <xref:System.Data.OracleClient.OracleNumber> a <xref:System.Data.OracleClient.OracleString>.</span><span class="sxs-lookup"><span data-stu-id="a2a03-122">Describes structures you can use to work with Oracle data types, including <xref:System.Data.OracleClient.OracleNumber> and <xref:System.Data.OracleClient.OracleString>.</span></span>  
  
 [<span data-ttu-id="a2a03-123">Pořadí Oracle</span><span class="sxs-lookup"><span data-stu-id="a2a03-123">Oracle Sequences</span></span>](../../../../docs/framework/data/adonet/oracle-sequences.md)  
 <span data-ttu-id="a2a03-124">Popisuje podporu pro načítání hodnoty klíče generované serverem Oracle pořadí.</span><span class="sxs-lookup"><span data-stu-id="a2a03-124">Describes support for retrieving the server-generated key Oracle Sequence values.</span></span>  
  
 [<span data-ttu-id="a2a03-125">Mapování datového typu Oracle</span><span class="sxs-lookup"><span data-stu-id="a2a03-125">Oracle Data Type Mappings</span></span>](../../../../docs/framework/data/adonet/oracle-data-type-mappings.md)  
 <span data-ttu-id="a2a03-126">Uvádí typy dat Oracle a jejich mapování <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="a2a03-126">Lists Oracle data types and their mappings to the <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 [<span data-ttu-id="a2a03-127">Oracle distribuovaných transakcí</span><span class="sxs-lookup"><span data-stu-id="a2a03-127">Oracle Distributed Transactions</span></span>](../../../../docs/framework/data/adonet/oracle-distributed-transactions.md)  
 <span data-ttu-id="a2a03-128">Popisuje, jak <xref:System.Data.OracleClient.OracleConnection> objekt automaticky využívá v existující distribuované transakce, pokud zjistí, že je aktivní transakce.</span><span class="sxs-lookup"><span data-stu-id="a2a03-128">Describes how the <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a2a03-129">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="a2a03-129">Related Sections</span></span>  
 [<span data-ttu-id="a2a03-130">Zabezpečení aplikací ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a2a03-130">Securing ADO.NET Applications</span></span>](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 <span data-ttu-id="a2a03-131">Popisuje postupy pro zabezpečené kódování při použití [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a2a03-131">Describes secure coding practices when using [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span></span>  
  
 [<span data-ttu-id="a2a03-132">Datové sady, DataTables a DataView</span><span class="sxs-lookup"><span data-stu-id="a2a03-132">DataSets, DataTables, and DataViews</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 <span data-ttu-id="a2a03-133">Popisuje, jak vytvořit a použít `DataSets`, typu `DataSets`, `DataTables`, a `DataViews`.</span><span class="sxs-lookup"><span data-stu-id="a2a03-133">Describes how to create and use `DataSets`, typed `DataSets`, `DataTables`, and `DataViews`.</span></span>  
  
 [<span data-ttu-id="a2a03-134">Načítání a upravovat Data v technologii ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a2a03-134">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 <span data-ttu-id="a2a03-135">Popisuje, jak pracovat s daty v ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="a2a03-135">Describes how to work with data in ADO.NET.</span></span>  
  
 [<span data-ttu-id="a2a03-136">SQL Server a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a2a03-136">SQL Server and ADO.NET</span></span>](../../../../docs/framework/data/adonet/sql/index.md)  
 <span data-ttu-id="a2a03-137">Popisuje, jak pracovat s funkcí, které jsou specifické pro [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a2a03-137">Describes how to work with features and functionality that are specific to [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="a2a03-138">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="a2a03-138">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 <span data-ttu-id="a2a03-139">Popisuje obecné třídy, které vám umožní psaní kódu nezávislé na zprostředkovatele [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a2a03-139">Describes generic classes that allow you to write provider-independent code in [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2a03-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="a2a03-140">See Also</span></span>  
 [<span data-ttu-id="a2a03-141">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a2a03-141">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)  
 [<span data-ttu-id="a2a03-142">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="a2a03-142">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
