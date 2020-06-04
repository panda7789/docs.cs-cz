---
title: Chybná konvence volání knihovny DLL
ms.date: 07/20/2015
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
ms.openlocfilehash: a60e44ce92b1805b0a5a6f1d4ce397c295eef202
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409878"
---
# <a name="bad-dll-calling-convention"></a>Chybná konvence volání knihovny DLL
Argumenty předané dynamické knihovně (DLL) se musí přesně shodovat s hodnotami, které rutina očekávala. Konvence volání se zabývat číslem, typem a pořadím argumentů. Váš program může volat rutinu v knihovně DLL, která je předána nesprávnému typu nebo počtu argumentů.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Zajistěte, aby všechny typy argumentů souhlasily s hodnotami uvedenými v deklaraci rutiny, kterou voláte.  
  
2. Ujistěte se, že jste předali stejný počet argumentů, které jsou uvedeny v deklaraci rutiny, které voláte.  
  
3. Pokud rutina DLL očekává argumenty podle hodnoty, ujistěte se, že `ByVal` je zadána pro tyto argumenty v deklaraci rutiny.  
  
## <a name="see-also"></a>Viz také

- [Typy chyb](../../programming-guide/language-features/error-types.md)
- [Call – příkaz](../statements/call-statement.md)
- [Declare – příkaz](../statements/declare-statement.md)
