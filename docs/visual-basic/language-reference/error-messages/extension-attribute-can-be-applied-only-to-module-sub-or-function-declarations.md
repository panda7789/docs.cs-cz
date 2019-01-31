---
title: Atribut 'Extension' lze použít pouze v deklaracích 'Module', 'Sub' nebo 'Function'.
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: e2e2c41d713b0b04b8bc7208a83d059f0d16bf06
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55278717"
---
# <a name="extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations"></a><span data-ttu-id="5999e-102">Atribut 'Extension' lze použít pouze v deklaracích 'Module', 'Sub' nebo 'Function'.</span><span class="sxs-lookup"><span data-stu-id="5999e-102">'Extension' attribute can be applied only to 'Module', 'Sub', or 'Function' declarations</span></span>
<span data-ttu-id="5999e-103">Jediný způsob, jak rozšířit datový typ v jazyce Visual Basic je definovat rozšiřující metodu v modulu standard.</span><span class="sxs-lookup"><span data-stu-id="5999e-103">The only way to extend a data type in Visual Basic is to define an extension method inside a standard module.</span></span> <span data-ttu-id="5999e-104">Metoda rozšíření může být `Sub` procedury nebo `Function` postup.</span><span class="sxs-lookup"><span data-stu-id="5999e-104">The extension method can be a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="5999e-105">Všechny metody rozšíření musí být označeny pomocí atributu rozšíření `<Extension()>`, z <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5999e-105">All extension methods must be marked with the extension attribute, `<Extension()>`, from the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="5999e-106">Volitelně může být označena modul, který obsahuje metodu rozšíření stejným způsobem.</span><span class="sxs-lookup"><span data-stu-id="5999e-106">Optionally, a module that contains an extension method may be marked in the same way.</span></span> <span data-ttu-id="5999e-107">Žádné další použití atributu rozšíření není platný.</span><span class="sxs-lookup"><span data-stu-id="5999e-107">No other use of the extension attribute is valid.</span></span>  
  
 <span data-ttu-id="5999e-108">**ID chyby:** BC36550</span><span class="sxs-lookup"><span data-stu-id="5999e-108">**Error ID:** BC36550</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5999e-109">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="5999e-109">To correct this error</span></span>  
  
-   <span data-ttu-id="5999e-110">Odebrání atributu rozšíření.</span><span class="sxs-lookup"><span data-stu-id="5999e-110">Remove the extension attribute.</span></span>  
  
-   <span data-ttu-id="5999e-111">Změnit návrh rozšíření jako metoda, definována v nadřazeném modulu.</span><span class="sxs-lookup"><span data-stu-id="5999e-111">Redesign your extension as a method, defined in an enclosing module.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5999e-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="5999e-112">Example</span></span>  
 <span data-ttu-id="5999e-113">Následující příklad definuje `Print` metodu `String` datového typu.</span><span class="sxs-lookup"><span data-stu-id="5999e-113">The following example defines a `Print` method for the `String` data type.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5999e-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5999e-114">See also</span></span>
- [<span data-ttu-id="5999e-115">Přehled atributy</span><span class="sxs-lookup"><span data-stu-id="5999e-115">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="5999e-116">Rozšiřující metody</span><span class="sxs-lookup"><span data-stu-id="5999e-116">Extension Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
- [<span data-ttu-id="5999e-117">Příkaz Module</span><span class="sxs-lookup"><span data-stu-id="5999e-117">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)
