---
title: Volání vlastnosti nebo metody nemůže obsahovat odkaz na soukromý objekt, a to ani jako argument, ani jako typ návratové hodnoty.
ms.date: 07/20/2015
f1_keywords:
- vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
ms.openlocfilehash: 36c71cdb345d0fdc0da2b58865a1f11956bcb944
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409969"
---
# <a name="a-property-or-method-call-cannot-include-a-reference-to-a-private-object-either-as-an-argument-or-as-a-return-value"></a>Volání vlastnosti nebo metody nemůže obsahovat odkaz na soukromý objekt, a to ani jako argument, ani jako typ návratové hodnoty.

Mezi možné příčiny této chyby patří:  
  
- Klient vyvolal vlastnost nebo metodu komponenty mimo proces a pokusil se předat odkaz na privátní objekt jako jeden z argumentů.  
  
- Mimo procesová komponenta vyvolala na svém klientovi metodu zpětného volání a pokusila se předat odkaz na privátní objekt.  
  
- Neprocesní komponenta se pokusila předat odkaz na privátní objekt jako argument události, kterou vyvolal.  
  
- Klient se pokusil přiřadit odkaz na privátní objekt k `ByRef` argumentu události, kterou zpracovává.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Odeberte odkaz.  
  
## <a name="see-also"></a>Viz také

- [Hlášen](../modifiers/private.md)
