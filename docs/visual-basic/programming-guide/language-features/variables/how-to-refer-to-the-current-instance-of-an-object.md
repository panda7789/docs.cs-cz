---
title: 'Postupy: Odkazování na aktuální instanci objektu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances [Visual Basic], referring to current
- current instance
- object variables [Visual Basic]
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
ms.openlocfilehash: d166ce62a2bb0522d1ca7011aeff7afe076c2d8e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54542194"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a><span data-ttu-id="36d57-102">Postupy: Odkazování na aktuální instanci objektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36d57-102">How to: Refer to the Current Instance of an Object (Visual Basic)</span></span>
<span data-ttu-id="36d57-103">*Aktuální instance* objektu je instance, ve kterém právě spouští kód.</span><span class="sxs-lookup"><span data-stu-id="36d57-103">The *current instance* of an object is the instance in which the code is currently executing.</span></span>  
  
 <span data-ttu-id="36d57-104">Můžete použít `Me` – klíčové slovo k odkazování na aktuální instanci.</span><span class="sxs-lookup"><span data-stu-id="36d57-104">You use the `Me` keyword to refer to the current instance.</span></span>  
  
### <a name="to-refer-to-the-current-instance"></a><span data-ttu-id="36d57-105">K odkazování na aktuální instanci</span><span class="sxs-lookup"><span data-stu-id="36d57-105">To refer to the current instance</span></span>  
  
-   <span data-ttu-id="36d57-106">Použít `Me` – klíčové slovo, které běžně používáte název proměnné objektu.</span><span class="sxs-lookup"><span data-stu-id="36d57-106">Use the `Me` keyword where you would normally use the name of an object variable.</span></span>  
  
    ```  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     <span data-ttu-id="36d57-107">I když `Me` se chová stejně jako objekt proměnné, nelze ji deklarovat ani nic jí přiřadit.</span><span class="sxs-lookup"><span data-stu-id="36d57-107">Although `Me` behaves like an object variable, you cannot declare it or assign anything to it.</span></span> <span data-ttu-id="36d57-108">`Me` vždy odkazuje na aktuální instanci.</span><span class="sxs-lookup"><span data-stu-id="36d57-108">`Me` always refers to the current instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36d57-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="36d57-109">See also</span></span>
- [<span data-ttu-id="36d57-110">Objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="36d57-110">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="36d57-111">Přiřazení objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="36d57-111">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="36d57-112">Me, My, MyBase a MyClass</span><span class="sxs-lookup"><span data-stu-id="36d57-112">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
