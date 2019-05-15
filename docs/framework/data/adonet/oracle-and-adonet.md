---
title: Oracle a ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
ms.openlocfilehash: a8668ee115a3babbdf1ef549a418187d2c5e26b8
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65583417"
---
# <a name="oracle-and-adonet"></a><span data-ttu-id="ce8da-102">Oracle a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ce8da-102">Oracle and ADO.NET</span></span>
> [!NOTE]
>  <span data-ttu-id="ce8da-103">Typy v <xref:System.Data.OracleClient> jsou zastaralé.</span><span class="sxs-lookup"><span data-stu-id="ce8da-103">The types in <xref:System.Data.OracleClient> are deprecated.</span></span> <span data-ttu-id="ce8da-104">Typy dál podporovat v aktuální verzi of.NET rozhraní Framework, ale bude v budoucí verzi odebrána.</span><span class="sxs-lookup"><span data-stu-id="ce8da-104">The types remain supported in the current version of.NET Framework but will be removed in a future release.</span></span> <span data-ttu-id="ce8da-105">Společnost Microsoft doporučuje používat Zprostředkovatel Oracle třetích stran.</span><span class="sxs-lookup"><span data-stu-id="ce8da-105">Microsoft recommends that you use a third-party Oracle provider.</span></span>  
  
 <span data-ttu-id="ce8da-106">Tato část popisuje funkce a chování, které jsou specifické pro zprostředkovatele dat .NET Framework pro Oracle.</span><span class="sxs-lookup"><span data-stu-id="ce8da-106">This section describes features and behaviors that are specific to the .NET Framework Data Provider for Oracle.</span></span>  
  
 <span data-ttu-id="ce8da-107">Zprostředkovatel dat .NET Framework pro Oracle poskytuje přístup k databázi Oracle pomocí Oracle volání rozhraní (OCI) podle software klienta Oracle.</span><span class="sxs-lookup"><span data-stu-id="ce8da-107">The .NET Framework Data Provider for Oracle provides access to an Oracle database using the Oracle Call Interface (OCI) as provided by Oracle Client software.</span></span> <span data-ttu-id="ce8da-108">Funkce zprostředkovatel dat slouží k podobný zprostředkovatele dat .NET Framework pro SQL Server, technologie OLE DB a ODBC.</span><span class="sxs-lookup"><span data-stu-id="ce8da-108">The functionality of the data provider is designed to be similar to that of the .NET Framework data providers for SQL Server, OLE DB, and ODBC.</span></span>  
  
 <span data-ttu-id="ce8da-109">Použití zprostředkovatele dat .NET Framework pro Oracle, aplikace musí odkazovat <xref:System.Data.OracleClient> oboru názvů následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="ce8da-109">To use the .NET Framework Data Provider for Oracle, an application must reference the <xref:System.Data.OracleClient> namespace as follows:</span></span>  
  
```vb  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data.OracleClient;  
```  
  
 <span data-ttu-id="ce8da-110">Také musíte zahrnout odkaz na knihovnu DLL při kompilaci kódu.</span><span class="sxs-lookup"><span data-stu-id="ce8da-110">You also must include a reference to the DLL when you compile your code.</span></span> <span data-ttu-id="ce8da-111">Například při kompilaci programu v jazyce C#, by měl obsahovat příkazového řádku:</span><span class="sxs-lookup"><span data-stu-id="ce8da-111">For example, if you are compiling a C# program, your command line should include:</span></span>  
  
```  
csc /r:System.Data.OracleClient.dll  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="ce8da-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="ce8da-112">In This Section</span></span>  
 [<span data-ttu-id="ce8da-113">Požadavky na systém</span><span class="sxs-lookup"><span data-stu-id="ce8da-113">System Requirements</span></span>](../../../../docs/framework/data/adonet/system-requirements-for-the-dotnet-data-provider-for-oracle.md)  
 <span data-ttu-id="ce8da-114">Popisuje požadavky pro použití zprostředkovatele dat .NET Framework pro Oracle a celé řady důvodů mějte na paměti při jeho použití.</span><span class="sxs-lookup"><span data-stu-id="ce8da-114">Describes requirements for using the .NET Framework Data Provider for Oracle, and describes a number of issues to be aware when using it.</span></span>  
  
 [<span data-ttu-id="ce8da-115">Soubory Oracle BFILE</span><span class="sxs-lookup"><span data-stu-id="ce8da-115">Oracle BFILEs</span></span>](../../../../docs/framework/data/adonet/oracle-bfiles.md)  
 <span data-ttu-id="ce8da-116">Popisuje <xref:System.Data.OracleClient.OracleBFile> třídu, která se používá pro práci s datovým typem Oracle BFILE.</span><span class="sxs-lookup"><span data-stu-id="ce8da-116">Describes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle BFILE data type.</span></span>  
  
 [<span data-ttu-id="ce8da-117">Soubory Oracle LOB</span><span class="sxs-lookup"><span data-stu-id="ce8da-117">Oracle LOBs</span></span>](../../../../docs/framework/data/adonet/oracle-lobs.md)  
 <span data-ttu-id="ce8da-118">Popisuje <xref:System.Data.OracleClient.OracleLob> třídu, která se používá pro práci s datovými typy Oracle LOB.</span><span class="sxs-lookup"><span data-stu-id="ce8da-118">Describes the <xref:System.Data.OracleClient.OracleLob> class, which is used to work with Oracle LOB data types.</span></span>  
  
 [<span data-ttu-id="ce8da-119">Soubory Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="ce8da-119">Oracle REF CURSORs</span></span>](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)  
 <span data-ttu-id="ce8da-120">Popisuje podporu pro datový typ Oracle REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="ce8da-120">Describes support for the Oracle REF CURSOR data type.</span></span>  
  
 [<span data-ttu-id="ce8da-121">Typy Oracle</span><span class="sxs-lookup"><span data-stu-id="ce8da-121">OracleTypes</span></span>](../../../../docs/framework/data/adonet/oracletypes.md)  
 <span data-ttu-id="ce8da-122">Popisuje, můžete použít pro práci s typy dat Oracle, včetně struktur <xref:System.Data.OracleClient.OracleNumber> a <xref:System.Data.OracleClient.OracleString>.</span><span class="sxs-lookup"><span data-stu-id="ce8da-122">Describes structures you can use to work with Oracle data types, including <xref:System.Data.OracleClient.OracleNumber> and <xref:System.Data.OracleClient.OracleString>.</span></span>  
  
 [<span data-ttu-id="ce8da-123">Sekvence Oracle</span><span class="sxs-lookup"><span data-stu-id="ce8da-123">Oracle Sequences</span></span>](../../../../docs/framework/data/adonet/oracle-sequences.md)  
 <span data-ttu-id="ce8da-124">Popisuje podporu pro načtení hodnoty klíče generovaný serverem sekvence Oracle.</span><span class="sxs-lookup"><span data-stu-id="ce8da-124">Describes support for retrieving the server-generated key Oracle Sequence values.</span></span>  
  
 [<span data-ttu-id="ce8da-125">Mapování datových typů Oracle</span><span class="sxs-lookup"><span data-stu-id="ce8da-125">Oracle Data Type Mappings</span></span>](../../../../docs/framework/data/adonet/oracle-data-type-mappings.md)  
 <span data-ttu-id="ce8da-126">Zobrazí seznam datových typů Oracle a jejich mapování na <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="ce8da-126">Lists Oracle data types and their mappings to the <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 [<span data-ttu-id="ce8da-127">Distribuované transakce Oracle</span><span class="sxs-lookup"><span data-stu-id="ce8da-127">Oracle Distributed Transactions</span></span>](../../../../docs/framework/data/adonet/oracle-distributed-transactions.md)  
 <span data-ttu-id="ce8da-128">Popisuje, jak <xref:System.Data.OracleClient.OracleConnection> objekt automaticky využívá v existující distribuovanou transakci, pokud určí, že je aktivní transakce.</span><span class="sxs-lookup"><span data-stu-id="ce8da-128">Describes how the <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ce8da-129">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="ce8da-129">Related Sections</span></span>  
 [<span data-ttu-id="ce8da-130">Zabezpečení aplikací ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ce8da-130">Securing ADO.NET Applications</span></span>](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 <span data-ttu-id="ce8da-131">Popisuje zabezpečené kódování postupy při používání [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ce8da-131">Describes secure coding practices when using [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span></span>  
  
 [<span data-ttu-id="ce8da-132">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="ce8da-132">DataSets, DataTables, and DataViews</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 <span data-ttu-id="ce8da-133">Popisuje, jak vytvořit a používat `DataSets`, zadaný `DataSets`, `DataTables`, a `DataViews`.</span><span class="sxs-lookup"><span data-stu-id="ce8da-133">Describes how to create and use `DataSets`, typed `DataSets`, `DataTables`, and `DataViews`.</span></span>  
  
 [<span data-ttu-id="ce8da-134">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ce8da-134">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 <span data-ttu-id="ce8da-135">Popisuje, jak pracovat s daty v ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="ce8da-135">Describes how to work with data in ADO.NET.</span></span>  
  
 [<span data-ttu-id="ce8da-136">SQL Server a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ce8da-136">SQL Server and ADO.NET</span></span>](../../../../docs/framework/data/adonet/sql/index.md)  
 <span data-ttu-id="ce8da-137">Popisuje, jak využívat funkce, které jsou specifické pro systém SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ce8da-137">Describes how to work with features and functionality that are specific to SQL Server.</span></span>  
  
 [<span data-ttu-id="ce8da-138">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="ce8da-138">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 <span data-ttu-id="ce8da-139">Popisuje obecné třídy, které umožňuje psát kód nezávislý na zprostředkovatele [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ce8da-139">Describes generic classes that allow you to write provider-independent code in [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce8da-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ce8da-140">See also</span></span>

- [<span data-ttu-id="ce8da-141">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ce8da-141">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)
- [<span data-ttu-id="ce8da-142">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="ce8da-142">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
