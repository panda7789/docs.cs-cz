---
title: Funkce VerifyClientKey (referenční dokumentace nespravovaného rozhraní API)
description: Funkce VerifyClientKey zajistí, že klíč klienta má správné zabezpečení.
ms.date: 11/06/2017
api_name:
- VerifyClientKey
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- VerifyClientKey
helpviewer_keywords:
- VerifyClientKey function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 47fee26a0c4c25e4bff5bca94e5e26daaf98cccd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59214712"
---
# <a name="verifyclientkey-function"></a>VerifyClientKey – funkce
Zajistí, že klíč klienta bude mít správné zabezpečení.  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntaxe  
  
```  
LONG VerifyClientKey(); 
```  

## <a name="return-value"></a>Návratová hodnota

Pokud funkce uspěje, vrácená hodnota je `ERROR_SUCCESS` (0).

Pokud funkce selže, vrácená hodnota je kód chyby definované v *WinError.h*.

## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** WMINet_Utils.def  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Viz také:

- [WMI a čítače výkonu (referenční dokumentace nespravovaného rozhraní API)](index.md)
