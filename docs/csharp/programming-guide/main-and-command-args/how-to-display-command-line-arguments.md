---
title: "Postupy: Zobrazení argumentů příkazového řádku (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f6ae495eef227c6e4d9fb9ca0d4d0c031163fd52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a>Postupy: Zobrazení argumentů příkazového řádku (Průvodce programováním v C#)
Argumenty spustitelný soubor na příkazovém řádku jsou přístupné prostřednictvím volitelný parametr pro `Main`. Argumenty, které jsou uvedeny v podobě pole řetězců. Každý element pole obsahuje jeden argument. Odeberou se mezer mezi argumenty. Představte si třeba tyto volání fiktivní spustitelný soubor příkazového řádku:  
  
|Zadejte na příkazový řádek|Pole řetězců předaný Main|  
|----------------------------|-------------------------------------|  
|**Executable.exe b c**|"a"<br /><br /> "b"<br /><br /> "c"|  
|**Executable.exe jeden dva**|"jedna"<br /><br /> "dva"|  
|**Executable.exe "jeden dva" tři**|"one two"<br /><br /> "tři"|  
  
> [!NOTE]
>  Když aplikace běží v sadě Visual Studio, můžete zadat argumenty příkazového řádku v [stránka ladění, Návrhář projektu](/visualstudio/ide/reference/debug-page-project-designer).  
  
## <a name="example"></a>Příklad  
 Tento příklad zobrazuje argumenty příkazového řádku předaný aplikace příkazového řádku. Výstup ukazuje je pro první položku v předchozí tabulce.  
  
 [!code-csharp[csProgGuideMain#9](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-display-command-line-arguments_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Sestavování pomocí csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
 [Main() a argumenty příkazového řádku](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [Postupy: přístup příkazového řádku argumenty pomocí příkazu foreach](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)  
 [Návratové hodnoty Main()](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
