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
ms.openlocfilehash: b10876c22d2f6dd5832baa0d498db7c4205a3fcb
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816280"
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a><span data-ttu-id="28cca-102">Postupy: Urychlení přístupu k objektu pomocí cesty dlouhou kvalifikací (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="28cca-102">How to: Speed Up Access to an Object with a Long Qualification Path (Visual Basic)</span></span>
<span data-ttu-id="28cca-103">Pokud využíváte častěji objekt, který se vyžaduje cesta kvalifikace několik metod a vlastností, můžete urychlit kódu není opakováním cesta kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="28cca-103">If you frequently access an object that requires a qualification path of several methods and properties, you can speed up your code by not repeating the qualification path.</span></span>  
  
 <span data-ttu-id="28cca-104">Existují dva způsoby opakující se cesta kvalifikace se můžete vyhnout.</span><span class="sxs-lookup"><span data-stu-id="28cca-104">There are two ways you can avoid repeating the qualification path.</span></span> <span data-ttu-id="28cca-105">Objekt můžete přiřadit k proměnné nebo ho můžete použít `With`... `End With` bloku.</span><span class="sxs-lookup"><span data-stu-id="28cca-105">You can assign the object to a variable, or you can use it in a `With`...`End With` block.</span></span>  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-assigning-it-to-a-variable"></a><span data-ttu-id="28cca-106">Ke zrychlení přístupu k objektu silně kvalifikovaný přiřazením do proměnné</span><span class="sxs-lookup"><span data-stu-id="28cca-106">To speed up access to a heavily qualified object by assigning it to a variable</span></span>  
  
1.  <span data-ttu-id="28cca-107">Deklarujte proměnnou typu objektu, který často přistupujete.</span><span class="sxs-lookup"><span data-stu-id="28cca-107">Declare a variable of the type of the object that you are accessing frequently.</span></span> <span data-ttu-id="28cca-108">Zadejte cestu kvalifikace v inicializaci části prohlášení.</span><span class="sxs-lookup"><span data-stu-id="28cca-108">Specify the qualification path in the initialization part of the declaration.</span></span>  
  
    ```  
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl  
    ```  
  
2.  <span data-ttu-id="28cca-109">Pro přístup ke členům objektu, použijte proměnnou.</span><span class="sxs-lookup"><span data-stu-id="28cca-109">Use the variable to access the object's members.</span></span>  
  
    ```  
    ctrlActv.Text = "Test"  
    ctrlActv.Location = New Point(100, 100)  
    ctrlActv.Show()  
    ```  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-using-a-withend-with-block"></a><span data-ttu-id="28cca-110">K urychlení přístupu k objektu silně kvalifikovaný pomocí With... Blok End With</span><span class="sxs-lookup"><span data-stu-id="28cca-110">To speed up access to a heavily qualified object by using a With...End With block</span></span>  
  
1.  <span data-ttu-id="28cca-111">Vložit cestu kvalifikaci `With` příkazu.</span><span class="sxs-lookup"><span data-stu-id="28cca-111">Put the qualification path in a `With` statement.</span></span>  
  
    ```  
    With someForm.ActiveForm.ActiveControl  
    ```  
  
2.  <span data-ttu-id="28cca-112">Přístup ke členům objektu uvnitř `With` blokovat, než `End With` příkazu.</span><span class="sxs-lookup"><span data-stu-id="28cca-112">Access the object's members inside the `With` block, before the `End With` statement.</span></span>  
  
    ```  
        .Text = "Test"  
        .Location = New Point(100, 100)  
        .Show()  
    End With  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="28cca-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="28cca-113">See also</span></span>

- [<span data-ttu-id="28cca-114">Objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="28cca-114">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="28cca-115">Příkaz With...End With</span><span class="sxs-lookup"><span data-stu-id="28cca-115">With...End With Statement</span></span>](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
