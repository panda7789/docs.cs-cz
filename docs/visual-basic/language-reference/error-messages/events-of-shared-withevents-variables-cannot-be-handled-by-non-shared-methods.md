---
title: Události sdílené proměnné WithEvents nelze zpracovat nesdílenými metodami.
ms.date: 07/20/2015
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords:
- BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
ms.openlocfilehash: 09f56d340322ee88afc54e7e8a53716777782d47
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54505767"
---
# <a name="events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a>Události sdílené proměnné WithEvents nelze zpracovat nesdílenými metodami.
Proměnná deklarovaná pomocí `Shared` jsou sdílené proměnné. Sdílené proměnné identifikuje přesně jednoho umístění úložiště. Proměnná deklarovaná pomocí `WithEvents` modifikátor vyhodnotí, že typ, ke kterému patří proměnné zpracovává sadu událostí, které vyvolává proměnné. Pokud je hodnota přiřazena k proměnné, vlastnost vytvořené `WithEvents` deklarace unhooks všechny existující obslužné rutiny události a připojí si novou obslužnou rutinu události prostřednictvím `Add` metody.  
  
 **ID chyby:** BC30594  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Deklarovat obslužnou rutinu události `Shared`.  
  
## <a name="see-also"></a>Viz také:
- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)
