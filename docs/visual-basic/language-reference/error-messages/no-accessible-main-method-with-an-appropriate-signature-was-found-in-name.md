---
title: Žádná dostupná &#39;hlavní&#39; v nebyla nalezena metoda s odpovídajícím podpisem &#39; &lt;název&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
ms.openlocfilehash: 3398195ef9d503e47ab569ff85cb2a827c4270f1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54501487"
---
# <a name="no-accessible-39main39-method-with-an-appropriate-signature-was-found-in-39ltnamegt39"></a>Žádná dostupná &#39;hlavní&#39; v nebyla nalezena metoda s odpovídajícím podpisem &#39; &lt;název&gt;&#39;
Musí mít aplikace příkazového řádku `Sub Main` definované. `Main` musí být deklarována jako `Public Shared` Pokud je definován ve třídě, nebo jako `Public` Pokud definovaný v modulu.  
  
 **ID chyby:** BC30737  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Definování `Public Sub Main` postup pro váš projekt. Deklarujte ho jako `Shared` pouze v případě definovat uvnitř třídy.  
  
## <a name="see-also"></a>Viz také:
- [Struktura programu v jazyce Visual Basic](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)
