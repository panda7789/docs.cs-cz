---
title: ". (Přístup ke členu) (Entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4733e3b2-3efa-4b96-b591-ac31350e96ad
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 36699b403241e9a5496e722e81c833be0ed63101
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="-member-access-entity-sql"></a><span data-ttu-id="4d90c-103">.</span><span class="sxs-lookup"><span data-stu-id="4d90c-103">.</span></span> <span data-ttu-id="4d90c-104">(Přístup ke členu) (Entita SQL)</span><span class="sxs-lookup"><span data-stu-id="4d90c-104">(Member Access) (Entity SQL)</span></span>
<span data-ttu-id="4d90c-105">Operátor tečky (.) je [!INCLUDE[esql](../../../../../../includes/esql-md.md)] operátor přístupu členů.</span><span class="sxs-lookup"><span data-stu-id="4d90c-105">The dot operator (.) is the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] member access operator.</span></span> <span data-ttu-id="4d90c-106">Operátor přístupu členů pomůže yield hodnotu vlastnost nebo pole instance typu strukturální konceptuálního modelu.</span><span class="sxs-lookup"><span data-stu-id="4d90c-106">You use the member access operator to yield the value of a property or field of an instance of structural conceptual model type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d90c-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4d90c-107">Syntax</span></span>  
  
```  
expression.identifier  
```  
  
## <a name="arguments"></a><span data-ttu-id="4d90c-108">Arguments</span><span class="sxs-lookup"><span data-stu-id="4d90c-108">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="4d90c-109">Instance typu strukturální konceptuálního modelu.</span><span class="sxs-lookup"><span data-stu-id="4d90c-109">An instance of a structural conceptual model type.</span></span>  
  
 `identifier`  
 <span data-ttu-id="4d90c-110">Vlastnost nebo pole, které patří k instanci objektu.</span><span class="sxs-lookup"><span data-stu-id="4d90c-110">A property or field that belongs to an object instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d90c-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4d90c-111">Remarks</span></span>  
 <span data-ttu-id="4d90c-112">Operátor tečky (.) slouží k extrakci polí ze záznamu, podobně jako extrahování vlastnosti komplexní nebo entity typu.</span><span class="sxs-lookup"><span data-stu-id="4d90c-112">The dot (.) operator may be used to extract fields from a record, similar to extracting properties of a complex or entity type.</span></span> <span data-ttu-id="4d90c-113">Například pokud n název typu je členem typu osoba, a p je instance typu osoba, p.n je výraz přístup právní člena, jehož výsledkem hodnota typu název.</span><span class="sxs-lookup"><span data-stu-id="4d90c-113">For example, if n of type Name is a member of type Person, and p is an instance of type Person, then p.n is a legal member access expression that yields a value of type Name.</span></span>  
  
 `select p.Name.FirstName from LOB.Person as p`  
  
## <a name="see-also"></a><span data-ttu-id="4d90c-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="4d90c-114">See Also</span></span>  
 [<span data-ttu-id="4d90c-115">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="4d90c-115">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
