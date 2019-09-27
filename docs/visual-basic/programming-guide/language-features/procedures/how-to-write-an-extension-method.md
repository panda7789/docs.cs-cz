---
title: 'Postupy: Zápis metody rozšíření (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: 31ccb18e0e6d1569764ec2a67201d7f758129425
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332761"
---
# <a name="how-to-write-an-extension-method-visual-basic"></a><span data-ttu-id="5c439-102">Postupy: Zápis metody rozšíření (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5c439-102">How to: Write an Extension Method (Visual Basic)</span></span>

<span data-ttu-id="5c439-103">Metody rozšíření umožňují přidat metody do existující třídy.</span><span class="sxs-lookup"><span data-stu-id="5c439-103">Extension methods enable you to add methods to an existing class.</span></span> <span data-ttu-id="5c439-104">Metodu rozšíření lze volat, jako kdyby byla instancí této třídy.</span><span class="sxs-lookup"><span data-stu-id="5c439-104">The extension method can be called as if it were an instance of that class.</span></span>

### <a name="to-define-an-extension-method"></a><span data-ttu-id="5c439-105">Definování rozšiřující metody</span><span class="sxs-lookup"><span data-stu-id="5c439-105">To define an extension method</span></span>

1. <span data-ttu-id="5c439-106">Otevřete v aplikaci Visual Studio novou nebo existující aplikaci Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5c439-106">Open a new or existing Visual Basic application in Visual Studio.</span></span>

2. <span data-ttu-id="5c439-107">V horní části souboru, ve kterém chcete definovat metodu rozšíření, zahrňte následující příkaz import:</span><span class="sxs-lookup"><span data-stu-id="5c439-107">At the top of the file in which you want to define an extension method, include the following import statement:</span></span>

    ```vb
    Imports System.Runtime.CompilerServices
    ```

3. <span data-ttu-id="5c439-108">V rámci modulu ve vaší nové nebo existující aplikaci spusťte definici metody s atributem rozšíření:</span><span class="sxs-lookup"><span data-stu-id="5c439-108">Within a module in your new or existing application, begin the method definition with the extension attribute:</span></span>

    ```vb
    <Extension()>
    ```

4. <span data-ttu-id="5c439-109">Deklarujte svou metodu běžným způsobem, s tím rozdílem, že typ prvního parametru musí být datový typ, který chcete zvětšit.</span><span class="sxs-lookup"><span data-stu-id="5c439-109">Declare your method in the ordinary way, except that the type of the first parameter must be the data type you want to extend.</span></span>

    ```vb
    <Extension()>
    Public Sub SubName(para1 As ExtendedType, <other parameters>)
         ' < Body of the method >
    End Sub
    ```

## <a name="example"></a><span data-ttu-id="5c439-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="5c439-110">Example</span></span>

 <span data-ttu-id="5c439-111">Následující příklad deklaruje metodu rozšíření v modulu `StringExtensions`.</span><span class="sxs-lookup"><span data-stu-id="5c439-111">The following example declares an extension method in module `StringExtensions`.</span></span> <span data-ttu-id="5c439-112">Druhý modul, `Module1`, importuje `StringExtensions` a volá metodu.</span><span class="sxs-lookup"><span data-stu-id="5c439-112">A second module, `Module1`, imports `StringExtensions` and calls the method.</span></span> <span data-ttu-id="5c439-113">Metoda rozšíření musí být v oboru, pokud je volána.</span><span class="sxs-lookup"><span data-stu-id="5c439-113">The extension method must be in scope when it is called.</span></span> <span data-ttu-id="5c439-114">Metoda rozšíření `PrintAndPunctuate` rozšiřuje třídu <xref:System.String> s metodou, která zobrazuje instanci řetězce následovaný řetězcem interpunkčních znamének odeslaných v podobě parametru.</span><span class="sxs-lookup"><span data-stu-id="5c439-114">Extension method `PrintAndPunctuate` extends the <xref:System.String> class with a method that displays the string instance followed by a string of punctuation symbols sent in as a parameter.</span></span>
  
```vb
' Declarations will typically be in a separate module.
Imports System.Runtime.CompilerServices

Module StringExtensions
    <Extension()>
    Public Sub PrintAndPunctuate(aString As String, punc As String)
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
  
 <span data-ttu-id="5c439-115">Všimněte si, že metoda je definována se dvěma parametry a volána pouze s jedním.</span><span class="sxs-lookup"><span data-stu-id="5c439-115">Notice that the method is defined with two parameters and called with only one.</span></span> <span data-ttu-id="5c439-116">První parametr `aString` v definici metody je vázán na `example`, instance `String`, která volá metodu.</span><span class="sxs-lookup"><span data-stu-id="5c439-116">The first parameter, `aString`, in the method definition is bound to `example`, the instance of `String` that calls the method.</span></span> <span data-ttu-id="5c439-117">Výstup příkladu je následující:</span><span class="sxs-lookup"><span data-stu-id="5c439-117">The output of the example is as follows:</span></span>
  
 ```console
 Hello?
 Hello!!!!
 ```
  
## <a name="see-also"></a><span data-ttu-id="5c439-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5c439-118">See also</span></span>

- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [<span data-ttu-id="5c439-119">Rozšiřující metody</span><span class="sxs-lookup"><span data-stu-id="5c439-119">Extension Methods</span></span>](extension-methods.md)
- [<span data-ttu-id="5c439-120">Příkaz Module</span><span class="sxs-lookup"><span data-stu-id="5c439-120">Module Statement</span></span>](../../../language-reference/statements/module-statement.md)
- [<span data-ttu-id="5c439-121">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="5c439-121">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="5c439-122">Obor v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5c439-122">Scope in Visual Basic</span></span>](../declared-elements/scope.md)
