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
# <a name="lambda-expression-will-not-be-removed-from-this-event-handler"></a>Výraz lambda nebude z této obslužné rutiny události odebrán.

Výraz lambda se z této obslužné rutiny události neodebere. Přiřaďte výraz lambda proměnné a použijte proměnnou k přidání a odebrání události.

Pokud jsou výrazy lambda použity s obslužnými rutinami událostí, nebudete se moci podívat na chování, které očekáváte. Kompilátor generuje novou metodu pro každou definici výrazu lambda, a to i v případě, že jsou identické. Proto následující kód zobrazí `False`.

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

Pokud jsou výrazy lambda použity s obslužnými rutinami událostí, může to vést k neočekávaným výsledkům. V následujícím příkladu není výraz lambda přidaný pomocí `AddHandler` odstraněn pomocí příkazu `RemoveHandler`.

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

Ve výchozím nastavení je tato zpráva upozornění. Další informace o tom, jak skrýt upozornění nebo považovat upozornění jako chyby, najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).

**ID chyby:** BC42326

## <a name="to-correct-this-error"></a>Oprava této chyby

Chcete-li se vyhnout upozornění a odebrat výraz lambda, přiřaďte výraz lambda proměnné a použijte proměnnou v příkazech `AddHandler` a `RemoveHandler`, jak je znázorněno v následujícím příkladu.

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

## <a name="see-also"></a>Viz také:

- [Výrazy lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [Volný převod delegáta](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [Události](../../../visual-basic/programming-guide/language-features/events/index.md)
