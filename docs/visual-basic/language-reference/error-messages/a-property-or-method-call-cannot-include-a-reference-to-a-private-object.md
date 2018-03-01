---
title: "Volání vlastnosti nebo metody nemůže obsahovat odkaz na soukromý objekt, a to ani jako argument, ani jako typ návratové hodnoty."
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cce2bc67beb7e4ac0664b5b7240f5eb3ea0204f9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
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
 [Privátní](../../../visual-basic/language-reference/modifiers/private.md)
