---
title: Implements – klauzule
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
ms.openlocfilehash: f114aee75356e59eafd9d3ba6af9c64402cb374f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345875"
---
# <a name="implements-clause-visual-basic"></a><span data-ttu-id="3c208-102">Implements – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c208-102">Implements Clause (Visual Basic)</span></span>
<span data-ttu-id="3c208-103">Indicates that a class or structure member is providing the implementation for a member defined in an interface.</span><span class="sxs-lookup"><span data-stu-id="3c208-103">Indicates that a class or structure member is providing the implementation for a member defined in an interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c208-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3c208-104">Remarks</span></span>  
<span data-ttu-id="3c208-105">The `Implements` keyword is not the same as the [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3c208-105">The `Implements` keyword is not the same as the [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span> <span data-ttu-id="3c208-106">You use the `Implements` statement to specify that a class or structure implements one or more interfaces, and then for each member you use the `Implements` keyword to specify which interface and which member it implements.</span><span class="sxs-lookup"><span data-stu-id="3c208-106">You use the `Implements` statement to specify that a class or structure implements one or more interfaces, and then for each member you use the `Implements` keyword to specify which interface and which member it implements.</span></span>

<span data-ttu-id="3c208-107">If a class or structure implements an interface, it must include the `Implements` statement immediately after the [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) or [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md), and it must implement all the members defined by the interface.</span><span class="sxs-lookup"><span data-stu-id="3c208-107">If a class or structure implements an interface, it must include the `Implements` statement immediately after the [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) or [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md), and it must implement all the members defined by the interface.</span></span>

## <a name="reimplementation"></a><span data-ttu-id="3c208-108">Reimplementation</span><span class="sxs-lookup"><span data-stu-id="3c208-108">Reimplementation</span></span>  
<span data-ttu-id="3c208-109">In a derived class, you can reimplement an interface member that the base class has already implemented.</span><span class="sxs-lookup"><span data-stu-id="3c208-109">In a derived class, you can reimplement an interface member that the base class has already implemented.</span></span> <span data-ttu-id="3c208-110">This is different from overriding the base class member in the following respects:</span><span class="sxs-lookup"><span data-stu-id="3c208-110">This is different from overriding the base class member in the following respects:</span></span>

- <span data-ttu-id="3c208-111">The base class member does not need to be [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) to be reimplemented.</span><span class="sxs-lookup"><span data-stu-id="3c208-111">The base class member does not need to be [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) to be reimplemented.</span></span>
- <span data-ttu-id="3c208-112">You can reimplement the member with a different name.</span><span class="sxs-lookup"><span data-stu-id="3c208-112">You can reimplement the member with a different name.</span></span>

<span data-ttu-id="3c208-113">The `Implements` keyword can be used in the following contexts:</span><span class="sxs-lookup"><span data-stu-id="3c208-113">The `Implements` keyword can be used in the following contexts:</span></span>

- [<span data-ttu-id="3c208-114">Příkaz Event</span><span class="sxs-lookup"><span data-stu-id="3c208-114">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="3c208-115">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="3c208-115">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="3c208-116">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="3c208-116">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="3c208-117">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="3c208-117">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="3c208-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3c208-118">See also</span></span>

- [<span data-ttu-id="3c208-119">Příkaz Implements</span><span class="sxs-lookup"><span data-stu-id="3c208-119">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
- [<span data-ttu-id="3c208-120">Příkaz Interface</span><span class="sxs-lookup"><span data-stu-id="3c208-120">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="3c208-121">Příkaz Class</span><span class="sxs-lookup"><span data-stu-id="3c208-121">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="3c208-122">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="3c208-122">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
