---
title: Oracle a ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
ms.openlocfilehash: ccfe40f218e3f09de53d6cb596a31b2520d9ff9b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783470"
---
# <a name="oracle-and-adonet"></a><span data-ttu-id="f2d0f-102">Oracle a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f2d0f-102">Oracle and ADO.NET</span></span>
> [!NOTE]
> <span data-ttu-id="f2d0f-103">Typy v <xref:System.Data.OracleClient> jsou zastaralé.</span><span class="sxs-lookup"><span data-stu-id="f2d0f-103">The types in <xref:System.Data.OracleClient> are deprecated.</span></span> <span data-ttu-id="f2d0f-104">Typy zůstanou podporované v aktuální verzi rozhraní of.NET Framework, ale v budoucí verzi se odeberou.</span><span class="sxs-lookup"><span data-stu-id="f2d0f-104">The types remain supported in the current version of.NET Framework but will be removed in a future release.</span></span> <span data-ttu-id="f2d0f-105">Microsoft doporučuje, abyste použili poskytovatele Oracle od jiného výrobce.</span><span class="sxs-lookup"><span data-stu-id="f2d0f-105">Microsoft recommends that you use a third-party Oracle provider.</span></span>  
  
 <span data-ttu-id="f2d0f-106">Tato část popisuje funkce a chování, které jsou specifické pro Zprostředkovatel dat .NET Framework pro Oracle.</span><span class="sxs-lookup"><span data-stu-id="f2d0f-106">This section describes features and behaviors that are specific to the .NET Framework Data Provider for Oracle.</span></span>  
  
 <span data-ttu-id="f2d0f-107">Zprostředkovatel dat .NET Framework pro Oracle poskytuje přístup k databázi Oracle pomocí rozhraní Oracle Call Interface (OCI), které poskytuje klientský software Oracle.</span><span class="sxs-lookup"><span data-stu-id="f2d0f-107">The .NET Framework Data Provider for Oracle provides access to an Oracle database using the Oracle Call Interface (OCI) as provided by Oracle Client software.</span></span> <span data-ttu-id="f2d0f-108">Funkce poskytovatele dat je navržena tak, aby byla podobná poskytovateli .NET Framework dat pro SQL Server, OLE DB a ODBC.</span><span class="sxs-lookup"><span data-stu-id="f2d0f-108">The functionality of the data provider is designed to be similar to that of the .NET Framework data providers for SQL Server, OLE DB, and ODBC.</span></span>  
  
 <span data-ttu-id="f2d0f-109">Chcete-li použít Zprostředkovatel dat .NET Framework pro Oracle, musí aplikace odkazovat na <xref:System.Data.OracleClient> obor názvů následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="f2d0f-109">To use the .NET Framework Data Provider for Oracle, an application must reference the <xref:System.Data.OracleClient> namespace as follows:</span></span>  
  
```vb  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data.OracleClient;  
```  
  
 <span data-ttu-id="f2d0f-110">Při kompilaci kódu je také nutné zahrnout odkaz na knihovnu DLL.</span><span class="sxs-lookup"><span data-stu-id="f2d0f-110">You also must include a reference to the DLL when you compile your code.</span></span> <span data-ttu-id="f2d0f-111">Například pokud kompilujete C# program, váš příkazový řádek by měl obsahovat:</span><span class="sxs-lookup"><span data-stu-id="f2d0f-111">For example, if you are compiling a C# program, your command line should include:</span></span>  
  
```  
csc /r:System.Data.OracleClient.dll  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="f2d0f-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="f2d0f-112">In This Section</span></span>  
 [<span data-ttu-id="f2d0f-113">Požadavky na systém</span><span class="sxs-lookup"><span data-stu-id="f2d0f-113">System Requirements</span></span>](system-requirements-for-the-dotnet-data-provider-for-oracle.md)  
 <span data-ttu-id="f2d0f-114">Popisuje požadavky na použití Zprostředkovatel dat .NET Framework pro Oracle a popisuje několik problémů, které je potřeba při použití použít.</span><span class="sxs-lookup"><span data-stu-id="f2d0f-114">Describes requirements for using the .NET Framework Data Provider for Oracle, and describes a number of issues to be aware when using it.</span></span>  
  
 [<span data-ttu-id="f2d0f-115">Soubory Oracle BFILE</span><span class="sxs-lookup"><span data-stu-id="f2d0f-115">Oracle BFILEs</span></span>](oracle-bfiles.md)  
 <span data-ttu-id="f2d0f-116"><xref:System.Data.OracleClient.OracleBFile> Popisuje třídu, která se používá pro práci s datovým typem Oracle BFILE.</span><span class="sxs-lookup"><span data-stu-id="f2d0f-116">Describes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle BFILE data type.</span></span>  
  
 [<span data-ttu-id="f2d0f-117">Soubory Oracle LOB</span><span class="sxs-lookup"><span data-stu-id="f2d0f-117">Oracle LOBs</span></span>](oracle-lobs.md)  
 <span data-ttu-id="f2d0f-118"><xref:System.Data.OracleClient.OracleLob> Popisuje třídu, která se používá pro práci s datovými typy společnosti Oracle LOB.</span><span class="sxs-lookup"><span data-stu-id="f2d0f-118">Describes the <xref:System.Data.OracleClient.OracleLob> class, which is used to work with Oracle LOB data types.</span></span>  
  
 [<span data-ttu-id="f2d0f-119">Soubory Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="f2d0f-119">Oracle REF CURSORs</span></span>](oracle-ref-cursors.md)  
 <span data-ttu-id="f2d0f-120">Popisuje podporu pro datový typ referenčního kurzoru Oracle REF.</span><span class="sxs-lookup"><span data-stu-id="f2d0f-120">Describes support for the Oracle REF CURSOR data type.</span></span>  
  
 [<span data-ttu-id="f2d0f-121">Typy Oracle</span><span class="sxs-lookup"><span data-stu-id="f2d0f-121">OracleTypes</span></span>](oracletypes.md)  
 <span data-ttu-id="f2d0f-122">Popisuje struktury, které můžete použít pro práci s datovými typy Oracle <xref:System.Data.OracleClient.OracleNumber> , <xref:System.Data.OracleClient.OracleString>včetně a.</span><span class="sxs-lookup"><span data-stu-id="f2d0f-122">Describes structures you can use to work with Oracle data types, including <xref:System.Data.OracleClient.OracleNumber> and <xref:System.Data.OracleClient.OracleString>.</span></span>  
  
 [<span data-ttu-id="f2d0f-123">Sekvence Oracle</span><span class="sxs-lookup"><span data-stu-id="f2d0f-123">Oracle Sequences</span></span>](oracle-sequences.md)  
 <span data-ttu-id="f2d0f-124">Popisuje podporu pro načtení hodnot sekvence Oracle vygenerovaných serverem klíčů.</span><span class="sxs-lookup"><span data-stu-id="f2d0f-124">Describes support for retrieving the server-generated key Oracle Sequence values.</span></span>  
  
 [<span data-ttu-id="f2d0f-125">Mapování datových typů Oracle</span><span class="sxs-lookup"><span data-stu-id="f2d0f-125">Oracle Data Type Mappings</span></span>](oracle-data-type-mappings.md)  
 <span data-ttu-id="f2d0f-126">Zobrazí seznam datových typů Oracle a jejich mapování na <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="f2d0f-126">Lists Oracle data types and their mappings to the <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 [<span data-ttu-id="f2d0f-127">Distribuované transakce Oracle</span><span class="sxs-lookup"><span data-stu-id="f2d0f-127">Oracle Distributed Transactions</span></span>](oracle-distributed-transactions.md)  
 <span data-ttu-id="f2d0f-128">Popisuje, jak <xref:System.Data.OracleClient.OracleConnection> objekt automaticky zařadí do existující distribuované transakce, pokud určuje, že je transakce aktivní.</span><span class="sxs-lookup"><span data-stu-id="f2d0f-128">Describes how the <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f2d0f-129">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="f2d0f-129">Related Sections</span></span>  
 [<span data-ttu-id="f2d0f-130">Zabezpečení aplikací ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f2d0f-130">Securing ADO.NET Applications</span></span>](securing-ado-net-applications.md)  
 <span data-ttu-id="f2d0f-131">Popisuje postupy zabezpečeného kódování při použití ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="f2d0f-131">Describes secure coding practices when using ADO.NET.</span></span>  
  
 [<span data-ttu-id="f2d0f-132">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="f2d0f-132">DataSets, DataTables, and DataViews</span></span>](./dataset-datatable-dataview/index.md)  
 <span data-ttu-id="f2d0f-133">Popisuje, jak vytvořit a používat `DataSets`, `DataTables`zadat `DataSets`, a `DataViews`.</span><span class="sxs-lookup"><span data-stu-id="f2d0f-133">Describes how to create and use `DataSets`, typed `DataSets`, `DataTables`, and `DataViews`.</span></span>  
  
 [<span data-ttu-id="f2d0f-134">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f2d0f-134">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)  
 <span data-ttu-id="f2d0f-135">Popisuje, jak pracovat s daty v ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="f2d0f-135">Describes how to work with data in ADO.NET.</span></span>  
  
 [<span data-ttu-id="f2d0f-136">SQL Server a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f2d0f-136">SQL Server and ADO.NET</span></span>](./sql/index.md)  
 <span data-ttu-id="f2d0f-137">Popisuje, jak pracovat s funkcemi a funkcemi, které jsou specifické pro SQL Server.</span><span class="sxs-lookup"><span data-stu-id="f2d0f-137">Describes how to work with features and functionality that are specific to SQL Server.</span></span>  
  
 [<span data-ttu-id="f2d0f-138">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="f2d0f-138">DbProviderFactories</span></span>](dbproviderfactories.md)  
 <span data-ttu-id="f2d0f-139">Popisuje obecné třídy, které umožňují napsat kód nezávislý na poskytovateli v ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="f2d0f-139">Describes generic classes that allow you to write provider-independent code in ADO.NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2d0f-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f2d0f-140">See also</span></span>

- [<span data-ttu-id="f2d0f-141">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f2d0f-141">ADO.NET</span></span>](index.md)
- [<span data-ttu-id="f2d0f-142">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f2d0f-142">ADO.NET Overview</span></span>](ado-net-overview.md)
