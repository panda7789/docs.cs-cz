---
title: V aplikaci '<name>' nebyla nalezena žádná dostupná metoda 'Main' s odpovídajícím podpisem.
ms.date: 07/20/2015
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
ms.openlocfilehash: 559c905d1e2e2de4500771a93d6116f9630011ba
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64591983"
---
# <a name="no-accessible-main-method-with-an-appropriate-signature-was-found-in-name"></a>Nebyla nalezena žádná metoda přístupné 'Main' s odpovídajícím podpisem v "\<název >"
Musí mít aplikace příkazového řádku `Sub Main` definované. `Main` musí být deklarována jako `Public Shared` Pokud je definován ve třídě, nebo jako `Public` Pokud definovaný v modulu.  
  
 **ID chyby:** BC30737  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Definování `Public Sub Main` postup pro váš projekt. Deklarujte ho jako `Shared` pouze v případě definovat uvnitř třídy.  
  
## <a name="see-also"></a>Viz také:

- [Struktura programu v jazyce Visual Basic](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)
