---
title: Příkaz není platný uvnitř metody nebo víceřádkového výrazu lambda.
ms.date: 07/20/2015
f1_keywords:
- vbc30024
- bc30024
helpviewer_keywords:
- BC30024
ms.assetid: 758e7a8f-429b-42c1-9a78-778e5b480e04
ms.openlocfilehash: f3c43d640259d5e1af545e2610088aab5d70453d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396243"
---
# <a name="statement-is-not-valid-inside-a-methodmultiline-lambda"></a>Příkaz není platný uvnitř metody nebo víceřádkového výrazu lambda.
Příkaz není platný v `Sub` `Function` proceduře,, Property `Get` nebo Property `Set` . Některé příkazy lze umístit na úrovni modulu nebo třídy. Ostatní, například `Option Strict` , musí být na úrovni oboru názvů a před všemi ostatními deklaracemi.  
  
 **ID chyby:** BC30024  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Odeberte příkaz z procedury.  
  
## <a name="see-also"></a>Viz také

- [Sub – příkaz](../statements/sub-statement.md)
- [Function – příkaz](../statements/function-statement.md)
- [Get – příkaz](../statements/get-statement.md)
- [Set – příkaz](../statements/set-statement.md)
