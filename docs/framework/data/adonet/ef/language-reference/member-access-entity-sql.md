---
title: . (Přístup ke členu) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4733e3b2-3efa-4b96-b591-ac31350e96ad
ms.openlocfilehash: 6ebedd2b381d035d199e151f64632acf7d502ff5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59139708"
---
# <a name="-member-access-entity-sql"></a><span data-ttu-id="f7118-103">.</span><span class="sxs-lookup"><span data-stu-id="f7118-103">.</span></span> <span data-ttu-id="f7118-104">(Přístup ke členu) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f7118-104">(Member Access) (Entity SQL)</span></span>
<span data-ttu-id="f7118-105">Tečka (.) je [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operátor přístupu členů.</span><span class="sxs-lookup"><span data-stu-id="f7118-105">The dot operator (.) is the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] member access operator.</span></span> <span data-ttu-id="f7118-106">Operátor přístupu členů použijete k získání hodnoty vlastnosti nebo pole instance typu strukturální koncepčního modelu.</span><span class="sxs-lookup"><span data-stu-id="f7118-106">You use the member access operator to yield the value of a property or field of an instance of structural conceptual model type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7118-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7118-107">Syntax</span></span>  
  
```  
expression.identifier  
```  
  
## <a name="arguments"></a><span data-ttu-id="f7118-108">Arguments</span><span class="sxs-lookup"><span data-stu-id="f7118-108">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="f7118-109">Instance typu strukturální koncepčního modelu.</span><span class="sxs-lookup"><span data-stu-id="f7118-109">An instance of a structural conceptual model type.</span></span>  
  
 `identifier`  
 <span data-ttu-id="f7118-110">Vlastnost nebo pole, které patří do instance objektu.</span><span class="sxs-lookup"><span data-stu-id="f7118-110">A property or field that belongs to an object instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7118-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f7118-111">Remarks</span></span>  
 <span data-ttu-id="f7118-112">Tečka (.) slouží k extrakci polí ze záznamu, podobně jako extrahování vlastnosti typu složitá nebo entity.</span><span class="sxs-lookup"><span data-stu-id="f7118-112">The dot (.) operator may be used to extract fields from a record, similar to extracting properties of a complex or entity type.</span></span> <span data-ttu-id="f7118-113">Například pokud n název typu je členem typu osoba, a p je instance typu osoba, pak p.n je právní člen přístup Výraz vracející hodnotu zadejte název.</span><span class="sxs-lookup"><span data-stu-id="f7118-113">For example, if n of type Name is a member of type Person, and p is an instance of type Person, then p.n is a legal member access expression that yields a value of type Name.</span></span>  
  
 `select p.Name.FirstName from LOB.Person as p`  
  
## <a name="see-also"></a><span data-ttu-id="f7118-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f7118-114">See also</span></span>

- [<span data-ttu-id="f7118-115">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f7118-115">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
