---
title: "'<typename>' nemůže dědit ze třídy <type> '<basetypename>', protože rozšiřuje přístup třídy Base <type> mimo sestavení."
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: dc979a66c73fdf15a4349a003680156e0ce27ed3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838947"
---
# <a name="typename-cannot-inherit-from-type-basetypename-because-it-expands-the-access-of-the-base-type-outside-the-assembly"></a><span data-ttu-id="fa9a1-102">"\<typename >' nemůže dědit od třídy \<typu >"\<basetypename >' protože rozšiřuje přístup základní třídy \<typ > mimo sestavení</span><span class="sxs-lookup"><span data-stu-id="fa9a1-102">'\<typename>' cannot inherit from \<type> '\<basetypename>' because it expands the access of the base \<type> outside the assembly</span></span>
<span data-ttu-id="fa9a1-103">Třídy nebo rozhraní dědí ze základní třídy nebo rozhraní, ale má míň omezující úroveň přístupu.</span><span class="sxs-lookup"><span data-stu-id="fa9a1-103">A class or interface inherits from a base class or interface but has a less restrictive access level.</span></span>  
  
 <span data-ttu-id="fa9a1-104">Například `Public` rozhraní zdědí `Friend` rozhraní, nebo `Protected` třída dědí z `Private` třídy.</span><span class="sxs-lookup"><span data-stu-id="fa9a1-104">For example, a `Public` interface inherits from a `Friend` interface, or a `Protected` class inherits from a `Private` class.</span></span> <span data-ttu-id="fa9a1-105">Tato třída zveřejňuje základní třídu nebo rozhraní pro přístup k mimo určené úroveň.</span><span class="sxs-lookup"><span data-stu-id="fa9a1-105">This exposes the base class or interface to access beyond the intended level.</span></span>  
  
 <span data-ttu-id="fa9a1-106">**ID chyby:** BC30910</span><span class="sxs-lookup"><span data-stu-id="fa9a1-106">**Error ID:** BC30910</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fa9a1-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="fa9a1-107">To correct this error</span></span>  
  
-   <span data-ttu-id="fa9a1-108">Změníte úroveň přístupu odvozené třídy nebo rozhraní, které má být omezující jako základní třídu nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fa9a1-108">Change the access level of the derived class or interface to be at least as restrictive as that of the base class or interface.</span></span>  
  
     <span data-ttu-id="fa9a1-109">-nebo-</span><span class="sxs-lookup"><span data-stu-id="fa9a1-109">-or-</span></span>  
  
-   <span data-ttu-id="fa9a1-110">Pokud požadujete méně omezující úroveň přístupu, odeberte `Inherits` příkazu.</span><span class="sxs-lookup"><span data-stu-id="fa9a1-110">If you require the less restrictive access level, remove the `Inherits` statement.</span></span> <span data-ttu-id="fa9a1-111">Nemůže dědit z více omezený základní třídu nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fa9a1-111">You cannot inherit from a more restricted base class or interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa9a1-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fa9a1-112">See also</span></span>

- [<span data-ttu-id="fa9a1-113">Příkaz Class</span><span class="sxs-lookup"><span data-stu-id="fa9a1-113">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="fa9a1-114">Příkaz Interface</span><span class="sxs-lookup"><span data-stu-id="fa9a1-114">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="fa9a1-115">Příkaz Inherits</span><span class="sxs-lookup"><span data-stu-id="fa9a1-115">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="fa9a1-116">Úrovně přístupu v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fa9a1-116">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
