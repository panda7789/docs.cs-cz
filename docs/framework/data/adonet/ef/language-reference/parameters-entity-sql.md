---
title: Parametry (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: 8fbca4f10a7c2c3dbaffff978a536b87d31a8df4
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319435"
---
# <a name="parameters-entity-sql"></a><span data-ttu-id="273e2-102">Parametry (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="273e2-102">Parameters (Entity SQL)</span></span>
<span data-ttu-id="273e2-103">Parametry jsou proměnné, které jsou definovány mimo [!INCLUDE[esql](../../../../../../includes/esql-md.md)], obvykle prostřednictvím rozhraní API vazby, které používá jazyk hostitele.</span><span class="sxs-lookup"><span data-stu-id="273e2-103">Parameters are variables that are defined outside [!INCLUDE[esql](../../../../../../includes/esql-md.md)], usually through a binding API that is used by a host language.</span></span> <span data-ttu-id="273e2-104">Každý parametr má název a typ.</span><span class="sxs-lookup"><span data-stu-id="273e2-104">Each parameter has a name and a type.</span></span> <span data-ttu-id="273e2-105">Názvy parametrů jsou definovány ve výrazech dotazů s symbolem (@) jako předponou.</span><span class="sxs-lookup"><span data-stu-id="273e2-105">Parameter names are defined in query expressions with the at (@) symbol as a prefix.</span></span> <span data-ttu-id="273e2-106">Tato vlastnost je nejednoznačná od názvů vlastností nebo jiných názvů, které jsou definovány v dotazu.</span><span class="sxs-lookup"><span data-stu-id="273e2-106">This disambiguates them from the names of properties or other names that are defined in the query.</span></span>  
  
 <span data-ttu-id="273e2-107">Rozhraní API pro vázání v hostitelském jazyce poskytuje rozhraní API pro parametry vazby.</span><span class="sxs-lookup"><span data-stu-id="273e2-107">The host-language binding API provides APIs for binding parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="273e2-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="273e2-108">Example</span></span>  
  
```sql  
SELECT c   
      FROM LOB.Customers AS c   
      WHERE c.Name = @name  
```  
  
## <a name="see-also"></a><span data-ttu-id="273e2-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="273e2-109">See also</span></span>

- [<span data-ttu-id="273e2-110">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="273e2-110">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="273e2-111">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="273e2-111">Entity SQL Overview</span></span>](entity-sql-overview.md)
