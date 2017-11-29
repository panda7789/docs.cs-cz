---
title: "Použití odchylek v delegátech (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7b5c20f1-6416-46a3-94b6-f109c31c842c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 435591d69e67c4fc4be8e781c5f63e025c71a8cf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="using-variance-in-delegates-visual-basic"></a>Použití odchylek v delegátech (Visual Basic)
Přiřadíte-li metodu s delegátem, *kovariance* a *kontravariance* poskytují flexibilitu pro odpovídající typu delegáta podpisem metoda. Kovariance umožňuje metoda má návratový typ, který je odvozený více než která definována v delegát. Kontravariance umožňuje metodu, která má parametr typy, které jsou odvozené méně než ty, které v typu delegáta.  
  
## <a name="example-1-covariance"></a>Příklad 1: kovariance  
  
### <a name="description"></a>Popis  
 Tento příklad ukazuje, jak lze pomocí metody, které mají návratové typy, které jsou odvozeny od návratový typ v hlavičce delegáta delegáti. Datový typ vrácený `DogsHandler` je typu `Dogs`, která je odvozena z `Mammals` typ, který je definován v delegát.  
  
### <a name="code"></a>Kód  
  
```vb  
Class Mammals  
End Class  
  
Class Dogs  
    Inherits Mammals  
End Class  
Class Test  
    Public Delegate Function HandlerMethod() As Mammals  
    Public Shared Function MammalsHandler() As Mammals  
        Return Nothing  
    End Function  
    Public Shared Function DogsHandler() As Dogs  
        Return Nothing  
    End Function  
    Sub Test()  
        Dim handlerMammals As HandlerMethod = AddressOf MammalsHandler  
        ' Covariance enables this assignment.  
        Dim handlerDogs As HandlerMethod = AddressOf DogsHandler  
    End Sub  
End Class  
```  
  
## <a name="example-2-contravariance"></a>Příklad 2: kontravariance  
  
### <a name="description"></a>Popis  
 Tento příklad ukazuje, jak delegáti lze provádět pomocí metod, které mají parametry typu, které jsou základní typy delegáta podpis parametr typu. S kontravariance můžete použít jeden obslužné rutiny události místo samostatné obslužné rutiny. Například můžete vytvořit obslužnou rutinu události, který přijímá `EventArgs` vstupní parametr a použít je s `Button.MouseClick` událost, která odešle `MouseEventArgs` typu jako parametr a také s `TextBox.KeyDown` událost, která odešle `KeyEventArgs` parametr.  
  
### <a name="code"></a>Kód  
  
```vb  
' Event hander that accepts a parameter of the EventArgs type.  
Private Sub MultiHandler(ByVal sender As Object,  
                         ByVal e As System.EventArgs)  
    Label1.Text = DateTime.Now  
End Sub  
  
Private Sub Form1_Load(ByVal sender As System.Object,  
    ByVal e As System.EventArgs) Handles MyBase.Load  
  
    ' You can use a method that has an EventArgs parameter,  
    ' although the event expects the KeyEventArgs parameter.  
    AddHandler Button1.KeyDown, AddressOf MultiHandler  
  
    ' You can use the same method   
    ' for the event that expects the MouseEventArgs parameter.  
    AddHandler Button1.MouseClick, AddressOf MultiHandler  
End Sub  
```  
  
## <a name="see-also"></a>Viz také  
 [Odchylky v delegátech (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)  
 [Použití odchylek pro Func a akce obecní delegáti (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
