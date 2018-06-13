---
title: Volání vlastnosti nebo metody nemůže obsahovat odkaz na soukromý objekt, a to ani jako argument, ani jako typ návratové hodnoty.
ms.date: 07/20/2015
f1_keywords:
- vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
ms.openlocfilehash: 1f36526eab1bc0964bf89398b6e0f3e74d09fdc6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583822"
---
# <a name="a-property-or-method-call-cannot-include-a-reference-to-a-private-object-either-as-an-argument-or-as-a-return-value"></a>Volání vlastnosti nebo metody nemůže obsahovat odkaz na soukromý objekt, a to ani jako argument, ani jako typ návratové hodnoty.
Mezi možné příčiny této chyby patří:  
  
-   Klient vyvolat vlastnosti nebo metody komponentu out-of-process a pokus o odkaz na soukromý objekt předat jako jednoho z argumentů.  
  
-   Komponentu mimo proces volá metodu zpětného volání na svého klienta a pokus o předání odkaz na soukromý objekt.  
  
-   Odkaz na soukromý objekt předat jako argument události, které se vyvolá pokus o komponentu mimo proces.  
  
-   Pokus o přiřazení odkaz na soukromý objekt klienta `ByRef` argument byl zpracování události.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Odeberte odkaz.  
  
## <a name="see-also"></a>Viz také  
 [Private](../../../visual-basic/language-reference/modifiers/private.md)
