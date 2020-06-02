---
title: Oracle a ADO.NET
description: Seznamte se s funkcemi a chováním .NET Framework Zprostředkovatel dat pro Oracle, který poskytuje přístup k databázi Oracle pomocí rozhraní volání Oracle.
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
ms.openlocfilehash: 8757352a7444fad802ea88ba58e0fe643c86cbb8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286686"
---
# <a name="oracle-and-adonet"></a><span data-ttu-id="73bb2-103">Oracle a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="73bb2-103">Oracle and ADO.NET</span></span>
> [!NOTE]
> <span data-ttu-id="73bb2-104">Typy v <xref:System.Data.OracleClient> jsou zastaralé.</span><span class="sxs-lookup"><span data-stu-id="73bb2-104">The types in <xref:System.Data.OracleClient> are deprecated.</span></span> <span data-ttu-id="73bb2-105">Typy zůstanou podporované v aktuální verzi rozhraní of.NET Framework, ale v budoucí verzi se odeberou.</span><span class="sxs-lookup"><span data-stu-id="73bb2-105">The types remain supported in the current version of.NET Framework but will be removed in a future release.</span></span> <span data-ttu-id="73bb2-106">Microsoft doporučuje, abyste použili poskytovatele Oracle od jiného výrobce.</span><span class="sxs-lookup"><span data-stu-id="73bb2-106">Microsoft recommends that you use a third-party Oracle provider.</span></span>  
  
 <span data-ttu-id="73bb2-107">Tato část popisuje funkce a chování, které jsou specifické pro Zprostředkovatel dat .NET Framework pro Oracle.</span><span class="sxs-lookup"><span data-stu-id="73bb2-107">This section describes features and behaviors that are specific to the .NET Framework Data Provider for Oracle.</span></span>  
  
 <span data-ttu-id="73bb2-108">Zprostředkovatel dat .NET Framework pro Oracle poskytuje přístup k databázi Oracle pomocí rozhraní Oracle Call Interface (OCI), které poskytuje klientský software Oracle.</span><span class="sxs-lookup"><span data-stu-id="73bb2-108">The .NET Framework Data Provider for Oracle provides access to an Oracle database using the Oracle Call Interface (OCI) as provided by Oracle Client software.</span></span> <span data-ttu-id="73bb2-109">Funkce poskytovatele dat je navržena tak, aby byla podobná poskytovateli .NET Framework dat pro SQL Server, OLE DB a ODBC.</span><span class="sxs-lookup"><span data-stu-id="73bb2-109">The functionality of the data provider is designed to be similar to that of the .NET Framework data providers for SQL Server, OLE DB, and ODBC.</span></span>  
  
 <span data-ttu-id="73bb2-110">Chcete-li použít Zprostředkovatel dat .NET Framework pro Oracle, musí aplikace odkazovat na <xref:System.Data.OracleClient> obor názvů následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="73bb2-110">To use the .NET Framework Data Provider for Oracle, an application must reference the <xref:System.Data.OracleClient> namespace as follows:</span></span>  
  
```vb  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data.OracleClient;  
```  
  
 <span data-ttu-id="73bb2-111">Při kompilaci kódu je také nutné zahrnout odkaz na knihovnu DLL.</span><span class="sxs-lookup"><span data-stu-id="73bb2-111">You also must include a reference to the DLL when you compile your code.</span></span> <span data-ttu-id="73bb2-112">Například pokud kompilujete program v jazyce C#, příkazový řádek by měl obsahovat:</span><span class="sxs-lookup"><span data-stu-id="73bb2-112">For example, if you are compiling a C# program, your command line should include:</span></span>  
  
```console
csc /r:System.Data.OracleClient.dll  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="73bb2-113">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="73bb2-113">In This Section</span></span>  
 [<span data-ttu-id="73bb2-114">Požadavky na systém</span><span class="sxs-lookup"><span data-stu-id="73bb2-114">System Requirements</span></span>](system-requirements-for-the-dotnet-data-provider-for-oracle.md)  
 <span data-ttu-id="73bb2-115">Popisuje požadavky na použití Zprostředkovatel dat .NET Framework pro Oracle a popisuje několik problémů, které je potřeba při použití použít.</span><span class="sxs-lookup"><span data-stu-id="73bb2-115">Describes requirements for using the .NET Framework Data Provider for Oracle, and describes a number of issues to be aware when using it.</span></span>  
  
 [<span data-ttu-id="73bb2-116">Soubory Oracle BFILE</span><span class="sxs-lookup"><span data-stu-id="73bb2-116">Oracle BFILEs</span></span>](oracle-bfiles.md)  
 <span data-ttu-id="73bb2-117">Popisuje <xref:System.Data.OracleClient.OracleBFile> třídu, která se používá pro práci s datovým typem Oracle BFILE.</span><span class="sxs-lookup"><span data-stu-id="73bb2-117">Describes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle BFILE data type.</span></span>  
  
 [<span data-ttu-id="73bb2-118">Soubory Oracle LOB</span><span class="sxs-lookup"><span data-stu-id="73bb2-118">Oracle LOBs</span></span>](oracle-lobs.md)  
 <span data-ttu-id="73bb2-119">Popisuje <xref:System.Data.OracleClient.OracleLob> třídu, která se používá pro práci s datovými typy společnosti Oracle LOB.</span><span class="sxs-lookup"><span data-stu-id="73bb2-119">Describes the <xref:System.Data.OracleClient.OracleLob> class, which is used to work with Oracle LOB data types.</span></span>  
  
 [<span data-ttu-id="73bb2-120">Soubory Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="73bb2-120">Oracle REF CURSORs</span></span>](oracle-ref-cursors.md)  
 <span data-ttu-id="73bb2-121">Popisuje podporu pro datový typ referenčního kurzoru Oracle REF.</span><span class="sxs-lookup"><span data-stu-id="73bb2-121">Describes support for the Oracle REF CURSOR data type.</span></span>  
  
 [<span data-ttu-id="73bb2-122">Typy Oracle</span><span class="sxs-lookup"><span data-stu-id="73bb2-122">OracleTypes</span></span>](oracletypes.md)  
 <span data-ttu-id="73bb2-123">Popisuje struktury, které můžete použít pro práci s datovými typy Oracle, včetně <xref:System.Data.OracleClient.OracleNumber> a <xref:System.Data.OracleClient.OracleString> .</span><span class="sxs-lookup"><span data-stu-id="73bb2-123">Describes structures you can use to work with Oracle data types, including <xref:System.Data.OracleClient.OracleNumber> and <xref:System.Data.OracleClient.OracleString>.</span></span>  
  
 [<span data-ttu-id="73bb2-124">Sekvence Oracle</span><span class="sxs-lookup"><span data-stu-id="73bb2-124">Oracle Sequences</span></span>](oracle-sequences.md)  
 <span data-ttu-id="73bb2-125">Popisuje podporu pro načtení hodnot sekvence Oracle vygenerovaných serverem klíčů.</span><span class="sxs-lookup"><span data-stu-id="73bb2-125">Describes support for retrieving the server-generated key Oracle Sequence values.</span></span>  
  
 [<span data-ttu-id="73bb2-126">Mapování datových typů Oracle</span><span class="sxs-lookup"><span data-stu-id="73bb2-126">Oracle Data Type Mappings</span></span>](oracle-data-type-mappings.md)  
 <span data-ttu-id="73bb2-127">Zobrazí seznam datových typů Oracle a jejich mapování na <xref:System.Data.OracleClient.OracleDataReader> .</span><span class="sxs-lookup"><span data-stu-id="73bb2-127">Lists Oracle data types and their mappings to the <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 [<span data-ttu-id="73bb2-128">Distribuované transakce Oracle</span><span class="sxs-lookup"><span data-stu-id="73bb2-128">Oracle Distributed Transactions</span></span>](oracle-distributed-transactions.md)  
 <span data-ttu-id="73bb2-129">Popisuje, jak <xref:System.Data.OracleClient.OracleConnection> objekt automaticky zařadí do existující distribuované transakce, pokud určuje, že je transakce aktivní.</span><span class="sxs-lookup"><span data-stu-id="73bb2-129">Describes how the <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="73bb2-130">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="73bb2-130">Related Sections</span></span>  
 [<span data-ttu-id="73bb2-131">Zabezpečení aplikací ADO.NET</span><span class="sxs-lookup"><span data-stu-id="73bb2-131">Securing ADO.NET Applications</span></span>](securing-ado-net-applications.md)  
 <span data-ttu-id="73bb2-132">Popisuje postupy zabezpečeného kódování při použití ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="73bb2-132">Describes secure coding practices when using ADO.NET.</span></span>  
  
 [<span data-ttu-id="73bb2-133">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="73bb2-133">DataSets, DataTables, and DataViews</span></span>](./dataset-datatable-dataview/index.md)  
 <span data-ttu-id="73bb2-134">Popisuje, jak vytvořit a používat `DataSets` , zadat `DataSets` , `DataTables` a `DataViews` .</span><span class="sxs-lookup"><span data-stu-id="73bb2-134">Describes how to create and use `DataSets`, typed `DataSets`, `DataTables`, and `DataViews`.</span></span>  
  
 [<span data-ttu-id="73bb2-135">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="73bb2-135">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)  
 <span data-ttu-id="73bb2-136">Popisuje, jak pracovat s daty v ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="73bb2-136">Describes how to work with data in ADO.NET.</span></span>  
  
 [<span data-ttu-id="73bb2-137">SQL Server a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="73bb2-137">SQL Server and ADO.NET</span></span>](./sql/index.md)  
 <span data-ttu-id="73bb2-138">Popisuje, jak pracovat s funkcemi a funkcemi, které jsou specifické pro SQL Server.</span><span class="sxs-lookup"><span data-stu-id="73bb2-138">Describes how to work with features and functionality that are specific to SQL Server.</span></span>  
  
 [<span data-ttu-id="73bb2-139">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="73bb2-139">DbProviderFactories</span></span>](dbproviderfactories.md)  
 <span data-ttu-id="73bb2-140">Popisuje obecné třídy, které umožňují napsat kód nezávislý na poskytovateli v ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="73bb2-140">Describes generic classes that allow you to write provider-independent code in ADO.NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73bb2-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="73bb2-141">See also</span></span>

- [<span data-ttu-id="73bb2-142">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="73bb2-142">ADO.NET</span></span>](index.md)
- [<span data-ttu-id="73bb2-143">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="73bb2-143">ADO.NET Overview</span></span>](ado-net-overview.md)
