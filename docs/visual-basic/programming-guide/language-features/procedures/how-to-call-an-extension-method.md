---
title: "Postupy: Volání metody rozšíření (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 25b5a86af15694e6f64f96a5d5d645a01f8f1f12
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-an-extension-method-visual-basic"></a><span data-ttu-id="e43c8-102">Postupy: Volání metody rozšíření (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e43c8-102">How to: Call an Extension Method (Visual Basic)</span></span>
<span data-ttu-id="e43c8-103">Rozšiřující metody umožňují přidání metody do existující třídy.</span><span class="sxs-lookup"><span data-stu-id="e43c8-103">Extension methods enable you to add methods to an existing class.</span></span> <span data-ttu-id="e43c8-104">Po metody rozšíření je deklarovaný a začlenění do oboru, můžete ji volat jako metodu instance typu, který rozšiřuje ji.</span><span class="sxs-lookup"><span data-stu-id="e43c8-104">After an extension method is declared and brought into scope, you can call it like an instance method of the type that it extends.</span></span> <span data-ttu-id="e43c8-105">Další informace o tom, jak zápis metody rozšíření najdete v tématu [postupy: zápis metody rozšíření](./how-to-write-an-extension-method.md).</span><span class="sxs-lookup"><span data-stu-id="e43c8-105">For more information about how to write an extension method, see [How to: Write an Extension Method](./how-to-write-an-extension-method.md).</span></span>  
  
 <span data-ttu-id="e43c8-106">Následující pokyny naleznete v metodě rozšíření `PrintAndPunctuate`, který se zobrazí řetězec instanci, která následuje libovolnou hodnotu vyvolá se odesílá ve pro druhý parametr `punc`.</span><span class="sxs-lookup"><span data-stu-id="e43c8-106">The following instructions refer to extension method `PrintAndPunctuate`, which will display the string instance that invokes it, followed by whatever value is sent in for the second parameter, `punc`.</span></span>  
  
```vb  
Imports System.Runtime.CompilerServices  
  
Module StringExtensions  
    <Extension()>   
    Public Sub PrintAndPunctuate(ByVal aString As String,   
                                 ByVal punc As String)  
        Console.WriteLine(aString & punc)  
    End Sub  
  
End Module  
```  
  
 <span data-ttu-id="e43c8-107">Metoda musí být v oboru, když je volána.</span><span class="sxs-lookup"><span data-stu-id="e43c8-107">The method must be in scope when it is called.</span></span>  
  
### <a name="to-call-an-extension-method"></a><span data-ttu-id="e43c8-108">Volání metody rozšíření</span><span class="sxs-lookup"><span data-stu-id="e43c8-108">To call an extension method</span></span>  
  
1.  <span data-ttu-id="e43c8-109">Deklarace proměnné, která má datový typ prvního parametru metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="e43c8-109">Declare a variable that has the data type of the first parameter of the extension method.</span></span> <span data-ttu-id="e43c8-110">Pro `PrintAndPunctuate`, musíte <xref:System.String> proměnné:</span><span class="sxs-lookup"><span data-stu-id="e43c8-110">For `PrintAndPunctuate`, you need a <xref:System.String> variable:</span></span>  
  
    ```  
    Dim example = "Ready"  
    ```  
  
2.  <span data-ttu-id="e43c8-111">Proměnná se volání metody rozšíření, a jeho hodnota je vázána na první parametr `aString`.</span><span class="sxs-lookup"><span data-stu-id="e43c8-111">That variable will invoke the extension method, and its value is bound to the first parameter, `aString`.</span></span> <span data-ttu-id="e43c8-112">Zobrazí příkaz následující volání `Ready?`.</span><span class="sxs-lookup"><span data-stu-id="e43c8-112">The following calling statement will display `Ready?`.</span></span>  
  
    ```  
    example.PrintAndPunctuate("?")  
    ```  
  
     <span data-ttu-id="e43c8-113">Všimněte si, že volání této metody rozšíření vypadá stejně jako všechna volání <xref:System.String> instance metody, které vyžadují jeden parametr:</span><span class="sxs-lookup"><span data-stu-id="e43c8-113">Notice that the call to this extension method looks just like a call to any one of the <xref:System.String> instance methods that require one parameter:</span></span>  
  
    ```  
    example.EndsWith("dy")  
    example.IndexOf("R")  
    ```  
  
3.  <span data-ttu-id="e43c8-114">Deklarování jiné proměnné řetězce a volání metody zjistíte, že funguje s libovolným řetězcem.</span><span class="sxs-lookup"><span data-stu-id="e43c8-114">Declare another string variable and call the method again to see that it works with any string.</span></span>  
  
    ```  
    Dim example2 = " or not"  
    example2.PrintAndPunctuate("!!!")  
    ```  
  
     <span data-ttu-id="e43c8-115">Výsledkem je, tentokrát: `or not!!!`.</span><span class="sxs-lookup"><span data-stu-id="e43c8-115">The result this time is: `or not!!!`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e43c8-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="e43c8-116">Example</span></span>  
 <span data-ttu-id="e43c8-117">Následující kód je kompletní příklad vytvoření a použití metody jednoduché rozšíření.</span><span class="sxs-lookup"><span data-stu-id="e43c8-117">The following code is a complete example of the creation and use of a simple extension method.</span></span>  
  
```vb  
Imports System.Runtime.CompilerServices  
Imports ConsoleApplication1.StringExtensions  
  
Module Module1  
  
    Sub Main()  
  
        Dim example = "Hello"  
        example.PrintAndPunctuate(".")  
        example.PrintAndPunctuate("!!!!")  
  
        Dim example2 = "Goodbye"  
        example2.PrintAndPunctuate("?")  
    End Sub  
  
    <Extension()>   
    Public Sub PrintAndPunctuate(ByVal aString As String,   
                                 ByVal punc As String)  
        Console.WriteLine(aString & punc)  
    End Sub  
End Module  
  
' Output:  
' Hello.  
' Hello!!!!  
' Goodbye?  
```  
  
## <a name="see-also"></a><span data-ttu-id="e43c8-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="e43c8-118">See Also</span></span>  
 [<span data-ttu-id="e43c8-119">Postupy: zápis metody rozšíření</span><span class="sxs-lookup"><span data-stu-id="e43c8-119">How to: Write an Extension Method</span></span>](./how-to-write-an-extension-method.md)  
 [<span data-ttu-id="e43c8-120">Metody rozšíření</span><span class="sxs-lookup"><span data-stu-id="e43c8-120">Extension Methods</span></span>](./extension-methods.md)  
 [<span data-ttu-id="e43c8-121">Rozsah v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e43c8-121">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
