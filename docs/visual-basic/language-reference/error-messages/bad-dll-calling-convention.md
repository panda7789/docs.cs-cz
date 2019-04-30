---
title: Chybná konvence volání knihovny DLL
ms.date: 07/20/2015
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
ms.openlocfilehash: f7b0c3a6edbe0b950195306fa66287ff9b209bfe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61935275"
---
# <a name="bad-dll-calling-convention"></a>Chybná konvence volání knihovny DLL
Argumenty předané dynamická knihovna (DLL) musí přesně odpovídat názvům rutina očekává. Konvence volání využívání počet, typ a pořadí argumentů. Váš program může být volání rutiny v knihovně DLL, který je předáván nesprávného typu nebo počet argumentů.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Ujistěte se, že všechny typy argumentů souhlasí s argumenty zadaného v deklaraci rutiny, která se označuje jako volání.  
  
2. Ujistěte se, že předáváte stejný počet argumentů, které jsou uvedené v deklaraci rutiny, která se označuje jako volání.  
  
3. Pokud rutina DLL očekává, že argumentů podle hodnoty, ujistěte se, že `ByVal` je určená pro tyto argumenty v deklaraci pro rutiny.  
  
## <a name="see-also"></a>Viz také:

- [Typy chyb](../../../visual-basic/programming-guide/language-features/error-types.md)
- [Příkaz Call](../../../visual-basic/language-reference/statements/call-statement.md)
- [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)
