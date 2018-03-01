---
title: "Typ pro proměnnou & č. 39; &lt;NázevProměnné&gt;& č. 39; nebudete ji odvodit, protože je vázána na pole v vymezeném oboru"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42110
- bc42110
helpviewer_keywords:
- BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 39968407f4de5436df324320c99dede4d72e2808
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="the-type-for-variable-39ltvariablenamegt39-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a><span data-ttu-id="4181c-102">Typ pro proměnnou & č. 39; &lt;NázevProměnné&gt;& č. 39; nebudete ji odvodit, protože je vázána na pole v vymezeném oboru</span><span class="sxs-lookup"><span data-stu-id="4181c-102">The type for variable &#39;&lt;variablename&gt;&#39; will not be inferred because it is bound to a field in an enclosing scope</span></span>
<span data-ttu-id="4181c-103">Typ pro proměnnou '\<NázevProměnné >, nebude ho odvodit, protože je vázána na pole v vymezeném oboru.</span><span class="sxs-lookup"><span data-stu-id="4181c-103">The type for variable '\<variablename>' will not be inferred because it is bound to a field in an enclosing scope.</span></span> <span data-ttu-id="4181c-104">Změňte název '\<NázevProměnné >', nebo použijte plně kvalifikovaný název (například 'Me.variablename' nebo 'MyBase.variablename').</span><span class="sxs-lookup"><span data-stu-id="4181c-104">Either change the name of '\<variablename>', or use the fully qualified name (for example, 'Me.variablename' or 'MyBase.variablename').</span></span>  
  
 <span data-ttu-id="4181c-105">Řídicí proměnná smyčky v kódu má stejný název jako pole třídy nebo jiných vymezeném oboru.</span><span class="sxs-lookup"><span data-stu-id="4181c-105">A loop control variable in your code has the same name as a field of the class or other enclosing scope.</span></span> <span data-ttu-id="4181c-106">Protože řídicí proměnná se používá bez `As` klauzuli je vázána na pole ve vymezeném oboru a kompilátor pro něj vytvořit novou proměnnou nebo odvození jeho typu.</span><span class="sxs-lookup"><span data-stu-id="4181c-106">Because the control variable is used without an `As` clause, it is bound to the field in the enclosing scope, and the compiler does not create a new variable for it or infer its type.</span></span>  
  
 <span data-ttu-id="4181c-107">V následujícím příkladu `Index`, proměnné ovládacího prvku v `For` příkaz, je vázán k `Index` pole `Customer` – třída.</span><span class="sxs-lookup"><span data-stu-id="4181c-107">In the following example, `Index`, the control variable in the `For` statement, is bound to the `Index` field in the `Customer` class.</span></span> <span data-ttu-id="4181c-108">Kompilátor nevytvoří nové proměnné pro řídicí proměnná `Index` nebo odvození jeho typu.</span><span class="sxs-lookup"><span data-stu-id="4181c-108">The compiler does not create a new variable for the control variable `Index` or infer its type.</span></span>  
  
```  
Class Customer  
  
    ' The class has a field named Index.  
    Private Index As Integer  
  
    Sub Main()  
  
    ' The following line will raise this warning.  
        For Index = 1 To 10  
            ' ...  
        Next  
  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="4181c-109">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="4181c-109">By default, this message is a warning.</span></span> <span data-ttu-id="4181c-110">Informace o tom, jak skrýt upozornění nebo způsobu zpracování upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="4181c-110">For information about how to hide warnings or how to treat warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="4181c-111">**ID chyby:** BC42110</span><span class="sxs-lookup"><span data-stu-id="4181c-111">**Error ID:** BC42110</span></span>  
  
### <a name="to-address-this-warning"></a><span data-ttu-id="4181c-112">Pro vyřešení tohoto upozornění</span><span class="sxs-lookup"><span data-stu-id="4181c-112">To address this warning</span></span>  
  
-   <span data-ttu-id="4181c-113">Zkontrolujte řídicí proměnná smyčky místní změnou názvu na identifikátor, který není také název pole třídy.</span><span class="sxs-lookup"><span data-stu-id="4181c-113">Make the loop control variable local by changing its name to an identifier that is not also the name of a field of the class.</span></span>  
  
    ```  
    For I = 1 To 10  
    ```  
  
-   <span data-ttu-id="4181c-114">Vysvětlení, že řídicí proměnná smyčky vytvoří vazbu k poli Třída pomocí prefixu `Me.` k názvu proměnné.</span><span class="sxs-lookup"><span data-stu-id="4181c-114">Clarify that the loop control variable binds to the class field by prefixing `Me.` to the variable name.</span></span>  
  
    ```  
    For Me.Index = 1 To 10  
    ```  
  
-   <span data-ttu-id="4181c-115">Aniž byste museli spoléhat na odvození místního typu, použijte `As` klauzule zadejte typ pro proměnnou řízení smyčky.</span><span class="sxs-lookup"><span data-stu-id="4181c-115">Instead of relying on local type inference, use an `As` clause to specify a type for the loop control variable.</span></span>  
  
    ```  
    For Index As Integer = 1 To 10  
    ```  
  
## <a name="example"></a><span data-ttu-id="4181c-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="4181c-116">Example</span></span>  
 <span data-ttu-id="4181c-117">Následující kód ukazuje předchozí příklad s první oprava na místě.</span><span class="sxs-lookup"><span data-stu-id="4181c-117">The following code shows the earlier example with the first correction in place.</span></span>  
  
```  
Class Customer  
  
    ' The class has a field named Index.  
    Private Index As Integer  
  
    Sub Main()  
  
        For I = 1 To 10  
            ' ...  
        Next  
  
    End Sub  
End Class  
```  
  
## <a name="see-also"></a><span data-ttu-id="4181c-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="4181c-118">See Also</span></span>  
 [<span data-ttu-id="4181c-119">Option Infer – příkaz</span><span class="sxs-lookup"><span data-stu-id="4181c-119">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [<span data-ttu-id="4181c-120">Pro každou... Next – příkaz</span><span class="sxs-lookup"><span data-stu-id="4181c-120">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [<span data-ttu-id="4181c-121">Pro... Next – příkaz</span><span class="sxs-lookup"><span data-stu-id="4181c-121">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="4181c-122">Postupy: odkazování na aktuální instanci objektu</span><span class="sxs-lookup"><span data-stu-id="4181c-122">How to: Refer to the Current Instance of an Object</span></span>](../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)  
 [<span data-ttu-id="4181c-123">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="4181c-123">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="4181c-124">ME, My, MyBase a MyClass</span><span class="sxs-lookup"><span data-stu-id="4181c-124">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
