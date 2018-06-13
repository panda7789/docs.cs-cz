---
title: Direktivy (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- directives, Visual Basic compiler
- Visual Basic code, directives
- directives
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
ms.openlocfilehash: 38d54feae5cf7bf41a825d1f6000811e2b56f319
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33584641"
---
# <a name="directives-visual-basic"></a>Direktivy (Visual Basic)
Témata v této části dokumentů direktivy kompilátoru jazyka Visual Basic zdrojového kódu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [#Const – direktiva](../../../visual-basic/language-reference/directives/const-directive.md) – definovat konstantu kompilátoru  
  
 [#ExternalSource – direktiva](../../../visual-basic/language-reference/directives/externalsource-directive.md) – označuje mapování mezi řádky zdroje a externí zdroj textu  
  
 [#If... Then... #Else direktivy](../../../visual-basic/language-reference/directives/if-then-else-directives.md) – kompilace vybrané bloky kódu  
  
 [#Region – direktiva](../../../visual-basic/language-reference/directives/region-directive.md) – sbalení a skrytí sekcí kódu v editoru Visual Studio  
  
 **#Disable, #Enable** – zakažte a povolte konkrétní varování pro oblasti kódu.  
  
```vb  
#Disable Warning BC42356 ' suppress warning about no awaits in this method  
    Async Function TestAsync() As Task  
        Console.WriteLine("testing")  
    End Function  
#Enable Warning BC42356  
```  
  
 Můžete zakázat a povolit příliš čárkami oddělený seznam kódů upozornění.  
  
## <a name="related-sections"></a>Související oddíly  
 [Referenční dokumentace jazyka Visual Basic](../../../visual-basic/language-reference/index.md)  
  
 [Visual Basic](../../../visual-basic/index.md)
