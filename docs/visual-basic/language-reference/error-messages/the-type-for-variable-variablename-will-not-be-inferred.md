---
title: Typ pro proměnnou '<variablename>' nebude odvozen, protože je připojen k poli v ohraničujícím oboru.
ms.date: 07/20/2015
f1_keywords:
- vbc42110
- bc42110
helpviewer_keywords:
- BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
ms.openlocfilehash: 98aeb5699fdd5e5e538a205acd37436019c3fc03
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363043"
---
# <a name="the-type-for-variable-variablename-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a><span data-ttu-id="ac2a1-102">Typ pro proměnnou '\<variablename>' nebude odvozen, protože je připojen k poli v ohraničujícím oboru.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-102">The type for variable '\<variablename>' will not be inferred because it is bound to a field in an enclosing scope</span></span>

<span data-ttu-id="ac2a1-103">Typ proměnné ' \<variablename> ' nebude odvozen, protože je svázán s polem v ohraničujícím oboru.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-103">The type for variable '\<variablename>' will not be inferred because it is bound to a field in an enclosing scope.</span></span> <span data-ttu-id="ac2a1-104">Buď změňte název \<variablename> , nebo použijte plně kvalifikovaný název (například "já. Variable" nebo "MyBase. Variable").</span><span class="sxs-lookup"><span data-stu-id="ac2a1-104">Either change the name of '\<variablename>', or use the fully qualified name (for example, 'Me.variablename' or 'MyBase.variablename').</span></span>

<span data-ttu-id="ac2a1-105">Řídicí proměnná smyčky v kódu má stejný název jako pole třídy nebo jiný ohraničující obor.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-105">A loop control variable in your code has the same name as a field of the class or other enclosing scope.</span></span> <span data-ttu-id="ac2a1-106">Vzhledem k tomu, že proměnná ovládacího prvku se používá bez `As` klauzule, je svázána s polem v ohraničujícím oboru a kompilátor pro něj nevytvoří novou proměnnou nebo odvodí její typ.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-106">Because the control variable is used without an `As` clause, it is bound to the field in the enclosing scope, and the compiler does not create a new variable for it or infer its type.</span></span>

<span data-ttu-id="ac2a1-107">V následujícím příkladu `Index` je proměnná ovládacího prvku v `For` příkazu svázána s `Index` polem ve `Customer` třídě.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-107">In the following example, `Index`, the control variable in the `For` statement, is bound to the `Index` field in the `Customer` class.</span></span> <span data-ttu-id="ac2a1-108">Kompilátor nevytvoří novou proměnnou pro proměnnou ovládacího prvku `Index` nebo odvodí její typ.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-108">The compiler does not create a new variable for the control variable `Index` or infer its type.</span></span>

```vb
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

<span data-ttu-id="ac2a1-109">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-109">By default, this message is a warning.</span></span> <span data-ttu-id="ac2a1-110">Informace o tom, jak skrýt upozornění nebo jak zacházet s upozorněními jako s chybami, najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="ac2a1-110">For information about how to hide warnings or how to treat warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

<span data-ttu-id="ac2a1-111">**ID chyby:** BC42110</span><span class="sxs-lookup"><span data-stu-id="ac2a1-111">**Error ID:** BC42110</span></span>

### <a name="to-address-this-warning"></a><span data-ttu-id="ac2a1-112">Řešení tohoto upozornění</span><span class="sxs-lookup"><span data-stu-id="ac2a1-112">To address this warning</span></span>

- <span data-ttu-id="ac2a1-113">Nastavte proměnnou ovládacího prvku smyčky místně změnou jejího názvu na identifikátor, který není zároveň názvem pole třídy.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-113">Make the loop control variable local by changing its name to an identifier that is not also the name of a field of the class.</span></span>

  ```vb
  For I = 1 To 10
  ```

- <span data-ttu-id="ac2a1-114">Objasnění, že řídicí proměnná smyčky se váže k poli Class pomocí prefixování `Me.` k názvu proměnné.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-114">Clarify that the loop control variable binds to the class field by prefixing `Me.` to the variable name.</span></span>

  ```vb
  For Me.Index = 1 To 10
  ```

- <span data-ttu-id="ac2a1-115">Namísto spoléhání na odvození místního typu, použijte `As` klauzuli k určení typu pro proměnnou ovládacího prvku smyčky.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-115">Instead of relying on local type inference, use an `As` clause to specify a type for the loop control variable.</span></span>

  ```vb
  For Index As Integer = 1 To 10
  ```

## <a name="example"></a><span data-ttu-id="ac2a1-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="ac2a1-116">Example</span></span>
 <span data-ttu-id="ac2a1-117">Následující kód ukazuje předchozí příklad s první opravou na místě.</span><span class="sxs-lookup"><span data-stu-id="ac2a1-117">The following code shows the earlier example with the first correction in place.</span></span>

```vb
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

## <a name="see-also"></a><span data-ttu-id="ac2a1-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="ac2a1-118">See also</span></span>

- [<span data-ttu-id="ac2a1-119">Option Infer – příkaz</span><span class="sxs-lookup"><span data-stu-id="ac2a1-119">Option Infer Statement</span></span>](../statements/option-infer-statement.md)
- [<span data-ttu-id="ac2a1-120">For Each...Next – příkaz</span><span class="sxs-lookup"><span data-stu-id="ac2a1-120">For Each...Next Statement</span></span>](../statements/for-each-next-statement.md)
- [<span data-ttu-id="ac2a1-121">For...Next – příkaz</span><span class="sxs-lookup"><span data-stu-id="ac2a1-121">For...Next Statement</span></span>](../statements/for-next-statement.md)
- [<span data-ttu-id="ac2a1-122">Postupy: Odkazování na aktuální instanci objektu</span><span class="sxs-lookup"><span data-stu-id="ac2a1-122">How to: Refer to the Current Instance of an Object</span></span>](../../programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)
- [<span data-ttu-id="ac2a1-123">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="ac2a1-123">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="ac2a1-124">Me, My, MyBase a MyClass</span><span class="sxs-lookup"><span data-stu-id="ac2a1-124">Me, My, MyBase, and MyClass</span></span>](../../programming-guide/program-structure/me-my-mybase-and-myclass.md)
