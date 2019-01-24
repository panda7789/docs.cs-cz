---
title: Implements – klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ImplementsClause
helpviewer_keywords:
- interface implementation [Visual Basic], reimplementation
- interface members [Visual Basic], reimplementation
- interface members [Visual Basic], Implements keyword
- interface members
- members [Visual Basic], reimplementation
- interface implementation [Visual Basic], Implements keyword
- interface members [Visual Basic], implementing
- Implements keyword [Visual Basic]
- Implements statement [Visual Basic], about Implements
- members [Visual Basic], implementing
- members [Visual Basic], Implements keyword
- reimplementation
ms.assetid: 5252cdf9-964d-4fc6-af0f-0449b7126b5a
ms.openlocfilehash: cb0ea5ce52effad4df541e6a9196b1faf279262e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54522505"
---
# <a name="implements-clause-visual-basic"></a><span data-ttu-id="fb14a-102">Implements – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fb14a-102">Implements Clause (Visual Basic)</span></span>
<span data-ttu-id="fb14a-103">Označuje, že člen třídy nebo struktury poskytuje implementaci pro člena definovaného v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fb14a-103">Indicates that a class or structure member is providing the implementation for a member defined in an interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb14a-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fb14a-104">Remarks</span></span>  
<span data-ttu-id="fb14a-105">`Implements` – Klíčové slovo není stejný jako [příkaz Implements](../../../visual-basic/language-reference/statements/implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fb14a-105">The `Implements` keyword is not the same as the [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span> <span data-ttu-id="fb14a-106">Můžete použít `Implements` příkaz určíte, že třída nebo struktura, jeden nebo více rozhraní implementuje, a pak použít pro každého člena `Implements` – klíčové slovo k určení, které rozhraní a který člen implementuje.</span><span class="sxs-lookup"><span data-stu-id="fb14a-106">You use the `Implements` statement to specify that a class or structure implements one or more interfaces, and then for each member you use the `Implements` keyword to specify which interface and which member it implements.</span></span>

<span data-ttu-id="fb14a-107">Pokud třída nebo struktura implementuje rozhraní, musí zahrnovat `Implements` příkaz ihned po [Class – příkaz](../../../visual-basic/language-reference/statements/class-statement.md) nebo [Structure – příkaz](../../../visual-basic/language-reference/statements/structure-statement.md), a musí implementovat všechny členy definované rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fb14a-107">If a class or structure implements an interface, it must include the `Implements` statement immediately after the [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) or [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md), and it must implement all the members defined by the interface.</span></span>

## <a name="reimplementation"></a><span data-ttu-id="fb14a-108">Patřící třídě</span><span class="sxs-lookup"><span data-stu-id="fb14a-108">Reimplementation</span></span>  
<span data-ttu-id="fb14a-109">V odvozené třídě můžete znovu implementovat člen rozhraní, která je již implementováno základní třídy.</span><span class="sxs-lookup"><span data-stu-id="fb14a-109">In a derived class, you can reimplement an interface member that the base class has already implemented.</span></span> <span data-ttu-id="fb14a-110">Tím se liší od přepsání člena základní třídy v těchto ohledech:</span><span class="sxs-lookup"><span data-stu-id="fb14a-110">This is different from overriding the base class member in the following respects:</span></span>

- <span data-ttu-id="fb14a-111">Členu základní třídy nemusí být [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) chcete být reimplemented.</span><span class="sxs-lookup"><span data-stu-id="fb14a-111">The base class member does not need to be [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) to be reimplemented.</span></span>
- <span data-ttu-id="fb14a-112">Můžete znovu implementovat člena s jiným názvem.</span><span class="sxs-lookup"><span data-stu-id="fb14a-112">You can reimplement the member with a different name.</span></span>

<span data-ttu-id="fb14a-113">`Implements` – Klíčové slovo lze použít v následujících kontextů:</span><span class="sxs-lookup"><span data-stu-id="fb14a-113">The `Implements` keyword can be used in the following contexts:</span></span>
- [<span data-ttu-id="fb14a-114">Příkaz Event</span><span class="sxs-lookup"><span data-stu-id="fb14a-114">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="fb14a-115">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="fb14a-115">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="fb14a-116">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="fb14a-116">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="fb14a-117">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="fb14a-117">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="fb14a-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fb14a-118">See also</span></span>
- [<span data-ttu-id="fb14a-119">Příkaz Implements</span><span class="sxs-lookup"><span data-stu-id="fb14a-119">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
- [<span data-ttu-id="fb14a-120">Příkaz Interface</span><span class="sxs-lookup"><span data-stu-id="fb14a-120">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="fb14a-121">Příkaz Class</span><span class="sxs-lookup"><span data-stu-id="fb14a-121">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="fb14a-122">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="fb14a-122">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
