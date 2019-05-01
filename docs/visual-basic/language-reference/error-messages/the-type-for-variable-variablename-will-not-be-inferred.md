---
title: Typ pro proměnnou '<variablename>' nebude odvozen, protože je připojen k poli v ohraničujícím oboru.
ms.date: 07/20/2015
f1_keywords:
- vbc42110
- bc42110
helpviewer_keywords:
- BC42110
ms.assetid: ef4442eb-08d1-434f-a03b-4aa2ed4e4414
ms.openlocfilehash: bcd142785d8ee736c6a1b41950fae80e4d26fa18
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013644"
---
# <a name="the-type-for-variable-variablename-will-not-be-inferred-because-it-is-bound-to-a-field-in-an-enclosing-scope"></a><span data-ttu-id="cda91-102">Typ pro proměnnou '\<NázevProměnné >' nebude odvozen, protože je vázán k poli v ohraničujícím oboru</span><span class="sxs-lookup"><span data-stu-id="cda91-102">The type for variable '\<variablename>' will not be inferred because it is bound to a field in an enclosing scope</span></span>
<span data-ttu-id="cda91-103">Typ pro proměnnou '\<NázevProměnné >' nebude odvozen, protože je vázán k poli v ohraničujícím oboru.</span><span class="sxs-lookup"><span data-stu-id="cda91-103">The type for variable '\<variablename>' will not be inferred because it is bound to a field in an enclosing scope.</span></span> <span data-ttu-id="cda91-104">Změňte název "\<NázevProměnné >", nebo použijte plně kvalifikovaný název (například 'Me.variablename' nebo "MyBase.variablename").</span><span class="sxs-lookup"><span data-stu-id="cda91-104">Either change the name of '\<variablename>', or use the fully qualified name (for example, 'Me.variablename' or 'MyBase.variablename').</span></span>  
  
 <span data-ttu-id="cda91-105">Řídicí proměnná smyčky for v kódu má stejný název jako pole třídy nebo jiných nadřazeném oboru.</span><span class="sxs-lookup"><span data-stu-id="cda91-105">A loop control variable in your code has the same name as a field of the class or other enclosing scope.</span></span> <span data-ttu-id="cda91-106">Protože proměnné ovládacího prvku se používá bez `As` klauzule, je svázaná s daným polem v nadřazeném oboru, a kompilátor pro něj vytvořit novou proměnnou nebo odvodit typ.</span><span class="sxs-lookup"><span data-stu-id="cda91-106">Because the control variable is used without an `As` clause, it is bound to the field in the enclosing scope, and the compiler does not create a new variable for it or infer its type.</span></span>  
  
 <span data-ttu-id="cda91-107">V následujícím příkladu `Index`, proměnné ovládacího prvku v `For` příkazu je vázán na `Index` pole `Customer` třídy.</span><span class="sxs-lookup"><span data-stu-id="cda91-107">In the following example, `Index`, the control variable in the `For` statement, is bound to the `Index` field in the `Customer` class.</span></span> <span data-ttu-id="cda91-108">Kompilátor nevytvoří nové proměnné pro proměnnou ovládacího prvku `Index` nebo jeho typ odvodit.</span><span class="sxs-lookup"><span data-stu-id="cda91-108">The compiler does not create a new variable for the control variable `Index` or infer its type.</span></span>  
  
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
  
 <span data-ttu-id="cda91-109">Ve výchozím nastavení tato zpráva je upozornění.</span><span class="sxs-lookup"><span data-stu-id="cda91-109">By default, this message is a warning.</span></span> <span data-ttu-id="cda91-110">Informace o tom, jak skrýt upozornění nebo jak zpracovávat upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="cda91-110">For information about how to hide warnings or how to treat warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="cda91-111">**ID chyby:** BC42110</span><span class="sxs-lookup"><span data-stu-id="cda91-111">**Error ID:** BC42110</span></span>  
  
### <a name="to-address-this-warning"></a><span data-ttu-id="cda91-112">Chcete-li vyřešit tato upozornění</span><span class="sxs-lookup"><span data-stu-id="cda91-112">To address this warning</span></span>  
  
- <span data-ttu-id="cda91-113">Díky řídicí proměnná smyčky for místní změny jeho názvu identifikátor, který není také název pole třídy.</span><span class="sxs-lookup"><span data-stu-id="cda91-113">Make the loop control variable local by changing its name to an identifier that is not also the name of a field of the class.</span></span>  
  
    ```  
    For I = 1 To 10  
    ```  
  
- <span data-ttu-id="cda91-114">Vysvětlení, že řídicí proměnná smyčky for váže pole třídy jsou `Me.` k názvu proměnné.</span><span class="sxs-lookup"><span data-stu-id="cda91-114">Clarify that the loop control variable binds to the class field by prefixing `Me.` to the variable name.</span></span>  
  
    ```  
    For Me.Index = 1 To 10  
    ```  
  
- <span data-ttu-id="cda91-115">Aniž byste museli spoléhat na odvození místního typu, použijte `As` klauzule zadat typ řídicí proměnná smyčky for.</span><span class="sxs-lookup"><span data-stu-id="cda91-115">Instead of relying on local type inference, use an `As` clause to specify a type for the loop control variable.</span></span>  
  
    ```  
    For Index As Integer = 1 To 10  
    ```  
  
## <a name="example"></a><span data-ttu-id="cda91-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="cda91-116">Example</span></span>  
 <span data-ttu-id="cda91-117">Následující kód ukazuje předchozí příklad s první opravu na místě.</span><span class="sxs-lookup"><span data-stu-id="cda91-117">The following code shows the earlier example with the first correction in place.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cda91-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cda91-118">See also</span></span>

- [<span data-ttu-id="cda91-119">Příkaz Option Infer</span><span class="sxs-lookup"><span data-stu-id="cda91-119">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="cda91-120">Příkaz For Each...Next</span><span class="sxs-lookup"><span data-stu-id="cda91-120">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="cda91-121">Příkaz For...Next</span><span class="sxs-lookup"><span data-stu-id="cda91-121">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="cda91-122">Postupy: Odkazování na aktuální instanci objektu</span><span class="sxs-lookup"><span data-stu-id="cda91-122">How to: Refer to the Current Instance of an Object</span></span>](../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)
- [<span data-ttu-id="cda91-123">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="cda91-123">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="cda91-124">Me, My, MyBase a MyClass</span><span class="sxs-lookup"><span data-stu-id="cda91-124">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
