---
title: 'Postupy: Urychlení přístupu k objektu pomocí cesty dlouhou kvalifikací (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
ms.openlocfilehash: 94c838a69aab9fcae9dc0c79b6038ee90e2369e7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769041"
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a><span data-ttu-id="7291b-102">Postupy: Urychlení přístupu k objektu pomocí cesty dlouhou kvalifikací (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7291b-102">How to: Speed Up Access to an Object with a Long Qualification Path (Visual Basic)</span></span>
<span data-ttu-id="7291b-103">Pokud využíváte častěji objekt, který se vyžaduje cesta kvalifikace několik metod a vlastností, můžete urychlit kódu není opakováním cesta kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="7291b-103">If you frequently access an object that requires a qualification path of several methods and properties, you can speed up your code by not repeating the qualification path.</span></span>  
  
 <span data-ttu-id="7291b-104">Existují dva způsoby opakující se cesta kvalifikace se můžete vyhnout.</span><span class="sxs-lookup"><span data-stu-id="7291b-104">There are two ways you can avoid repeating the qualification path.</span></span> <span data-ttu-id="7291b-105">Objekt můžete přiřadit k proměnné nebo ho můžete použít `With`... `End With` bloku.</span><span class="sxs-lookup"><span data-stu-id="7291b-105">You can assign the object to a variable, or you can use it in a `With`...`End With` block.</span></span>  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-assigning-it-to-a-variable"></a><span data-ttu-id="7291b-106">Ke zrychlení přístupu k objektu silně kvalifikovaný přiřazením do proměnné</span><span class="sxs-lookup"><span data-stu-id="7291b-106">To speed up access to a heavily qualified object by assigning it to a variable</span></span>  
  
1. <span data-ttu-id="7291b-107">Deklarujte proměnnou typu objektu, který často přistupujete.</span><span class="sxs-lookup"><span data-stu-id="7291b-107">Declare a variable of the type of the object that you are accessing frequently.</span></span> <span data-ttu-id="7291b-108">Zadejte cestu kvalifikace v inicializaci části prohlášení.</span><span class="sxs-lookup"><span data-stu-id="7291b-108">Specify the qualification path in the initialization part of the declaration.</span></span>  
  
    ```  
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl  
    ```  
  
2. <span data-ttu-id="7291b-109">Pro přístup ke členům objektu, použijte proměnnou.</span><span class="sxs-lookup"><span data-stu-id="7291b-109">Use the variable to access the object's members.</span></span>  
  
    ```  
    ctrlActv.Text = "Test"  
    ctrlActv.Location = New Point(100, 100)  
    ctrlActv.Show()  
    ```  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-using-a-withend-with-block"></a><span data-ttu-id="7291b-110">K urychlení přístupu k objektu silně kvalifikovaný pomocí With... Blok End With</span><span class="sxs-lookup"><span data-stu-id="7291b-110">To speed up access to a heavily qualified object by using a With...End With block</span></span>  
  
1. <span data-ttu-id="7291b-111">Vložit cestu kvalifikaci `With` příkazu.</span><span class="sxs-lookup"><span data-stu-id="7291b-111">Put the qualification path in a `With` statement.</span></span>  
  
    ```  
    With someForm.ActiveForm.ActiveControl  
    ```  
  
2. <span data-ttu-id="7291b-112">Přístup ke členům objektu uvnitř `With` blokovat, než `End With` příkazu.</span><span class="sxs-lookup"><span data-stu-id="7291b-112">Access the object's members inside the `With` block, before the `End With` statement.</span></span>  
  
    ```  
        .Text = "Test"  
        .Location = New Point(100, 100)  
        .Show()  
    End With  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="7291b-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7291b-113">See also</span></span>

- [<span data-ttu-id="7291b-114">Objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="7291b-114">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="7291b-115">Příkaz With...End With</span><span class="sxs-lookup"><span data-stu-id="7291b-115">With...End With Statement</span></span>](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
