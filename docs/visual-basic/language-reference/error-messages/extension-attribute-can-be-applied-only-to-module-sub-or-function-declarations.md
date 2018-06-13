---
title: '&#39;Rozšíření&#39; atribut lze použít pouze &#39;modulu&#39;, &#39;Sub&#39;, nebo &#39;funkce&#39; deklarace'
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: d7f8829cb879d612711ac6bcc6bf4aa065fbe323
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587316"
---
# <a name="39extension39-attribute-can-be-applied-only-to-39module39-39sub39-or-39function39-declarations"></a><span data-ttu-id="d57cd-102">&#39;Rozšíření&#39; atribut lze použít pouze &#39;modulu&#39;, &#39;Sub&#39;, nebo &#39;funkce&#39; deklarace</span><span class="sxs-lookup"><span data-stu-id="d57cd-102">&#39;Extension&#39; attribute can be applied only to &#39;Module&#39;, &#39;Sub&#39;, or &#39;Function&#39; declarations</span></span>
<span data-ttu-id="d57cd-103">Jediný způsob, jak rozšířit datový typ v jazyce Visual Basic je definovat metody rozšíření uvnitř standardní modulu.</span><span class="sxs-lookup"><span data-stu-id="d57cd-103">The only way to extend a data type in Visual Basic is to define an extension method inside a standard module.</span></span> <span data-ttu-id="d57cd-104">Rozšíření metoda může být `Sub` postup nebo `Function` postupu.</span><span class="sxs-lookup"><span data-stu-id="d57cd-104">The extension method can be a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="d57cd-105">Všechny metody rozšíření musí být označen atributem rozšíření, `<Extension()>`, z <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="d57cd-105">All extension methods must be marked with the extension attribute, `<Extension()>`, from the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="d57cd-106">Modul, který obsahuje metody rozšíření Volitelně mohou být označeny stejným způsobem.</span><span class="sxs-lookup"><span data-stu-id="d57cd-106">Optionally, a module that contains an extension method may be marked in the same way.</span></span> <span data-ttu-id="d57cd-107">Žádné jiné použití atributu rozšíření je platný.</span><span class="sxs-lookup"><span data-stu-id="d57cd-107">No other use of the extension attribute is valid.</span></span>  
  
 <span data-ttu-id="d57cd-108">**ID chyby:** BC36550</span><span class="sxs-lookup"><span data-stu-id="d57cd-108">**Error ID:** BC36550</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d57cd-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="d57cd-109">To correct this error</span></span>  
  
-   <span data-ttu-id="d57cd-110">Odeberte atribut rozšíření.</span><span class="sxs-lookup"><span data-stu-id="d57cd-110">Remove the extension attribute.</span></span>  
  
-   <span data-ttu-id="d57cd-111">Změnit návrh rozšíření jako metodu, definované v nadřazených modulu.</span><span class="sxs-lookup"><span data-stu-id="d57cd-111">Redesign your extension as a method, defined in an enclosing module.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d57cd-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="d57cd-112">Example</span></span>  
 <span data-ttu-id="d57cd-113">V následujícím příkladu definuje `Print` metodu `String` datového typu.</span><span class="sxs-lookup"><span data-stu-id="d57cd-113">The following example defines a `Print` method for the `String` data type.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d57cd-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="d57cd-114">See Also</span></span>  
 [<span data-ttu-id="d57cd-115">Přehled atributy</span><span class="sxs-lookup"><span data-stu-id="d57cd-115">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)  
 [<span data-ttu-id="d57cd-116">Rozšiřující metody</span><span class="sxs-lookup"><span data-stu-id="d57cd-116">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)  
 [<span data-ttu-id="d57cd-117">Příkaz Module</span><span class="sxs-lookup"><span data-stu-id="d57cd-117">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)
