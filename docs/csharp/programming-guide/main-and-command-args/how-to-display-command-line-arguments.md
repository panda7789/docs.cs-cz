---
title: Jak zobrazit argumenty příkazového řádku - Průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: 210dad71220572535a0325fac925b0453b0d4e03
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712023"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a>Jak zobrazit argumenty příkazového řádku (Průvodce programováním jazyka C#)
Argumenty poskytnuté spustitelnému souboru na příkazovém řádku `Main`jsou přístupné prostřednictvím volitelného parametru . Argumenty jsou k dispozici ve formě pole řetězců. Každý prvek pole obsahuje jeden argument. Prázdné místo mezi argumenty je odebráno. Zvažte například tato vyvolání příkazového řádku fiktivního spustitelného souboru:  
  
|Vstup na příkazovém řádku|Pole řetězců předaných main|  
|----------------------------|-------------------------------------|  
|**spustitelný.exe a b c**|"a"<br /><br /> "b"<br /><br /> "c"|  
|**spustitelný soubor exe jeden dva**|"jedna"<br /><br /> "dva"|  
|**spustitelný soubor exe "jedna dvě" tři**|"one two"<br /><br /> "tři"|  
  
> [!NOTE]
> Pokud spouštěte aplikaci v sadě Visual Studio, můžete zadat argumenty příkazového řádku na [stránce ladění, Návrháře projektu](/visualstudio/ide/reference/debug-page-project-designer).  
  
## <a name="example"></a>Příklad  
 V tomto příkladu jsou zobrazeny argumenty příkazového řádku předané aplikaci příkazového řádku. Zobrazený výstup je pro první položku ve výše uvedené tabulce.  
  
 [!code-csharp[csProgGuideMain#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#9)]  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Sestavování pomocí programu csc.exe v příkazovém řádku](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [Argumenty Main() a příkazového řádku](./index.md)
- [Návratové hodnoty Main()](./main-return-values.md)
