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
# <a name="lambda-expression-will-not-be-removed-from-this-event-handler"></a>Výraz lambda nebude z této obslužné rutiny události odebrán.
Výraz lambda nebude odebrán z této obslužné rutiny události. Přiřaďte výraz lambda proměnné a proměnnou použijte k přidání a odebrání události.  
  
 Při výrazů lambda se používají s obslužné rutiny událostí, se nemusí zobrazit chování, které jste očekávali. Kompilátor vygeneruje nové metody pro každou definici výrazu lambda i v případě, že jsou identické. Proto následující kód zobrazí `False`.  
  
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
  
 Když výrazů lambda se používají s obslužné rutiny událostí, to může způsobit neočekávané výsledky. V následujícím příkladu výraz lambda přidal `AddHandler` se odebral `RemoveHandler` příkazu.  
  
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
  
 Ve výchozím nastavení tato zpráva je upozornění. Další informace o tom, jak skrýt upozornění nebo zpracovávat upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC42326  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Pokud chcete zabránit upozornění a odebrat výraz lambda, přiřaďte výraz lambda proměnné a použít v obou `AddHandler` a `RemoveHandler` příkazy, jak je znázorněno v následujícím příkladu.  
  
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
