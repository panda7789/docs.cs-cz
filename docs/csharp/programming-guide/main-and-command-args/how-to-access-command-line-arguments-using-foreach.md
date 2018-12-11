---
title: 'Postupy: Přístup k argumentům příkazového řádku pomocí příkazu foreach - C# Průvodce programováním pro službu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#]
ms.assetid: 89c3e335-3f5b-4e24-8c5a-b8036561fe8a
ms.openlocfilehash: 79c798bb6ec16fc639d37defc40da5af770e5bba
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53242429"
---
# <a name="how-to-access-command-line-arguments-using-foreach-c-programming-guide"></a>Postupy: Přístup k argumentům příkazového řádku pomocí příkazu foreach (C# Programming Guide)
Dalším přístupem k iterování přes pole je použít [foreach](../../../csharp/language-reference/keywords/foreach-in.md) jak je uvedeno v tomto příkladu. Příkaz `foreach` lze použít k iteraci přes pole, kolekci třídy rozhraní .NET Framework nebo jakékoli třídy nebo struktury, která implementuje rozhraní <xref:System.Collections.IEnumerable>.  
  
> [!NOTE]
>  Při spuštění aplikace v sadě Visual Studio, můžete zadat argumenty příkazového řádku [stránka ladění, Návrhář projektu](/visualstudio/ide/reference/debug-page-project-designer).  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak vytisknout argumenty příkazového řádku pomocí příkazu `foreach`.  
  
 [!code-csharp[csProgGuideMain#10](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_1.cs)]  
  
 [!code-csharp[csProgGuideMain#11](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_2.cs)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Array>  
- <xref:System.Collections>  
- [Sestavování pomocí programu csc.exe v příkazovém řádku](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [foreach, in](../../../csharp/language-reference/keywords/foreach-in.md)  
- [Argumenty Main() a příkazového řádku](../../../csharp/programming-guide/main-and-command-args/index.md)  
- [Postupy: Zobrazení argumentů příkazového řádku](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)  
- [Návratové hodnoty Main()](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
