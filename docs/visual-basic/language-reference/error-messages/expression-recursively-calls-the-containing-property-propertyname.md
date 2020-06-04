---
title: Výraz rekurzivně volá nadřazenou vlastnost '<propertyname>'.
ms.date: 07/20/2015
f1_keywords:
- vbc42026
- BC42026
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
ms.openlocfilehash: e3a9f4cf2f4105d2c449813bf0c593860df7d1f0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409527"
---
# <a name="expression-recursively-calls-the-containing-property-propertyname"></a><span data-ttu-id="ae162-102">Výraz rekurzivně volá nadřazenou vlastnost '\<propertyname>'.</span><span class="sxs-lookup"><span data-stu-id="ae162-102">Expression recursively calls the containing property '\<propertyname>'</span></span>
<span data-ttu-id="ae162-103">Příkaz v `Set` proceduře definice vlastnosti ukládá hodnotu do názvu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ae162-103">A statement in the `Set` procedure of a property definition stores a value into the name of the property.</span></span>  
  
 <span data-ttu-id="ae162-104">Doporučený postup pro uchovávání hodnoty vlastnosti je definovat `Private` proměnnou v kontejneru vlastností a použít ji v `Get` `Set` postupech a.</span><span class="sxs-lookup"><span data-stu-id="ae162-104">The recommended approach to holding the value of a property is to define a `Private` variable in the property's container and use it in both the `Get` and `Set` procedures.</span></span> <span data-ttu-id="ae162-105">`Set`Procedura by pak měla uložit příchozí hodnotu v této `Private` proměnné.</span><span class="sxs-lookup"><span data-stu-id="ae162-105">The `Set` procedure should then store the incoming value in this `Private` variable.</span></span>  
  
 <span data-ttu-id="ae162-106">`Get`Procedura se chová jako `Function` procedura, takže může přiřadit hodnotu k názvu vlastnosti a vracet řízení, když se setkáte s `End Get` příkazem.</span><span class="sxs-lookup"><span data-stu-id="ae162-106">The `Get` procedure behaves like a `Function` procedure, so it can assign a value to the property name and return control by encountering the `End Get` statement.</span></span> <span data-ttu-id="ae162-107">Doporučený postup je však zahrnout `Private` proměnnou jako hodnotu v [příkazu return](../statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ae162-107">The recommended approach, however, is to include the `Private` variable as the value in a [Return Statement](../statements/return-statement.md).</span></span>  
  
 <span data-ttu-id="ae162-108">`Set`Procedura se chová jako `Sub` procedura, která nevrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ae162-108">The `Set` procedure behaves like a `Sub` procedure, which does not return a value.</span></span> <span data-ttu-id="ae162-109">Proto procedura nebo název vlastnosti nemá v rámci procedury žádný zvláštní význam `Set` a do ní nelze uložit hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ae162-109">Therefore, the procedure or property name has no special meaning within a `Set` procedure, and you cannot store a value into it.</span></span>  
  
 <span data-ttu-id="ae162-110">Následující příklad ilustruje přístup, který může způsobit tuto chybu, následovanou doporučeným přístupem.</span><span class="sxs-lookup"><span data-stu-id="ae162-110">The following example illustrates the approach that can cause this error, followed by the recommended approach.</span></span>  
  
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
  
 <span data-ttu-id="ae162-111">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="ae162-111">By default, this message is a warning.</span></span> <span data-ttu-id="ae162-112">Další informace o skrývání upozornění nebo zpracování upozornění jako chyb najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="ae162-112">For more information about hiding warnings or treating warnings as errors, please see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="ae162-113">**ID chyby:** BC42026</span><span class="sxs-lookup"><span data-stu-id="ae162-113">**Error ID:** BC42026</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ae162-114">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="ae162-114">To correct this error</span></span>  
  
- <span data-ttu-id="ae162-115">Přepište definici vlastnosti tak, aby používala doporučený přístup, jak je znázorněno v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ae162-115">Rewrite the property definition to use the recommended approach as illustrated in the preceding example.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae162-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="ae162-116">See also</span></span>

- [<span data-ttu-id="ae162-117">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="ae162-117">Property Procedures</span></span>](../../programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="ae162-118">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="ae162-118">Property Statement</span></span>](../statements/property-statement.md)
- [<span data-ttu-id="ae162-119">Set – příkaz</span><span class="sxs-lookup"><span data-stu-id="ae162-119">Set Statement</span></span>](../statements/set-statement.md)
