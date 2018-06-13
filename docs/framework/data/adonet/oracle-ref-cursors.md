---
title: Kurzory REF Oracle
ms.date: 03/30/2017
ms.assetid: c6b25b8b-0bdd-41b2-9c7c-661f070c2247
ms.openlocfilehash: 7aae9b2e4b39cf164a93ba82212b5705f583d761
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758721"
---
# <a name="oracle-ref-cursors"></a><span data-ttu-id="a8e9f-102">Kurzory REF Oracle</span><span class="sxs-lookup"><span data-stu-id="a8e9f-102">Oracle REF CURSORs</span></span>
<span data-ttu-id="a8e9f-103">Zprostředkovatel dat .NET Framework pro Oracle podporuje Oracle **REF kurzor** datového typu.</span><span class="sxs-lookup"><span data-stu-id="a8e9f-103">The .NET Framework Data Provider for Oracle supports the Oracle **REF CURSOR** data type.</span></span> <span data-ttu-id="a8e9f-104">Při použití zprostředkovatele dat pro práci s kurzory REF Oracle, měli byste zvážit následující chování.</span><span class="sxs-lookup"><span data-stu-id="a8e9f-104">When using the data provider to work with Oracle REF CURSORs, you should consider the following behaviors.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a8e9f-105">Některé chování se liší od zprostředkovatele Microsoft OLE DB pro Oracle (MSDAORA).</span><span class="sxs-lookup"><span data-stu-id="a8e9f-105">Some behaviors differ from those of the Microsoft OLE DB Provider for Oracle (MSDAORA).</span></span>  
  
-   <span data-ttu-id="a8e9f-106">Z důvodů výkonu poskytovatele dat Oracle nemá vazbu automaticky **REF kurzor** datové typy, jako je tomu MSDAORA, pokud je výslovně určit.</span><span class="sxs-lookup"><span data-stu-id="a8e9f-106">For performance reasons, the Data Provider for Oracle does not automatically bind **REF CURSOR** data types, as MSDAORA does, unless you explicitly specify them.</span></span>  
  
-   <span data-ttu-id="a8e9f-107">Poskytovatel dat nepodporuje žádné řídicí sekvence ODBC, včetně řídicí {třídy resultset} slouží k zadání parametry REF KURZORU.</span><span class="sxs-lookup"><span data-stu-id="a8e9f-107">The data provider does not support any ODBC escape sequences, including the {resultset} escape used to specify REF CURSOR parameters.</span></span>  
  
-   <span data-ttu-id="a8e9f-108">K provedení uložené procedury, jež vrátí REF kurzory, je nutné definovat parametry v <xref:System.Data.OracleClient.OracleParameterCollection> s <xref:System.Data.OracleClient.OracleType> z **kurzor** a <xref:System.Data.OracleClient.OracleParameter.Direction%2A> z **výstup**.</span><span class="sxs-lookup"><span data-stu-id="a8e9f-108">To execute a stored procedure that returns REF CURSORs, you must define the parameters in the <xref:System.Data.OracleClient.OracleParameterCollection> with an <xref:System.Data.OracleClient.OracleType> of **Cursor** and a <xref:System.Data.OracleClient.OracleParameter.Direction%2A> of **Output**.</span></span> <span data-ttu-id="a8e9f-109">Zprostředkovatel dat podporuje jako výstupní parametry pouze vazby REF kurzory.</span><span class="sxs-lookup"><span data-stu-id="a8e9f-109">The data provider supports binding REF CURSORs as output parameters only.</span></span> <span data-ttu-id="a8e9f-110">Zprostředkovatel nepodporuje REF kurzory jako vstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="a8e9f-110">The provider does not support REF CURSORs as input parameters.</span></span>  
  
-   <span data-ttu-id="a8e9f-111">Získání <xref:System.Data.OracleClient.OracleDataReader> z parametru hodnota není podporována.</span><span class="sxs-lookup"><span data-stu-id="a8e9f-111">Obtaining an <xref:System.Data.OracleClient.OracleDataReader> from the parameter value is not supported.</span></span> <span data-ttu-id="a8e9f-112">Hodnoty jsou typu <xref:System.DBNull> po provedení příkazu.</span><span class="sxs-lookup"><span data-stu-id="a8e9f-112">The values are of type <xref:System.DBNull> after command execution.</span></span>  
  
-   <span data-ttu-id="a8e9f-113">Jediným **CommandBehavior** hodnota výčtu, která funguje s kurzory REF (například při volání metody <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>) je **CloseConnection**; všechny další se ignorují.</span><span class="sxs-lookup"><span data-stu-id="a8e9f-113">The only **CommandBehavior** enumeration value that works with REF CURSORs (for example, when calling <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>) is **CloseConnection**; all others are ignored.</span></span>  
  
-   <span data-ttu-id="a8e9f-114">Pořadí REF kurzory v **připojení OracleDataReader** v řádu parametrů v závisí **OracleParameterCollection**.</span><span class="sxs-lookup"><span data-stu-id="a8e9f-114">The order of REF CURSORs in the **OracleDataReader** depends on the order of the parameters in the **OracleParameterCollection**.</span></span> <span data-ttu-id="a8e9f-115"><xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> Vlastnost je ignorována.</span><span class="sxs-lookup"><span data-stu-id="a8e9f-115">The <xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> property is ignored.</span></span>  
  
-   <span data-ttu-id="a8e9f-116">PL/SQL **tabulky** datový typ není podporován.</span><span class="sxs-lookup"><span data-stu-id="a8e9f-116">The PL/SQL **TABLE** data type is not supported.</span></span> <span data-ttu-id="a8e9f-117">REF kurzory jsou však efektivnější.</span><span class="sxs-lookup"><span data-stu-id="a8e9f-117">However, REF CURSORs are more efficient.</span></span> <span data-ttu-id="a8e9f-118">Pokud je nutné použít **tabulky** datový typ, použijte zprostředkovatele technologie OLE DB .NET dat s MSDAORA.</span><span class="sxs-lookup"><span data-stu-id="a8e9f-118">If you must use a **TABLE** data type, use the OLE DB .NET Data Provider with MSDAORA.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a8e9f-119">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="a8e9f-119">In This Section</span></span>  
 [<span data-ttu-id="a8e9f-120">Příklady REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="a8e9f-120">REF CURSOR Examples</span></span>](../../../../docs/framework/data/adonet/ref-cursor-examples.md)  
 <span data-ttu-id="a8e9f-121">Obsahuje tři příklady, které ukazují použití REF kurzory.</span><span class="sxs-lookup"><span data-stu-id="a8e9f-121">Contains three examples that demonstrate using REF CURSORs.</span></span>  
  
 [<span data-ttu-id="a8e9f-122">Parametry REF CURSOR v čtečce OracleDataReader</span><span class="sxs-lookup"><span data-stu-id="a8e9f-122">REF CURSOR Parameters in an OracleDataReader</span></span>](../../../../docs/framework/data/adonet/ref-cursor-parameters-in-an-oracledatareader.md)  
 <span data-ttu-id="a8e9f-123">Ukazuje, jak provést PL/SQL uložené procedury, která vrátí parametr REF kurzor a přečte hodnotu jako **připojení OracleDataReader**.</span><span class="sxs-lookup"><span data-stu-id="a8e9f-123">Demonstrates how to execute a PL/SQL stored procedure that returns a REF CURSOR parameter, and reads the value as an **OracleDataReader**.</span></span>  
  
 [<span data-ttu-id="a8e9f-124">Načítání dat z více typů REF CURSOR pomocí čtečky OracleDataReader</span><span class="sxs-lookup"><span data-stu-id="a8e9f-124">Retrieving Data from Multiple REF CURSORs Using an OracleDataReader</span></span>](../../../../docs/framework/data/adonet/retrieving-data-from-multiple-ref-cursors.md)  
 <span data-ttu-id="a8e9f-125">Ukazuje, jak provést PL/SQL uložené procedury, která vrátí dva parametry REF kurzor a přečte hodnoty pomocí **připojení OracleDataReader**.</span><span class="sxs-lookup"><span data-stu-id="a8e9f-125">Demonstrates how to execute a PL/SQL stored procedure that returns two REF CURSOR parameters, and reads the values using an **OracleDataReader**.</span></span>  
  
 [<span data-ttu-id="a8e9f-126">Naplnění datové sady pomocí jednoho nebo více typů REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="a8e9f-126">Filling a DataSet Using One or More REF CURSORs</span></span>](../../../../docs/framework/data/adonet/filling-a-dataset-using-one-or-more-ref-cursors.md)  
 <span data-ttu-id="a8e9f-127">Ukazuje, jak provést PL/SQL uložené procedury, která vrátí dva parametry REF kurzor a výplní <xref:System.Data.DataSet> s řádky, které jsou vráceny.</span><span class="sxs-lookup"><span data-stu-id="a8e9f-127">Demonstrates how to execute a PL/SQL stored procedure that returns two REF CURSOR parameters, and fills a <xref:System.Data.DataSet> with the rows that are returned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8e9f-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="a8e9f-128">See Also</span></span>  
 [<span data-ttu-id="a8e9f-129">Oracle a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a8e9f-129">Oracle and ADO.NET</span></span>](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [<span data-ttu-id="a8e9f-130">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="a8e9f-130">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
