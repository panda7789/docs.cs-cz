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
ms.openlocfilehash: 46ab1a1148e8d73d91293aedfc407e5efdc7cfb4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404560"
---
# <a name="implements-clause-visual-basic"></a><span data-ttu-id="20c2c-102">Implements – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20c2c-102">Implements Clause (Visual Basic)</span></span>
<span data-ttu-id="20c2c-103">Indikuje, že člen třídy nebo struktury poskytuje implementaci pro člena definovaného v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="20c2c-103">Indicates that a class or structure member is providing the implementation for a member defined in an interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20c2c-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="20c2c-104">Remarks</span></span>  
<span data-ttu-id="20c2c-105">`Implements`Klíčové slovo není stejné jako [příkaz Implements](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="20c2c-105">The `Implements` keyword is not the same as the [Implements Statement](implements-statement.md).</span></span> <span data-ttu-id="20c2c-106">Pomocí `Implements` příkazu určíte, že třída nebo struktura implementuje jedno nebo více rozhraní, a poté pro každého člena, který použijete `Implements` klíčové slovo k určení, které rozhraní a který člen implementuje.</span><span class="sxs-lookup"><span data-stu-id="20c2c-106">You use the `Implements` statement to specify that a class or structure implements one or more interfaces, and then for each member you use the `Implements` keyword to specify which interface and which member it implements.</span></span>

<span data-ttu-id="20c2c-107">Pokud třída nebo struktura implementuje rozhraní, musí obsahovat `Implements` příkaz ihned po příkazu [třídy](class-statement.md) nebo [příkazu struktury](structure-statement.md)a musí implementovat všechny členy definované rozhraním.</span><span class="sxs-lookup"><span data-stu-id="20c2c-107">If a class or structure implements an interface, it must include the `Implements` statement immediately after the [Class Statement](class-statement.md) or [Structure Statement](structure-statement.md), and it must implement all the members defined by the interface.</span></span>

## <a name="reimplementation"></a><span data-ttu-id="20c2c-108">Implementaci</span><span class="sxs-lookup"><span data-stu-id="20c2c-108">Reimplementation</span></span>  
<span data-ttu-id="20c2c-109">V odvozené třídě můžete znovu implementovat člena rozhraní, který je základní třídou již implementován.</span><span class="sxs-lookup"><span data-stu-id="20c2c-109">In a derived class, you can reimplement an interface member that the base class has already implemented.</span></span> <span data-ttu-id="20c2c-110">To se liší od přepsání člena základní třídy v následujících ohledech:</span><span class="sxs-lookup"><span data-stu-id="20c2c-110">This is different from overriding the base class member in the following respects:</span></span>

- <span data-ttu-id="20c2c-111">Člen základní třídy není nutné [přepsat](../modifiers/overridable.md) , aby jej bylo možné znovu implementovat.</span><span class="sxs-lookup"><span data-stu-id="20c2c-111">The base class member does not need to be [Overridable](../modifiers/overridable.md) to be reimplemented.</span></span>
- <span data-ttu-id="20c2c-112">Člena můžete znovu implementovat s jiným názvem.</span><span class="sxs-lookup"><span data-stu-id="20c2c-112">You can reimplement the member with a different name.</span></span>

<span data-ttu-id="20c2c-113">`Implements`Klíčové slovo lze použít v následujících kontextech:</span><span class="sxs-lookup"><span data-stu-id="20c2c-113">The `Implements` keyword can be used in the following contexts:</span></span>

- [<span data-ttu-id="20c2c-114">Event – příkaz</span><span class="sxs-lookup"><span data-stu-id="20c2c-114">Event Statement</span></span>](event-statement.md)
- [<span data-ttu-id="20c2c-115">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="20c2c-115">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="20c2c-116">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="20c2c-116">Property Statement</span></span>](property-statement.md)
- [<span data-ttu-id="20c2c-117">Sub – příkaz</span><span class="sxs-lookup"><span data-stu-id="20c2c-117">Sub Statement</span></span>](sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="20c2c-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="20c2c-118">See also</span></span>

- [<span data-ttu-id="20c2c-119">Implements – Příkaz</span><span class="sxs-lookup"><span data-stu-id="20c2c-119">Implements Statement</span></span>](implements-statement.md)
- [<span data-ttu-id="20c2c-120">Interface – příkaz</span><span class="sxs-lookup"><span data-stu-id="20c2c-120">Interface Statement</span></span>](interface-statement.md)
- [<span data-ttu-id="20c2c-121">Class – příkaz</span><span class="sxs-lookup"><span data-stu-id="20c2c-121">Class Statement</span></span>](class-statement.md)
- [<span data-ttu-id="20c2c-122">Structure – příkaz</span><span class="sxs-lookup"><span data-stu-id="20c2c-122">Structure Statement</span></span>](structure-statement.md)
