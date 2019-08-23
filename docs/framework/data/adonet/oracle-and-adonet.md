---
title: Oracle a ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
ms.openlocfilehash: 381f796bec31bece354001ad46bf5079381d1b3d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914548"
---
# <a name="oracle-and-adonet"></a><span data-ttu-id="a6aa8-102">Oracle a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a6aa8-102">Oracle and ADO.NET</span></span>
> [!NOTE]
> <span data-ttu-id="a6aa8-103">Typy v <xref:System.Data.OracleClient> jsou zastaralé.</span><span class="sxs-lookup"><span data-stu-id="a6aa8-103">The types in <xref:System.Data.OracleClient> are deprecated.</span></span> <span data-ttu-id="a6aa8-104">Typy zůstanou podporované v aktuální verzi rozhraní of.NET Framework, ale v budoucí verzi se odeberou.</span><span class="sxs-lookup"><span data-stu-id="a6aa8-104">The types remain supported in the current version of.NET Framework but will be removed in a future release.</span></span> <span data-ttu-id="a6aa8-105">Microsoft doporučuje, abyste použili poskytovatele Oracle od jiného výrobce.</span><span class="sxs-lookup"><span data-stu-id="a6aa8-105">Microsoft recommends that you use a third-party Oracle provider.</span></span>  
  
 <span data-ttu-id="a6aa8-106">Tato část popisuje funkce a chování, které jsou specifické pro Zprostředkovatel dat .NET Framework pro Oracle.</span><span class="sxs-lookup"><span data-stu-id="a6aa8-106">This section describes features and behaviors that are specific to the .NET Framework Data Provider for Oracle.</span></span>  
  
 <span data-ttu-id="a6aa8-107">Zprostředkovatel dat .NET Framework pro Oracle poskytuje přístup k databázi Oracle pomocí rozhraní Oracle Call Interface (OCI), které poskytuje klientský software Oracle.</span><span class="sxs-lookup"><span data-stu-id="a6aa8-107">The .NET Framework Data Provider for Oracle provides access to an Oracle database using the Oracle Call Interface (OCI) as provided by Oracle Client software.</span></span> <span data-ttu-id="a6aa8-108">Funkce poskytovatele dat je navržena tak, aby byla podobná poskytovateli .NET Framework dat pro SQL Server, OLE DB a ODBC.</span><span class="sxs-lookup"><span data-stu-id="a6aa8-108">The functionality of the data provider is designed to be similar to that of the .NET Framework data providers for SQL Server, OLE DB, and ODBC.</span></span>  
  
 <span data-ttu-id="a6aa8-109">Chcete-li použít Zprostředkovatel dat .NET Framework pro Oracle, musí aplikace odkazovat na <xref:System.Data.OracleClient> obor názvů následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="a6aa8-109">To use the .NET Framework Data Provider for Oracle, an application must reference the <xref:System.Data.OracleClient> namespace as follows:</span></span>  
  
```vb  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data.OracleClient;  
```  
  
 <span data-ttu-id="a6aa8-110">Při kompilaci kódu je také nutné zahrnout odkaz na knihovnu DLL.</span><span class="sxs-lookup"><span data-stu-id="a6aa8-110">You also must include a reference to the DLL when you compile your code.</span></span> <span data-ttu-id="a6aa8-111">Například pokud kompilujete C# program, váš příkazový řádek by měl obsahovat:</span><span class="sxs-lookup"><span data-stu-id="a6aa8-111">For example, if you are compiling a C# program, your command line should include:</span></span>  
  
```  
csc /r:System.Data.OracleClient.dll  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="a6aa8-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="a6aa8-112">In This Section</span></span>  
 [<span data-ttu-id="a6aa8-113">Požadavky na systém</span><span class="sxs-lookup"><span data-stu-id="a6aa8-113">System Requirements</span></span>](../../../../docs/framework/data/adonet/system-requirements-for-the-dotnet-data-provider-for-oracle.md)  
 <span data-ttu-id="a6aa8-114">Popisuje požadavky na použití Zprostředkovatel dat .NET Framework pro Oracle a popisuje několik problémů, které je potřeba při použití použít.</span><span class="sxs-lookup"><span data-stu-id="a6aa8-114">Describes requirements for using the .NET Framework Data Provider for Oracle, and describes a number of issues to be aware when using it.</span></span>  
  
 [<span data-ttu-id="a6aa8-115">Soubory Oracle BFILE</span><span class="sxs-lookup"><span data-stu-id="a6aa8-115">Oracle BFILEs</span></span>](../../../../docs/framework/data/adonet/oracle-bfiles.md)  
 <span data-ttu-id="a6aa8-116"><xref:System.Data.OracleClient.OracleBFile> Popisuje třídu, která se používá pro práci s datovým typem Oracle BFILE.</span><span class="sxs-lookup"><span data-stu-id="a6aa8-116">Describes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle BFILE data type.</span></span>  
  
 [<span data-ttu-id="a6aa8-117">Soubory Oracle LOB</span><span class="sxs-lookup"><span data-stu-id="a6aa8-117">Oracle LOBs</span></span>](../../../../docs/framework/data/adonet/oracle-lobs.md)  
 <span data-ttu-id="a6aa8-118"><xref:System.Data.OracleClient.OracleLob> Popisuje třídu, která se používá pro práci s datovými typy společnosti Oracle LOB.</span><span class="sxs-lookup"><span data-stu-id="a6aa8-118">Describes the <xref:System.Data.OracleClient.OracleLob> class, which is used to work with Oracle LOB data types.</span></span>  
  
 [<span data-ttu-id="a6aa8-119">Soubory Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="a6aa8-119">Oracle REF CURSORs</span></span>](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)  
 <span data-ttu-id="a6aa8-120">Popisuje podporu pro datový typ referenčního kurzoru Oracle REF.</span><span class="sxs-lookup"><span data-stu-id="a6aa8-120">Describes support for the Oracle REF CURSOR data type.</span></span>  
  
 [<span data-ttu-id="a6aa8-121">Typy Oracle</span><span class="sxs-lookup"><span data-stu-id="a6aa8-121">OracleTypes</span></span>](../../../../docs/framework/data/adonet/oracletypes.md)  
 <span data-ttu-id="a6aa8-122">Popisuje struktury, které můžete použít pro práci s datovými typy Oracle <xref:System.Data.OracleClient.OracleNumber> , <xref:System.Data.OracleClient.OracleString>včetně a.</span><span class="sxs-lookup"><span data-stu-id="a6aa8-122">Describes structures you can use to work with Oracle data types, including <xref:System.Data.OracleClient.OracleNumber> and <xref:System.Data.OracleClient.OracleString>.</span></span>  
  
 [<span data-ttu-id="a6aa8-123">Sekvence Oracle</span><span class="sxs-lookup"><span data-stu-id="a6aa8-123">Oracle Sequences</span></span>](../../../../docs/framework/data/adonet/oracle-sequences.md)  
 <span data-ttu-id="a6aa8-124">Popisuje podporu pro načtení hodnot sekvence Oracle vygenerovaných serverem klíčů.</span><span class="sxs-lookup"><span data-stu-id="a6aa8-124">Describes support for retrieving the server-generated key Oracle Sequence values.</span></span>  
  
 [<span data-ttu-id="a6aa8-125">Mapování datových typů Oracle</span><span class="sxs-lookup"><span data-stu-id="a6aa8-125">Oracle Data Type Mappings</span></span>](../../../../docs/framework/data/adonet/oracle-data-type-mappings.md)  
 <span data-ttu-id="a6aa8-126">Zobrazí seznam datových typů Oracle a jejich mapování na <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="a6aa8-126">Lists Oracle data types and their mappings to the <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 [<span data-ttu-id="a6aa8-127">Distribuované transakce Oracle</span><span class="sxs-lookup"><span data-stu-id="a6aa8-127">Oracle Distributed Transactions</span></span>](../../../../docs/framework/data/adonet/oracle-distributed-transactions.md)  
 <span data-ttu-id="a6aa8-128">Popisuje, jak <xref:System.Data.OracleClient.OracleConnection> objekt automaticky zařadí do existující distribuované transakce, pokud určuje, že je transakce aktivní.</span><span class="sxs-lookup"><span data-stu-id="a6aa8-128">Describes how the <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a6aa8-129">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="a6aa8-129">Related Sections</span></span>  
 [<span data-ttu-id="a6aa8-130">Zabezpečení aplikací ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a6aa8-130">Securing ADO.NET Applications</span></span>](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 <span data-ttu-id="a6aa8-131">Popisuje postupy zabezpečeného kódování při použití ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="a6aa8-131">Describes secure coding practices when using ADO.NET.</span></span>  
  
 [<span data-ttu-id="a6aa8-132">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="a6aa8-132">DataSets, DataTables, and DataViews</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 <span data-ttu-id="a6aa8-133">Popisuje, jak vytvořit a používat `DataSets`, `DataTables`zadat `DataSets`, a `DataViews`.</span><span class="sxs-lookup"><span data-stu-id="a6aa8-133">Describes how to create and use `DataSets`, typed `DataSets`, `DataTables`, and `DataViews`.</span></span>  
  
 [<span data-ttu-id="a6aa8-134">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a6aa8-134">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 <span data-ttu-id="a6aa8-135">Popisuje, jak pracovat s daty v ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="a6aa8-135">Describes how to work with data in ADO.NET.</span></span>  
  
 [<span data-ttu-id="a6aa8-136">SQL Server a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a6aa8-136">SQL Server and ADO.NET</span></span>](../../../../docs/framework/data/adonet/sql/index.md)  
 <span data-ttu-id="a6aa8-137">Popisuje, jak pracovat s funkcemi a funkcemi, které jsou specifické pro SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a6aa8-137">Describes how to work with features and functionality that are specific to SQL Server.</span></span>  
  
 [<span data-ttu-id="a6aa8-138">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="a6aa8-138">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 <span data-ttu-id="a6aa8-139">Popisuje obecné třídy, které umožňují napsat kód nezávislý na poskytovateli v ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="a6aa8-139">Describes generic classes that allow you to write provider-independent code in ADO.NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6aa8-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a6aa8-140">See also</span></span>

- [<span data-ttu-id="a6aa8-141">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a6aa8-141">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)
- [<span data-ttu-id="a6aa8-142">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="a6aa8-142">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
