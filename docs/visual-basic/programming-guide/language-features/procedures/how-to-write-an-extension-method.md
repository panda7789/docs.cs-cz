---
title: "Postupy: Zápis metody rozšíření (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 65cdabf59886e7457a327ee9cde968a6a73f2280
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-an-extension-method-visual-basic"></a><span data-ttu-id="6754e-102">Postupy: Zápis metody rozšíření (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6754e-102">How to: Write an Extension Method (Visual Basic)</span></span>
<span data-ttu-id="6754e-103">Rozšiřující metody umožňují přidání metody do existující třídy.</span><span class="sxs-lookup"><span data-stu-id="6754e-103">Extension methods enable you to add methods to an existing class.</span></span> <span data-ttu-id="6754e-104">Rozšíření metodu lze volat, jako by šlo instance této třídy.</span><span class="sxs-lookup"><span data-stu-id="6754e-104">The extension method can be called as if it were an instance of that class.</span></span>  
  
### <a name="to-define-an-extension-method"></a><span data-ttu-id="6754e-105">Chcete-li definovat metody rozšíření</span><span class="sxs-lookup"><span data-stu-id="6754e-105">To define an extension method</span></span>  
  
1.  <span data-ttu-id="6754e-106">Otevřete nové nebo existující aplikace Visual Basic v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6754e-106">Open a new or existing Visual Basic application in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="6754e-107">V horní části souboru, ve kterém chcete definovat metody rozšíření patří následující příkaz importu:</span><span class="sxs-lookup"><span data-stu-id="6754e-107">At the top of the file in which you want to define an extension method, include the following import statement:</span></span>  
  
    ```  
    Imports System.Runtime.CompilerServices  
    ```  
  
3.  <span data-ttu-id="6754e-108">V modulu v nové nebo existující aplikace začněte definici metody s atributem rozšíření:</span><span class="sxs-lookup"><span data-stu-id="6754e-108">Within a module in your new or existing application, begin the method definition with the extension attribute:</span></span>  
  
    ```  
    <Extension()>  
    ```  
  
4.  <span data-ttu-id="6754e-109">Deklarujte metodu běžným způsobem s tím rozdílem, že typ prvního parametru musí být datový typ, který chcete rozšířit.</span><span class="sxs-lookup"><span data-stu-id="6754e-109">Declare your method in the ordinary way, except that the type of the first parameter must be the data type you want to extend.</span></span>  
  
    ```  
    <Extension()>   
    Public Sub subName (ByVal para1 As ExtendedType, <other parameters>)  
         ' < Body of the method >  
    End Sub  
    ```  
  
## <a name="example"></a><span data-ttu-id="6754e-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="6754e-110">Example</span></span>  
 <span data-ttu-id="6754e-111">Následující příklad uvádí metody rozšíření v modulu `StringExtensions`.</span><span class="sxs-lookup"><span data-stu-id="6754e-111">The following example declares an extension method in module `StringExtensions`.</span></span> <span data-ttu-id="6754e-112">Druhý modul `Module1`, naimportuje `StringExtensions` a volá metodu.</span><span class="sxs-lookup"><span data-stu-id="6754e-112">A second module, `Module1`, imports `StringExtensions` and calls the method.</span></span> <span data-ttu-id="6754e-113">Metody rozšíření musí být v oboru, když je volána.</span><span class="sxs-lookup"><span data-stu-id="6754e-113">The extension method must be in scope when it is called.</span></span> <span data-ttu-id="6754e-114">Metody rozšíření `PrintAndPunctuate` rozšiřuje <xref:System.String> se metoda, která zobrazí instanci řetězec, za nímž následuje řetězec interpunkčních znamének odesláno jako parametr.</span><span class="sxs-lookup"><span data-stu-id="6754e-114">Extension method `PrintAndPunctuate` extends the <xref:System.String> class with a method that displays the string instance followed by a string of punctuation symbols sent in as a parameter.</span></span>  
  
```vb  
' Declarations will typically be in a separate module.  
Imports System.Runtime.CompilerServices  
  
Module StringExtensions  
    <Extension()>   
    Public Sub PrintAndPunctuate(ByVal aString As String,   
                                 ByVal punc As String)  
        Console.WriteLine(aString & punc)  
    End Sub  
  
End Module  
```  
  
```vb  
' Import the module that holds the extension method you want to use,   
' and call it.  
  
Imports ConsoleApplication2.StringExtensions  
  
Module Module1  
  
    Sub Main()  
        Dim example = "Hello"  
        example.PrintAndPunctuate("?")  
        example.PrintAndPunctuate("!!!!")  
    End Sub  
  
End Module  
```  
  
 <span data-ttu-id="6754e-115">Všimněte si, že metoda je definován s dva parametry a s názvem jen s jednou.</span><span class="sxs-lookup"><span data-stu-id="6754e-115">Notice that the method is defined with two parameters and called with only one.</span></span> <span data-ttu-id="6754e-116">První parametr `aString`, v metodě je vázána definice `example`, instanci `String` , který volá metodu.</span><span class="sxs-lookup"><span data-stu-id="6754e-116">The first parameter, `aString`, in the method definition is bound to `example`, the instance of `String` that calls the method.</span></span> <span data-ttu-id="6754e-117">Výstup tohoto příkladu je následující:</span><span class="sxs-lookup"><span data-stu-id="6754e-117">The output of the example is as follows:</span></span>  
  
 `Hello?`  
  
 `Hello!!!!`  
  
## <a name="see-also"></a><span data-ttu-id="6754e-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="6754e-118">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.ExtensionAttribute>  
 [<span data-ttu-id="6754e-119">Metody rozšíření</span><span class="sxs-lookup"><span data-stu-id="6754e-119">Extension Methods</span></span>](./extension-methods.md)  
 [<span data-ttu-id="6754e-120">Module – příkaz</span><span class="sxs-lookup"><span data-stu-id="6754e-120">Module Statement</span></span>](../../../../visual-basic/language-reference/statements/module-statement.md)  
 [<span data-ttu-id="6754e-121">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="6754e-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="6754e-122">Rozsah v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6754e-122">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
