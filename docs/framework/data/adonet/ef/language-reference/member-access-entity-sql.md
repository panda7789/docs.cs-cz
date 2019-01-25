---
title: . (Přístup ke členu) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4733e3b2-3efa-4b96-b591-ac31350e96ad
ms.openlocfilehash: e2874e5bff8d8c34f700a81bf52c6729df49aca5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54626666"
---
# <a name="-member-access-entity-sql"></a><span data-ttu-id="d0664-103">.</span><span class="sxs-lookup"><span data-stu-id="d0664-103">.</span></span> <span data-ttu-id="d0664-104">(Přístup ke členu) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="d0664-104">(Member Access) (Entity SQL)</span></span>
<span data-ttu-id="d0664-105">Tečka (.) je [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operátor přístupu členů.</span><span class="sxs-lookup"><span data-stu-id="d0664-105">The dot operator (.) is the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] member access operator.</span></span> <span data-ttu-id="d0664-106">Operátor přístupu členů použijete k získání hodnoty vlastnosti nebo pole instance typu strukturální koncepčního modelu.</span><span class="sxs-lookup"><span data-stu-id="d0664-106">You use the member access operator to yield the value of a property or field of an instance of structural conceptual model type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0664-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d0664-107">Syntax</span></span>  
  
```  
expression.identifier  
```  
  
## <a name="arguments"></a><span data-ttu-id="d0664-108">Arguments</span><span class="sxs-lookup"><span data-stu-id="d0664-108">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="d0664-109">Instance typu strukturální koncepčního modelu.</span><span class="sxs-lookup"><span data-stu-id="d0664-109">An instance of a structural conceptual model type.</span></span>  
  
 `identifier`  
 <span data-ttu-id="d0664-110">Vlastnost nebo pole, které patří do instance objektu.</span><span class="sxs-lookup"><span data-stu-id="d0664-110">A property or field that belongs to an object instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0664-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d0664-111">Remarks</span></span>  
 <span data-ttu-id="d0664-112">Tečka (.) slouží k extrakci polí ze záznamu, podobně jako extrahování vlastnosti typu složitá nebo entity.</span><span class="sxs-lookup"><span data-stu-id="d0664-112">The dot (.) operator may be used to extract fields from a record, similar to extracting properties of a complex or entity type.</span></span> <span data-ttu-id="d0664-113">Například pokud n název typu je členem typu osoba, a p je instance typu osoba, pak p.n je právní člen přístup Výraz vracející hodnotu zadejte název.</span><span class="sxs-lookup"><span data-stu-id="d0664-113">For example, if n of type Name is a member of type Person, and p is an instance of type Person, then p.n is a legal member access expression that yields a value of type Name.</span></span>  
  
 `select p.Name.FirstName from LOB.Person as p`  
  
## <a name="see-also"></a><span data-ttu-id="d0664-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d0664-114">See also</span></span>
- [<span data-ttu-id="d0664-115">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="d0664-115">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
