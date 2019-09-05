---
title: . (Přístup ke členu) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4733e3b2-3efa-4b96-b591-ac31350e96ad
ms.openlocfilehash: 1db6be632da90eaa7a761bb213e395182ae42347
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250298"
---
# <a name="-member-access-entity-sql"></a><span data-ttu-id="4db96-103">.</span><span class="sxs-lookup"><span data-stu-id="4db96-103">.</span></span> <span data-ttu-id="4db96-104">(Přístup ke členu) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="4db96-104">(Member Access) (Entity SQL)</span></span>
<span data-ttu-id="4db96-105">Operátor tečka (.) je [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operátor přístupu členů.</span><span class="sxs-lookup"><span data-stu-id="4db96-105">The dot operator (.) is the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] member access operator.</span></span> <span data-ttu-id="4db96-106">Operátor přístupu členů slouží k získání hodnoty vlastnosti nebo pole instance strukturálního koncepčního modelu.</span><span class="sxs-lookup"><span data-stu-id="4db96-106">You use the member access operator to yield the value of a property or field of an instance of structural conceptual model type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4db96-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4db96-107">Syntax</span></span>  
  
```  
expression.identifier  
```  
  
## <a name="arguments"></a><span data-ttu-id="4db96-108">Arguments</span><span class="sxs-lookup"><span data-stu-id="4db96-108">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="4db96-109">Instance strukturálního typu koncepčního modelu.</span><span class="sxs-lookup"><span data-stu-id="4db96-109">An instance of a structural conceptual model type.</span></span>  
  
 `identifier`  
 <span data-ttu-id="4db96-110">Vlastnost nebo pole, které patří do instance objektu.</span><span class="sxs-lookup"><span data-stu-id="4db96-110">A property or field that belongs to an object instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4db96-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4db96-111">Remarks</span></span>  
 <span data-ttu-id="4db96-112">Operátor tečka (.) se dá použít k extrakci polí ze záznamu, podobně jako extrakce vlastností komplexního typu nebo typu entity.</span><span class="sxs-lookup"><span data-stu-id="4db96-112">The dot (.) operator may be used to extract fields from a record, similar to extracting properties of a complex or entity type.</span></span> <span data-ttu-id="4db96-113">Například pokud n typu názvu je členem typu Person a p je instance typu person, pak p. n je platným výrazem přístupu člena, který je výsledkem hodnoty typu název.</span><span class="sxs-lookup"><span data-stu-id="4db96-113">For example, if n of type Name is a member of type Person, and p is an instance of type Person, then p.n is a legal member access expression that yields a value of type Name.</span></span>  
  
 `select p.Name.FirstName from LOB.Person as p`  
  
## <a name="see-also"></a><span data-ttu-id="4db96-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4db96-114">See also</span></span>

- [<span data-ttu-id="4db96-115">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="4db96-115">Entity SQL Reference</span></span>](entity-sql-reference.md)
