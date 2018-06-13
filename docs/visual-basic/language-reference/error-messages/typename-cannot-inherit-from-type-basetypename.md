---
title: '&#39;&lt;TypeName&gt; &#39; nemůže Zdědit z &lt;typ&gt; &#39; &lt;basetypename&gt; &#39; protože rozšiřuje přístup základní &lt;typ&gt; mimo sestavení'
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: f747b2b24f5fecc22b9e1fbc6ba26b634e9ead2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33598421"
---
# <a name="39lttypenamegt39-cannot-inherit-from-lttypegt-39ltbasetypenamegt39-because-it-expands-the-access-of-the-base-lttypegt-outside-the-assembly"></a><span data-ttu-id="f40a1-102">&#39;&lt;TypeName&gt; &#39; nemůže Zdědit z &lt;typ&gt; &#39; &lt;basetypename&gt; &#39; protože rozšiřuje přístup základní &lt;typ&gt; mimo sestavení</span><span class="sxs-lookup"><span data-stu-id="f40a1-102">&#39;&lt;typename&gt;&#39; cannot inherit from &lt;type&gt; &#39;&lt;basetypename&gt;&#39; because it expands the access of the base &lt;type&gt; outside the assembly</span></span>
<span data-ttu-id="f40a1-103">Třídy nebo rozhraní dědí vlastnosti ze základní třídy nebo rozhraní ale je méně omezující úroveň přístupu.</span><span class="sxs-lookup"><span data-stu-id="f40a1-103">A class or interface inherits from a base class or interface but has a less restrictive access level.</span></span>  
  
 <span data-ttu-id="f40a1-104">Například `Public` rozhraní dědí z `Friend` rozhraní, nebo `Protected` třída dědí z `Private` třídy.</span><span class="sxs-lookup"><span data-stu-id="f40a1-104">For example, a `Public` interface inherits from a `Friend` interface, or a `Protected` class inherits from a `Private` class.</span></span> <span data-ttu-id="f40a1-105">To zpřístupňuje základní třídy nebo rozhraní pro přístup k mimo určený úroveň.</span><span class="sxs-lookup"><span data-stu-id="f40a1-105">This exposes the base class or interface to access beyond the intended level.</span></span>  
  
 <span data-ttu-id="f40a1-106">**ID chyby:** BC30910</span><span class="sxs-lookup"><span data-stu-id="f40a1-106">**Error ID:** BC30910</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f40a1-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="f40a1-107">To correct this error</span></span>  
  
-   <span data-ttu-id="f40a1-108">Změníte úroveň přístupu tohoto odvozené třídy nebo rozhraní na omezující jako základní třídy nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f40a1-108">Change the access level of the derived class or interface to be at least as restrictive as that of the base class or interface.</span></span>  
  
     <span data-ttu-id="f40a1-109">-nebo-</span><span class="sxs-lookup"><span data-stu-id="f40a1-109">-or-</span></span>  
  
-   <span data-ttu-id="f40a1-110">Pokud budete potřebovat méně omezující úroveň přístupu, odeberte `Inherits` příkaz.</span><span class="sxs-lookup"><span data-stu-id="f40a1-110">If you require the less restrictive access level, remove the `Inherits` statement.</span></span> <span data-ttu-id="f40a1-111">Nelze zdědit omezenější základní třídy nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f40a1-111">You cannot inherit from a more restricted base class or interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f40a1-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="f40a1-112">See Also</span></span>  
 [<span data-ttu-id="f40a1-113">Příkaz Class</span><span class="sxs-lookup"><span data-stu-id="f40a1-113">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
 [<span data-ttu-id="f40a1-114">Příkaz Interface</span><span class="sxs-lookup"><span data-stu-id="f40a1-114">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [<span data-ttu-id="f40a1-115">Příkaz Inherits</span><span class="sxs-lookup"><span data-stu-id="f40a1-115">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [<span data-ttu-id="f40a1-116">Úrovně přístupu v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f40a1-116">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
