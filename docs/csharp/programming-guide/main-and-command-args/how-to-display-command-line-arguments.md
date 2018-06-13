---
title: 'Postupy: Zobrazení argumentů příkazového řádku (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: 7b9e488e84c78c8fdbf64431f42ea5797fdca916
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33334133"
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
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Sestavování pomocí programu csc.exe v příkazovém řádku](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
 [Argumenty Main() a příkazového řádku](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [Postupy: Přístup k argumentům příkazového řádku pomocí příkazu foreach](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)  
 [Návratové hodnoty Main()](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
