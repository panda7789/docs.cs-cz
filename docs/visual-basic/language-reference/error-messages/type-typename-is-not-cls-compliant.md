---
title: Typ <typename> není kompatibilní se specifikací CLS.
ms.date: 07/20/2015
f1_keywords:
- bc40041
- vbc40041
helpviewer_keywords:
- BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
ms.openlocfilehash: 243f51b3e6c798c82fdbe7b28557c4f96c728bf2
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55281720"
---
# <a name="type-typename-is-not-cls-compliant"></a>Typ \<typename > není kompatibilní se Specifikací CLS
Proměnná, vlastnost nebo návratová hodnota funkce je deklarována s datovým typem, který není kompatibilní se Specifikací CLS.  
  
 Aplikace má být zajištěn soulad [jazyková nezávislost a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS), musí používat jenom typy kompatibilní se Specifikací CLS.  
  
 Následující datové typy jazyka Visual Basic nejsou kompatibilní se Specifikací CLS:  
  
-   [Datový typ SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [Datový typ UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [Datový typ ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [Datový typ UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 **ID chyby:** BC40041  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Pokud vaše aplikace musí být kompatibilní se Specifikací CLS, změňte datový typ tohoto elementu na nejbližší typ. kompatibilní se Specifikací CLS. Například místo hodnoty `UInteger` je možné použít `Integer` Pokud nepotřebujete rozsah hodnot nad 2 147 483 647. Pokud budete potřebovat delší rozsah, můžete nahradit `UInteger` s `Long`.  
  
-   Pokud vaše aplikace nemusí být kompatibilní se Specifikací CLS, není potřeba nic měnit. Měli byste vědět, jeho nedodržování předpisů, ale.