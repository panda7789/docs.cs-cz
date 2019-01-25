---
title: Volání vlastnosti nebo metody nemůže obsahovat odkaz na soukromý objekt, a to ani jako argument, ani jako typ návratové hodnoty.
ms.date: 07/20/2015
f1_keywords:
- vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
ms.openlocfilehash: 5f0740af49bb369be87a1a33973b67f59acf3ab6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54700829"
---
# <a name="a-property-or-method-call-cannot-include-a-reference-to-a-private-object-either-as-an-argument-or-as-a-return-value"></a>Volání vlastnosti nebo metody nemůže obsahovat odkaz na soukromý objekt, a to ani jako argument, ani jako typ návratové hodnoty.
Mezi možné příčiny této chyby patří:  
  
-   Klient vyvolat vlastnost nebo metoda komponentu mimo proces a došlo k pokusu o předání odkazem na soukromý objekt jako jeden z argumentů.  
  
-   Jako součást mimo proces volal metodu zpětného volání na jeho klienta a došlo k pokusu o předání odkazem na soukromý objekt.  
  
-   Jako součást na více instancí procesu došlo k pokusu o odkaz na soukromý objekt předat jako argument, který byl vyvolání události.  
  
-   Pokus o přiřazení odkaz na soukromý objekt klienta `ByRef` argument události byla zpracování.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Odeberte odkaz.  
  
## <a name="see-also"></a>Viz také:
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
