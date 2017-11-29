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
# <a name="using-variance-in-delegates-visual-basic"></a><span data-ttu-id="c13d6-102">Použití odchylek v delegátech (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c13d6-102">Using Variance in Delegates (Visual Basic)</span></span>
<span data-ttu-id="c13d6-103">Přiřadíte-li metodu s delegátem, *kovariance* a *kontravariance* poskytují flexibilitu pro odpovídající typu delegáta podpisem metoda.</span><span class="sxs-lookup"><span data-stu-id="c13d6-103">When you assign a method to a delegate, *covariance* and *contravariance* provide flexibility for matching a delegate type with a method signature.</span></span> <span data-ttu-id="c13d6-104">Kovariance umožňuje metoda má návratový typ, který je odvozený více než která definována v delegát.</span><span class="sxs-lookup"><span data-stu-id="c13d6-104">Covariance permits a method to have return type that is more derived than that defined in the delegate.</span></span> <span data-ttu-id="c13d6-105">Kontravariance umožňuje metodu, která má parametr typy, které jsou odvozené méně než ty, které v typu delegáta.</span><span class="sxs-lookup"><span data-stu-id="c13d6-105">Contravariance permits a method that has parameter types that are less derived than those in the delegate type.</span></span>  
  
## <a name="example-1-covariance"></a><span data-ttu-id="c13d6-106">Příklad 1: kovariance</span><span class="sxs-lookup"><span data-stu-id="c13d6-106">Example 1: Covariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="c13d6-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c13d6-107">Description</span></span>  
 <span data-ttu-id="c13d6-108">Tento příklad ukazuje, jak lze pomocí metody, které mají návratové typy, které jsou odvozeny od návratový typ v hlavičce delegáta delegáti.</span><span class="sxs-lookup"><span data-stu-id="c13d6-108">This example demonstrates how delegates can be used with methods that have return types that are derived from the return type in the delegate signature.</span></span> <span data-ttu-id="c13d6-109">Datový typ vrácený `DogsHandler` je typu `Dogs`, která je odvozena z `Mammals` typ, který je definován v delegát.</span><span class="sxs-lookup"><span data-stu-id="c13d6-109">The data type returned by `DogsHandler` is of type `Dogs`, which derives from the `Mammals` type that is defined in the delegate.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c13d6-110">Kód</span><span class="sxs-lookup"><span data-stu-id="c13d6-110">Code</span></span>  
  
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
  
## <a name="example-2-contravariance"></a><span data-ttu-id="c13d6-111">Příklad 2: kontravariance</span><span class="sxs-lookup"><span data-stu-id="c13d6-111">Example 2: Contravariance</span></span>  
  
### <a name="description"></a><span data-ttu-id="c13d6-112">Popis</span><span class="sxs-lookup"><span data-stu-id="c13d6-112">Description</span></span>  
 <span data-ttu-id="c13d6-113">Tento příklad ukazuje, jak delegáti lze provádět pomocí metod, které mají parametry typu, které jsou základní typy delegáta podpis parametr typu.</span><span class="sxs-lookup"><span data-stu-id="c13d6-113">This example demonstrates how delegates can be used with methods that have parameters of a type that are base types of the delegate signature parameter type.</span></span> <span data-ttu-id="c13d6-114">S kontravariance můžete použít jeden obslužné rutiny události místo samostatné obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="c13d6-114">With contravariance, you can use one event handler instead of separate handlers.</span></span> <span data-ttu-id="c13d6-115">Například můžete vytvořit obslužnou rutinu události, který přijímá `EventArgs` vstupní parametr a použít je s `Button.MouseClick` událost, která odešle `MouseEventArgs` typu jako parametr a také s `TextBox.KeyDown` událost, která odešle `KeyEventArgs` parametr.</span><span class="sxs-lookup"><span data-stu-id="c13d6-115">For example, you can create an event handler that accepts an `EventArgs` input parameter and use it with a `Button.MouseClick` event that sends a `MouseEventArgs` type as a parameter, and also with a `TextBox.KeyDown` event that sends a `KeyEventArgs` parameter.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c13d6-116">Kód</span><span class="sxs-lookup"><span data-stu-id="c13d6-116">Code</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c13d6-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="c13d6-117">See Also</span></span>  
 [<span data-ttu-id="c13d6-118">Odchylky v delegátech (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c13d6-118">Variance in Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)  
 [<span data-ttu-id="c13d6-119">Použití odchylek pro Func a akce obecní delegáti (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c13d6-119">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
