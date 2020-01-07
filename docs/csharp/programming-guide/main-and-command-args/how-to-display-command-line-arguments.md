---
title: Postup zobrazení argumentů příkazového řádku – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: 3ae2f65696c6661ab4f732b604267116996162b2
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635168"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a>Postup zobrazení argumentů příkazového řádku (C# Průvodce programováním)
Argumenty poskytované spustitelnému souboru na příkazovém řádku jsou přístupné prostřednictvím volitelného parametru pro `Main`. Argumenty jsou k dispozici ve formě pole řetězců. Každý prvek pole obsahuje jeden argument. Odeberou se prázdné místo mezi argumenty. Například zvažte tyto vyvolání příkazového řádku fiktivního spustitelného souboru:  
  
|Vstup na příkazovém řádku|Pole řetězců předaných do Main|  
|----------------------------|-------------------------------------|  
|**spustitelný soubor. exe a b c**|určitého<br /><br /> b<br /><br /> r|  
|**spustitelný soubor. exe 1 2**|hodinu<br /><br /> "two"|  
|**spustitelný soubor. exe "1 2" 3**|"one two"<br /><br /> 3|  
  
> [!NOTE]
> Při spuštění aplikace v aplikaci Visual Studio můžete zadat argumenty příkazového řádku na [stránce ladění, Návrháři projektu](/visualstudio/ide/reference/debug-page-project-designer).  
  
## <a name="example"></a>Příklad  
 Tento příklad zobrazuje argumenty příkazového řádku předané aplikaci příkazového řádku. Zobrazený výstup je pro první položku v tabulce výše.  
  
 [!code-csharp[csProgGuideMain#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#9)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Sestavování pomocí programu csc.exe v příkazovém řádku](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [Argumenty Main() a příkazového řádku](./index.md)
- [Návratové hodnoty Main()](./main-return-values.md)
