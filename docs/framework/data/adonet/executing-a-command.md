---
title: Spuštění příkazu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 40494916-c25a-4cb8-8f7c-fcb8d378464e
ms.openlocfilehash: f749ea37e1655f006e4de26e7cb279b778fe4faf
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795105"
---
# <a name="executing-a-command"></a><span data-ttu-id="ceb0e-102">Spuštění příkazu</span><span class="sxs-lookup"><span data-stu-id="ceb0e-102">Executing a Command</span></span>
<span data-ttu-id="ceb0e-103">Každý .NET Framework poskytovatel dat, který je součástí .NET Framework, má svůj vlastní objekt příkazu, <xref:System.Data.Common.DbCommand>který dědí z.</span><span class="sxs-lookup"><span data-stu-id="ceb0e-103">Each .NET Framework data provider included with the .NET Framework has its own command object that inherits from <xref:System.Data.Common.DbCommand>.</span></span> <span data-ttu-id="ceb0e-104">Zprostředkovatel dat .NET Framework pro OLE DB obsahuje <xref:System.Data.OleDb.OleDbCommand> objekt, .NET Framework Zprostředkovatel dat pro SQL Server <xref:System.Data.SqlClient.SqlCommand> obsahuje objekt, .NET Framework Zprostředkovatel dat pro rozhraní ODBC zahrnuje <xref:System.Data.Odbc.OdbcCommand> objekt a .NET Framework Zprostředkovatel dat pro Oracle obsahuje <xref:System.Data.OracleClient.OracleCommand> objekt.</span><span class="sxs-lookup"><span data-stu-id="ceb0e-104">The .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbCommand> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlCommand> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcCommand> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleCommand> object.</span></span> <span data-ttu-id="ceb0e-105">Každý z těchto objektů zveřejňuje metody pro spouštění příkazů na základě typu příkazu a požadované návratové hodnoty, jak je popsáno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="ceb0e-105">Each of these objects exposes methods for executing commands based on the type of command and desired return value, as described in the following table.</span></span>  
  
|<span data-ttu-id="ceb0e-106">Příkaz</span><span class="sxs-lookup"><span data-stu-id="ceb0e-106">Command</span></span>|<span data-ttu-id="ceb0e-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="ceb0e-107">Return Value</span></span>|  
|-------------|------------------|  
|`ExecuteReader`|<span data-ttu-id="ceb0e-108">Vrátí hodnotu `DataReader` objektu.</span><span class="sxs-lookup"><span data-stu-id="ceb0e-108">Returns a `DataReader` object.</span></span>|  
|`ExecuteScalar`|<span data-ttu-id="ceb0e-109">Vrátí jednu skalární hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ceb0e-109">Returns a single scalar value.</span></span>|  
|`ExecuteNonQuery`|<span data-ttu-id="ceb0e-110">Provede příkaz, který nevrací žádné řádky.</span><span class="sxs-lookup"><span data-stu-id="ceb0e-110">Executes a command that does not return any rows.</span></span>|  
|`ExecuteXMLReader`|<span data-ttu-id="ceb0e-111"><xref:System.Xml.XmlReader>Vrátí.</span><span class="sxs-lookup"><span data-stu-id="ceb0e-111">Returns an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="ceb0e-112">K dispozici `SqlCommand` pouze pro objekt.</span><span class="sxs-lookup"><span data-stu-id="ceb0e-112">Available for a `SqlCommand` object only.</span></span>|  
  
 <span data-ttu-id="ceb0e-113">Každý objekt příkazu silného typu také podporuje <xref:System.Data.CommandType> výčet, který určuje, jak je řetězec příkazu interpretován, jak je popsáno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="ceb0e-113">Each strongly typed command object also supports a <xref:System.Data.CommandType> enumeration that specifies how a command string is interpreted, as described in the following table.</span></span>  
  
|<span data-ttu-id="ceb0e-114">CommandType</span><span class="sxs-lookup"><span data-stu-id="ceb0e-114">CommandType</span></span>|<span data-ttu-id="ceb0e-115">Popis</span><span class="sxs-lookup"><span data-stu-id="ceb0e-115">Description</span></span>|  
|-----------------|-----------------|  
|`Text`|<span data-ttu-id="ceb0e-116">Příkaz SQL definující příkazy, které mají být provedeny ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="ceb0e-116">An SQL command defining the statements to be executed at the data source.</span></span>|  
|`StoredProcedure`|<span data-ttu-id="ceb0e-117">Název uložené procedury.</span><span class="sxs-lookup"><span data-stu-id="ceb0e-117">The name of the stored procedure.</span></span> <span data-ttu-id="ceb0e-118">Můžete použít `Parameters` vlastnost příkazu pro přístup k vstupnímu a výstupnímu parametru a návratovým hodnotám bez ohledu na to `Execute` , která metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="ceb0e-118">You can use the `Parameters` property of a command to access input and output parameters and return values, regardless of which `Execute` method is called.</span></span> <span data-ttu-id="ceb0e-119">Při použití `ExecuteReader`, návratové hodnoty a výstupní parametry nebudou přístupné, `DataReader` dokud není zavřeno.</span><span class="sxs-lookup"><span data-stu-id="ceb0e-119">When using `ExecuteReader`, return values and output parameters will not be accessible until the `DataReader` is closed.</span></span>|  
|`TableDirect`|<span data-ttu-id="ceb0e-120">Název tabulky.</span><span class="sxs-lookup"><span data-stu-id="ceb0e-120">The name of a table.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ceb0e-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="ceb0e-121">Example</span></span>  
 <span data-ttu-id="ceb0e-122">Následující příklad kódu ukazuje, jak vytvořit <xref:System.Data.SqlClient.SqlCommand> objekt pro provedení uložené procedury nastavením vlastností.</span><span class="sxs-lookup"><span data-stu-id="ceb0e-122">The following code example demonstrates how to create a <xref:System.Data.SqlClient.SqlCommand> object to execute a stored procedure by setting its properties.</span></span> <span data-ttu-id="ceb0e-123"><xref:System.Data.SqlClient.SqlParameter> Objekt se používá k určení vstupního parametru pro uloženou proceduru.</span><span class="sxs-lookup"><span data-stu-id="ceb0e-123">A <xref:System.Data.SqlClient.SqlParameter> object is used to specify the input parameter to the stored procedure.</span></span> <span data-ttu-id="ceb0e-124">Příkaz se provede pomocí <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> metody a výstup <xref:System.Data.SqlClient.SqlDataReader> z konzoly se zobrazí v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="ceb0e-124">The command is executed using the <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> method, and the output from the <xref:System.Data.SqlClient.SqlDataReader> is displayed in the console window.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/VB/source.vb#1)]  
  
### <a name="troubleshooting-commands"></a><span data-ttu-id="ceb0e-125">Příkazy pro řešení potíží</span><span class="sxs-lookup"><span data-stu-id="ceb0e-125">Troubleshooting Commands</span></span>  
 <span data-ttu-id="ceb0e-126">.NET Framework Zprostředkovatel dat pro SQL Server přidá čítače výkonu, které vám umožní detekovat občasné problémy související s neúspěšnými prováděními příkazů.</span><span class="sxs-lookup"><span data-stu-id="ceb0e-126">The .NET Framework Data Provider for SQL Server adds performance counters to enable you to detect intermittent problems related to failed command executions.</span></span> <span data-ttu-id="ceb0e-127">Další informace najdete v tématu [čítače výkonu](performance-counters.md).</span><span class="sxs-lookup"><span data-stu-id="ceb0e-127">For more information see [Performance Counters](performance-counters.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ceb0e-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ceb0e-128">See also</span></span>

- [<span data-ttu-id="ceb0e-129">Příkazy a parametry</span><span class="sxs-lookup"><span data-stu-id="ceb0e-129">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="ceb0e-130">Adaptéry a čtečky dat</span><span class="sxs-lookup"><span data-stu-id="ceb0e-130">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="ceb0e-131">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ceb0e-131">ADO.NET Overview</span></span>](ado-net-overview.md)
