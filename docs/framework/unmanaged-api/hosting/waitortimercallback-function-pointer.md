---
title: WAITORTIMERCALLBACK – ukazatel na funkci
ms.date: 03/30/2017
api_name:
- WAITORTIMERCALLBACK
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- WAITORTIMERCALLBACK
helpviewer_keywords:
- WAITORTIMERCALLBACK function pointer [.NET Framework hosting]
ms.assetid: 1fec4aef-0a06-4df0-bae7-d31a9ef9603d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f938c7dcf08654eef1e2403426eb5c54d6d2a6b3
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490119"
---
# <a name="waitortimercallback-function-pointer"></a>WAITORTIMERCALLBACK – ukazatel na funkci
Odkazuje na funkci, která upozorňuje hostitele, popisovače čekání (<xref:System.Threading.WaitHandle>) buď byl signalizován nebo vypršel časový limit.  
  
 Tento ukazatel na funkci se již nepoužívá v rozhraní .NET Framework 4.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef VOID (__stdcall *WAITORTIMERCALLBACK) (  
    [in] PVOID lpParameter,  
    [in] BOOL  TimerOrWaitFired  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `lpParameter`  
 [in] Ukazatel na objekt, který obsahuje informace stanovené hostitelem.  
  
 `TimerOrWaitFired`  
 [in] `true` Pokud popisovač čekání vypršel časový limit, nebo `false` Pokud bylo signalizováno.  
  
## <a name="remarks"></a>Poznámky  
 Funkce, které `WAITORTIMERCALLBACK` body je funkce zpětného volání a musí být implementováno tvůrci hostitelské aplikace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorWks.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Zastaralé funkce pro hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
