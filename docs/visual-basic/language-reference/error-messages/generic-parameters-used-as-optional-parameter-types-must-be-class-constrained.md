---
title: Obecné parametry použité jako typy volitelného parametru musí mít omezení třídy.
ms.date: 07/20/2015
f1_keywords:
- vbc32124
- bc32124
helpviewer_keywords:
- BC32124
ms.assetid: 55aa8b2a-9ce3-4620-a710-2f9b0feb6143
ms.openlocfilehash: 7e2b59f758ef236717a912694576b514e2ae8a60
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="generic-parameters-used-as-optional-parameter-types-must-be-class-constrained"></a>Obecné parametry použité jako typy volitelného parametru musí mít omezení třídy.
Postup je deklarovaný s volitelný parametr, který používá parametr typu, který není omezen být odkazového typu.  
  
 Vždy je třeba zadat výchozí hodnotu pro každý volitelný parametr. Pokud má parametr hodnotu typu odkaz, volitelná hodnota musí být `Nothing`, což je platná hodnota pro jakýkoli typ odkazu. Ale pokud je parametr typu hodnoty, tento typ musí být typu základní datové předdefinovaná v nástroji Visual Basic. Je to proto, že hodnota kompozitního typu, například do vlastní struktury nemá žádný platný výchozí hodnotu.  
  
 Použijete-li parametr typu pro volitelný parametr, musí zaručit, že je typu odkazu. aby se zabránilo možnost Typ hodnoty žádný platný výchozí hodnotou. To znamená, že je parametr typu omezit buď pomocí `Class` – klíčové slovo nebo s názvem určité třídy.  
  
 **ID chyby:** BC32124  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Omezit parametr typu tak, aby přijímal pouze odkaz na typ, nebo nepoužívejte ho pro volitelný parametr.  
  
## <a name="see-also"></a>Viz také  
 [Obecné typy v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Seznam typů](../../../visual-basic/language-reference/statements/type-list.md)  
 [Příkaz Class](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Nepovinné parametry](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)  
 [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Nothing](../../../visual-basic/language-reference/nothing.md)
