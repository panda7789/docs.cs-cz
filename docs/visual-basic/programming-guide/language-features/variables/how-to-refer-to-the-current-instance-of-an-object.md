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
ms.openlocfilehash: 6c216dbc59bcad7a9f24bb01f856c3d29c288dbb
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005664"
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a><span data-ttu-id="7a6e3-102">Postupy: Odkazování na aktuální instanci objektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7a6e3-102">How to: Refer to the Current Instance of an Object (Visual Basic)</span></span>
<span data-ttu-id="7a6e3-103">*Aktuální instance* objektu je instance, ve které je právě spuštěn kód.</span><span class="sxs-lookup"><span data-stu-id="7a6e3-103">The *current instance* of an object is the instance in which the code is currently executing.</span></span>  
  
 <span data-ttu-id="7a6e3-104">Pomocí klíčového slova `Me` můžete odkazovat na aktuální instanci.</span><span class="sxs-lookup"><span data-stu-id="7a6e3-104">You use the `Me` keyword to refer to the current instance.</span></span>  
  
### <a name="to-refer-to-the-current-instance"></a><span data-ttu-id="7a6e3-105">Pro odkazování na aktuální instanci</span><span class="sxs-lookup"><span data-stu-id="7a6e3-105">To refer to the current instance</span></span>  
  
- <span data-ttu-id="7a6e3-106">Použijte klíčové slovo `Me`, kde byste normálně použili název proměnné objektu.</span><span class="sxs-lookup"><span data-stu-id="7a6e3-106">Use the `Me` keyword where you would normally use the name of an object variable.</span></span>  
  
    ```vb  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     <span data-ttu-id="7a6e3-107">I když `Me` se chová jako proměnná objektu, nemůžete ji deklarovat nebo k ní přiřadit cokoli.</span><span class="sxs-lookup"><span data-stu-id="7a6e3-107">Although `Me` behaves like an object variable, you cannot declare it or assign anything to it.</span></span> <span data-ttu-id="7a6e3-108">`Me` vždy odkazuje na aktuální instanci.</span><span class="sxs-lookup"><span data-stu-id="7a6e3-108">`Me` always refers to the current instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a6e3-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7a6e3-109">See also</span></span>

- [<span data-ttu-id="7a6e3-110">Objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="7a6e3-110">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="7a6e3-111">Přiřazení objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="7a6e3-111">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="7a6e3-112">Me, My, MyBase a MyClass</span><span class="sxs-lookup"><span data-stu-id="7a6e3-112">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
