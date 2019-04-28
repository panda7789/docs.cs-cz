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
ms.openlocfilehash: 3c44748798d5ed554fc9fbded9c3a4d981a66d2f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769028"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a><span data-ttu-id="7c10d-102">Postupy: Odkazování na aktuální instanci objektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7c10d-102">How to: Refer to the Current Instance of an Object (Visual Basic)</span></span>
<span data-ttu-id="7c10d-103">*Aktuální instance* objektu je instance, ve kterém právě spouští kód.</span><span class="sxs-lookup"><span data-stu-id="7c10d-103">The *current instance* of an object is the instance in which the code is currently executing.</span></span>  
  
 <span data-ttu-id="7c10d-104">Můžete použít `Me` – klíčové slovo k odkazování na aktuální instanci.</span><span class="sxs-lookup"><span data-stu-id="7c10d-104">You use the `Me` keyword to refer to the current instance.</span></span>  
  
### <a name="to-refer-to-the-current-instance"></a><span data-ttu-id="7c10d-105">K odkazování na aktuální instanci</span><span class="sxs-lookup"><span data-stu-id="7c10d-105">To refer to the current instance</span></span>  
  
- <span data-ttu-id="7c10d-106">Použít `Me` – klíčové slovo, které běžně používáte název proměnné objektu.</span><span class="sxs-lookup"><span data-stu-id="7c10d-106">Use the `Me` keyword where you would normally use the name of an object variable.</span></span>  
  
    ```  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     <span data-ttu-id="7c10d-107">I když `Me` se chová stejně jako objekt proměnné, nelze ji deklarovat ani nic jí přiřadit.</span><span class="sxs-lookup"><span data-stu-id="7c10d-107">Although `Me` behaves like an object variable, you cannot declare it or assign anything to it.</span></span> <span data-ttu-id="7c10d-108">`Me` vždy odkazuje na aktuální instanci.</span><span class="sxs-lookup"><span data-stu-id="7c10d-108">`Me` always refers to the current instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c10d-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7c10d-109">See also</span></span>

- [<span data-ttu-id="7c10d-110">Objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="7c10d-110">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="7c10d-111">Přiřazení objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="7c10d-111">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="7c10d-112">Me, My, MyBase a MyClass</span><span class="sxs-lookup"><span data-stu-id="7c10d-112">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
