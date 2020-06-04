---
title: V aplikaci '<name>' nebyla nalezena žádná dostupná metoda 'Main' s odpovídajícím podpisem.
ms.date: 07/20/2015
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
ms.openlocfilehash: 6760b931ceb2ad5c2c04169d664da8629badc487
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409410"
---
# <a name="no-accessible-main-method-with-an-appropriate-signature-was-found-in-name"></a>V aplikaci '\<name>' nebyla nalezena žádná dostupná metoda 'Main' s odpovídajícím podpisem.
Aplikace příkazového řádku musí mít `Sub Main` definován. `Main`musí být deklarován, jako by `Public Shared` byla definována ve třídě, nebo jako `Public` definice v modulu.  
  
 **ID chyby:** BC30737  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Definujte `Public Sub Main` proceduru pro projekt. Deklarujte ho jako `Shared` if a jenom v případě, že ho definujete uvnitř třídy.  
  
## <a name="see-also"></a>Viz také

- [Struktura programu jazyka Visual Basic](../../programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [Procedury](../../programming-guide/language-features/procedures/index.md)
