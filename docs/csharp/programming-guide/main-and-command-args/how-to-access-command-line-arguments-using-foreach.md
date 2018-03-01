---
title: "Postupy: Přístup k argumentům příkazového řádku pomocí příkazu foreach (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- command-line arguments [C#]
ms.assetid: 89c3e335-3f5b-4e24-8c5a-b8036561fe8a
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 557e72342901fab8bbe66e9cc3405cb4b2d9c1e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-command-line-arguments-using-foreach-c-programming-guide"></a>Postupy: Přístup k argumentům příkazového řádku pomocí příkazu foreach (Průvodce programováním v C#)
Další postup pro iterování přes pole je použití [foreach](../../../csharp/language-reference/keywords/foreach-in.md) příkaz, jak je znázorněno v tomto příkladu. Příkaz `foreach` lze použít k iteraci přes pole, kolekci třídy rozhraní .NET Framework nebo jakékoli třídy nebo struktury, která implementuje rozhraní <xref:System.Collections.IEnumerable>.  
  
> [!NOTE]
>  Při spuštění aplikace v sadě Visual Studio, můžete zadat argumenty příkazového řádku v [stránka ladění, Návrhář projektu](/visualstudio/ide/reference/debug-page-project-designer).  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak vytisknout argumenty příkazového řádku pomocí příkazu `foreach`.  
  
 [!code-csharp[csProgGuideMain#10](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_1.cs)]  
  
 [!code-csharp[csProgGuideMain#11](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_2.cs)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Array>  
 <xref:System.Collections>  
 [Sestavování pomocí csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [foreach v](../../../csharp/language-reference/keywords/foreach-in.md)  
 [Main() a argumenty příkazového řádku](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [Postupy: Zobrazení argumentů příkazového řádku](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)  
 [Návratové hodnoty Main()](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
