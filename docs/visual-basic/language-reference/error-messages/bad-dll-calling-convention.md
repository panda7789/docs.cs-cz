---
title: Chybná konvence volání knihovny DLL
ms.date: 07/20/2015
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
ms.openlocfilehash: d8c7f7aea46162215115689305f4010cb513b020
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="bad-dll-calling-convention"></a>Chybná konvence volání knihovny DLL
Argumenty předávané dynamická knihovna (DLL) musí přesně odpovídat názvům rutina očekává. Konvence volání řešit počet, typ a pořadí argumentů. Váš program může být volání rutiny v knihovně DLL, který je předáván nesprávného typu nebo počet argumentů.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Zajistěte, aby že všechny typy argumentů souhlas s těmi, zadaný v deklaraci rutiny, která jsou volání.  
  
2.  Ujistěte se, že předáváte stejný počet argumentů uvedené v deklaraci rutiny, která jsou volání.  
  
3.  Pokud rutina DLL očekává argumentů podle hodnoty, ujistěte se, `ByVal` je zadán pro tyto argumenty v deklaraci pro rutiny.  
  
## <a name="see-also"></a>Viz také  
 [Typy chyb](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [Příkaz Call](../../../visual-basic/language-reference/statements/call-statement.md)  
 [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)
