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
ms.openlocfilehash: dcd20f21a989c327dcfcf27d5638d500b6e4b6da
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929321"
---
# <a name="implements-clause-visual-basic"></a><span data-ttu-id="cf4db-102">Implements – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf4db-102">Implements Clause (Visual Basic)</span></span>
<span data-ttu-id="cf4db-103">Indikuje, že člen třídy nebo struktury poskytuje implementaci pro člena definovaného v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cf4db-103">Indicates that a class or structure member is providing the implementation for a member defined in an interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf4db-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cf4db-104">Remarks</span></span>  
<span data-ttu-id="cf4db-105">Klíčové slovo není stejné jako [příkaz Implements.](../../../visual-basic/language-reference/statements/implements-statement.md) `Implements`</span><span class="sxs-lookup"><span data-stu-id="cf4db-105">The `Implements` keyword is not the same as the [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span> <span data-ttu-id="cf4db-106">Pomocí `Implements` příkazu určíte, že třída nebo struktura implementuje jedno nebo více rozhraní, a poté pro každého člena, který `Implements` použijete klíčové slovo k určení, které rozhraní a který člen implementuje.</span><span class="sxs-lookup"><span data-stu-id="cf4db-106">You use the `Implements` statement to specify that a class or structure implements one or more interfaces, and then for each member you use the `Implements` keyword to specify which interface and which member it implements.</span></span>

<span data-ttu-id="cf4db-107">Pokud třída nebo struktura implementuje rozhraní, musí obsahovat `Implements` příkaz ihned po příkazu [třídy](../../../visual-basic/language-reference/statements/class-statement.md) nebo [příkazu struktury](../../../visual-basic/language-reference/statements/structure-statement.md)a musí implementovat všechny členy definované rozhraním.</span><span class="sxs-lookup"><span data-stu-id="cf4db-107">If a class or structure implements an interface, it must include the `Implements` statement immediately after the [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) or [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md), and it must implement all the members defined by the interface.</span></span>

## <a name="reimplementation"></a><span data-ttu-id="cf4db-108">Implementaci</span><span class="sxs-lookup"><span data-stu-id="cf4db-108">Reimplementation</span></span>  
<span data-ttu-id="cf4db-109">V odvozené třídě můžete znovu implementovat člena rozhraní, který je základní třídou již implementován.</span><span class="sxs-lookup"><span data-stu-id="cf4db-109">In a derived class, you can reimplement an interface member that the base class has already implemented.</span></span> <span data-ttu-id="cf4db-110">To se liší od přepsání člena základní třídy v následujících ohledech:</span><span class="sxs-lookup"><span data-stu-id="cf4db-110">This is different from overriding the base class member in the following respects:</span></span>

- <span data-ttu-id="cf4db-111">Člen základní třídy není nutné [přepsat](../../../visual-basic/language-reference/modifiers/overridable.md) , aby jej bylo možné znovu implementovat.</span><span class="sxs-lookup"><span data-stu-id="cf4db-111">The base class member does not need to be [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) to be reimplemented.</span></span>
- <span data-ttu-id="cf4db-112">Člena můžete znovu implementovat s jiným názvem.</span><span class="sxs-lookup"><span data-stu-id="cf4db-112">You can reimplement the member with a different name.</span></span>

<span data-ttu-id="cf4db-113">`Implements` Klíčové slovo lze použít v následujících kontextech:</span><span class="sxs-lookup"><span data-stu-id="cf4db-113">The `Implements` keyword can be used in the following contexts:</span></span>

- [<span data-ttu-id="cf4db-114">Příkaz Event</span><span class="sxs-lookup"><span data-stu-id="cf4db-114">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="cf4db-115">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="cf4db-115">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="cf4db-116">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="cf4db-116">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="cf4db-117">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="cf4db-117">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="cf4db-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cf4db-118">See also</span></span>

- [<span data-ttu-id="cf4db-119">Příkaz Implements</span><span class="sxs-lookup"><span data-stu-id="cf4db-119">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
- [<span data-ttu-id="cf4db-120">Příkaz Interface</span><span class="sxs-lookup"><span data-stu-id="cf4db-120">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="cf4db-121">Příkaz Class</span><span class="sxs-lookup"><span data-stu-id="cf4db-121">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="cf4db-122">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="cf4db-122">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
