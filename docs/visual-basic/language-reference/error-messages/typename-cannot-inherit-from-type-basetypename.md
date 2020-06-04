---
title: "'<typename>' nemůže dědit ze třídy <type> '<basetypename>', protože rozšiřuje přístup třídy Base <type> mimo sestavení."
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: aa04c558abbcc4259c2821cdcbdc1669b91ffee0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402769"
---
# <a name="typename-cannot-inherit-from-type-basetypename-because-it-expands-the-access-of-the-base-type-outside-the-assembly"></a><span data-ttu-id="1bdba-102">'\<typename>' nemůže dědit ze třídy \<type> '\<basetypename>', protože rozšiřuje přístup třídy Base \<type> mimo sestavení.</span><span class="sxs-lookup"><span data-stu-id="1bdba-102">'\<typename>' cannot inherit from \<type> '\<basetypename>' because it expands the access of the base \<type> outside the assembly</span></span>
<span data-ttu-id="1bdba-103">Třída nebo rozhraní dědí ze základní třídy nebo rozhraní, ale má méně omezující úroveň přístupu.</span><span class="sxs-lookup"><span data-stu-id="1bdba-103">A class or interface inherits from a base class or interface but has a less restrictive access level.</span></span>  
  
 <span data-ttu-id="1bdba-104">Například `Public` rozhraní dědí z `Friend` rozhraní nebo `Protected` Třída dědí z `Private` třídy.</span><span class="sxs-lookup"><span data-stu-id="1bdba-104">For example, a `Public` interface inherits from a `Friend` interface, or a `Protected` class inherits from a `Private` class.</span></span> <span data-ttu-id="1bdba-105">Tím se zpřístupňuje základní třída nebo rozhraní pro přístup mimo zamýšlenou úroveň.</span><span class="sxs-lookup"><span data-stu-id="1bdba-105">This exposes the base class or interface to access beyond the intended level.</span></span>  
  
 <span data-ttu-id="1bdba-106">**ID chyby:** BC30910</span><span class="sxs-lookup"><span data-stu-id="1bdba-106">**Error ID:** BC30910</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1bdba-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="1bdba-107">To correct this error</span></span>  
  
- <span data-ttu-id="1bdba-108">Změňte úroveň přístupu odvozené třídy nebo rozhraní tak, aby byla alespoň stejná jako omezení základní třídy nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1bdba-108">Change the access level of the derived class or interface to be at least as restrictive as that of the base class or interface.</span></span>  
  
     <span data-ttu-id="1bdba-109">-nebo-</span><span class="sxs-lookup"><span data-stu-id="1bdba-109">-or-</span></span>  
  
- <span data-ttu-id="1bdba-110">Pokud požadujete úroveň přístupu méně omezující, odeberte `Inherits` příkaz.</span><span class="sxs-lookup"><span data-stu-id="1bdba-110">If you require the less restrictive access level, remove the `Inherits` statement.</span></span> <span data-ttu-id="1bdba-111">Nemůžete dědit z více než omezené základní třídy nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1bdba-111">You cannot inherit from a more restricted base class or interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bdba-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="1bdba-112">See also</span></span>

- [<span data-ttu-id="1bdba-113">Class – příkaz</span><span class="sxs-lookup"><span data-stu-id="1bdba-113">Class Statement</span></span>](../statements/class-statement.md)
- [<span data-ttu-id="1bdba-114">Interface – příkaz</span><span class="sxs-lookup"><span data-stu-id="1bdba-114">Interface Statement</span></span>](../statements/interface-statement.md)
- [<span data-ttu-id="1bdba-115">Inherits – příkaz</span><span class="sxs-lookup"><span data-stu-id="1bdba-115">Inherits Statement</span></span>](../statements/inherits-statement.md)
- [<span data-ttu-id="1bdba-116">Úrovně přístupu v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1bdba-116">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
