---
title: 'Postupy: Volání metody rozšíření'
ms.date: 07/20/2015
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
ms.openlocfilehash: a19705a8f90833d48869df26a18d19b0ad1488e0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340395"
---
# <a name="how-to-call-an-extension-method-visual-basic"></a><span data-ttu-id="4d7b5-102">Postupy: Volání metody rozšíření (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d7b5-102">How to: Call an Extension Method (Visual Basic)</span></span>

<span data-ttu-id="4d7b5-103">Metody rozšíření umožňují přidat metody do existující třídy.</span><span class="sxs-lookup"><span data-stu-id="4d7b5-103">Extension methods enable you to add methods to an existing class.</span></span> <span data-ttu-id="4d7b5-104">Poté, co je metoda rozšíření deklarována a uvedena do rozsahu, lze ji volat jako metodu instance typu, který rozšiřuje.</span><span class="sxs-lookup"><span data-stu-id="4d7b5-104">After an extension method is declared and brought into scope, you can call it like an instance method of the type that it extends.</span></span> <span data-ttu-id="4d7b5-105">Další informace o tom, jak napsat rozšiřující metodu, naleznete v tématu [How to: Write a Extension](./how-to-write-an-extension-method.md).</span><span class="sxs-lookup"><span data-stu-id="4d7b5-105">For more information about how to write an extension method, see [How to: Write an Extension Method](./how-to-write-an-extension-method.md).</span></span>

 <span data-ttu-id="4d7b5-106">Následující pokyny odkazují na metodu rozšíření `PrintAndPunctuate`, která zobrazí instanci řetězce, která ji vyvolá, a za druhým parametrem je odeslána jakákoli hodnota, `punc`.</span><span class="sxs-lookup"><span data-stu-id="4d7b5-106">The following instructions refer to extension method `PrintAndPunctuate`, which will display the string instance that invokes it, followed by whatever value is sent in for the second parameter, `punc`.</span></span>

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

<span data-ttu-id="4d7b5-107">Metoda musí být v oboru, pokud je volána.</span><span class="sxs-lookup"><span data-stu-id="4d7b5-107">The method must be in scope when it is called.</span></span>

### <a name="to-call-an-extension-method"></a><span data-ttu-id="4d7b5-108">Volání metody rozšíření</span><span class="sxs-lookup"><span data-stu-id="4d7b5-108">To call an extension method</span></span>

1. <span data-ttu-id="4d7b5-109">Deklarujte proměnnou, která má datový typ prvního parametru metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="4d7b5-109">Declare a variable that has the data type of the first parameter of the extension method.</span></span> <span data-ttu-id="4d7b5-110">Pro `PrintAndPunctuate`potřebujete <xref:System.String> proměnnou:</span><span class="sxs-lookup"><span data-stu-id="4d7b5-110">For `PrintAndPunctuate`, you need a <xref:System.String> variable:</span></span>

    ```vb
    Dim example = "Ready"
    ```

2. <span data-ttu-id="4d7b5-111">Tato proměnná vyvolá metodu rozšíření a její hodnota je svázána s prvním parametrem `aString`.</span><span class="sxs-lookup"><span data-stu-id="4d7b5-111">That variable will invoke the extension method, and its value is bound to the first parameter, `aString`.</span></span> <span data-ttu-id="4d7b5-112">Následující volání příkazu zobrazí `Ready?`.</span><span class="sxs-lookup"><span data-stu-id="4d7b5-112">The following calling statement will display `Ready?`.</span></span>

    ```vb
    example.PrintAndPunctuate("?")
    ```

     <span data-ttu-id="4d7b5-113">Všimněte si, že volání této metody rozšíření vypadá stejně jako volání libovolné metody instance <xref:System.String>, která vyžaduje jeden parametr:</span><span class="sxs-lookup"><span data-stu-id="4d7b5-113">Notice that the call to this extension method looks just like a call to any one of the <xref:System.String> instance methods that require one parameter:</span></span>

    ```vb
    example.EndsWith("dy")
    example.IndexOf("R")
    ```

3. <span data-ttu-id="4d7b5-114">Deklarujte další řetězcovou proměnnou a zavolejte metodu znovu, abyste viděli, že funguje s libovolným řetězcem.</span><span class="sxs-lookup"><span data-stu-id="4d7b5-114">Declare another string variable and call the method again to see that it works with any string.</span></span>

    ```vb
    Dim example2 = " or not"
    example2.PrintAndPunctuate("!!!")
    ```

     <span data-ttu-id="4d7b5-115">Výsledek tohoto času: `or not!!!`.</span><span class="sxs-lookup"><span data-stu-id="4d7b5-115">The result this time is: `or not!!!`.</span></span>

## <a name="example"></a><span data-ttu-id="4d7b5-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="4d7b5-116">Example</span></span>
 <span data-ttu-id="4d7b5-117">Následující kód je kompletní příklad vytváření a použití jednoduché metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="4d7b5-117">The following code is a complete example of the creation and use of a simple extension method.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4d7b5-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4d7b5-118">See also</span></span>

- [<span data-ttu-id="4d7b5-119">Postupy: Zápis rozšiřující metody</span><span class="sxs-lookup"><span data-stu-id="4d7b5-119">How to: Write an Extension Method</span></span>](./how-to-write-an-extension-method.md)
- [<span data-ttu-id="4d7b5-120">Rozšiřující metody</span><span class="sxs-lookup"><span data-stu-id="4d7b5-120">Extension Methods</span></span>](./extension-methods.md)
- [<span data-ttu-id="4d7b5-121">Obor v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4d7b5-121">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
