---
title: Žádné dostupné &#39;hlavní&#39; nebyla nalezena metoda s odpovídajícím podpisem v &#39; &lt;název&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
ms.openlocfilehash: 6a60e26a2bd0e31c0f92dbbfb2518c75f304d9f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593217"
---
# <a name="no-accessible-39main39-method-with-an-appropriate-signature-was-found-in-39ltnamegt39"></a>Žádné dostupné &#39;hlavní&#39; nebyla nalezena metoda s odpovídajícím podpisem v &#39; &lt;název&gt;&#39;
Aplikace příkazového řádku musí mít `Sub Main` definované. `Main` musí být deklarována jako `Public Shared` Pokud je definována v třídě nebo jako `Public` Pokud definovaná v modulu.  
  
 **ID chyby:** BC30737  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Definování `Public Sub Main` postup pro váš projekt. Deklarujte ji jako `Shared` jenom v případě můžete definovat uvnitř třídy.  
  
## <a name="see-also"></a>Viz také  
 [Struktura programu v jazyce Visual Basic](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)
