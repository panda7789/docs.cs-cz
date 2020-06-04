---
title: Klíčové slovo '<keyword>' je platné pouze v rámci metody instance.
ms.date: 07/20/2015
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
ms.openlocfilehash: 537689405ea30bdd7c075320eba58a8723a93cdb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397399"
---
# <a name="keyword-is-valid-only-within-an-instance-method"></a><span data-ttu-id="330fe-102">Klíčové slovo '\<keyword>' je platné pouze v rámci metody instance.</span><span class="sxs-lookup"><span data-stu-id="330fe-102">'\<keyword>' is valid only within an instance method</span></span>
<span data-ttu-id="330fe-103">`Me` `MyClass` `MyBase` Klíčová slova, a odkazují na konkrétní instance třídy.</span><span class="sxs-lookup"><span data-stu-id="330fe-103">The `Me`, `MyClass`, and `MyBase` keywords refer to specific class instances.</span></span> <span data-ttu-id="330fe-104">Nemůžete je použít uvnitř sdíleného `Function` nebo `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="330fe-104">You cannot use them inside a shared `Function` or `Sub` procedure.</span></span>  
  
 <span data-ttu-id="330fe-105">**ID chyby:** BC30043</span><span class="sxs-lookup"><span data-stu-id="330fe-105">**Error ID:** BC30043</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="330fe-106">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="330fe-106">To correct this error</span></span>  
  
- <span data-ttu-id="330fe-107">Odeberte klíčové slovo z procedury nebo odeberte `Shared` klíčové slovo z deklarace procedury.</span><span class="sxs-lookup"><span data-stu-id="330fe-107">Remove the keyword from the procedure, or remove the `Shared` keyword from the procedure declaration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="330fe-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="330fe-108">See also</span></span>

- [<span data-ttu-id="330fe-109">Přiřazení proměnné objektu</span><span class="sxs-lookup"><span data-stu-id="330fe-109">Object Variable Assignment</span></span>](../../programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="330fe-110">Me, My, MyBase a MyClass</span><span class="sxs-lookup"><span data-stu-id="330fe-110">Me, My, MyBase, and MyClass</span></span>](../../programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="330fe-111">Základní informace o dědičnosti</span><span class="sxs-lookup"><span data-stu-id="330fe-111">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
