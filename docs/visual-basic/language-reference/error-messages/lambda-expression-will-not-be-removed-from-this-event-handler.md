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
# <a name="lambda-expression-will-not-be-removed-from-this-event-handler"></a>Výraz lambda nebude z této obslužné rutiny události odebrán.

Výraz lambda se z této obslužné rutiny události neodebere. Přiřaďte výraz lambda proměnné a použijte proměnnou k přidání a odebrání události.

Pokud jsou výrazy lambda použity s obslužnými rutinami událostí, nebudete se moci podívat na chování, které očekáváte. Kompilátor generuje novou metodu pro každou definici výrazu lambda, a to i v případě, že jsou identické. Proto se zobrazí následující kód `False` .

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

Pokud jsou výrazy lambda použity s obslužnými rutinami událostí, může to vést k neočekávaným výsledkům. V následujícím příkladu výraz lambda přidaný pomocí `AddHandler` není `RemoveHandler` příkazem odstraněn.

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

Chcete-li se vyhnout upozornění a odebrat výraz lambda, přiřaďte výraz lambda proměnné a použijte proměnnou v `AddHandler` `RemoveHandler` příkazech a, jak je znázorněno v následujícím příkladu.

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

## <a name="see-also"></a>Viz také

- [Výrazy lambda](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [Volný převod delegáta](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [Události](../../programming-guide/language-features/events/index.md)
