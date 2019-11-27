---
title: Direktivy
ms.date: 07/20/2015
helpviewer_keywords:
- directives, Visual Basic compiler
- Visual Basic code, directives
- directives
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
ms.openlocfilehash: d76e10ad5ce8ad3accdc84f97146e0816048d8f3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343806"
---
# <a name="directives-visual-basic"></a>Direktivy (Visual Basic)

Témata v tomto oddílu dokumentují direktivy kompilátoru Visual Basic zdrojového kódu.  
  
## <a name="in-this-section"></a>V tomto oddílu  

 [#Const direktiva](../../../visual-basic/language-reference/directives/const-directive.md) – definice konstanty kompilátoru  
  
 [#ExternalSource direktiva](../../../visual-basic/language-reference/directives/externalsource-directive.md) – označuje mapování mezi zdrojovými řádky a textem externím ke zdroji.  
  
 [#If... Then... #Else – direktivy](../../../visual-basic/language-reference/directives/if-then-else-directives.md) – zkompiluje vybrané bloky kódu  
  
 [#Region direktiva](../../../visual-basic/language-reference/directives/region-directive.md) – sbalení a skrytí oddílů kódu v editoru sady Visual Studio  
  
 **#Disable, #Enable** --zakázat a povolit specifická upozornění pro oblasti kódu.  
  
```vb  
#Disable Warning BC42356 ' suppress warning about no awaits in this method  
    Async Function TestAsync() As Task  
        Console.WriteLine("testing")  
    End Function  
#Enable Warning BC42356  
```  
  
 Můžete zakázat a povolit čárkami oddělený seznam kódů upozornění.  
  
## <a name="related-sections"></a>Související oddíly  

 [Referenční příručka jazyka Visual Basic](../../../visual-basic/language-reference/index.md)  
  
 [Visual Basic](../../../visual-basic/index.md)
