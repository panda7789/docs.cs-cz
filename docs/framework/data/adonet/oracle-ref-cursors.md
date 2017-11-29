---
title: Kurzory REF Oracle
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c6b25b8b-0bdd-41b2-9c7c-661f070c2247
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 277e12e59ea85be4d22e28a59bd7404e5e0111f3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="oracle-ref-cursors"></a><span data-ttu-id="79cde-102">Kurzory REF Oracle</span><span class="sxs-lookup"><span data-stu-id="79cde-102">Oracle REF CURSORs</span></span>
<span data-ttu-id="79cde-103">Zprostředkovatel dat .NET Framework pro Oracle podporuje Oracle **REF kurzor** datového typu.</span><span class="sxs-lookup"><span data-stu-id="79cde-103">The .NET Framework Data Provider for Oracle supports the Oracle **REF CURSOR** data type.</span></span> <span data-ttu-id="79cde-104">Při použití zprostředkovatele dat pro práci s kurzory REF Oracle, měli byste zvážit následující chování.</span><span class="sxs-lookup"><span data-stu-id="79cde-104">When using the data provider to work with Oracle REF CURSORs, you should consider the following behaviors.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="79cde-105">Některé chování se liší od zprostředkovatele Microsoft OLE DB pro Oracle (MSDAORA).</span><span class="sxs-lookup"><span data-stu-id="79cde-105">Some behaviors differ from those of the Microsoft OLE DB Provider for Oracle (MSDAORA).</span></span>  
  
-   <span data-ttu-id="79cde-106">Z důvodů výkonu poskytovatele dat Oracle nemá vazbu automaticky **REF kurzor** datové typy, jako je tomu MSDAORA, pokud je výslovně určit.</span><span class="sxs-lookup"><span data-stu-id="79cde-106">For performance reasons, the Data Provider for Oracle does not automatically bind **REF CURSOR** data types, as MSDAORA does, unless you explicitly specify them.</span></span>  
  
-   <span data-ttu-id="79cde-107">Poskytovatel dat nepodporuje žádné řídicí sekvence ODBC, včetně řídicí {třídy resultset} slouží k zadání parametry REF KURZORU.</span><span class="sxs-lookup"><span data-stu-id="79cde-107">The data provider does not support any ODBC escape sequences, including the {resultset} escape used to specify REF CURSOR parameters.</span></span>  
  
-   <span data-ttu-id="79cde-108">K provedení uložené procedury, jež vrátí REF kurzory, je nutné definovat parametry v <xref:System.Data.OracleClient.OracleParameterCollection> s <xref:System.Data.OracleClient.OracleType> z **kurzor** a <xref:System.Data.OracleClient.OracleParameter.Direction%2A> z **výstup**.</span><span class="sxs-lookup"><span data-stu-id="79cde-108">To execute a stored procedure that returns REF CURSORs, you must define the parameters in the <xref:System.Data.OracleClient.OracleParameterCollection> with an <xref:System.Data.OracleClient.OracleType> of **Cursor** and a <xref:System.Data.OracleClient.OracleParameter.Direction%2A> of **Output**.</span></span> <span data-ttu-id="79cde-109">Zprostředkovatel dat podporuje jako výstupní parametry pouze vazby REF kurzory.</span><span class="sxs-lookup"><span data-stu-id="79cde-109">The data provider supports binding REF CURSORs as output parameters only.</span></span> <span data-ttu-id="79cde-110">Zprostředkovatel nepodporuje REF kurzory jako vstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="79cde-110">The provider does not support REF CURSORs as input parameters.</span></span>  
  
-   <span data-ttu-id="79cde-111">Získání <xref:System.Data.OracleClient.OracleDataReader> z parametru hodnota není podporována.</span><span class="sxs-lookup"><span data-stu-id="79cde-111">Obtaining an <xref:System.Data.OracleClient.OracleDataReader> from the parameter value is not supported.</span></span> <span data-ttu-id="79cde-112">Hodnoty jsou typu <xref:System.DBNull> po provedení příkazu.</span><span class="sxs-lookup"><span data-stu-id="79cde-112">The values are of type <xref:System.DBNull> after command execution.</span></span>  
  
-   <span data-ttu-id="79cde-113">Jediným **CommandBehavior** hodnota výčtu, která funguje s kurzory REF (například při volání metody <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>) je **CloseConnection**; všechny další se ignorují.</span><span class="sxs-lookup"><span data-stu-id="79cde-113">The only **CommandBehavior** enumeration value that works with REF CURSORs (for example, when calling <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A>) is **CloseConnection**; all others are ignored.</span></span>  
  
-   <span data-ttu-id="79cde-114">Pořadí REF kurzory v **připojení OracleDataReader** v řádu parametrů v závisí **OracleParameterCollection**.</span><span class="sxs-lookup"><span data-stu-id="79cde-114">The order of REF CURSORs in the **OracleDataReader** depends on the order of the parameters in the **OracleParameterCollection**.</span></span> <span data-ttu-id="79cde-115"><xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> Vlastnost je ignorována.</span><span class="sxs-lookup"><span data-stu-id="79cde-115">The <xref:System.Data.OracleClient.OracleParameter.ParameterName%2A> property is ignored.</span></span>  
  
-   <span data-ttu-id="79cde-116">PL/SQL **tabulky** datový typ není podporován.</span><span class="sxs-lookup"><span data-stu-id="79cde-116">The PL/SQL **TABLE** data type is not supported.</span></span> <span data-ttu-id="79cde-117">REF kurzory jsou však efektivnější.</span><span class="sxs-lookup"><span data-stu-id="79cde-117">However, REF CURSORs are more efficient.</span></span> <span data-ttu-id="79cde-118">Pokud je nutné použít **tabulky** datový typ, použijte zprostředkovatele technologie OLE DB .NET dat s MSDAORA.</span><span class="sxs-lookup"><span data-stu-id="79cde-118">If you must use a **TABLE** data type, use the OLE DB .NET Data Provider with MSDAORA.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="79cde-119">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="79cde-119">In This Section</span></span>  
 [<span data-ttu-id="79cde-120">Příklady REF KURZORU</span><span class="sxs-lookup"><span data-stu-id="79cde-120">REF CURSOR Examples</span></span>](../../../../docs/framework/data/adonet/ref-cursor-examples.md)  
 <span data-ttu-id="79cde-121">Obsahuje tři příklady, které ukazují použití REF kurzory.</span><span class="sxs-lookup"><span data-stu-id="79cde-121">Contains three examples that demonstrate using REF CURSORs.</span></span>  
  
 [<span data-ttu-id="79cde-122">Parametry KURZORU REF v připojení OracleDataReader</span><span class="sxs-lookup"><span data-stu-id="79cde-122">REF CURSOR Parameters in an OracleDataReader</span></span>](../../../../docs/framework/data/adonet/ref-cursor-parameters-in-an-oracledatareader.md)  
 <span data-ttu-id="79cde-123">Ukazuje, jak provést PL/SQL uložené procedury, která vrátí parametr REF kurzor a přečte hodnotu jako **připojení OracleDataReader**.</span><span class="sxs-lookup"><span data-stu-id="79cde-123">Demonstrates how to execute a PL/SQL stored procedure that returns a REF CURSOR parameter, and reads the value as an **OracleDataReader**.</span></span>  
  
 [<span data-ttu-id="79cde-124">Načítání dat z více REF kurzory pomocí připojení OracleDataReader</span><span class="sxs-lookup"><span data-stu-id="79cde-124">Retrieving Data from Multiple REF CURSORs Using an OracleDataReader</span></span>](../../../../docs/framework/data/adonet/retrieving-data-from-multiple-ref-cursors.md)  
 <span data-ttu-id="79cde-125">Ukazuje, jak provést PL/SQL uložené procedury, která vrátí dva parametry REF kurzor a přečte hodnoty pomocí **připojení OracleDataReader**.</span><span class="sxs-lookup"><span data-stu-id="79cde-125">Demonstrates how to execute a PL/SQL stored procedure that returns two REF CURSOR parameters, and reads the values using an **OracleDataReader**.</span></span>  
  
 [<span data-ttu-id="79cde-126">Naplnění datové sady pomocí jednoho nebo více REF kurzory</span><span class="sxs-lookup"><span data-stu-id="79cde-126">Filling a DataSet Using One or More REF CURSORs</span></span>](../../../../docs/framework/data/adonet/filling-a-dataset-using-one-or-more-ref-cursors.md)  
 <span data-ttu-id="79cde-127">Ukazuje, jak provést PL/SQL uložené procedury, která vrátí dva parametry REF kurzor a výplní <xref:System.Data.DataSet> s řádky, které jsou vráceny.</span><span class="sxs-lookup"><span data-stu-id="79cde-127">Demonstrates how to execute a PL/SQL stored procedure that returns two REF CURSOR parameters, and fills a <xref:System.Data.DataSet> with the rows that are returned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79cde-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="79cde-128">See Also</span></span>  
 [<span data-ttu-id="79cde-129">Oracle a ADO.NET</span><span class="sxs-lookup"><span data-stu-id="79cde-129">Oracle and ADO.NET</span></span>](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [<span data-ttu-id="79cde-130">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="79cde-130">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
