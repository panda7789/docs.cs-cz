---
title: 'Postupy: Zápis metody rozšíření'
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: 697508f86ff4ff0a89150b65782121395d0fed12
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346016"
---
# <a name="how-to-write-an-extension-method-visual-basic"></a><span data-ttu-id="fae20-102">Postupy: Zápis metody rozšíření (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fae20-102">How to: Write an Extension Method (Visual Basic)</span></span>

<span data-ttu-id="fae20-103">Metody rozšíření umožňují přidat metody do existující třídy.</span><span class="sxs-lookup"><span data-stu-id="fae20-103">Extension methods enable you to add methods to an existing class.</span></span> <span data-ttu-id="fae20-104">Metodu rozšíření lze volat, jako kdyby byla instancí této třídy.</span><span class="sxs-lookup"><span data-stu-id="fae20-104">The extension method can be called as if it were an instance of that class.</span></span>

### <a name="to-define-an-extension-method"></a><span data-ttu-id="fae20-105">Definování rozšiřující metody</span><span class="sxs-lookup"><span data-stu-id="fae20-105">To define an extension method</span></span>

1. <span data-ttu-id="fae20-106">Otevřete v aplikaci Visual Studio novou nebo existující aplikaci Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fae20-106">Open a new or existing Visual Basic application in Visual Studio.</span></span>

2. <span data-ttu-id="fae20-107">V horní části souboru, ve kterém chcete definovat metodu rozšíření, zahrňte následující příkaz import:</span><span class="sxs-lookup"><span data-stu-id="fae20-107">At the top of the file in which you want to define an extension method, include the following import statement:</span></span>

    ```vb
    Imports System.Runtime.CompilerServices
    ```

3. <span data-ttu-id="fae20-108">V rámci modulu ve vaší nové nebo existující aplikaci spusťte definici metody s atributem [`<Extension>`](xref:System.Runtime.CompilerServices.ExtensionAttribute) :</span><span class="sxs-lookup"><span data-stu-id="fae20-108">Within a module in your new or existing application, begin the method definition with the [`<Extension>`](xref:System.Runtime.CompilerServices.ExtensionAttribute) attribute:</span></span>

    ```vb
    <Extension()>
    ```

    <span data-ttu-id="fae20-109">Všimněte si, že atribut `Extension` lze použít pouze pro metodu (`Sub` nebo `Function` procedury) v [modulu](../../../language-reference/statements/module-statement.md)Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fae20-109">Note that the `Extension` attribute can only be applied to a method (a `Sub` or `Function` procedure) in a Visual Basic [Module](../../../language-reference/statements/module-statement.md).</span></span> <span data-ttu-id="fae20-110">Pokud ji použijete pro metodu v `Class` nebo `Structure`, kompilátor Visual Basic generuje Error [BC36551](../../../misc/bc36551.md), "metody rozšíření mohou být definovány pouze v modulech".</span><span class="sxs-lookup"><span data-stu-id="fae20-110">If you apply it to a method in a `Class` or a `Structure`, the Visual Basic compiler generates error [BC36551](../../../misc/bc36551.md), "Extension methods can be defined only in modules."</span></span>

4. <span data-ttu-id="fae20-111">Deklarujte svou metodu běžným způsobem, s tím rozdílem, že typ prvního parametru musí být datový typ, který chcete zvětšit.</span><span class="sxs-lookup"><span data-stu-id="fae20-111">Declare your method in the ordinary way, except that the type of the first parameter must be the data type you want to extend.</span></span>

    ```vb
    <Extension()>
    Public Sub SubName(para1 As ExtendedType, <other parameters>)
         ' < Body of the method >
    End Sub
    ```

## <a name="example"></a><span data-ttu-id="fae20-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="fae20-112">Example</span></span>

<span data-ttu-id="fae20-113">Následující příklad deklaruje metodu rozšíření v modulu `StringExtensions`.</span><span class="sxs-lookup"><span data-stu-id="fae20-113">The following example declares an extension method in module `StringExtensions`.</span></span> <span data-ttu-id="fae20-114">Druhý modul, `Module1`, importuje `StringExtensions` a volá metodu.</span><span class="sxs-lookup"><span data-stu-id="fae20-114">A second module, `Module1`, imports `StringExtensions` and calls the method.</span></span> <span data-ttu-id="fae20-115">Metoda rozšíření musí být v oboru, pokud je volána.</span><span class="sxs-lookup"><span data-stu-id="fae20-115">The extension method must be in scope when it is called.</span></span> <span data-ttu-id="fae20-116">Metoda rozšíření `PrintAndPunctuate` rozšiřuje třídu <xref:System.String> s metodou, která zobrazuje instanci řetězce následovaným řetězcem interpunkčních znamének odeslaných v podobě parametru.</span><span class="sxs-lookup"><span data-stu-id="fae20-116">Extension method `PrintAndPunctuate` extends the <xref:System.String> class with a method that displays the string instance followed by a string of punctuation symbols sent in as a parameter.</span></span>

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

<span data-ttu-id="fae20-117">Všimněte si, že metoda je definována se dvěma parametry a volána pouze s jedním.</span><span class="sxs-lookup"><span data-stu-id="fae20-117">Notice that the method is defined with two parameters and called with only one.</span></span> <span data-ttu-id="fae20-118">První parametr `aString`v definici metody je vázán na `example`, instance `String`, která volá metodu.</span><span class="sxs-lookup"><span data-stu-id="fae20-118">The first parameter, `aString`, in the method definition is bound to `example`, the instance of `String` that calls the method.</span></span> <span data-ttu-id="fae20-119">Výstup příkladu je následující:</span><span class="sxs-lookup"><span data-stu-id="fae20-119">The output of the example is as follows:</span></span>

```console
Hello?
Hello!!!!
```

## <a name="see-also"></a><span data-ttu-id="fae20-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fae20-120">See also</span></span>

- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [<span data-ttu-id="fae20-121">Rozšiřující metody</span><span class="sxs-lookup"><span data-stu-id="fae20-121">Extension Methods</span></span>](extension-methods.md)
- [<span data-ttu-id="fae20-122">Příkaz Module</span><span class="sxs-lookup"><span data-stu-id="fae20-122">Module Statement</span></span>](../../../language-reference/statements/module-statement.md)
- [<span data-ttu-id="fae20-123">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="fae20-123">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="fae20-124">Obor v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fae20-124">Scope in Visual Basic</span></span>](../declared-elements/scope.md)
