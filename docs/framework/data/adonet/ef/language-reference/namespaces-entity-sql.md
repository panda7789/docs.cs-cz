---
title: "Obory názvů (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 83991c21-60db-4af9-aca3-b416f6cae98e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 1f97b28bce20fa71f82942fa5f123d7c2ac6616a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="namespaces-entity-sql"></a><span data-ttu-id="cb9cb-102">Obory názvů (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="cb9cb-102">Namespaces (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="cb9cb-103">představuje obory názvů, aby nedocházelo ke konfliktům název pro globální identifikátory například názvy typů, sady entit, funkce a tak dále.</span><span class="sxs-lookup"><span data-stu-id="cb9cb-103"> introduces namespaces to avoid name conflicts for global identifiers such as type names, entity sets, functions, and so on.</span></span> <span data-ttu-id="cb9cb-104">Podpora oboru názvů v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] je podobná podpora oboru názvů v [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cb9cb-104">The namespace support in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is similar to the namespace support in the [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)].</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="cb9cb-105">poskytuje dvě formy v klauzuli USING: kvalifikovaný obory názvů (kde alias kratší je zadáno pro obor názvů) a nekvalifikované obory názvů, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="cb9cb-105"> provides two forms of the USING clause: qualified namespaces (where a shorter alias is provided for the namespace), and unqualified namespaces, as illustrated in the following example:</span></span>  
  
 `USING System.Data;`  
  
 `USING tsql = System.Data;`  
  
## <a name="name-resolution-rules"></a><span data-ttu-id="cb9cb-106">Název pravidla překladu</span><span class="sxs-lookup"><span data-stu-id="cb9cb-106">Name Resolution Rules</span></span>  
 <span data-ttu-id="cb9cb-107">Pokud v místní obory, nelze přeložit identifikátor [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pokusí vyhledat název v globálních oborech (obory názvů).</span><span class="sxs-lookup"><span data-stu-id="cb9cb-107">If an identifier cannot be resolved in the local scopes, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to locate the name in the global scopes (the namespaces).</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="cb9cb-108">poprvé pokusí o shodovat s identifikátorem (předpona) s jedním z kvalifikovaný obory názvů.</span><span class="sxs-lookup"><span data-stu-id="cb9cb-108"> first tries to match the identifier (prefix) with one of the qualified namespaces.</span></span> <span data-ttu-id="cb9cb-109">Pokud není nalezena shoda, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zkusí vyřešit zbytek identifikátoru v určeném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="cb9cb-109">If there is a match, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to resolve the rest of the identifier in the specified namespace.</span></span> <span data-ttu-id="cb9cb-110">Pokud není nalezena žádná shoda, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="cb9cb-110">If no match is found, an exception is thrown.</span></span>  
  
 <span data-ttu-id="cb9cb-111">Dále [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pokusí vyhledat všechny neúplné obory názvů (zadané v prologu) pro identifikátor.</span><span class="sxs-lookup"><span data-stu-id="cb9cb-111">Next, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to search all unqualified namespaces (specified in the prolog) for the identifier.</span></span> <span data-ttu-id="cb9cb-112">Pokud identifikátor může být umístěno v přesně jeden obor názvů, je vrácena tohoto umístění.</span><span class="sxs-lookup"><span data-stu-id="cb9cb-112">If the identifier can be located in exactly one namespace, that location is returned.</span></span> <span data-ttu-id="cb9cb-113">Pokud má více než jeden obor názvů shody pro tento identifikátor, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="cb9cb-113">If more than one namespace has a match for that identifier, an exception is thrown.</span></span> <span data-ttu-id="cb9cb-114">Pokud žádný obor názvů může identifikovat pro identifikátor, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] předává název na další pasivním rozsahu ( <xref:System.Data.Common.DbCommand> nebo <xref:System.Data.Common.DbConnection> objektu), jak je popsáno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="cb9cb-114">If no namespace can be identified for the identifier, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] passes the name onto the next outward scope (the <xref:System.Data.Common.DbCommand> or <xref:System.Data.Common.DbConnection> object), as illustrated in the following example:</span></span>  
  
```  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)  
```  
  
## <a name="differences-from-the-net-framework"></a><span data-ttu-id="cb9cb-115">Rozdíl oproti rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="cb9cb-115">Differences from the .NET Framework</span></span>  
 <span data-ttu-id="cb9cb-116">V [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)], můžete použít částečně kvalifikovaný obory názvů.</span><span class="sxs-lookup"><span data-stu-id="cb9cb-116">In the [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)], you can use partially qualified namespaces.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="cb9cb-117">neumožňuje to.</span><span class="sxs-lookup"><span data-stu-id="cb9cb-117"> does not allow this.</span></span>  
  
## <a name="adonet-usage"></a><span data-ttu-id="cb9cb-118">Použití technologie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="cb9cb-118">ADO.NET Usage</span></span>  
 <span data-ttu-id="cb9cb-119">Dotazy jsou vyjádřit pomocí ADO.NET <xref:System.Data.Common.DbCommand> objekty.</span><span class="sxs-lookup"><span data-stu-id="cb9cb-119">Queries are expressed through ADO.NET <xref:System.Data.Common.DbCommand> objects.</span></span> <span data-ttu-id="cb9cb-120"><xref:System.Data.Common.DbCommand>objekty se dají vytvářet přes <xref:System.Data.Common.DbConnection> objekty.</span><span class="sxs-lookup"><span data-stu-id="cb9cb-120"><xref:System.Data.Common.DbCommand> objects can be built over <xref:System.Data.Common.DbConnection> objects.</span></span> <span data-ttu-id="cb9cb-121">Obory názvů, můžete také zadat jako součást <xref:System.Data.Common.DbCommand> a <xref:System.Data.Common.DbConnection> objekty.</span><span class="sxs-lookup"><span data-stu-id="cb9cb-121">Namespaces can also be specified as part of the <xref:System.Data.Common.DbCommand> and <xref:System.Data.Common.DbConnection> objects.</span></span> <span data-ttu-id="cb9cb-122">Pokud [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nelze přeložit identifikátor v samotném dotazu jsou zjištěný externí obory názvů (podle pravidla podobné).</span><span class="sxs-lookup"><span data-stu-id="cb9cb-122">If [!INCLUDE[esql](../../../../../../includes/esql-md.md)] cannot resolve an identifier within the query itself, the external namespaces are probed (based on similar rules).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb9cb-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="cb9cb-123">See Also</span></span>  
 [<span data-ttu-id="cb9cb-124">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="cb9cb-124">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="cb9cb-125">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="cb9cb-125">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
