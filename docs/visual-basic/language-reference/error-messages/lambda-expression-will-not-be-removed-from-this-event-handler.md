---
title: Výraz lambda nebude z této obslužné rutiny události odebrán.
ms.date: 07/20/2015
f1_keywords:
- bc42326
- vbc42326
helpviewer_keywords:
- BC42326
ms.assetid: 63214dc6-0112-4245-8ebf-7c9e8f5a5782
ms.openlocfilehash: 52107589c6bbebbd34ecbb090845f4031612c276
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72578926"
---
# <a name="lambda-expression-will-not-be-removed-from-this-event-handler"></a><span data-ttu-id="aff0b-102">Výraz lambda nebude z této obslužné rutiny události odebrán.</span><span class="sxs-lookup"><span data-stu-id="aff0b-102">Lambda expression will not be removed from this event handler</span></span>

<span data-ttu-id="aff0b-103">Výraz lambda se z této obslužné rutiny události neodebere.</span><span class="sxs-lookup"><span data-stu-id="aff0b-103">Lambda expression will not be removed from this event handler.</span></span> <span data-ttu-id="aff0b-104">Přiřaďte výraz lambda proměnné a použijte proměnnou k přidání a odebrání události.</span><span class="sxs-lookup"><span data-stu-id="aff0b-104">Assign the lambda expression to a variable and use the variable to add and remove the event.</span></span>

<span data-ttu-id="aff0b-105">Pokud jsou výrazy lambda použity s obslužnými rutinami událostí, nebudete se moci podívat na chování, které očekáváte.</span><span class="sxs-lookup"><span data-stu-id="aff0b-105">When lambda expressions are used with event handlers, you may not see the behavior you expect.</span></span> <span data-ttu-id="aff0b-106">Kompilátor generuje novou metodu pro každou definici výrazu lambda, a to i v případě, že jsou identické.</span><span class="sxs-lookup"><span data-stu-id="aff0b-106">The compiler generates a new method for each lambda expression definition, even if they are identical.</span></span> <span data-ttu-id="aff0b-107">Proto následující kód zobrazí `False`.</span><span class="sxs-lookup"><span data-stu-id="aff0b-107">Therefore, the following code displays `False`.</span></span>

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

<span data-ttu-id="aff0b-108">Pokud jsou výrazy lambda použity s obslužnými rutinami událostí, může to vést k neočekávaným výsledkům.</span><span class="sxs-lookup"><span data-stu-id="aff0b-108">When lambda expressions are used with event handlers, this may cause unexpected results.</span></span> <span data-ttu-id="aff0b-109">V následujícím příkladu není výraz lambda přidaný pomocí `AddHandler` odstraněn pomocí příkazu `RemoveHandler`.</span><span class="sxs-lookup"><span data-stu-id="aff0b-109">In the following example, the lambda expression added by `AddHandler` is not removed by the `RemoveHandler` statement.</span></span>

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

<span data-ttu-id="aff0b-110">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="aff0b-110">By default, this message is a warning.</span></span> <span data-ttu-id="aff0b-111">Další informace o tom, jak skrýt upozornění nebo považovat upozornění jako chyby, najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="aff0b-111">For more information about how to hide warnings or treat warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

<span data-ttu-id="aff0b-112">**ID chyby:** BC42326</span><span class="sxs-lookup"><span data-stu-id="aff0b-112">**Error ID:** BC42326</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="aff0b-113">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="aff0b-113">To correct this error</span></span>

<span data-ttu-id="aff0b-114">Chcete-li se vyhnout upozornění a odebrat výraz lambda, přiřaďte výraz lambda proměnné a použijte proměnnou v příkazech `AddHandler` a `RemoveHandler`, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="aff0b-114">To avoid the warning and remove the lambda expression, assign the lambda expression to a variable and use the variable in both the `AddHandler` and `RemoveHandler` statements, as shown in the following example.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="aff0b-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aff0b-115">See also</span></span>

- [<span data-ttu-id="aff0b-116">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="aff0b-116">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="aff0b-117">Volný převod delegáta</span><span class="sxs-lookup"><span data-stu-id="aff0b-117">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [<span data-ttu-id="aff0b-118">Události</span><span class="sxs-lookup"><span data-stu-id="aff0b-118">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
