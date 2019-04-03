---
title: <type1>"<typename>musí implementovat<methodname>'pro rozhraní'<interfacename>.
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: b8bcb16798284a09608ba6942226ef07c6859d4f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824193"
---
# <a name="type1typename-must-implement-methodname-for-interface-interfacename"></a><span data-ttu-id="9cbfe-102">\<Type1 >'\<typename >' musí implementovat '\<methodname > "rozhraní"\<interfacename > "</span><span class="sxs-lookup"><span data-stu-id="9cbfe-102">\<type1>'\<typename>' must implement '\<methodname>' for interface '\<interfacename>'</span></span>
<span data-ttu-id="9cbfe-103">Třída nebo struktura, deklarací identity pro implementaci rozhraní, ale neimplementuje postupu definované rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9cbfe-103">A class or structure claims to implement an interface but does not implement a procedure defined by the interface.</span></span> <span data-ttu-id="9cbfe-104">Musíte implementovat každého člena rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9cbfe-104">Every member of the interface must be implemented.</span></span>  
  
 <span data-ttu-id="9cbfe-105">**ID chyby:** BC30149</span><span class="sxs-lookup"><span data-stu-id="9cbfe-105">**Error ID:** BC30149</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9cbfe-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="9cbfe-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="9cbfe-107">Procedura se stejným názvem a signaturou, jak jsou definovány v rozhraní deklarujte.</span><span class="sxs-lookup"><span data-stu-id="9cbfe-107">Declare a procedure with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="9cbfe-108">Nezapomeňte uvést alespoň `End Function` nebo `End Sub` příkazu.</span><span class="sxs-lookup"><span data-stu-id="9cbfe-108">Be sure to include at least the `End Function` or `End Sub` statement.</span></span>  
  
2.  <span data-ttu-id="9cbfe-109">Přidat `Implements` klauzuli na konec objektu `Function` nebo `Sub` příkazu.</span><span class="sxs-lookup"><span data-stu-id="9cbfe-109">Add an `Implements` clause to the end of the `Function` or `Sub` statement.</span></span> <span data-ttu-id="9cbfe-110">Příklad:</span><span class="sxs-lookup"><span data-stu-id="9cbfe-110">For example:</span></span>  
  
    ```  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="9cbfe-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9cbfe-111">See also</span></span>

- [<span data-ttu-id="9cbfe-112">Příkaz Implements</span><span class="sxs-lookup"><span data-stu-id="9cbfe-112">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
- [<span data-ttu-id="9cbfe-113">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="9cbfe-113">Interfaces</span></span>](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
