---
title: Direktivy (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- directives, Visual Basic compiler
- Visual Basic code, directives
- directives
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
ms.openlocfilehash: 38d54feae5cf7bf41a825d1f6000811e2b56f319
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2018
ms.locfileid: "43000882"
---
# <a name="directives-visual-basic"></a>Direktivy (Visual Basic)
Témata v této části dokumentu direktivy kompilátoru jazyka Visual Basic zdrojového kódu.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [#Const – direktiva](../../../visual-basic/language-reference/directives/const-directive.md) – Definujte konstantu kompilátoru  
  
 [#ExternalSource – direktiva](../../../visual-basic/language-reference/directives/externalsource-directive.md) – určete mapování mezi zdrojovými řádky a textem mimo zdroj  
  
 [#If... Pak... #Else direktivy](../../../visual-basic/language-reference/directives/if-then-else-directives.md) – zkompilujte vybrané bloky kódu  
  
 [#Region – direktiva](../../../visual-basic/language-reference/directives/region-directive.md) – sbalit a skrýt části kódu v editoru sady Visual Studio  
  
 **#Disable, #Enable** – zakažte a povolte určité varování pro oblasti kódu.  
  
```vb  
#Disable Warning BC42356 ' suppress warning about no awaits in this method  
    Async Function TestAsync() As Task  
        Console.WriteLine("testing")  
    End Function  
#Enable Warning BC42356  
```  
  
 Můžete zakázat a povolit příliš čárkou oddělený seznam kódů upozornění.  
  
## <a name="related-sections"></a>Související oddíly  
 [Referenční příručka jazyka Visual Basic](../../../visual-basic/language-reference/index.md)  
  
 [Visual Basic](../../../visual-basic/index.md)
