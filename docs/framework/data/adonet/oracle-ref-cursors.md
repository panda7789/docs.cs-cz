---
title: Soubory Oracle REF CURSOR
ms.date: 03/30/2017
ms.assetid: c6b25b8b-0bdd-41b2-9c7c-661f070c2247
ms.openlocfilehash: 7c6b326b15a2af58da9206adf28070e57fec600c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963504"
---
# <a name="oracle-ref-cursors"></a><span data-ttu-id="69ec5-102">Soubory Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="69ec5-102">Oracle REF CURSORs</span></span>
<span data-ttu-id="69ec5-103">Zprostředkovatel dat .NET Framework pro Oracle podporuje datový typ **textový kurzor Oracle ref** .</span><span class="sxs-lookup"><span data-stu-id="69ec5-103">The .NET Framework Data Provider for Oracle supports the Oracle **REF CURSOR** data type.</span></span> <span data-ttu-id="69ec5-104">Pokud používáte zprostředkovatele dat pro práci s REFERENČNÍmi KURZORy Oracle, měli byste zvážit následující chování.</span><span class="sxs-lookup"><span data-stu-id="69ec5-104">When using the data provider to work with Oracle REF CURSORs, you should consider the following behaviors.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="69ec5-105">Některé chování se liší od Zprostředkovatel Microsoft OLE DB pro Oracle (MADAORA).</span><span class="sxs-lookup"><span data-stu-id="69ec5-105">Some behaviors differ from those of the Microsoft OLE DB Provider for Oracle (MSDAORA).</span></span>  
  
- <span data-ttu-id="69ec5-106">Z důvodů výkonu Zprostředkovatel dat pro Oracle automaticky navazovat datové typy **REF CURSOR** , jako madaora, pokud je explicitně neurčíte.</span><span class="sxs-lookup"><span data-stu-id="69ec5-106">For performance reasons, the Data Provider for Oracle does not automatically bind **REF CURSOR** data types, as MSDAORA does, unless you explicitly specify them.</span></span>  
  
- <span data-ttu-id="69ec5-107">Zprostředkovatel dat nepodporuje žádné řídicí sekvence ODBC, včetně řídicího panelu {resultset}, který slouží k zadání parametrů REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="69ec5-107">The data provider does not support any ODBC escape sequences, including the {resultset} escape used to specify REF CURSOR parameters.</span></span>  
  
- <span data-ttu-id="69ec5-108">Chcete-li spustit uloženou proceduru, která vrací referenční kurzory, je nutné definovat <xref:System.Data.OracleClient.OracleParameterCollection> parametry v <xref:System.Data.OracleClient.OracleType> prvku s kurzorem <xref:System.Data.OracleClient.OracleParameter.Direction%2A> a **výstupem**.</span><span class="sxs-lookup"><span data-stu-id="69ec5-108">To execute a stored procedure that returns REF CURSORs, you must define the parameters in the <xref:System.Data.OracleClient.OracleParameterCollection> with an <xref:System.Data.OracleClient.OracleType> of **Cursor** and a <xref:System.Data.OracleClient.OracleParameter.Direction%2A> of **Output**.</span></span> <span data-ttu-id="69ec5-109">Zprostředkovatel dat podporuje vazby referenčních odkazů pouze jako výstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="69ec5-109">The data provider supports binding REF CURSORs as output parameters only.</span></span> <span data-ttu-id="69ec5-110">Zprostředkovatel nepodporuje referenční KURZORy jako vstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="69ec5-110">The provider does not support REF CURSORs as input parameters.</span></span>  
  
- <span data-ttu-id="69ec5-111">Získání hodnoty <xref:System.Data.OracleClient.OracleDataReader> z parametru není podporováno.</span><span class="sxs-lookup"><span data-stu-id="69ec5-111">Obtaining an <xref:System.Data.OracleClient.OracleDataReader> from the parameter value is not supported.</span></span> <span data-ttu-id="69ec5-112">Hodnoty jsou typu <xref:System.DBNull> po provedení příkazu.</span><span class="sxs-lookup"><span data-stu-id="69ec5-112">The values are of type <xref:System.DBNull> after command execution.</span></span>  
  
- <span data-ttu-id="69ec5-113">Jediná hodnota výčtu **CommandBehavior** , která funguje s referenčními kurzory (například při volání <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>), je **CloseConnection**; všechny ostatní jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="69ec5-113">The only **CommandBehavior** enumeration value that works with REF CURSORs (for example, when calling <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>) is **CloseConnection**; all others are ignored.</span></span>  
  
- <span data-ttu-id="69ec5-114">Pořadí REFERENČNÍch KURZORů v **OracleDataReader** závisí na pořadí parametrů v **OracleParameterCollection**.</span><span class="sxs-lookup"><span data-stu-id="69ec5-114">The order of REF CURSORs in the **OracleDataReader** depends on the order of the parameters in the **OracleParameterCollection**.</span></span> <span data-ttu-id="69ec5-115"><xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> Vlastnost je ignorována.</span><span class="sxs-lookup"><span data-stu-id="69ec5-115">The <xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> property is ignored.</span></span>  
  
- <span data-ttu-id="69ec5-116">Datový typ **tabulka** PL/SQL není podporován.</span><span class="sxs-lookup"><span data-stu-id="69ec5-116">The PL/SQL **TABLE** data type is not supported.</span></span> <span data-ttu-id="69ec5-117">Nicméně referenční KURZORy jsou efektivnější.</span><span class="sxs-lookup"><span data-stu-id="69ec5-117">However, REF CURSORs are more efficient.</span></span> <span data-ttu-id="69ec5-118">Pokud je nutné použít datový typ **tabulka** , použijte OLE DB .NET zprostředkovatel dat s madaora.</span><span class="sxs-lookup"><span data-stu-id="69ec5-118">If you must use a **TABLE** data type, use the OLE DB .NET Data Provider with MSDAORA.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="69ec5-119">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="69ec5-119">In This Section</span></span>  
 [<span data-ttu-id="69ec5-120">Příklady REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="69ec5-120">REF CURSOR Examples</span></span>](../../../../docs/framework/data/adonet/ref-cursor-examples.md)  
 <span data-ttu-id="69ec5-121">Obsahuje tři příklady, které ukazují použití REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="69ec5-121">Contains three examples that demonstrate using REF CURSORs.</span></span>  
  
 [<span data-ttu-id="69ec5-122">Parametry REF CURSOR v čtečce OracleDataReader</span><span class="sxs-lookup"><span data-stu-id="69ec5-122">REF CURSOR Parameters in an OracleDataReader</span></span>](../../../../docs/framework/data/adonet/ref-cursor-parameters-in-an-oracledatareader.md)  
 <span data-ttu-id="69ec5-123">Ukazuje, jak spustit uloženou proceduru PL/SQL, která vrací parametr REF CURSOR, a přečte hodnotu jako **OracleDataReader**.</span><span class="sxs-lookup"><span data-stu-id="69ec5-123">Demonstrates how to execute a PL/SQL stored procedure that returns a REF CURSOR parameter, and reads the value as an **OracleDataReader**.</span></span>  
  
 [<span data-ttu-id="69ec5-124">Načítání dat z více typů REF CURSOR pomocí čtečky OracleDataReader</span><span class="sxs-lookup"><span data-stu-id="69ec5-124">Retrieving Data from Multiple REF CURSORs Using an OracleDataReader</span></span>](../../../../docs/framework/data/adonet/retrieving-data-from-multiple-ref-cursors.md)  
 <span data-ttu-id="69ec5-125">Ukazuje, jak spustit uloženou proceduru PL/SQL, která vrací dva parametry REF CURSOR a přečte hodnoty pomocí **OracleDataReader**.</span><span class="sxs-lookup"><span data-stu-id="69ec5-125">Demonstrates how to execute a PL/SQL stored procedure that returns two REF CURSOR parameters, and reads the values using an **OracleDataReader**.</span></span>  
  
 [<span data-ttu-id="69ec5-126">Naplnění datové sady pomocí jednoho nebo více typů REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="69ec5-126">Filling a DataSet Using One or More REF CURSORs</span></span>](../../../../docs/framework/data/adonet/filling-a-dataset-using-one-or-more-ref-cursors.md)  
 <span data-ttu-id="69ec5-127">Ukazuje, jak spustit uloženou proceduru PL/SQL, která vrací dva parametry REF CURSOR a vyplní <xref:System.Data.DataSet> řádky, které jsou vráceny.</span><span class="sxs-lookup"><span data-stu-id="69ec5-127">Demonstrates how to execute a PL/SQL stored procedure that returns two REF CURSOR parameters, and fills a <xref:System.Data.DataSet> with the rows that are returned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69ec5-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="69ec5-128">See also</span></span>

- [<span data-ttu-id="69ec5-129">Oracle a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="69ec5-129">Oracle and ADO.NET</span></span>](../../../../docs/framework/data/adonet/oracle-and-adonet.md)
- [<span data-ttu-id="69ec5-130">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="69ec5-130">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
