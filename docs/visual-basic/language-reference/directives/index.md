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
  