---
title: Výraz rekurzivně volá nadřazenou vlastnost '<propertyname>'.
ms.date: 07/20/2015
f1_keywords:
- vbc42026
- BC42026
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
ms.openlocfilehash: 42177f22e632e4a05b1f0b4d934f3e56ab9ff0f2
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698571"
---
# <a name="expression-recursively-calls-the-containing-property-propertyname"></a><span data-ttu-id="c6a5a-102">Výraz rekurzivně volá nadřazenou vlastnost\<PropertyName >.</span><span class="sxs-lookup"><span data-stu-id="c6a5a-102">Expression recursively calls the containing property '\<propertyname>'</span></span>
<span data-ttu-id="c6a5a-103">Příkaz v `Set` proceduře definice vlastnosti ukládá hodnotu do názvu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c6a5a-103">A statement in the `Set` procedure of a property definition stores a value into the name of the property.</span></span>  
  
 <span data-ttu-id="c6a5a-104">Doporučený postup pro uchovávání hodnoty vlastnosti je definovat `Private` proměnnou v kontejneru vlastností a použít ji v postupech `Get` a `Set`.</span><span class="sxs-lookup"><span data-stu-id="c6a5a-104">The recommended approach to holding the value of a property is to define a `Private` variable in the property's container and use it in both the `Get` and `Set` procedures.</span></span> <span data-ttu-id="c6a5a-105">Procedura `Set` by pak měla uložit příchozí hodnotu v této `Private` proměnné.</span><span class="sxs-lookup"><span data-stu-id="c6a5a-105">The `Set` procedure should then store the incoming value in this `Private` variable.</span></span>  
  
 <span data-ttu-id="c6a5a-106">Postup `Get` se chová jako `Function` postup, takže může přiřadit hodnotu názvu vlastnosti a vrátit řízení návratovým prvkem, který nalezne příkaz `End Get`.</span><span class="sxs-lookup"><span data-stu-id="c6a5a-106">The `Get` procedure behaves like a `Function` procedure, so it can assign a value to the property name and return control by encountering the `End Get` statement.</span></span> <span data-ttu-id="c6a5a-107">Doporučený postup je však zahrnout proměnnou `Private` jako hodnotu v [příkazu return](../../../visual-basic/language-reference/statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c6a5a-107">The recommended approach, however, is to include the `Private` variable as the value in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
 <span data-ttu-id="c6a5a-108">Procedura `Set` se chová jako `Sub` procedura, která nevrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c6a5a-108">The `Set` procedure behaves like a `Sub` procedure, which does not return a value.</span></span> <span data-ttu-id="c6a5a-109">Název procedury nebo vlastnosti proto v rámci `Set` procedury nemá žádný zvláštní význam a do ní nelze uložit hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c6a5a-109">Therefore, the procedure or property name has no special meaning within a `Set` procedure, and you cannot store a value into it.</span></span>  
  
 <span data-ttu-id="c6a5a-110">Následující příklad ilustruje přístup, který může způsobit tuto chybu, následovanou doporučeným přístupem.</span><span class="sxs-lookup"><span data-stu-id="c6a5a-110">The following example illustrates the approach that can cause this error, followed by the recommended approach.</span></span>  
  
```vb  
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
  
 <span data-ttu-id="c6a5a-111">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="c6a5a-111">By default, this message is a warning.</span></span> <span data-ttu-id="c6a5a-112">Další informace o skrývání upozornění nebo zpracování upozornění jako chyb najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="c6a5a-112">For more information about hiding warnings or treating warnings as errors, please see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="c6a5a-113">**ID chyby:** BC42026</span><span class="sxs-lookup"><span data-stu-id="c6a5a-113">**Error ID:** BC42026</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c6a5a-114">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="c6a5a-114">To correct this error</span></span>  
  
- <span data-ttu-id="c6a5a-115">Přepište definici vlastnosti tak, aby používala doporučený přístup, jak je znázorněno v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="c6a5a-115">Rewrite the property definition to use the recommended approach as illustrated in the preceding example.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6a5a-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c6a5a-116">See also</span></span>

- [<span data-ttu-id="c6a5a-117">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="c6a5a-117">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="c6a5a-118">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="c6a5a-118">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="c6a5a-119">Příkaz Set</span><span class="sxs-lookup"><span data-stu-id="c6a5a-119">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
