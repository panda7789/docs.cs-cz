---
title: 'Postupy: Zobrazení argumentů příkazového řádku - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: c88219d03d40c814338a1b09ccd37cfc03c2d577
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881017"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a>Postupy: Zobrazení argumentů příkazového řádku (C# Průvodce programováním v)
Argumenty pro spustitelný soubor na příkazovém řádku k dispozici jsou přístupné prostřednictvím volitelný parametr pro `Main`. Argumenty jsou k dispozici ve formě pole řetězců. Každý prvek pole obsahuje jeden argument. Odeberou se prázdné znaky mezi argumenty. Představte si třeba tyto příkazového řádku volání fiktivní spustitelný soubor:  
  
|Zadejte na příkazový řádek|Pole řetězců, které jsou předány do hlavní|  
|----------------------------|-------------------------------------|  
|**Executable.exe a b c.**|"a"<br /><br /> "b"<br /><br /> "c"|  
|**Executable.exe jeden dvě**|"jedna"<br /><br /> "two"|  
|**Executable.exe "jeden dvě" tři**|"one two"<br /><br /> "tři"|  
  
> [!NOTE]
>  Při spouštění aplikace v sadě Visual Studio, můžete zadat argumenty příkazového řádku [stránka ladění, Návrhář projektu](/visualstudio/ide/reference/debug-page-project-designer).  
  
## <a name="example"></a>Příklad  
 Tento příklad zobrazuje argumenty příkazového řádku předané do aplikace příkazového řádku. Výstup se pro první položku v tabulce výše.  
  
 [!code-csharp[csProgGuideMain#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#9)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Sestavování pomocí programu csc.exe v příkazovém řádku](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [Argumenty Main() a příkazového řádku](../../../csharp/programming-guide/main-and-command-args/index.md)
- [Návratové hodnoty Main()](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
