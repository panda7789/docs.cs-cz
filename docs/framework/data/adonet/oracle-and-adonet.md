---
title: Oracle a ADO.NET
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
ms.openlocfilehash: 5683f2b4ba57021ff6dda3a51baca016f886b605
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980077"
---
# <a name="oracle-and-adonet"></a><span data-ttu-id="8a778-102">Oracle a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8a778-102">Oracle and ADO.NET</span></span>
> [!NOTE]
> <span data-ttu-id="8a778-103">Typy v <xref:System.Data.OracleClient> jsou zastaralé.</span><span class="sxs-lookup"><span data-stu-id="8a778-103">The types in <xref:System.Data.OracleClient> are deprecated.</span></span> <span data-ttu-id="8a778-104">Typy zůstanou podporované v aktuální verzi rozhraní of.NET Framework, ale v budoucí verzi se odeberou.</span><span class="sxs-lookup"><span data-stu-id="8a778-104">The types remain supported in the current version of.NET Framework but will be removed in a future release.</span></span> <span data-ttu-id="8a778-105">Microsoft doporučuje, abyste použili poskytovatele Oracle od jiného výrobce.</span><span class="sxs-lookup"><span data-stu-id="8a778-105">Microsoft recommends that you use a third-party Oracle provider.</span></span>  
  
 <span data-ttu-id="8a778-106">Tato část popisuje funkce a chování, které jsou specifické pro Zprostředkovatel dat .NET Framework pro Oracle.</span><span class="sxs-lookup"><span data-stu-id="8a778-106">This section describes features and behaviors that are specific to the .NET Framework Data Provider for Oracle.</span></span>  
  
 <span data-ttu-id="8a778-107">Zprostředkovatel dat .NET Framework pro Oracle poskytuje přístup k databázi Oracle pomocí rozhraní Oracle Call Interface (OCI), které poskytuje klientský software Oracle.</span><span class="sxs-lookup"><span data-stu-id="8a778-107">The .NET Framework Data Provider for Oracle provides access to an Oracle database using the Oracle Call Interface (OCI) as provided by Oracle Client software.</span></span> <span data-ttu-id="8a778-108">Funkce poskytovatele dat je navržena tak, aby byla podobná poskytovateli .NET Framework dat pro SQL Server, OLE DB a ODBC.</span><span class="sxs-lookup"><span data-stu-id="8a778-108">The functionality of the data provider is designed to be similar to that of the .NET Framework data providers for SQL Server, OLE DB, and ODBC.</span></span>  
  
 <span data-ttu-id="8a778-109">Chcete-li použít Zprostředkovatel dat .NET Framework pro Oracle, musí aplikace odkazovat na obor názvů <xref:System.Data.OracleClient> následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="8a778-109">To use the .NET Framework Data Provider for Oracle, an application must reference the <xref:System.Data.OracleClient> namespace as follows:</span></span>  
  
```vb  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data.OracleClient;  
```  
  
 <span data-ttu-id="8a778-110">Při kompilaci kódu je také nutné zahrnout odkaz na knihovnu DLL.</span><span class="sxs-lookup"><span data-stu-id="8a778-110">You also must include a reference to the DLL when you compile your code.</span></span> <span data-ttu-id="8a778-111">Například pokud kompilujete C# program, váš příkazový řádek by měl obsahovat:</span><span class="sxs-lookup"><span data-stu-id="8a778-111">For example, if you are compiling a C# program, your command line should include:</span></span>  
  
```console
csc /r:System.Data.OracleClient.dll  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="8a778-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="8a778-112">In This Section</span></span>  
 [<span data-ttu-id="8a778-113">Požadavky na systém</span><span class="sxs-lookup"><span data-stu-id="8a778-113">System Requirements</span></span>](system-requirements-for-the-dotnet-data-provider-for-oracle.md)  
 <span data-ttu-id="8a778-114">Popisuje požadavky na použití Zprostředkovatel dat .NET Framework pro Oracle a popisuje několik problémů, které je potřeba při použití použít.</span><span class="sxs-lookup"><span data-stu-id="8a778-114">Describes requirements for using the .NET Framework Data Provider for Oracle, and describes a number of issues to be aware when using it.</span></span>  
  
 [<span data-ttu-id="8a778-115">Soubory Oracle BFILE</span><span class="sxs-lookup"><span data-stu-id="8a778-115">Oracle BFILEs</span></span>](oracle-bfiles.md)  
 <span data-ttu-id="8a778-116">Popisuje třídu <xref:System.Data.OracleClient.OracleBFile>, která se používá pro práci s datovým typem Oracle BFILE.</span><span class="sxs-lookup"><span data-stu-id="8a778-116">Describes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle BFILE data type.</span></span>  
  
 [<span data-ttu-id="8a778-117">Soubory Oracle LOB</span><span class="sxs-lookup"><span data-stu-id="8a778-117">Oracle LOBs</span></span>](oracle-lobs.md)  
 <span data-ttu-id="8a778-118">Popisuje třídu <xref:System.Data.OracleClient.OracleLob>, která se používá pro práci s datovými typy LOB společnosti Oracle.</span><span class="sxs-lookup"><span data-stu-id="8a778-118">Describes the <xref:System.Data.OracleClient.OracleLob> class, which is used to work with Oracle LOB data types.</span></span>  
  
 [<span data-ttu-id="8a778-119">Soubory Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="8a778-119">Oracle REF CURSORs</span></span>](oracle-ref-cursors.md)  
 <span data-ttu-id="8a778-120">Popisuje podporu pro datový typ referenčního kurzoru Oracle REF.</span><span class="sxs-lookup"><span data-stu-id="8a778-120">Describes support for the Oracle REF CURSOR data type.</span></span>  
  
 [<span data-ttu-id="8a778-121">Typy Oracle</span><span class="sxs-lookup"><span data-stu-id="8a778-121">OracleTypes</span></span>](oracletypes.md)  
 <span data-ttu-id="8a778-122">Popisuje struktury, které můžete použít pro práci s datovými typy Oracle, včetně <xref:System.Data.OracleClient.OracleNumber> a <xref:System.Data.OracleClient.OracleString>.</span><span class="sxs-lookup"><span data-stu-id="8a778-122">Describes structures you can use to work with Oracle data types, including <xref:System.Data.OracleClient.OracleNumber> and <xref:System.Data.OracleClient.OracleString>.</span></span>  
  
 [<span data-ttu-id="8a778-123">Sekvence Oracle</span><span class="sxs-lookup"><span data-stu-id="8a778-123">Oracle Sequences</span></span>](oracle-sequences.md)  
 <span data-ttu-id="8a778-124">Popisuje podporu pro načtení hodnot sekvence Oracle vygenerovaných serverem klíčů.</span><span class="sxs-lookup"><span data-stu-id="8a778-124">Describes support for retrieving the server-generated key Oracle Sequence values.</span></span>  
  
 [<span data-ttu-id="8a778-125">Mapování datových typů Oracle</span><span class="sxs-lookup"><span data-stu-id="8a778-125">Oracle Data Type Mappings</span></span>](oracle-data-type-mappings.md)  
 <span data-ttu-id="8a778-126">Zobrazí seznam datových typů Oracle a jejich mapování na <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="8a778-126">Lists Oracle data types and their mappings to the <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 [<span data-ttu-id="8a778-127">Distribuované transakce Oracle</span><span class="sxs-lookup"><span data-stu-id="8a778-127">Oracle Distributed Transactions</span></span>](oracle-distributed-transactions.md)  
 <span data-ttu-id="8a778-128">Popisuje způsob, jakým objekt <xref:System.Data.OracleClient.OracleConnection> automaticky zařadí do existující distribuované transakce, pokud zjistí, že je transakce aktivní.</span><span class="sxs-lookup"><span data-stu-id="8a778-128">Describes how the <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8a778-129">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="8a778-129">Related Sections</span></span>  
 [<span data-ttu-id="8a778-130">Zabezpečení aplikací ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8a778-130">Securing ADO.NET Applications</span></span>](securing-ado-net-applications.md)  
 <span data-ttu-id="8a778-131">Popisuje postupy zabezpečeného kódování při použití ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="8a778-131">Describes secure coding practices when using ADO.NET.</span></span>  
  
 [<span data-ttu-id="8a778-132">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="8a778-132">DataSets, DataTables, and DataViews</span></span>](./dataset-datatable-dataview/index.md)  
 <span data-ttu-id="8a778-133">Popisuje, jak vytvořit a používat `DataSets`, typové `DataSets`, `DataTables`a `DataViews`.</span><span class="sxs-lookup"><span data-stu-id="8a778-133">Describes how to create and use `DataSets`, typed `DataSets`, `DataTables`, and `DataViews`.</span></span>  
  
 [<span data-ttu-id="8a778-134">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8a778-134">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)  
 <span data-ttu-id="8a778-135">Popisuje, jak pracovat s daty v ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="8a778-135">Describes how to work with data in ADO.NET.</span></span>  
  
 [<span data-ttu-id="8a778-136">SQL Server a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8a778-136">SQL Server and ADO.NET</span></span>](./sql/index.md)  
 <span data-ttu-id="8a778-137">Popisuje, jak pracovat s funkcemi a funkcemi, které jsou specifické pro SQL Server.</span><span class="sxs-lookup"><span data-stu-id="8a778-137">Describes how to work with features and functionality that are specific to SQL Server.</span></span>  
  
 [<span data-ttu-id="8a778-138">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="8a778-138">DbProviderFactories</span></span>](dbproviderfactories.md)  
 <span data-ttu-id="8a778-139">Popisuje obecné třídy, které umožňují napsat kód nezávislý na poskytovateli v ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="8a778-139">Describes generic classes that allow you to write provider-independent code in ADO.NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a778-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8a778-140">See also</span></span>

- [<span data-ttu-id="8a778-141">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8a778-141">ADO.NET</span></span>](index.md)
- [<span data-ttu-id="8a778-142">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8a778-142">ADO.NET Overview</span></span>](ado-net-overview.md)
