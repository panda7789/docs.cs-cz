---
title: Výraz rekurzivně volá vlastnost obsahující &#39; &lt;propertyname&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc42026
- BC42026
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
ms.openlocfilehash: f14e2645772b22a8f6ff2385dcd316a42d1d5cf0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588840"
---
# <a name="expression-recursively-calls-the-containing-property-39ltpropertynamegt39"></a><span data-ttu-id="2dfa1-102">Výraz rekurzivně volá vlastnost obsahující &#39; &lt;propertyname&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="2dfa1-102">Expression recursively calls the containing property &#39;&lt;propertyname&gt;&#39;</span></span>
<span data-ttu-id="2dfa1-103">Příkaz v `Set` postup definici vlastnosti ukládá hodnotu do názvu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="2dfa1-103">A statement in the `Set` procedure of a property definition stores a value into the name of the property.</span></span>  
  
 <span data-ttu-id="2dfa1-104">Je doporučeným přístupem k hodnota vlastnosti, která uchovává k definování `Private` proměnné v kontejneru vlastnosti a použít ho v obou `Get` a `Set` postupy.</span><span class="sxs-lookup"><span data-stu-id="2dfa1-104">The recommended approach to holding the value of a property is to define a `Private` variable in the property's container and use it in both the `Get` and `Set` procedures.</span></span> <span data-ttu-id="2dfa1-105">`Set` Postup by pak uložení příchozí hodnoty v tomto `Private` proměnné.</span><span class="sxs-lookup"><span data-stu-id="2dfa1-105">The `Set` procedure should then store the incoming value in this `Private` variable.</span></span>  
  
 <span data-ttu-id="2dfa1-106">`Get` Postup chová jako `Function` postup, takže se můžete přiřadit hodnotu pro název vlastnosti a vrátit řízení podle zjištění `End Get` příkaz.</span><span class="sxs-lookup"><span data-stu-id="2dfa1-106">The `Get` procedure behaves like a `Function` procedure, so it can assign a value to the property name and return control by encountering the `End Get` statement.</span></span> <span data-ttu-id="2dfa1-107">Doporučený postup je však zahrnout `Private` jako hodnota v proměnné [příkaz Return](../../../visual-basic/language-reference/statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2dfa1-107">The recommended approach, however, is to include the `Private` variable as the value in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
 <span data-ttu-id="2dfa1-108">`Set` Postupu se chová stejně jako `Sub` postup, který nevrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2dfa1-108">The `Set` procedure behaves like a `Sub` procedure, which does not return a value.</span></span> <span data-ttu-id="2dfa1-109">Proto název postupu nebo vlastnost nemá žádný speciální význam v rámci `Set` postup a nelze uložit do ní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2dfa1-109">Therefore, the procedure or property name has no special meaning within a `Set` procedure, and you cannot store a value into it.</span></span>  
  
 <span data-ttu-id="2dfa1-110">Následující příklad ukazuje postup, který může způsobit, že tato chyba, za nímž následuje o doporučený postup.</span><span class="sxs-lookup"><span data-stu-id="2dfa1-110">The following example illustrates the approach that can cause this error, followed by the recommended approach.</span></span>  
  
```  
Public Class illustrateProperties  
' The code in the following property causes this error.  
    Public Property badProp() As Char  
        Get  
            Dim charValue As Char  
            ' Insert code to update charValue.  
            badProp = charValue  
        End Get  
        Set(ByVal Value As Char)  
            ' The following statement causes this error.  
            badProp = Value  
            ' The value stored in the local variable badProp  
            ' is not used by the Get procedure in this property.  
        End Set  
    End Property  
' The following code uses the recommended approach.  
    Private propValue As Char  
    Public Property goodProp() As Char  
        Get  
            ' Insert code to update propValue.  
            Return propValue  
        End Get  
        Set(ByVal Value As Char)  
            propValue = Value  
        End Set  
    End Property  
End Class  
```  
  
 <span data-ttu-id="2dfa1-111">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="2dfa1-111">By default, this message is a warning.</span></span> <span data-ttu-id="2dfa1-112">Další informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="2dfa1-112">For more information about hiding warnings or treating warnings as errors, please see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="2dfa1-113">**ID chyby:** BC42026</span><span class="sxs-lookup"><span data-stu-id="2dfa1-113">**Error ID:** BC42026</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2dfa1-114">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="2dfa1-114">To correct this error</span></span>  
  
-   <span data-ttu-id="2dfa1-115">Přepisování definice vlastnosti, která použijte doporučený postup, jak je ukázáno v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="2dfa1-115">Rewrite the property definition to use the recommended approach as illustrated in the preceding example.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dfa1-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="2dfa1-116">See Also</span></span>  
 [<span data-ttu-id="2dfa1-117">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="2dfa1-117">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [<span data-ttu-id="2dfa1-118">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="2dfa1-118">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="2dfa1-119">Příkaz Set</span><span class="sxs-lookup"><span data-stu-id="2dfa1-119">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
