---
title: Jak zobrazit argumenty příkazového řádku – Průvodce programováním v C#
description: Naučte se zobrazovat argumenty příkazového řádku. Podívejte se na příklad kódu a zobrazte další dostupné prostředky.
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: 1ac5dc5a5f4e974c9202d2ce23f61071494e1977
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381811"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a>Jak zobrazit argumenty příkazového řádku (Průvodce programováním v C#)
Argumenty poskytované spustitelnému souboru na příkazovém řádku jsou přístupné prostřednictvím volitelného parametru `Main` . Argumenty jsou k dispozici ve formě pole řetězců. Každý prvek pole obsahuje jeden argument. Odeberou se prázdné místo mezi argumenty. Například zvažte tyto vyvolání příkazového řádku fiktivního spustitelného souboru:  
  
|Vstup na příkazovém řádku|Pole řetězců předaných do Main|  
|----------------------------|-------------------------------------|  
|**executable.exe a b c**|určitého<br /><br /> b<br /><br /> r|  
|**executable.exe 1 2**|hodinu<br /><br /> Druhá|  
|**executable.exe "1 2" 3**|"one two"<br /><br /> 3|  
  
> [!NOTE]
> Při spuštění aplikace v aplikaci Visual Studio můžete zadat argumenty příkazového řádku na [stránce ladění, Návrháři projektu](/visualstudio/ide/reference/debug-page-project-designer).  
  
## <a name="example"></a>Příklad  
 Tento příklad zobrazuje argumenty příkazového řádku předané aplikaci příkazového řádku. Zobrazený výstup je pro první položku v tabulce výše.  
  
 [!code-csharp[csProgGuideMain#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#9)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v C#](../index.md)
- [Sestavování pomocí programu csc.exe v příkazovém řádku](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [Argumenty Main () a příkazového řádku](./index.md)
- [Návratové hodnoty Main()](./main-return-values.md)
