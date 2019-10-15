---
title: . (Přístup ke členu) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4733e3b2-3efa-4b96-b591-ac31350e96ad
ms.openlocfilehash: 8e63caba9e9efb91d5c4629b9da0b1feca905ace
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319652"
---
# <a name="-member-access-entity-sql"></a><span data-ttu-id="8a3b8-103">.</span><span class="sxs-lookup"><span data-stu-id="8a3b8-103">.</span></span> <span data-ttu-id="8a3b8-104">(Přístup ke členu) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="8a3b8-104">(Member Access) (Entity SQL)</span></span>
<span data-ttu-id="8a3b8-105">Operátor tečka (.) je operátor přístupu člena [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8a3b8-105">The dot operator (.) is the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] member access operator.</span></span> <span data-ttu-id="8a3b8-106">Operátor přístupu členů slouží k získání hodnoty vlastnosti nebo pole instance strukturálního koncepčního modelu.</span><span class="sxs-lookup"><span data-stu-id="8a3b8-106">You use the member access operator to yield the value of a property or field of an instance of structural conceptual model type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a3b8-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8a3b8-107">Syntax</span></span>  
  
```sql  
expression.identifier  
```  
  
## <a name="arguments"></a><span data-ttu-id="8a3b8-108">Arguments</span><span class="sxs-lookup"><span data-stu-id="8a3b8-108">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="8a3b8-109">Instance strukturálního typu koncepčního modelu.</span><span class="sxs-lookup"><span data-stu-id="8a3b8-109">An instance of a structural conceptual model type.</span></span>  
  
 `identifier`  
 <span data-ttu-id="8a3b8-110">Vlastnost nebo pole, které patří do instance objektu.</span><span class="sxs-lookup"><span data-stu-id="8a3b8-110">A property or field that belongs to an object instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a3b8-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8a3b8-111">Remarks</span></span>  
 <span data-ttu-id="8a3b8-112">Operátor tečka (.) se dá použít k extrakci polí ze záznamu, podobně jako extrakce vlastností komplexního typu nebo typu entity.</span><span class="sxs-lookup"><span data-stu-id="8a3b8-112">The dot (.) operator may be used to extract fields from a record, similar to extracting properties of a complex or entity type.</span></span> <span data-ttu-id="8a3b8-113">Například pokud n typu názvu je členem typu Person a p je instance typu person, pak p. n je platným výrazem přístupu člena, který je výsledkem hodnoty typu název.</span><span class="sxs-lookup"><span data-stu-id="8a3b8-113">For example, if n of type Name is a member of type Person, and p is an instance of type Person, then p.n is a legal member access expression that yields a value of type Name.</span></span>  
  
 `select p.Name.FirstName from LOB.Person as p`  
  
## <a name="see-also"></a><span data-ttu-id="8a3b8-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8a3b8-114">See also</span></span>

- [<span data-ttu-id="8a3b8-115">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="8a3b8-115">Entity SQL Reference</span></span>](entity-sql-reference.md)
