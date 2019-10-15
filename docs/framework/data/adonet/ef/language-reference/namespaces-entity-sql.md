---
title: Obory názvů (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 83991c21-60db-4af9-aca3-b416f6cae98e
ms.openlocfilehash: 7f05067c4bdb859f3661f775c2502852b6658522
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319564"
---
# <a name="namespaces-entity-sql"></a><span data-ttu-id="aa3e8-102">Obory názvů (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="aa3e8-102">Namespaces (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="aa3e8-103">zavádí obory názvů, aby nedocházelo ke konfliktům názvů pro globální identifikátory, jako jsou názvy typů, sady entit, funkce a tak dále.</span><span class="sxs-lookup"><span data-stu-id="aa3e8-103">introduces namespaces to avoid name conflicts for global identifiers such as type names, entity sets, functions, and so on.</span></span> <span data-ttu-id="aa3e8-104">Podpora oboru názvů v [!INCLUDE[esql](../../../../../../includes/esql-md.md)] je podobná podpoře oboru názvů v .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="aa3e8-104">The namespace support in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is similar to the namespace support in the .NET Framework.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="aa3e8-105">poskytuje dva formy klauzule USING: kvalifikované obory názvů (kde je k dispozici kratší alias pro obor názvů) a nekvalifikované obory názvů, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="aa3e8-105">provides two forms of the USING clause: qualified namespaces (where a shorter alias is provided for the namespace), and unqualified namespaces, as illustrated in the following example:</span></span>  
  
 `USING System.Data;`  
  
 `USING tsql = System.Data;`  
  
## <a name="name-resolution-rules"></a><span data-ttu-id="aa3e8-106">Pravidla překladu názvů</span><span class="sxs-lookup"><span data-stu-id="aa3e8-106">Name Resolution Rules</span></span>  
 <span data-ttu-id="aa3e8-107">Pokud identifikátor nelze přeložit v místních oborech, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] se pokusí najít název v globálním oboru (obory názvů).</span><span class="sxs-lookup"><span data-stu-id="aa3e8-107">If an identifier cannot be resolved in the local scopes, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to locate the name in the global scopes (the namespaces).</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="aa3e8-108">se nejprve pokusí porovnat identifikátor (předponu) s jedním z kvalifikovaných oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="aa3e8-108">first tries to match the identifier (prefix) with one of the qualified namespaces.</span></span> <span data-ttu-id="aa3e8-109">Pokud se vyskytne shoda, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] se pokusí přeložit zbytek identifikátoru v zadaném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="aa3e8-109">If there is a match, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to resolve the rest of the identifier in the specified namespace.</span></span> <span data-ttu-id="aa3e8-110">Pokud není nalezena žádná shoda, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="aa3e8-110">If no match is found, an exception is thrown.</span></span>  
  
 <span data-ttu-id="aa3e8-111">V dalším kroku se [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pokusí vyhledat všechny nekvalifikované obory názvů (zadané v prologu) pro identifikátor.</span><span class="sxs-lookup"><span data-stu-id="aa3e8-111">Next, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to search all unqualified namespaces (specified in the prolog) for the identifier.</span></span> <span data-ttu-id="aa3e8-112">Pokud identifikátor může být umístěn v přesně jednom oboru názvů, toto umístění je vráceno.</span><span class="sxs-lookup"><span data-stu-id="aa3e8-112">If the identifier can be located in exactly one namespace, that location is returned.</span></span> <span data-ttu-id="aa3e8-113">Pokud má více než jeden obor názvů shodu pro tento identifikátor, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="aa3e8-113">If more than one namespace has a match for that identifier, an exception is thrown.</span></span> <span data-ttu-id="aa3e8-114">Pokud pro identifikátor není možné identifikovat obor názvů, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] předává název do dalšího vnějšího rozsahu (objekt <xref:System.Data.Common.DbCommand> nebo <xref:System.Data.Common.DbConnection>), jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="aa3e8-114">If no namespace can be identified for the identifier, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] passes the name onto the next outward scope (the <xref:System.Data.Common.DbCommand> or <xref:System.Data.Common.DbConnection> object), as illustrated in the following example:</span></span>  
  
```sql  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)  
```  
  
## <a name="differences-from-the-net-framework"></a><span data-ttu-id="aa3e8-115">Rozdíly mezi .NET Framework</span><span class="sxs-lookup"><span data-stu-id="aa3e8-115">Differences from the .NET Framework</span></span>  
 <span data-ttu-id="aa3e8-116">V .NET Framework můžete použít částečně kvalifikované obory názvů.</span><span class="sxs-lookup"><span data-stu-id="aa3e8-116">In the .NET Framework, you can use partially qualified namespaces.</span></span> <span data-ttu-id="aa3e8-117">@no__t – 0 to nepovoluje.</span><span class="sxs-lookup"><span data-stu-id="aa3e8-117">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] does not allow this.</span></span>  
  
## <a name="adonet-usage"></a><span data-ttu-id="aa3e8-118">Využití ADO.NET</span><span class="sxs-lookup"><span data-stu-id="aa3e8-118">ADO.NET Usage</span></span>  
 <span data-ttu-id="aa3e8-119">Dotazy jsou vyjádřeny prostřednictvím objektů ADO.NET <xref:System.Data.Common.DbCommand>.</span><span class="sxs-lookup"><span data-stu-id="aa3e8-119">Queries are expressed through ADO.NET <xref:System.Data.Common.DbCommand> objects.</span></span> <span data-ttu-id="aa3e8-120">objekty <xref:System.Data.Common.DbCommand> lze vytvořit pomocí objektů <xref:System.Data.Common.DbConnection>.</span><span class="sxs-lookup"><span data-stu-id="aa3e8-120"><xref:System.Data.Common.DbCommand> objects can be built over <xref:System.Data.Common.DbConnection> objects.</span></span> <span data-ttu-id="aa3e8-121">Obory názvů lze také zadat jako součást objektů <xref:System.Data.Common.DbCommand> a <xref:System.Data.Common.DbConnection>.</span><span class="sxs-lookup"><span data-stu-id="aa3e8-121">Namespaces can also be specified as part of the <xref:System.Data.Common.DbCommand> and <xref:System.Data.Common.DbConnection> objects.</span></span> <span data-ttu-id="aa3e8-122">Pokud [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nemůže vyřešit identifikátor v rámci samotného dotazu, externí obory názvů se sondují (na základě podobných pravidel).</span><span class="sxs-lookup"><span data-stu-id="aa3e8-122">If [!INCLUDE[esql](../../../../../../includes/esql-md.md)] cannot resolve an identifier within the query itself, the external namespaces are probed (based on similar rules).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa3e8-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aa3e8-123">See also</span></span>

- [<span data-ttu-id="aa3e8-124">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="aa3e8-124">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="aa3e8-125">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="aa3e8-125">Entity SQL Overview</span></span>](entity-sql-overview.md)
