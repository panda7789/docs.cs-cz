---
title: Oracle a ADO.NET
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
ms.openlocfilehash: 9a60499674f0192bb7589f227bffb6f907f682d9
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43561746"
---
# <a name="oracle-and-adonet"></a><span data-ttu-id="4bee4-102">Oracle a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4bee4-102">Oracle and ADO.NET</span></span>
> [!NOTE]
>  <span data-ttu-id="4bee4-103">Typy v <xref:System.Data.OracleClient> jsou zastaralé.</span><span class="sxs-lookup"><span data-stu-id="4bee4-103">The types in <xref:System.Data.OracleClient> are deprecated.</span></span> <span data-ttu-id="4bee4-104">Typy dál podporovat v aktuální verzi of.NET rozhraní Framework, ale bude v budoucí verzi odebrána.</span><span class="sxs-lookup"><span data-stu-id="4bee4-104">The types remain supported in the current version of.NET Framework but will be removed in a future release.</span></span> <span data-ttu-id="4bee4-105">Společnost Microsoft doporučuje používat Zprostředkovatel Oracle třetích stran.</span><span class="sxs-lookup"><span data-stu-id="4bee4-105">Microsoft recommends that you use a third-party Oracle provider.</span></span>  
  
 <span data-ttu-id="4bee4-106">Tato část popisuje funkce a chování, které jsou specifické pro [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider pro Oracle.</span><span class="sxs-lookup"><span data-stu-id="4bee4-106">This section describes features and behaviors that are specific to the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle.</span></span>  
  
 <span data-ttu-id="4bee4-107">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Poskytuje přístup k databázi Oracle pomocí Oracle volání rozhraní (OCI) podle software klienta Oracle Data Provider pro Oracle.</span><span class="sxs-lookup"><span data-stu-id="4bee4-107">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle provides access to an Oracle database using the Oracle Call Interface (OCI) as provided by Oracle Client software.</span></span> <span data-ttu-id="4bee4-108">Funkce poskytovatele dat byla navržena jako podobný [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatele dat pro SQL Server, technologie OLE DB a ODBC.</span><span class="sxs-lookup"><span data-stu-id="4bee4-108">The functionality of the data provider is designed to be similar to that of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data providers for SQL Server, OLE DB, and ODBC.</span></span>  
  
 <span data-ttu-id="4bee4-109">Použít [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider pro Oracle, aplikace musí odkazovat <xref:System.Data.OracleClient> oboru názvů následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="4bee4-109">To use the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle, an application must reference the <xref:System.Data.OracleClient> namespace as follows:</span></span>  
  
```vb  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data.OracleClient;  
```  
  
 <span data-ttu-id="4bee4-110">Také musíte zahrnout odkaz na knihovnu DLL při kompilaci kódu.</span><span class="sxs-lookup"><span data-stu-id="4bee4-110">You also must include a reference to the DLL when you compile your code.</span></span> <span data-ttu-id="4bee4-111">Například při kompilaci programu v jazyce C#, by měl obsahovat příkazového řádku:</span><span class="sxs-lookup"><span data-stu-id="4bee4-111">For example, if you are compiling a C# program, your command line should include:</span></span>  
  
```  
csc /r:System.Data.OracleClient.dll  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="4bee4-112">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="4bee4-112">In This Section</span></span>  
 [<span data-ttu-id="4bee4-113">Požadavky na systém</span><span class="sxs-lookup"><span data-stu-id="4bee4-113">System Requirements</span></span>](../../../../docs/framework/data/adonet/system-requirements-for-the-dotnet-data-provider-for-oracle.md)  
 <span data-ttu-id="4bee4-114">Popisuje požadavky pro použití [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider pro Oracle a popisuje celou řadu problémů mějte na paměti při jeho použití.</span><span class="sxs-lookup"><span data-stu-id="4bee4-114">Describes requirements for using the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Data Provider for Oracle, and describes a number of issues to be aware when using it.</span></span>  
  
 [<span data-ttu-id="4bee4-115">Soubory Oracle BFILE</span><span class="sxs-lookup"><span data-stu-id="4bee4-115">Oracle BFILEs</span></span>](../../../../docs/framework/data/adonet/oracle-bfiles.md)  
 <span data-ttu-id="4bee4-116">Popisuje <xref:System.Data.OracleClient.OracleBFile> třídu, která se používá pro práci s datovým typem Oracle BFILE.</span><span class="sxs-lookup"><span data-stu-id="4bee4-116">Describes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle BFILE data type.</span></span>  
  
 [<span data-ttu-id="4bee4-117">Soubory Oracle LOB</span><span class="sxs-lookup"><span data-stu-id="4bee4-117">Oracle LOBs</span></span>](../../../../docs/framework/data/adonet/oracle-lobs.md)  
 <span data-ttu-id="4bee4-118">Popisuje <xref:System.Data.OracleClient.OracleLob> třídu, která se používá pro práci s datovými typy Oracle LOB.</span><span class="sxs-lookup"><span data-stu-id="4bee4-118">Describes the <xref:System.Data.OracleClient.OracleLob> class, which is used to work with Oracle LOB data types.</span></span>  
  
 [<span data-ttu-id="4bee4-119">Soubory Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="4bee4-119">Oracle REF CURSORs</span></span>](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)  
 <span data-ttu-id="4bee4-120">Popisuje podporu pro datový typ Oracle REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="4bee4-120">Describes support for the Oracle REF CURSOR data type.</span></span>  
  
 [<span data-ttu-id="4bee4-121">Typy Oracle</span><span class="sxs-lookup"><span data-stu-id="4bee4-121">OracleTypes</span></span>](../../../../docs/framework/data/adonet/oracletypes.md)  
 <span data-ttu-id="4bee4-122">Popisuje, můžete použít pro práci s typy dat Oracle, včetně struktur <xref:System.Data.OracleClient.OracleNumber> a <xref:System.Data.OracleClient.OracleString>.</span><span class="sxs-lookup"><span data-stu-id="4bee4-122">Describes structures you can use to work with Oracle data types, including <xref:System.Data.OracleClient.OracleNumber> and <xref:System.Data.OracleClient.OracleString>.</span></span>  
  
 [<span data-ttu-id="4bee4-123">Sekvence Oracle</span><span class="sxs-lookup"><span data-stu-id="4bee4-123">Oracle Sequences</span></span>](../../../../docs/framework/data/adonet/oracle-sequences.md)  
 <span data-ttu-id="4bee4-124">Popisuje podporu pro načtení hodnoty klíče generovaný serverem sekvence Oracle.</span><span class="sxs-lookup"><span data-stu-id="4bee4-124">Describes support for retrieving the server-generated key Oracle Sequence values.</span></span>  
  
 [<span data-ttu-id="4bee4-125">Mapování datových typů Oracle</span><span class="sxs-lookup"><span data-stu-id="4bee4-125">Oracle Data Type Mappings</span></span>](../../../../docs/framework/data/adonet/oracle-data-type-mappings.md)  
 <span data-ttu-id="4bee4-126">Zobrazí seznam datových typů Oracle a jejich mapování na <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="4bee4-126">Lists Oracle data types and their mappings to the <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 [<span data-ttu-id="4bee4-127">Distribuované transakce Oracle</span><span class="sxs-lookup"><span data-stu-id="4bee4-127">Oracle Distributed Transactions</span></span>](../../../../docs/framework/data/adonet/oracle-distributed-transactions.md)  
 <span data-ttu-id="4bee4-128">Popisuje, jak <xref:System.Data.OracleClient.OracleConnection> objekt automaticky využívá v existující distribuovanou transakci, pokud určí, že je aktivní transakce.</span><span class="sxs-lookup"><span data-stu-id="4bee4-128">Describes how the <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4bee4-129">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="4bee4-129">Related Sections</span></span>  
 [<span data-ttu-id="4bee4-130">Zabezpečení aplikací ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4bee4-130">Securing ADO.NET Applications</span></span>](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 <span data-ttu-id="4bee4-131">Popisuje zabezpečené kódování postupy při používání [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4bee4-131">Describes secure coding practices when using [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span></span>  
  
 [<span data-ttu-id="4bee4-132">Datové sady, datové tabulky a datová zobrazení</span><span class="sxs-lookup"><span data-stu-id="4bee4-132">DataSets, DataTables, and DataViews</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 <span data-ttu-id="4bee4-133">Popisuje, jak vytvořit a používat `DataSets`, zadaný `DataSets`, `DataTables`, a `DataViews`.</span><span class="sxs-lookup"><span data-stu-id="4bee4-133">Describes how to create and use `DataSets`, typed `DataSets`, `DataTables`, and `DataViews`.</span></span>  
  
 [<span data-ttu-id="4bee4-134">Načítání a úpravy dat v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4bee4-134">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 <span data-ttu-id="4bee4-135">Popisuje, jak pracovat s daty v ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="4bee4-135">Describes how to work with data in ADO.NET.</span></span>  
  
 [<span data-ttu-id="4bee4-136">SQL Server a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4bee4-136">SQL Server and ADO.NET</span></span>](../../../../docs/framework/data/adonet/sql/index.md)  
 <span data-ttu-id="4bee4-137">Popisuje, jak využívat funkce, které jsou specifické pro systém SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4bee4-137">Describes how to work with features and functionality that are specific to SQL Server.</span></span>  
  
 [<span data-ttu-id="4bee4-138">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="4bee4-138">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 <span data-ttu-id="4bee4-139">Popisuje obecné třídy, které umožňuje psát kód nezávislý na zprostředkovatele [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4bee4-139">Describes generic classes that allow you to write provider-independent code in [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bee4-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="4bee4-140">See Also</span></span>  
 [<span data-ttu-id="4bee4-141">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4bee4-141">ADO.NET</span></span>](../../../../docs/framework/data/adonet/index.md)  
 [<span data-ttu-id="4bee4-142">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="4bee4-142">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
