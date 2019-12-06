---
title: Direktivy
ms.date: 07/20/2015
helpviewer_keywords:
- directives, Visual Basic compiler
- Visual Basic code, directives
- directives
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
ms.openlocfilehash: b5e857198351b30c0d7a38dce1a9e6d1209b5258
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74838140"
---
# <a name="directives-visual-basic"></a><span data-ttu-id="0ddcd-102">Direktivy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ddcd-102">Directives (Visual Basic)</span></span>

<span data-ttu-id="0ddcd-103">Témata v tomto oddílu dokumentují direktivy kompilátoru Visual Basic zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="0ddcd-103">The topics in this section document the Visual Basic source code compiler directives.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0ddcd-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="0ddcd-104">In This Section</span></span>  

 <span data-ttu-id="0ddcd-105">[#Const direktiva](../../../visual-basic/language-reference/directives/const-directive.md) – definice konstanty kompilátoru</span><span class="sxs-lookup"><span data-stu-id="0ddcd-105">[#Const Directive](../../../visual-basic/language-reference/directives/const-directive.md) -- Define a compiler constant</span></span>  
  
 <span data-ttu-id="0ddcd-106">[#ExternalSource direktiva](../../../visual-basic/language-reference/directives/externalsource-directive.md) – označuje mapování mezi zdrojovými řádky a textem externím ke zdroji.</span><span class="sxs-lookup"><span data-stu-id="0ddcd-106">[#ExternalSource Directive](../../../visual-basic/language-reference/directives/externalsource-directive.md) -- Indicate a mapping between source lines and text external to the source</span></span>  
  
 <span data-ttu-id="0ddcd-107">[#If... Then... #Else – direktivy](../../../visual-basic/language-reference/directives/if-then-else-directives.md) – zkompiluje vybrané bloky kódu</span><span class="sxs-lookup"><span data-stu-id="0ddcd-107">[#If...Then...#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md) -- Compile selected blocks of code</span></span>  
  
 <span data-ttu-id="0ddcd-108">[#Region direktiva](../../../visual-basic/language-reference/directives/region-directive.md) – sbalení a skrytí oddílů kódu v editoru sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0ddcd-108">[#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md) -- Collapse and hide sections of code in the Visual Studio editor</span></span>  
  
 <span data-ttu-id="0ddcd-109">**#Disable, #Enable** --zakázat a povolit specifická upozornění pro oblasti kódu.</span><span class="sxs-lookup"><span data-stu-id="0ddcd-109">**#Disable, #Enable** -- Disable and enable specific warnings for regions of code.</span></span>  
  
```vb  
#Disable Warning BC42356 ' suppress warning about no awaits in this method  
    Async Function TestAsync() As Task  
        Console.WriteLine("testing")  
    End Function  
#Enable Warning BC42356  
```  
  
 <span data-ttu-id="0ddcd-110">Můžete zakázat a povolit čárkami oddělený seznam kódů upozornění.</span><span class="sxs-lookup"><span data-stu-id="0ddcd-110">You can disable and enable a comma-separated list of warning codes too.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0ddcd-111">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="0ddcd-111">Related Sections</span></span>  

 [<span data-ttu-id="0ddcd-112">Referenční příručka jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0ddcd-112">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)  
  