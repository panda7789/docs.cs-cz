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
ms.openlocfilehash: 94d601125049f0c215b3b03bf8b13d2959872c3d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54711756"
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
