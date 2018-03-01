---
title: "Použití proměnné iterace ve výrazu lambda může mít neočekávané důsledky."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42324
- bc42324
helpviewer_keywords:
- BC42324
ms.assetid: b5c2c4bd-3b2a-4a73-aaeb-55728eb03b68
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fb707cd4e09a149d21b70bb0f998a40c7ed58b49
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="using-the-iteration-variable-in-a-lambda-expression-may-have-unexpected-results"></a><span data-ttu-id="08dff-102">Použití proměnné iterace ve výrazu lambda může mít neočekávané důsledky.</span><span class="sxs-lookup"><span data-stu-id="08dff-102">Using the iteration variable in a lambda expression may have unexpected results</span></span>
<span data-ttu-id="08dff-103">Použití proměnné iterace ve výrazu lambda může mít neočekávané výsledky.</span><span class="sxs-lookup"><span data-stu-id="08dff-103">Using the iteration variable in a lambda expression may have unexpected results.</span></span> <span data-ttu-id="08dff-104">Místo toho vytvořte místní proměnné v rámci smyčky a přiřaďte ho hodnotu proměnné iterace.</span><span class="sxs-lookup"><span data-stu-id="08dff-104">Instead, create a local variable within the loop and assign it the value of the iteration variable.</span></span>  
  
 <span data-ttu-id="08dff-105">Toto upozornění se zobrazí v případě použití proměnné iterace smyčky ve výrazu lambda, který je deklarován uvnitř smyčky.</span><span class="sxs-lookup"><span data-stu-id="08dff-105">This warning appears when you use a loop iteration variable in a lambda expression that is declared inside the loop.</span></span> <span data-ttu-id="08dff-106">Například v následujícím příkladu způsobí, že se objeví upozornění.</span><span class="sxs-lookup"><span data-stu-id="08dff-106">For example, the following example causes the warning to appear.</span></span>  
  
```vb  
For i As Integer = 1 To 10  
    ' The warning is given for the use of i.  
    Dim exampleFunc As Func(Of Integer) = Function() i  
Next  
```  
  
 <span data-ttu-id="08dff-107">Následující příklad ukazuje neočekávané výsledky, které můžou nastat.</span><span class="sxs-lookup"><span data-stu-id="08dff-107">The following example shows the unexpected results that might occur.</span></span>  
  
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
  
 <span data-ttu-id="08dff-108">`For` Smyčky vytvoří pole výrazů lambda, z nichž každý vrátí hodnotu proměnné iterace smyčky `i`.</span><span class="sxs-lookup"><span data-stu-id="08dff-108">The `For` loop creates an array of lambda expressions, each of which returns the value of the loop iteration variable `i`.</span></span> <span data-ttu-id="08dff-109">V jsou-li výrazy lambda `For Each` smyčku, můžete očekávat, že najdete v části 0, 1, 2, 3 a 4 zobrazí, následných hodnoty `i` v `For` smyčky.</span><span class="sxs-lookup"><span data-stu-id="08dff-109">When the lambda expressions are evaluated in the `For Each` loop, you might expect to see 0, 1, 2, 3, and 4 displayed, the successive values of `i` in the `For` loop.</span></span> <span data-ttu-id="08dff-110">Místo toho uvidíte konečná hodnota `i` zobrazí pětkrát:</span><span class="sxs-lookup"><span data-stu-id="08dff-110">Instead, you see the final value of `i` displayed five times:</span></span>  
  
 `5`  
  
 `5`  
  
 `5`  
  
 `5`  
  
 `5`  
  
 <span data-ttu-id="08dff-111">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="08dff-111">By default, this message is a warning.</span></span> <span data-ttu-id="08dff-112">Další informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="08dff-112">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="08dff-113">**ID chyby:** BC42324</span><span class="sxs-lookup"><span data-stu-id="08dff-113">**Error ID:** BC42324</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="08dff-114">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="08dff-114">To correct this error</span></span>  
  
-   <span data-ttu-id="08dff-115">Přiřadit hodnotu proměnné iterace místní proměnné a pomocí místní proměnné ve výrazu lambda.</span><span class="sxs-lookup"><span data-stu-id="08dff-115">Assign the value of the iteration variable to a local variable, and use the local variable in the lambda expression.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="08dff-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="08dff-116">See Also</span></span>  
 [<span data-ttu-id="08dff-117">Lambda – výrazy</span><span class="sxs-lookup"><span data-stu-id="08dff-117">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
