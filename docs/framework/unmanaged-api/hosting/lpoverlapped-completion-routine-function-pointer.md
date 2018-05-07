---
title: LPOVERLAPPED_COMPLETION_ROUTINE – ukazatel na funkci
ms.date: 03/30/2017
api_name:
- LPOVERLAPPED_COMPLETION_ROUTINE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- LPOVERLAPPED_COMPLETION_ROUTINE
helpviewer_keywords:
- LPOVERLAPPED_COMPLETION_ROUTINE function pointer [.NET Framework hosting]
ms.assetid: 5fb645d9-b818-401c-8c2c-c30d86de58ba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cd4b7ffef9c0ba3aba54387245b2d5c9ec1ae906
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="lpoverlappedcompletionroutine-function-pointer"></a>LPOVERLAPPED_COMPLETION_ROUTINE – ukazatel na funkci
Odkazuje na funkci, která upozorní hostitele, když překryté (tedy asynchronní) vstupně-výstupních operací na zařízení byla dokončena.  
  
 Tento ukazatel na funkci se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef VOID (*LPOVERLAPPED_COMPLETION_ROUTINE) (  
    [in] DWORD  dwErrorCode,  
    [in] DWORD  dwNumberOfBytesTransfered,  
    [in] LPVOID lpOverlapped  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwErrorCode`  
 [v] Hodnotu, která je kód chyby, pokud bylo ukončeno zařízení; Tato hodnota je, jinak hodnota nula.  
  
 Zavření zařízení způsobí, že všechna nevyřízená vstupně-výstupních operací na zařízení provést okamžitě.  
  
 `dwNumberOfBytesTransfered`  
 [v] Počet bajtů přenesených vstupně-výstupní operace.  
  
 `lpOverlapped`  
 [v] Ukazatel na strukturu, která obsahuje informace, které umožňuje dokončit požadavek na vstupně-výstupní operace.  
  
## <a name="remarks"></a>Poznámky  
 Funkce, ke kterému `LPOVERLAPPED_COMPLETION_ROUTINE` body je funkce zpětného volání a musí být implementována zapisovačem hostitelskou aplikaci. Funkce zpětného volání umožňuje hostiteli zpracovat dokončenou žádost vstupně-výstupní operace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorWks.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Zastaralé funkce pro hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
