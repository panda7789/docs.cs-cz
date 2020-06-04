---
title: Výraz lambda nebude z této obslužné rutiny události odebrán.
ms.date: 07/20/2015
f1_keywords:
- bc42326
- vbc42326
helpviewer_keywords:
- BC42326
ms.assetid: 63214dc6-0112-4245-8ebf-7c9e8f5a5782
ms.openlocfilehash: 07ace3f1b9c5e512227dc1f718ef768b631c8303
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397373"
---
# <a name="lambda-expression-will-not-be-removed-from-this-event-handler"></a><span data-ttu-id="ffefd-102">Výraz lambda nebude z této obslužné rutiny události odebrán.</span><span class="sxs-lookup"><span data-stu-id="ffefd-102">Lambda expression will not be removed from this event handler</span></span>

<span data-ttu-id="ffefd-103">Výraz lambda se z této obslužné rutiny události neodebere.</span><span class="sxs-lookup"><span data-stu-id="ffefd-103">Lambda expression will not be removed from this event handler.</span></span> <span data-ttu-id="ffefd-104">Přiřaďte výraz lambda proměnné a použijte proměnnou k přidání a odebrání události.</span><span class="sxs-lookup"><span data-stu-id="ffefd-104">Assign the lambda expression to a variable and use the variable to add and remove the event.</span></span>

<span data-ttu-id="ffefd-105">Pokud jsou výrazy lambda použity s obslužnými rutinami událostí, nebudete se moci podívat na chování, které očekáváte.</span><span class="sxs-lookup"><span data-stu-id="ffefd-105">When lambda expressions are used with event handlers, you may not see the behavior you expect.</span></span> <span data-ttu-id="ffefd-106">Kompilátor generuje novou metodu pro každou definici výrazu lambda, a to i v případě, že jsou identické.</span><span class="sxs-lookup"><span data-stu-id="ffefd-106">The compiler generates a new method for each lambda expression definition, even if they are identical.</span></span> <span data-ttu-id="ffefd-107">Proto se zobrazí následující kód `False` .</span><span class="sxs-lookup"><span data-stu-id="ffefd-107">Therefore, the following code displays `False`.</span></span>

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

<span data-ttu-id="ffefd-108">Pokud jsou výrazy lambda použity s obslužnými rutinami událostí, může to vést k neočekávaným výsledkům.</span><span class="sxs-lookup"><span data-stu-id="ffefd-108">When lambda expressions are used with event handlers, this may cause unexpected results.</span></span> <span data-ttu-id="ffefd-109">V následujícím příkladu výraz lambda přidaný pomocí `AddHandler` není `RemoveHandler` příkazem odstraněn.</span><span class="sxs-lookup"><span data-stu-id="ffefd-109">In the following example, the lambda expression added by `AddHandler` is not removed by the `RemoveHandler` statement.</span></span>

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

<span data-ttu-id="ffefd-110">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="ffefd-110">By default, this message is a warning.</span></span> <span data-ttu-id="ffefd-111">Další informace o tom, jak skrýt upozornění nebo považovat upozornění jako chyby, najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="ffefd-111">For more information about how to hide warnings or treat warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

<span data-ttu-id="ffefd-112">**ID chyby:** BC42326</span><span class="sxs-lookup"><span data-stu-id="ffefd-112">**Error ID:** BC42326</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="ffefd-113">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="ffefd-113">To correct this error</span></span>

<span data-ttu-id="ffefd-114">Chcete-li se vyhnout upozornění a odebrat výraz lambda, přiřaďte výraz lambda proměnné a použijte proměnnou v `AddHandler` `RemoveHandler` příkazech a, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ffefd-114">To avoid the warning and remove the lambda expression, assign the lambda expression to a variable and use the variable in both the `AddHandler` and `RemoveHandler` statements, as shown in the following example.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ffefd-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="ffefd-115">See also</span></span>

- [<span data-ttu-id="ffefd-116">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="ffefd-116">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="ffefd-117">Volný převod delegáta</span><span class="sxs-lookup"><span data-stu-id="ffefd-117">Relaxed Delegate Conversion</span></span>](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [<span data-ttu-id="ffefd-118">Události</span><span class="sxs-lookup"><span data-stu-id="ffefd-118">Events</span></span>](../../programming-guide/language-features/events/index.md)
