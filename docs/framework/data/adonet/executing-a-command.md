---
title: "Spouštění příkazu"
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
ms.assetid: 40494916-c25a-4cb8-8f7c-fcb8d378464e
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e09685c92652e1fcac2486031ecb49bf8399be59
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="executing-a-command"></a><span data-ttu-id="bef5f-102">Spouštění příkazu</span><span class="sxs-lookup"><span data-stu-id="bef5f-102">Executing a Command</span></span>
<span data-ttu-id="bef5f-103">Zprostředkovatel dat .NET Framework, jednotlivých součástí rozhraní .NET Framework má svou vlastní objekt příkazu, který dědí z <xref:System.Data.Common.DbCommand>.</span><span class="sxs-lookup"><span data-stu-id="bef5f-103">Each .NET Framework data provider included with the .NET Framework has its own command object that inherits from <xref:System.Data.Common.DbCommand>.</span></span> <span data-ttu-id="bef5f-104">Zahrnuje zprostředkovatel dat .NET Framework pro OLE DB <xref:System.Data.OleDb.OleDbCommand> objektu, zahrnuje zprostředkovatel dat .NET Framework pro SQL Server <xref:System.Data.SqlClient.SqlCommand> objektu, zahrnuje zprostředkovatel dat .NET Framework pro ODBC <xref:System.Data.Odbc.OdbcCommand> objektu a rozhraní .NET Framework Zprostředkovatel dat pro Oracle zahrnuje <xref:System.Data.OracleClient.OracleCommand> objektu.</span><span class="sxs-lookup"><span data-stu-id="bef5f-104">The .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbCommand> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlCommand> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcCommand> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleCommand> object.</span></span> <span data-ttu-id="bef5f-105">Každá z těchto metod zpřístupňuje objekty pro provádění příkazů na základě typu příkazu a potřeby návratovou hodnotu, jak je popsáno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="bef5f-105">Each of these objects exposes methods for executing commands based on the type of command and desired return value, as described in the following table.</span></span>  
  
|<span data-ttu-id="bef5f-106">Příkaz</span><span class="sxs-lookup"><span data-stu-id="bef5f-106">Command</span></span>|<span data-ttu-id="bef5f-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="bef5f-107">Return Value</span></span>|  
|-------------|------------------|  
|`ExecuteReader`|<span data-ttu-id="bef5f-108">Vrátí hodnotu `DataReader` objektu.</span><span class="sxs-lookup"><span data-stu-id="bef5f-108">Returns a `DataReader` object.</span></span>|  
|`ExecuteScalar`|<span data-ttu-id="bef5f-109">Vrátí jednu skalární hodnotu.</span><span class="sxs-lookup"><span data-stu-id="bef5f-109">Returns a single scalar value.</span></span>|  
|`ExecuteNonQuery`|<span data-ttu-id="bef5f-110">Spustí příkaz, který nevrací žádné řádky.</span><span class="sxs-lookup"><span data-stu-id="bef5f-110">Executes a command that does not return any rows.</span></span>|  
|`ExecuteXMLReader`|<span data-ttu-id="bef5f-111">Vrátí <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="bef5f-111">Returns an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="bef5f-112">K dispozici pro `SqlCommand` pouze objekt.</span><span class="sxs-lookup"><span data-stu-id="bef5f-112">Available for a `SqlCommand` object only.</span></span>|  
  
 <span data-ttu-id="bef5f-113">Každý objekt silného typu příkazu podporuje také <xref:System.Data.CommandType> výčet, který určuje, jak se interpretují příkazového řetězce, jak je popsáno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="bef5f-113">Each strongly typed command object also supports a <xref:System.Data.CommandType> enumeration that specifies how a command string is interpreted, as described in the following table.</span></span>  
  
|<span data-ttu-id="bef5f-114">Typ příkazu CommandType</span><span class="sxs-lookup"><span data-stu-id="bef5f-114">CommandType</span></span>|<span data-ttu-id="bef5f-115">Popis</span><span class="sxs-lookup"><span data-stu-id="bef5f-115">Description</span></span>|  
|-----------------|-----------------|  
|`Text`|<span data-ttu-id="bef5f-116">Příkaz SQL definování příkazy ve zdroji dat spouštění.</span><span class="sxs-lookup"><span data-stu-id="bef5f-116">An SQL command defining the statements to be executed at the data source.</span></span>|  
|`StoredProcedure`|<span data-ttu-id="bef5f-117">Název uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="bef5f-117">The name of the stored procedure.</span></span> <span data-ttu-id="bef5f-118">Můžete použít `Parameters` vlastnost příkaz, který má přístup k vstupní a výstupní parametry a návratové hodnoty, bez ohledu na to, které `Execute` metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="bef5f-118">You can use the `Parameters` property of a command to access input and output parameters and return values, regardless of which `Execute` method is called.</span></span> <span data-ttu-id="bef5f-119">Při použití `ExecuteReader`, návratové hodnoty a výstupní parametry nebudou přístupné, dokud `DataReader` je uzavřený.</span><span class="sxs-lookup"><span data-stu-id="bef5f-119">When using `ExecuteReader`, return values and output parameters will not be accessible until the `DataReader` is closed.</span></span>|  
|`TableDirect`|<span data-ttu-id="bef5f-120">Název tabulky.</span><span class="sxs-lookup"><span data-stu-id="bef5f-120">The name of a table.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="bef5f-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="bef5f-121">Example</span></span>  
 <span data-ttu-id="bef5f-122">Následující příklad kódu ukazuje, jak vytvořit <xref:System.Data.SqlClient.SqlCommand> objekt ke spuštění uložené procedury nastavením jeho vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="bef5f-122">The following code example demonstrates how to create a <xref:System.Data.SqlClient.SqlCommand> object to execute a stored procedure by setting its properties.</span></span> <span data-ttu-id="bef5f-123">A <xref:System.Data.SqlClient.SqlParameter> objekt se používá k určení vstupní parametr uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="bef5f-123">A <xref:System.Data.SqlClient.SqlParameter> object is used to specify the input parameter to the stored procedure.</span></span> <span data-ttu-id="bef5f-124">Provedení příkazu pomocí <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> metoda a výstup <xref:System.Data.SqlClient.SqlDataReader> se zobrazí v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="bef5f-124">The command is executed using the <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> method, and the output from the <xref:System.Data.SqlClient.SqlDataReader> is displayed in the console window.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/VB/source.vb#1)]  
  
### <a name="troubleshooting-commands"></a><span data-ttu-id="bef5f-125">Řešení potíží s příkazy</span><span class="sxs-lookup"><span data-stu-id="bef5f-125">Troubleshooting Commands</span></span>  
 <span data-ttu-id="bef5f-126">Zprostředkovatel dat .NET Framework pro SQL Server přidá čítačů výkonu vám umožní zjistit přerušované problémy související s jednotlivými spuštěními příkazu se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="bef5f-126">The .NET Framework Data Provider for SQL Server adds performance counters to enable you to detect intermittent problems related to failed command executions.</span></span> <span data-ttu-id="bef5f-127">Další informace najdete v části [čítače výkonu](../../../../docs/framework/data/adonet/performance-counters.md).</span><span class="sxs-lookup"><span data-stu-id="bef5f-127">For more information see [Performance Counters](../../../../docs/framework/data/adonet/performance-counters.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bef5f-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="bef5f-128">See Also</span></span>  
 [<span data-ttu-id="bef5f-129">Příkazy a parametry</span><span class="sxs-lookup"><span data-stu-id="bef5f-129">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="bef5f-130">DataAdapters a DataReaders</span><span class="sxs-lookup"><span data-stu-id="bef5f-130">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="bef5f-131">Práce s DataReaders</span><span class="sxs-lookup"><span data-stu-id="bef5f-131">Working with DataReaders</span></span>](http://msdn.microsoft.com/en-us/126a966a-d08d-4d22-a19f-f432908b2b54)  
 [<span data-ttu-id="bef5f-132">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="bef5f-132">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
