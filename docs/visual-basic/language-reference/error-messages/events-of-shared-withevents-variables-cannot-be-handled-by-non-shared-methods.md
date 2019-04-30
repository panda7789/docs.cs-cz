---
title: Události sdílené proměnné WithEvents nelze zpracovat nesdílenými metodami.
ms.date: 07/20/2015
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords:
- BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
ms.openlocfilehash: 2b32043898986b3e3e68fab18c5f907843d7691c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61803251"
---
# <a name="events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a>Události sdílené proměnné WithEvents nelze zpracovat nesdílenými metodami.
Proměnná deklarovaná pomocí `Shared` jsou sdílené proměnné. Sdílené proměnné identifikuje přesně jednoho umístění úložiště. Proměnná deklarovaná pomocí `WithEvents` modifikátor vyhodnotí, že typ, ke kterému patří proměnné zpracovává sadu událostí, které vyvolává proměnné. Pokud je hodnota přiřazena k proměnné, vlastnost vytvořené `WithEvents` deklarace unhooks všechny existující obslužné rutiny události a připojí si novou obslužnou rutinu události prostřednictvím `Add` metody.  
  
 **ID chyby:** BC30594  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Deklarovat obslužnou rutinu události `Shared`.  
  
## <a name="see-also"></a>Viz také:

- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)
