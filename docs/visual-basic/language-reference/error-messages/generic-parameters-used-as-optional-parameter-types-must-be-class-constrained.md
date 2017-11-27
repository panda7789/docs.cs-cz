---
title: "Obecné parametry použité jako typy volitelného parametru musí mít omezení třídy."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32124
- bc32124
helpviewer_keywords: BC32124
ms.assetid: 55aa8b2a-9ce3-4620-a710-2f9b0feb6143
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a13ea66f12e54db4e585577e20e1f5396669f1a8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [Class – příkaz](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Volitelné parametry](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)  
 [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Nic](../../../visual-basic/language-reference/nothing.md)
