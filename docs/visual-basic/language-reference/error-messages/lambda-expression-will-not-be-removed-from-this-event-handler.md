---
title: Výraz lambda nebude z této obslužné rutiny události odebrán.
ms.date: 07/20/2015
f1_keywords:
- bc42326
- vbc42326
helpviewer_keywords:
- BC42326
ms.assetid: 63214dc6-0112-4245-8ebf-7c9e8f5a5782
ms.openlocfilehash: 2f8b10082bb39c76ba1393daf8327df2ed631caf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568098"
---
# <a name="lambda-expression-will-not-be-removed-from-this-event-handler"></a><span data-ttu-id="696ce-102">Výraz lambda nebude z této obslužné rutiny události odebrán.</span><span class="sxs-lookup"><span data-stu-id="696ce-102">Lambda expression will not be removed from this event handler</span></span>
<span data-ttu-id="696ce-103">Výraz lambda nebude odebrán z této obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="696ce-103">Lambda expression will not be removed from this event handler.</span></span> <span data-ttu-id="696ce-104">Přiřaďte výraz lambda proměnné a proměnnou použijte k přidání a odebrání události.</span><span class="sxs-lookup"><span data-stu-id="696ce-104">Assign the lambda expression to a variable and use the variable to add and remove the event.</span></span>  
  
 <span data-ttu-id="696ce-105">Při výrazů lambda se používají s obslužné rutiny událostí, se nemusí zobrazit chování, které jste očekávali.</span><span class="sxs-lookup"><span data-stu-id="696ce-105">When lambda expressions are used with event handlers, you may not see the behavior you expect.</span></span> <span data-ttu-id="696ce-106">Kompilátor vygeneruje nové metody pro každou definici výrazu lambda i v případě, že jsou identické.</span><span class="sxs-lookup"><span data-stu-id="696ce-106">The compiler generates a new method for each lambda expression definition, even if they are identical.</span></span> <span data-ttu-id="696ce-107">Proto následující kód zobrazí `False`.</span><span class="sxs-lookup"><span data-stu-id="696ce-107">Therefore, the following code displays `False`.</span></span>  
  
```vb  
Module Module1  
  
    Sub Main()  
        Dim fun1 As ChangeInteger = Function(p As Integer) p + 1  
        Dim fun2 As ChangeInteger = Function(p As Integer) p + 1  
        Console.WriteLine(fun1 = fun2)  
    End Sub  
  
    Delegate Function ChangeInteger(ByVal x As Integer) As Integer  
  
End Module  
```  
  
 <span data-ttu-id="696ce-108">Když výrazů lambda se používají s obslužné rutiny událostí, to může způsobit neočekávané výsledky.</span><span class="sxs-lookup"><span data-stu-id="696ce-108">When lambda expressions are used with event handlers, this may cause unexpected results.</span></span> <span data-ttu-id="696ce-109">V následujícím příkladu výraz lambda přidal `AddHandler` se odebral `RemoveHandler` příkazu.</span><span class="sxs-lookup"><span data-stu-id="696ce-109">In the following example, the lambda expression added by `AddHandler` is not removed by the `RemoveHandler` statement.</span></span>  
  
```vb  
Module Module1  
  
    Event ProcessInteger(ByVal x As Integer)  
  
    Sub Main()  
  
        ' The following line adds one listener to the event.  
        AddHandler ProcessInteger, Function(m As Integer) m  
  
        ' The following statement searches the current listeners   
        ' for a match to remove. However, this lambda is not the same  
        ' as the previous one, so nothing is removed.  
        RemoveHandler ProcessInteger, Function(m As Integer) m  
  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="696ce-110">Ve výchozím nastavení tato zpráva je upozornění.</span><span class="sxs-lookup"><span data-stu-id="696ce-110">By default, this message is a warning.</span></span> <span data-ttu-id="696ce-111">Další informace o tom, jak skrýt upozornění nebo zpracovávat upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="696ce-111">For more information about how to hide warnings or treat warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="696ce-112">**ID chyby:** BC42326</span><span class="sxs-lookup"><span data-stu-id="696ce-112">**Error ID:** BC42326</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="696ce-113">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="696ce-113">To correct this error</span></span>  
  
-   <span data-ttu-id="696ce-114">Pokud chcete zabránit upozornění a odebrat výraz lambda, přiřaďte výraz lambda proměnné a použít v obou `AddHandler` a `RemoveHandler` příkazy, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="696ce-114">To avoid the warning and remove the lambda expression, assign the lambda expression to a variable and use the variable in both the `AddHandler` and `RemoveHandler` statements, as shown in the following example.</span></span>  
  
```vb  
Module Module1  
  
    Event ProcessInteger(ByVal x As Integer)  
  
    Dim PrintHandler As ProcessIntegerEventHandler  
  
    Sub Main()  
  
        ' Assign the lambda expression to a variable.  
        PrintHandler = Function(m As Integer) m  
  
        ' Use the variable to add the listener.  
        AddHandler ProcessInteger, PrintHandler  
  
        ' Use the variable again when you want to remove the listener.  
        RemoveHandler ProcessInteger, PrintHandler  
  
    End Sub  
End Module  
```  
  
## <a name="see-also"></a><span data-ttu-id="696ce-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="696ce-115">See also</span></span>
- [<span data-ttu-id="696ce-116">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="696ce-116">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="696ce-117">Volný převod delegáta</span><span class="sxs-lookup"><span data-stu-id="696ce-117">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [<span data-ttu-id="696ce-118">Události</span><span class="sxs-lookup"><span data-stu-id="696ce-118">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
