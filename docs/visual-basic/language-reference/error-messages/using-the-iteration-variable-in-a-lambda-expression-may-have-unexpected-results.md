---
title: Použití proměnné iterace ve výrazu lambda může mít neočekávané důsledky.
ms.date: 07/20/2015
f1_keywords:
- vbc42324
- bc42324
helpviewer_keywords:
- BC42324
ms.assetid: b5c2c4bd-3b2a-4a73-aaeb-55728eb03b68
ms.openlocfilehash: 3335da503b6fb9c33e44266997cc945214a3a365
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/29/2019
ms.locfileid: "64913090"
---
# <a name="using-the-iteration-variable-in-a-lambda-expression-may-have-unexpected-results"></a><span data-ttu-id="74ac5-102">Použití proměnné iterace ve výrazu lambda může mít neočekávané důsledky.</span><span class="sxs-lookup"><span data-stu-id="74ac5-102">Using the iteration variable in a lambda expression may have unexpected results</span></span>
<span data-ttu-id="74ac5-103">Použití proměnné iterace ve výrazu lambda může mít neočekávané výsledky.</span><span class="sxs-lookup"><span data-stu-id="74ac5-103">Using the iteration variable in a lambda expression may have unexpected results.</span></span> <span data-ttu-id="74ac5-104">Místo toho vytvořte v cyklu lokální proměnnou a přiřaďte jí hodnotu proměnné iterace.</span><span class="sxs-lookup"><span data-stu-id="74ac5-104">Instead, create a local variable within the loop and assign it the value of the iteration variable.</span></span>  
  
 <span data-ttu-id="74ac5-105">Toto upozornění se zobrazí při použití proměnné iterace smyčky ve výrazu lambda, který je deklarován uvnitř smyčky.</span><span class="sxs-lookup"><span data-stu-id="74ac5-105">This warning appears when you use a loop iteration variable in a lambda expression that is declared inside the loop.</span></span> <span data-ttu-id="74ac5-106">Například následující příklad způsobí upozornění se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="74ac5-106">For example, the following example causes the warning to appear.</span></span>  
  
```vb  
For i As Integer = 1 To 10  
    ' The warning is given for the use of i.  
    Dim exampleFunc As Func(Of Integer) = Function() i  
Next  
```  
  
 <span data-ttu-id="74ac5-107">Následující příklad ukazuje neočekávané výsledky, které mohou nastat.</span><span class="sxs-lookup"><span data-stu-id="74ac5-107">The following example shows the unexpected results that might occur.</span></span>  
  
```vb  
Module Module1  
    Sub Main()  
        Dim array1 As Func(Of Integer)() = New Func(Of Integer)(4) {}  
  
        For i As Integer = 0 To 4  
            array1(i) = Function() i  
        Next  
  
        For Each funcElement In array1  
            System.Console.WriteLine(funcElement())  
        Next  
  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="74ac5-108">`For` Smyčky je vytvořeno pole výrazů lambda, z nichž každý vrátí hodnotu proměnné iterace smyčky `i`.</span><span class="sxs-lookup"><span data-stu-id="74ac5-108">The `For` loop creates an array of lambda expressions, each of which returns the value of the loop iteration variable `i`.</span></span> <span data-ttu-id="74ac5-109">Když jsou lambda výrazy vyhodnocovány v `For Each` smyčky, můžete očekávat, že naleznete v tématu 0, 1, 2, 3 a 4 zobrazí po sobě jdoucích hodnot `i` v `For` smyčky.</span><span class="sxs-lookup"><span data-stu-id="74ac5-109">When the lambda expressions are evaluated in the `For Each` loop, you might expect to see 0, 1, 2, 3, and 4 displayed, the successive values of `i` in the `For` loop.</span></span> <span data-ttu-id="74ac5-110">Místo toho uvidíte konečná hodnota `i` zobrazí pětkrát:</span><span class="sxs-lookup"><span data-stu-id="74ac5-110">Instead, you see the final value of `i` displayed five times:</span></span>  
  
 `5`  
  
 `5`  
  
 `5`  
  
 `5`  
  
 `5`  
  
 <span data-ttu-id="74ac5-111">Ve výchozím nastavení tato zpráva je upozornění.</span><span class="sxs-lookup"><span data-stu-id="74ac5-111">By default, this message is a warning.</span></span> <span data-ttu-id="74ac5-112">Další informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="74ac5-112">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="74ac5-113">**ID chyby:** BC42324</span><span class="sxs-lookup"><span data-stu-id="74ac5-113">**Error ID:** BC42324</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="74ac5-114">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="74ac5-114">To correct this error</span></span>  
  
- <span data-ttu-id="74ac5-115">Přiřadit hodnotu proměnné iterace na místní proměnnou a použijte místní proměnnou ve výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="74ac5-115">Assign the value of the iteration variable to a local variable, and use the local variable in the lambda expression.</span></span>  
  
```vb  
Module Module1  
    Sub Main()  
        Dim array1 As Func(Of Integer)() = New Func(Of Integer)(4) {}  
  
        For i As Integer = 0 To 4  
            Dim j = i  
            array1(i) = Function() j  
        Next  
  
        For Each funcElement In array1  
            System.Console.WriteLine(funcElement())  
        Next  
  
    End Sub  
End Module  
```  
  
## <a name="see-also"></a><span data-ttu-id="74ac5-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="74ac5-116">See also</span></span>

- [<span data-ttu-id="74ac5-117">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="74ac5-117">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
