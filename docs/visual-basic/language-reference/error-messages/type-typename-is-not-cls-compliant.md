---
title: Typ <typename> není kompatibilní se specifikací CLS.
ms.date: 07/20/2015
f1_keywords:
- bc40041
- vbc40041
helpviewer_keywords:
- BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
ms.openlocfilehash: eacf5036ebc6fc31dfa0e8de39c4fb574c9072b3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84386955"
---
# <a name="type-typename-is-not-cls-compliant"></a>Typ \<typename> není kompatibilní se specifikací CLS.
Proměnná, vlastnost nebo návrat funkce jsou deklarovány s datovým typem, který není kompatibilní se specifikací CLS.  
  
 Aby aplikace splňovala [jazykovou nezávislost a součásti nezávislé na jazyce](../../../standard/language-independence-and-language-independent-components.md) (CLS), musí používat pouze typy kompatibilní se specifikací CLS.  
  
 Následující Visual Basic datové typy nejsou kompatibilní se specifikací CLS:  
  
- [SByte – datový typ](../data-types/sbyte-data-type.md)  
  
- [UInteger – datový typ](../data-types/uinteger-data-type.md)  
  
- [ULong – datový typ](../data-types/ulong-data-type.md)  
  
- [UShort – datový typ](../data-types/ushort-data-type.md)  
  
 **ID chyby:** BC40041  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Pokud vaše aplikace musí být kompatibilní se specifikací CLS, změňte datový typ tohoto prvku na nejbližší typ kompatibilní se specifikací CLS. Například, `UInteger` `Integer` Pokud nepotřebujete rozsah hodnoty nad 2 147 483 647, můžete použít třeba místo. Pokud budete potřebovat Rozšířený rozsah, můžete nahradit `UInteger` `Long` .  
  
- Pokud vaše aplikace nemusí být kompatibilní se specifikací CLS, nemusíte měnit žádné změny. Měli byste si uvědomit, že nedodržující předpisy byste ale.
