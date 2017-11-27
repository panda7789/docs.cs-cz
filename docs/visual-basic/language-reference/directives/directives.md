---
title: Direktivy (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- directives, Visual Basic compiler
- Visual Basic code, directives
- directives
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8219f17f1b8093b4d02b370c7b008101923b1873
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="directives-visual-basic"></a><span data-ttu-id="acd0b-102">Direktivy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="acd0b-102">Directives (Visual Basic)</span></span>
<span data-ttu-id="acd0b-103">Témata v této části dokumentů direktivy kompilátoru jazyka Visual Basic zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="acd0b-103">The topics in this section document the Visual Basic source code compiler directives.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="acd0b-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="acd0b-104">In This Section</span></span>  
 <span data-ttu-id="acd0b-105">[#Const – direktiva](../../../visual-basic/language-reference/directives/const-directive.md) – definovat konstantu kompilátoru</span><span class="sxs-lookup"><span data-stu-id="acd0b-105">[#Const Directive](../../../visual-basic/language-reference/directives/const-directive.md) -- Define a compiler constant</span></span>  
  
 <span data-ttu-id="acd0b-106">[#ExternalSource – direktiva](../../../visual-basic/language-reference/directives/externalsource-directive.md) – označuje mapování mezi řádky zdroje a externí zdroj textu</span><span class="sxs-lookup"><span data-stu-id="acd0b-106">[#ExternalSource Directive](../../../visual-basic/language-reference/directives/externalsource-directive.md) -- Indicate a mapping between source lines and text external to the source</span></span>  
  
 <span data-ttu-id="acd0b-107">[#If... Then... #Else direktivy](../../../visual-basic/language-reference/directives/if-then-else-directives.md) – kompilace vybrané bloky kódu</span><span class="sxs-lookup"><span data-stu-id="acd0b-107">[#If...Then...#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md) -- Compile selected blocks of code</span></span>  
  
 <span data-ttu-id="acd0b-108">[#Region – direktiva](../../../visual-basic/language-reference/directives/region-directive.md) – sbalení a skrytí sekcí kódu v editoru Visual Studio</span><span class="sxs-lookup"><span data-stu-id="acd0b-108">[#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md) -- Collapse and hide sections of code in the Visual Studio editor</span></span>  
  
 <span data-ttu-id="acd0b-109">**#Disable, #Enable** – zakažte a povolte konkrétní varování pro oblasti kódu.</span><span class="sxs-lookup"><span data-stu-id="acd0b-109">**#Disable, #Enable** -- Disable and enable specific warnings for regions of code.</span></span>  
  
```vb  
#Disable Warning BC42356 ' suppress warning about no awaits in this method  
    Async Function TestAsync() As Task  
        Console.WriteLine("testing")  
    End Function  
#Enable Warning BC42356  
```  
  
 <span data-ttu-id="acd0b-110">Můžete zakázat a povolit příliš čárkami oddělený seznam kódů upozornění.</span><span class="sxs-lookup"><span data-stu-id="acd0b-110">You can disable and enable a comma-separated list of warning codes too.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="acd0b-111">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="acd0b-111">Related Sections</span></span>  
 [<span data-ttu-id="acd0b-112">Referenční dokumentace jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="acd0b-112">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)  
  
 [<span data-ttu-id="acd0b-113">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="acd0b-113">Visual Basic</span></span>](../../../visual-basic/index.md)
