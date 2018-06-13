---
title: '&#39;&lt;– klíčové slovo&gt; &#39; je platná pouze v rámci metody instance'
ms.date: 07/20/2015
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
ms.openlocfilehash: 2d9e26aa7dccf1b9c6390a20a59b10a0d248969d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586357"
---
# <a name="39ltkeywordgt39-is-valid-only-within-an-instance-method"></a><span data-ttu-id="6a323-102">&#39;&lt;– klíčové slovo&gt; &#39; je platná pouze v rámci metody instance</span><span class="sxs-lookup"><span data-stu-id="6a323-102">&#39;&lt;keyword&gt;&#39; is valid only within an instance method</span></span>
<span data-ttu-id="6a323-103">`Me`, `MyClass`, A `MyBase` klíčová slova odkazovat na instancí určité třídy.</span><span class="sxs-lookup"><span data-stu-id="6a323-103">The `Me`, `MyClass`, and `MyBase` keywords refer to specific class instances.</span></span> <span data-ttu-id="6a323-104">Proto je nelze použít uvnitř sdílenou `Function` nebo `Sub` postupu.</span><span class="sxs-lookup"><span data-stu-id="6a323-104">You cannot use them inside a shared `Function` or `Sub` procedure.</span></span>  
  
 <span data-ttu-id="6a323-105">**ID chyby:** BC30043</span><span class="sxs-lookup"><span data-stu-id="6a323-105">**Error ID:** BC30043</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6a323-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="6a323-106">To correct this error</span></span>  
  
-   <span data-ttu-id="6a323-107">Postup odebrání klíčové slovo nebo odebrat `Shared` – klíčové slovo z deklarace procedury.</span><span class="sxs-lookup"><span data-stu-id="6a323-107">Remove the keyword from the procedure, or remove the `Shared` keyword from the procedure declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a323-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="6a323-108">See Also</span></span>  
 [<span data-ttu-id="6a323-109">Přiřazení objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="6a323-109">Object Variable Assignment</span></span>](../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [<span data-ttu-id="6a323-110">Me, My, MyBase a MyClass</span><span class="sxs-lookup"><span data-stu-id="6a323-110">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [<span data-ttu-id="6a323-111">Základní informace o dědičnosti</span><span class="sxs-lookup"><span data-stu-id="6a323-111">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
