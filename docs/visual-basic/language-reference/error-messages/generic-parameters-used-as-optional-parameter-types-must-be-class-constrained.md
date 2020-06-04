---
title: Obecné parametry použité jako typy volitelného parametru musí mít omezení třídy.
ms.date: 07/20/2015
f1_keywords:
- vbc32124
- bc32124
helpviewer_keywords:
- BC32124
ms.assetid: 55aa8b2a-9ce3-4620-a710-2f9b0feb6143
ms.openlocfilehash: 273ea592e73be5d76a4ffef077e691014a108347
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402924"
---
# <a name="generic-parameters-used-as-optional-parameter-types-must-be-class-constrained"></a>Obecné parametry použité jako typy volitelného parametru musí mít omezení třídy.
Procedura je deklarována s volitelným parametrem, který používá parametr typu, který není omezen na typ odkazu.  
  
 Pro každý volitelný parametr je vždy nutné zadat výchozí hodnotu. Pokud je parametr typu odkazu, musí být volitelná hodnota `Nothing` , což je platná hodnota libovolného typu odkazu. Nicméně, pokud je parametr typu hodnoty, tento typ musí být základní datový typ předdefinovaný Visual Basic. Důvodem je to, že složený typ hodnoty, jako je například uživatelsky definovaná struktura, nemá platnou výchozí hodnotu.  
  
 Použijete-li parametr typu pro volitelný parametr, je nutné zaručit, že se jedná o typ odkazu, aby nedocházelo k možnosti typu hodnoty bez platné výchozí hodnoty. To znamená, že je nutné parametr typu omezit buď pomocí `Class` klíčového slova, nebo s názvem konkrétní třídy.  
  
 **ID chyby:** BC32124  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Omezte parametr typu tak, aby přijímal pouze typ odkazu, nebo ho nepoužívejte pro volitelný parametr.  
  
## <a name="see-also"></a>Viz také

- [Obecné typy v Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
- [Seznam typů](../statements/type-list.md)
- [Class – příkaz](../statements/class-statement.md)
- [Volitelné parametry](../../programming-guide/language-features/procedures/optional-parameters.md)
- [Struktury](../../programming-guide/language-features/data-types/structures.md)
- [Nothing](../nothing.md)
