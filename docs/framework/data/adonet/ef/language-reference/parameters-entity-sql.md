---
title: Parametry (entita SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: e1bb633f7f7c7908a5f424991f20a5cd89aee5aa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150011"
---
# <a name="parameters-entity-sql"></a><span data-ttu-id="ae671-102">Parametry (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="ae671-102">Parameters (Entity SQL)</span></span>
<span data-ttu-id="ae671-103">Parametry jsou proměnné, které [!INCLUDE[esql](../../../../../../includes/esql-md.md)]jsou definovány mimo , obvykle prostřednictvím rozhraní API vazby, které používá hostitelský jazyk.</span><span class="sxs-lookup"><span data-stu-id="ae671-103">Parameters are variables that are defined outside [!INCLUDE[esql](../../../../../../includes/esql-md.md)], usually through a binding API that is used by a host language.</span></span> <span data-ttu-id="ae671-104">Každý parametr má název a typ.</span><span class="sxs-lookup"><span data-stu-id="ae671-104">Each parameter has a name and a type.</span></span> <span data-ttu-id="ae671-105">Názvy parametrů jsou definovány ve výrazech dotazu se symbolem at (@) jako předponou.</span><span class="sxs-lookup"><span data-stu-id="ae671-105">Parameter names are defined in query expressions with the at (@) symbol as a prefix.</span></span> <span data-ttu-id="ae671-106">To je rozptýluje od názvů vlastností nebo jiných názvů, které jsou definovány v dotazu.</span><span class="sxs-lookup"><span data-stu-id="ae671-106">This disambiguates them from the names of properties or other names that are defined in the query.</span></span>  
  
 <span data-ttu-id="ae671-107">Rozhraní API vazby hostitelského jazyka poskytuje rozhraní API pro parametry vazby.</span><span class="sxs-lookup"><span data-stu-id="ae671-107">The host-language binding API provides APIs for binding parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae671-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="ae671-108">Example</span></span>  
  
```sql  
SELECT c
      FROM LOB.Customers AS c
      WHERE c.Name = @name  
```  
  
## <a name="see-also"></a><span data-ttu-id="ae671-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="ae671-109">See also</span></span>

- [<span data-ttu-id="ae671-110">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="ae671-110">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="ae671-111">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="ae671-111">Entity SQL Overview</span></span>](entity-sql-overview.md)
