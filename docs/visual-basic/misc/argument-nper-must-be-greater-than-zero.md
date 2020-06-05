---
title: Argument pper musí být větší než nula.
ms.date: 07/20/2015
f1_keywords:
- vbrRate_NPerMustBeGTZero
ms.assetid: d49242df-dbd1-4b26-bd8c-ed56d24fdfcd
ms.openlocfilehash: 0c2cf0f0000de44e1be796bb2de962b45c1d6969
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84368059"
---
# <a name="argument-nper-must-be-greater-than-zero"></a>Argument pper musí být větší než nula.
`NPer`Funkce, která vrátí hodnotu `Double` určující počet období pro anuitu na základě pravidelných pevných plateb a pevné úrokové sazby, vyžaduje argument větší než nula.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Kontrola pravopisu argumentů ve výrazu. Nesprávně napsaný název proměnné může implicitně vytvořit číselnou proměnnou, která je inicializovaná na nulu.  
  
- Zkontroluje předchozí operace s proměnnými ve výrazu, zejména ty, které byly předány do procedury jako argumenty z jiných postupů.  
  
## <a name="see-also"></a>Viz také

- [Předávání argumentů podle hodnoty a reference](../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
