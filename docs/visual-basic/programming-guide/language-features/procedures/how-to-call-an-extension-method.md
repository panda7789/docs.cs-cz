---
title: 'Postupy: Volání metody rozšíření (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
ms.openlocfilehash: 5cb0684637a716dfec947740ba345c62eaabddd7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59313798"
---
# <a name="how-to-call-an-extension-method-visual-basic"></a><span data-ttu-id="052bc-102">Postupy: Volání metody rozšíření (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="052bc-102">How to: Call an Extension Method (Visual Basic)</span></span>
<span data-ttu-id="052bc-103">Rozšiřující metody umožňují přidat metody do existující třídy.</span><span class="sxs-lookup"><span data-stu-id="052bc-103">Extension methods enable you to add methods to an existing class.</span></span> <span data-ttu-id="052bc-104">Po metodu rozšíření deklarovat a přeneseny do rozsahu, můžete ji volat jako metodu instance typu, který rozšiřuje.</span><span class="sxs-lookup"><span data-stu-id="052bc-104">After an extension method is declared and brought into scope, you can call it like an instance method of the type that it extends.</span></span> <span data-ttu-id="052bc-105">Další informace o tom, jak psát metodu rozšíření, naleznete v tématu [jak: Zápis metody rozšíření](./how-to-write-an-extension-method.md).</span><span class="sxs-lookup"><span data-stu-id="052bc-105">For more information about how to write an extension method, see [How to: Write an Extension Method](./how-to-write-an-extension-method.md).</span></span>  
  
 <span data-ttu-id="052bc-106">Následující pokyny najdete v metodě rozšíření `PrintAndPunctuate`, instanci řetězce, která volá následuje libovolné hodnoty. Tím se zobrazí se posílá ve druhém parametru `punc`.</span><span class="sxs-lookup"><span data-stu-id="052bc-106">The following instructions refer to extension method `PrintAndPunctuate`, which will display the string instance that invokes it, followed by whatever value is sent in for the second parameter, `punc`.</span></span>  
  
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
  
 <span data-ttu-id="052bc-107">Metoda musí být v rozsahu, když je volána.</span><span class="sxs-lookup"><span data-stu-id="052bc-107">The method must be in scope when it is called.</span></span>  
  
### <a name="to-call-an-extension-method"></a><span data-ttu-id="052bc-108">K volání metody rozšíření</span><span class="sxs-lookup"><span data-stu-id="052bc-108">To call an extension method</span></span>  
  
1. <span data-ttu-id="052bc-109">Deklarujte proměnné, která má datový typ prvního parametru metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="052bc-109">Declare a variable that has the data type of the first parameter of the extension method.</span></span> <span data-ttu-id="052bc-110">Pro `PrintAndPunctuate`, je nutné <xref:System.String> proměnné:</span><span class="sxs-lookup"><span data-stu-id="052bc-110">For `PrintAndPunctuate`, you need a <xref:System.String> variable:</span></span>  
  
    ```  
    Dim example = "Ready"  
    ```  
  
2. <span data-ttu-id="052bc-111">Že proměnné se vyvolat metodu rozšíření, a její hodnota je vázaná na první parametr `aString`.</span><span class="sxs-lookup"><span data-stu-id="052bc-111">That variable will invoke the extension method, and its value is bound to the first parameter, `aString`.</span></span> <span data-ttu-id="052bc-112">Následující volání příkazu se zobrazí `Ready?`.</span><span class="sxs-lookup"><span data-stu-id="052bc-112">The following calling statement will display `Ready?`.</span></span>  
  
    ```  
    example.PrintAndPunctuate("?")  
    ```  
  
     <span data-ttu-id="052bc-113">Všimněte si, že volání této metody rozšíření vypadá stejně, jako je jeden z volání <xref:System.String> instanci metody, které vyžadují jeden parametr:</span><span class="sxs-lookup"><span data-stu-id="052bc-113">Notice that the call to this extension method looks just like a call to any one of the <xref:System.String> instance methods that require one parameter:</span></span>  
  
    ```  
    example.EndsWith("dy")  
    example.IndexOf("R")  
    ```  
  
3. <span data-ttu-id="052bc-114">Deklarování proměnné jiného řetězce a volání metody znovu, abyste viděli, jestli funguje s libovolným řetězcem.</span><span class="sxs-lookup"><span data-stu-id="052bc-114">Declare another string variable and call the method again to see that it works with any string.</span></span>  
  
    ```  
    Dim example2 = " or not"  
    example2.PrintAndPunctuate("!!!")  
    ```  
  
     <span data-ttu-id="052bc-115">Výsledkem této doby je: `or not!!!`.</span><span class="sxs-lookup"><span data-stu-id="052bc-115">The result this time is: `or not!!!`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="052bc-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="052bc-116">Example</span></span>  
 <span data-ttu-id="052bc-117">Následující kód je kompletní příklad vytvoření a použití metody jednoduché rozšíření.</span><span class="sxs-lookup"><span data-stu-id="052bc-117">The following code is a complete example of the creation and use of a simple extension method.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="052bc-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="052bc-118">See also</span></span>

- [<span data-ttu-id="052bc-119">Postupy: Zápis metody rozšíření</span><span class="sxs-lookup"><span data-stu-id="052bc-119">How to: Write an Extension Method</span></span>](./how-to-write-an-extension-method.md)
- [<span data-ttu-id="052bc-120">Rozšiřující metody</span><span class="sxs-lookup"><span data-stu-id="052bc-120">Extension Methods</span></span>](./extension-methods.md)
- [<span data-ttu-id="052bc-121">Obor v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="052bc-121">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
