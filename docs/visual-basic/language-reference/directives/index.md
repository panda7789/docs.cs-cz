---
title: Direktivy
ms.date: 07/20/2015
helpviewer_keywords:
- directives, Visual Basic compiler
- Visual Basic code, directives
- directives
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
ms.openlocfilehash: b5fcf3cb8801bc99dd2096c28cc41ebefeb34592
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409995"
---
# <a name="directives-visual-basic"></a>Direktivy (Visual Basic)

Témata v tomto oddílu dokumentují direktivy kompilátoru Visual Basic zdrojového kódu.  
  
## <a name="in-this-section"></a>V tomto oddílu  

 [#Const direktiva](const-directive.md) – definice konstanty kompilátoru  
  
 [#ExternalSource direktiva](externalsource-directive.md) – označuje mapování mezi zdrojovými řádky a textem externím ke zdroji.  
  
 [#If... Then... #Else – direktivy](if-then-else-directives.md) – zkompiluje vybrané bloky kódu  
  
 [#Region direktiva](region-directive.md) – sbalení a skrytí oddílů kódu v editoru sady Visual Studio  
  
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

 [Reference jazyka Visual Basic](../index.md)  
  