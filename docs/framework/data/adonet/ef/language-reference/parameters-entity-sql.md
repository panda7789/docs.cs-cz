---
title: Parametry (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8d618edd-0988-4ff2-8263-ce59448af7a5
ms.openlocfilehash: 723e40f523f8bb573e0ffcb1863ed0c082ea9d8d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249589"
---
# <a name="parameters-entity-sql"></a><span data-ttu-id="2b61f-102">Parametry (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="2b61f-102">Parameters (Entity SQL)</span></span>
<span data-ttu-id="2b61f-103">Parametry jsou proměnné, které jsou definovány [!INCLUDE[esql](../../../../../../includes/esql-md.md)]mimo, obvykle prostřednictvím rozhraní API vazby, které používá jazyk hostitele.</span><span class="sxs-lookup"><span data-stu-id="2b61f-103">Parameters are variables that are defined outside [!INCLUDE[esql](../../../../../../includes/esql-md.md)], usually through a binding API that is used by a host language.</span></span> <span data-ttu-id="2b61f-104">Každý parametr má název a typ.</span><span class="sxs-lookup"><span data-stu-id="2b61f-104">Each parameter has a name and a type.</span></span> <span data-ttu-id="2b61f-105">Názvy parametrů jsou definovány ve výrazech dotazů s symbolem (@) jako předponou.</span><span class="sxs-lookup"><span data-stu-id="2b61f-105">Parameter names are defined in query expressions with the at (@) symbol as a prefix.</span></span> <span data-ttu-id="2b61f-106">Tato vlastnost je nejednoznačná od názvů vlastností nebo jiných názvů, které jsou definovány v dotazu.</span><span class="sxs-lookup"><span data-stu-id="2b61f-106">This disambiguates them from the names of properties or other names that are defined in the query.</span></span>  
  
 <span data-ttu-id="2b61f-107">Rozhraní API pro vázání v hostitelském jazyce poskytuje rozhraní API pro parametry vazby.</span><span class="sxs-lookup"><span data-stu-id="2b61f-107">The host-language binding API provides APIs for binding parameters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b61f-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="2b61f-108">Example</span></span>  
  
```  
select c   
      from LOB.Customers as c   
      where c.Name = @name  
```  
  
## <a name="see-also"></a><span data-ttu-id="2b61f-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2b61f-109">See also</span></span>

- [<span data-ttu-id="2b61f-110">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="2b61f-110">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="2b61f-111">Přehled Entity SQL</span><span class="sxs-lookup"><span data-stu-id="2b61f-111">Entity SQL Overview</span></span>](entity-sql-overview.md)
