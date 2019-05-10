---
title: Soubory Oracle REF CURSOR
ms.date: 03/30/2017
ms.assetid: c6b25b8b-0bdd-41b2-9c7c-661f070c2247
ms.openlocfilehash: 0a98bfd401aaabfb754c422cc753bc5092f9f76c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64633342"
---
# <a name="oracle-ref-cursors"></a><span data-ttu-id="180e0-102">Soubory Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="180e0-102">Oracle REF CURSORs</span></span>
<span data-ttu-id="180e0-103">Zprostředkovatel dat .NET Framework pro Oracle podporuje Oracle **REF CURSOR** datového typu.</span><span class="sxs-lookup"><span data-stu-id="180e0-103">The .NET Framework Data Provider for Oracle supports the Oracle **REF CURSOR** data type.</span></span> <span data-ttu-id="180e0-104">Při použití zprostředkovatele dat pro práci se soubory Oracle REF CURSOR, měli byste zvážit následující chování.</span><span class="sxs-lookup"><span data-stu-id="180e0-104">When using the data provider to work with Oracle REF CURSORs, you should consider the following behaviors.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="180e0-105">Některá chování se liší od těch, které zprostředkovatel Microsoft OLE DB pro Oracle (MSDAORA).</span><span class="sxs-lookup"><span data-stu-id="180e0-105">Some behaviors differ from those of the Microsoft OLE DB Provider for Oracle (MSDAORA).</span></span>  
  
- <span data-ttu-id="180e0-106">Z důvodů výkonu Data Provider pro Oracle nemá vazbu automaticky **REF CURSOR** datové typy, stejně jako MSDAORA, pokud je explicitně neurčíte.</span><span class="sxs-lookup"><span data-stu-id="180e0-106">For performance reasons, the Data Provider for Oracle does not automatically bind **REF CURSOR** data types, as MSDAORA does, unless you explicitly specify them.</span></span>  
  
- <span data-ttu-id="180e0-107">Poskytovatel dat nepodporuje žádné ODBC řídicí sekvence, včetně řídicí {třídy resultset} používá k určení parametry REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="180e0-107">The data provider does not support any ODBC escape sequences, including the {resultset} escape used to specify REF CURSOR parameters.</span></span>  
  
- <span data-ttu-id="180e0-108">K provedení uložené procedury, která vrací typů REF CURSOR, je nutné definovat parametry <xref:System.Data.OracleClient.OracleParameterCollection> s <xref:System.Data.OracleClient.OracleType> z **kurzor** a <xref:System.Data.OracleClient.OracleParameter.Direction%2A> z **výstup**.</span><span class="sxs-lookup"><span data-stu-id="180e0-108">To execute a stored procedure that returns REF CURSORs, you must define the parameters in the <xref:System.Data.OracleClient.OracleParameterCollection> with an <xref:System.Data.OracleClient.OracleType> of **Cursor** and a <xref:System.Data.OracleClient.OracleParameter.Direction%2A> of **Output**.</span></span> <span data-ttu-id="180e0-109">Zprostředkovatel dat podporuje jako výstupní parametry pouze vazby typů REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="180e0-109">The data provider supports binding REF CURSORs as output parameters only.</span></span> <span data-ttu-id="180e0-110">Zprostředkovatel nepodporuje typů REF CURSOR jako vstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="180e0-110">The provider does not support REF CURSORs as input parameters.</span></span>  
  
- <span data-ttu-id="180e0-111">Získání <xref:System.Data.OracleClient.OracleDataReader> z parametru hodnota není podporována.</span><span class="sxs-lookup"><span data-stu-id="180e0-111">Obtaining an <xref:System.Data.OracleClient.OracleDataReader> from the parameter value is not supported.</span></span> <span data-ttu-id="180e0-112">Hodnoty jsou typu <xref:System.DBNull> po spuštění příkazu.</span><span class="sxs-lookup"><span data-stu-id="180e0-112">The values are of type <xref:System.DBNull> after command execution.</span></span>  
  
- <span data-ttu-id="180e0-113">Jediná **CommandBehavior** hodnota výčtu, která funguje s typů REF CURSOR (například při volání metody <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>) je **CloseConnection**; případné další se ignorují.</span><span class="sxs-lookup"><span data-stu-id="180e0-113">The only **CommandBehavior** enumeration value that works with REF CURSORs (for example, when calling <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>) is **CloseConnection**; all others are ignored.</span></span>  
  
- <span data-ttu-id="180e0-114">Pořadí typů REF CURSOR v **připojení OracleDataReader** pořadí parametrů v závisí **OracleParameterCollection**.</span><span class="sxs-lookup"><span data-stu-id="180e0-114">The order of REF CURSORs in the **OracleDataReader** depends on the order of the parameters in the **OracleParameterCollection**.</span></span> <span data-ttu-id="180e0-115"><xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> Vlastnost se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="180e0-115">The <xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> property is ignored.</span></span>  
  
- <span data-ttu-id="180e0-116">PL/SQL **tabulky** datový typ není podporován.</span><span class="sxs-lookup"><span data-stu-id="180e0-116">The PL/SQL **TABLE** data type is not supported.</span></span> <span data-ttu-id="180e0-117">Typů REF CURSOR jsou však efektivnější.</span><span class="sxs-lookup"><span data-stu-id="180e0-117">However, REF CURSORs are more efficient.</span></span> <span data-ttu-id="180e0-118">Pokud je nutné použít **tabulky** datový typ, použijte zprostředkovatele OLE DB .NET Data Provider s MSDAORA.</span><span class="sxs-lookup"><span data-stu-id="180e0-118">If you must use a **TABLE** data type, use the OLE DB .NET Data Provider with MSDAORA.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="180e0-119">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="180e0-119">In This Section</span></span>  
 [<span data-ttu-id="180e0-120">Příklady REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="180e0-120">REF CURSOR Examples</span></span>](../../../../docs/framework/data/adonet/ref-cursor-examples.md)  
 <span data-ttu-id="180e0-121">Obsahuje tři příklady, které ukazují používání typů REF CURSOR.</span><span class="sxs-lookup"><span data-stu-id="180e0-121">Contains three examples that demonstrate using REF CURSORs.</span></span>  
  
 [<span data-ttu-id="180e0-122">Parametry REF CURSOR v čtečce OracleDataReader</span><span class="sxs-lookup"><span data-stu-id="180e0-122">REF CURSOR Parameters in an OracleDataReader</span></span>](../../../../docs/framework/data/adonet/ref-cursor-parameters-in-an-oracledatareader.md)  
 <span data-ttu-id="180e0-123">Ukazuje, jak provést PL/uložené procedury SQL, který vrací parametr REF CURSOR a přečte hodnotu jako **připojení OracleDataReader**.</span><span class="sxs-lookup"><span data-stu-id="180e0-123">Demonstrates how to execute a PL/SQL stored procedure that returns a REF CURSOR parameter, and reads the value as an **OracleDataReader**.</span></span>  
  
 [<span data-ttu-id="180e0-124">Načítání dat z více typů REF CURSOR pomocí čtečky OracleDataReader</span><span class="sxs-lookup"><span data-stu-id="180e0-124">Retrieving Data from Multiple REF CURSORs Using an OracleDataReader</span></span>](../../../../docs/framework/data/adonet/retrieving-data-from-multiple-ref-cursors.md)  
 <span data-ttu-id="180e0-125">Ukazuje, jak provést PL/SQL uložené procedury, která vrací dva parametry REF CURSOR a čte hodnoty pomocí **připojení OracleDataReader**.</span><span class="sxs-lookup"><span data-stu-id="180e0-125">Demonstrates how to execute a PL/SQL stored procedure that returns two REF CURSOR parameters, and reads the values using an **OracleDataReader**.</span></span>  
  
 [<span data-ttu-id="180e0-126">Naplnění datové sady pomocí jednoho nebo více typů REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="180e0-126">Filling a DataSet Using One or More REF CURSORs</span></span>](../../../../docs/framework/data/adonet/filling-a-dataset-using-one-or-more-ref-cursors.md)  
 <span data-ttu-id="180e0-127">Ukazuje, jak provést PL/SQL uložené procedury, která vrací dva parametry REF CURSOR a doplní <xref:System.Data.DataSet> s řádky, které jsou vráceny.</span><span class="sxs-lookup"><span data-stu-id="180e0-127">Demonstrates how to execute a PL/SQL stored procedure that returns two REF CURSOR parameters, and fills a <xref:System.Data.DataSet> with the rows that are returned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="180e0-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="180e0-128">See also</span></span>

- [<span data-ttu-id="180e0-129">Oracle a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="180e0-129">Oracle and ADO.NET</span></span>](../../../../docs/framework/data/adonet/oracle-and-adonet.md)
- [<span data-ttu-id="180e0-130">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="180e0-130">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
