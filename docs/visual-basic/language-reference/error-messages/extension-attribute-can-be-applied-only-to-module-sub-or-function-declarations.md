---
title: '&#39;Rozšíření&#39; atribut se dá použít jenom s &#39;modulu&#39;, &#39;Sub&#39;, nebo &#39;funkce&#39; deklarace'
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: fabd602f31a362fe33954253d565e86a065e0a83
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718231"
---
# <a name="39extension39-attribute-can-be-applied-only-to-39module39-39sub39-or-39function39-declarations"></a><span data-ttu-id="97b0e-102">&#39;Rozšíření&#39; atribut se dá použít jenom s &#39;modulu&#39;, &#39;Sub&#39;, nebo &#39;funkce&#39; deklarace</span><span class="sxs-lookup"><span data-stu-id="97b0e-102">&#39;Extension&#39; attribute can be applied only to &#39;Module&#39;, &#39;Sub&#39;, or &#39;Function&#39; declarations</span></span>
<span data-ttu-id="97b0e-103">Jediný způsob, jak rozšířit datový typ v jazyce Visual Basic je definovat rozšiřující metodu v modulu standard.</span><span class="sxs-lookup"><span data-stu-id="97b0e-103">The only way to extend a data type in Visual Basic is to define an extension method inside a standard module.</span></span> <span data-ttu-id="97b0e-104">Metoda rozšíření může být `Sub` procedury nebo `Function` postup.</span><span class="sxs-lookup"><span data-stu-id="97b0e-104">The extension method can be a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="97b0e-105">Všechny metody rozšíření musí být označeny pomocí atributu rozšíření `<Extension()>`, z <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="97b0e-105">All extension methods must be marked with the extension attribute, `<Extension()>`, from the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="97b0e-106">Volitelně může být označena modul, který obsahuje metodu rozšíření stejným způsobem.</span><span class="sxs-lookup"><span data-stu-id="97b0e-106">Optionally, a module that contains an extension method may be marked in the same way.</span></span> <span data-ttu-id="97b0e-107">Žádné další použití atributu rozšíření není platný.</span><span class="sxs-lookup"><span data-stu-id="97b0e-107">No other use of the extension attribute is valid.</span></span>  
  
 <span data-ttu-id="97b0e-108">**ID chyby:** BC36550</span><span class="sxs-lookup"><span data-stu-id="97b0e-108">**Error ID:** BC36550</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="97b0e-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="97b0e-109">To correct this error</span></span>  
  
-   <span data-ttu-id="97b0e-110">Odebrání atributu rozšíření.</span><span class="sxs-lookup"><span data-stu-id="97b0e-110">Remove the extension attribute.</span></span>  
  
-   <span data-ttu-id="97b0e-111">Změnit návrh rozšíření jako metoda, definována v nadřazeném modulu.</span><span class="sxs-lookup"><span data-stu-id="97b0e-111">Redesign your extension as a method, defined in an enclosing module.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97b0e-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="97b0e-112">Example</span></span>  
 <span data-ttu-id="97b0e-113">Následující příklad definuje `Print` metodu `String` datového typu.</span><span class="sxs-lookup"><span data-stu-id="97b0e-113">The following example defines a `Print` method for the `String` data type.</span></span>  
  
```  
Imports StringUtility  
Imports System.Runtime.CompilerServices  
Namespace StringUtility  
    <Extension()>   
    Module StringExtensions  
        <Extension()>   
        Public Sub Print (ByVal str As String)  
            Console.WriteLine(str)  
        End Sub  
    End Module  
End Namespace  
```  
  
## <a name="see-also"></a><span data-ttu-id="97b0e-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="97b0e-114">See also</span></span>
- [<span data-ttu-id="97b0e-115">Přehled atributy</span><span class="sxs-lookup"><span data-stu-id="97b0e-115">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="97b0e-116">Rozšiřující metody</span><span class="sxs-lookup"><span data-stu-id="97b0e-116">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
- [<span data-ttu-id="97b0e-117">Příkaz Module</span><span class="sxs-lookup"><span data-stu-id="97b0e-117">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)
