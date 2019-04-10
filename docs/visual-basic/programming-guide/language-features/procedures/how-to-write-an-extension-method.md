---
title: 'Postupy: Zápis metody rozšíření (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: 00d62d275f7afc06e066a375dc1ffcd74b23c9ed
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59313759"
---
# <a name="how-to-write-an-extension-method-visual-basic"></a><span data-ttu-id="8e79b-102">Postupy: Zápis metody rozšíření (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8e79b-102">How to: Write an Extension Method (Visual Basic)</span></span>
<span data-ttu-id="8e79b-103">Rozšiřující metody umožňují přidat metody do existující třídy.</span><span class="sxs-lookup"><span data-stu-id="8e79b-103">Extension methods enable you to add methods to an existing class.</span></span> <span data-ttu-id="8e79b-104">Metody rozšíření lze volat, jako by šlo instanci dané třídy.</span><span class="sxs-lookup"><span data-stu-id="8e79b-104">The extension method can be called as if it were an instance of that class.</span></span>  
  
### <a name="to-define-an-extension-method"></a><span data-ttu-id="8e79b-105">Chcete-li definovat metodu rozšíření</span><span class="sxs-lookup"><span data-stu-id="8e79b-105">To define an extension method</span></span>  
  
1. <span data-ttu-id="8e79b-106">Otevření nové nebo existující aplikace v jazyce Visual Basic v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8e79b-106">Open a new or existing Visual Basic application in Visual Studio.</span></span>  
  
2. <span data-ttu-id="8e79b-107">V horní části souboru, ve kterém chcete definovat rozšiřující metodu patří následující příkaz importu:</span><span class="sxs-lookup"><span data-stu-id="8e79b-107">At the top of the file in which you want to define an extension method, include the following import statement:</span></span>  
  
    ```  
    Imports System.Runtime.CompilerServices  
    ```  
  
3. <span data-ttu-id="8e79b-108">V rámci modulu v nové nebo existující aplikace začněte definici metody s atributem rozšíření:</span><span class="sxs-lookup"><span data-stu-id="8e79b-108">Within a module in your new or existing application, begin the method definition with the extension attribute:</span></span>  
  
    ```  
    <Extension()>  
    ```  
  
4. <span data-ttu-id="8e79b-109">Deklarujte metodu běžným způsobem s tím rozdílem, že první parametr typu musí být datový typ, který chcete rozšířit.</span><span class="sxs-lookup"><span data-stu-id="8e79b-109">Declare your method in the ordinary way, except that the type of the first parameter must be the data type you want to extend.</span></span>  
  
    ```  
    <Extension()>   
    Public Sub subName (ByVal para1 As ExtendedType, <other parameters>)  
         ' < Body of the method >  
    End Sub  
    ```  
  
## <a name="example"></a><span data-ttu-id="8e79b-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="8e79b-110">Example</span></span>  
 <span data-ttu-id="8e79b-111">Následující příklad deklaruje rozšiřující metodu v modulu `StringExtensions`.</span><span class="sxs-lookup"><span data-stu-id="8e79b-111">The following example declares an extension method in module `StringExtensions`.</span></span> <span data-ttu-id="8e79b-112">Druhý modul `Module1`, importuje `StringExtensions` a volá metodu.</span><span class="sxs-lookup"><span data-stu-id="8e79b-112">A second module, `Module1`, imports `StringExtensions` and calls the method.</span></span> <span data-ttu-id="8e79b-113">Metoda rozšíření musí být v rozsahu, když je volána.</span><span class="sxs-lookup"><span data-stu-id="8e79b-113">The extension method must be in scope when it is called.</span></span> <span data-ttu-id="8e79b-114">Metoda rozšíření `PrintAndPunctuate` rozšiřuje <xref:System.String> třídu s metodou, která zobrazuje instanci řetězce, za nímž následuje řetězec interpunkčních znamének poslaná jako parametr.</span><span class="sxs-lookup"><span data-stu-id="8e79b-114">Extension method `PrintAndPunctuate` extends the <xref:System.String> class with a method that displays the string instance followed by a string of punctuation symbols sent in as a parameter.</span></span>  
  
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
  
 <span data-ttu-id="8e79b-115">Všimněte si, že metoda je definováno se dvěma parametry a volat pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="8e79b-115">Notice that the method is defined with two parameters and called with only one.</span></span> <span data-ttu-id="8e79b-116">První parametr `aString`, v metodě definice je vázán na `example`, instanci `String` , která volá metodu.</span><span class="sxs-lookup"><span data-stu-id="8e79b-116">The first parameter, `aString`, in the method definition is bound to `example`, the instance of `String` that calls the method.</span></span> <span data-ttu-id="8e79b-117">Výstup v příkladu vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="8e79b-117">The output of the example is as follows:</span></span>  
  
 `Hello?`  
  
 `Hello!!!!`  
  
## <a name="see-also"></a><span data-ttu-id="8e79b-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8e79b-118">See also</span></span>

- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [<span data-ttu-id="8e79b-119">Metody rozšíření</span><span class="sxs-lookup"><span data-stu-id="8e79b-119">Extension Methods</span></span>](./extension-methods.md)
- [<span data-ttu-id="8e79b-120">Module – příkaz</span><span class="sxs-lookup"><span data-stu-id="8e79b-120">Module Statement</span></span>](../../../../visual-basic/language-reference/statements/module-statement.md)
- [<span data-ttu-id="8e79b-121">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="8e79b-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="8e79b-122">Rozsah v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8e79b-122">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
