---
title: "Typ &lt;typename&gt; není kompatibilní se specifikací CLS"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40041
- vbc40041
helpviewer_keywords: BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 16c12ee6c4f6efa20b9bab5ccf10077496b931ac
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2017
---
# <a name="type-lttypenamegt-is-not-cls-compliant"></a>Typ &lt;typename&gt; není kompatibilní se specifikací CLS
Proměnná, vlastnost nebo funkce návratový je deklarovaný s datovým typem, který není kompatibilní se specifikací CLS.  
  
 Pro aplikace splňovat [jazyková nezávislost a jazykově nezávislé komponenty](../../../../docs/standard/language-independence-and-language-independent-components.md) (CLS), musí používat pouze typy kompatibilní se specifikací CLS.  
  
 Následující [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] datové typy nejsou kompatibilní se specifikací CLS:  
  
-   [SByte – datový typ](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [Uinteger – datový typ](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [Ulong – datový typ](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [Ushort – datový typ](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 **ID chyby:** BC40041  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Pokud vaše aplikace musí být kompatibilní se specifikací CLS, změňte datový typ tohoto elementu na nejbližší typ kompatibilní se specifikací CLS. Například v místě z `UInteger` je možné použít `Integer` Pokud nepotřebujete rozsah hodnot výše 2 147 483 647. Pokud potřebujete rozšířené rozsahu, můžete nahradit `UInteger` s `Long`.  
  
-   Pokud vaše aplikace nemusí být kompatibilní se specifikací CLS, není potřeba nic nezmění. Je třeba věnovat pozornost jeho nekompatibilitu, ale.  
  
## <a name="see-also"></a>Viz také  
 [\<PAVE přes > zápis kompatibilní se specifikací CLS kódu](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
