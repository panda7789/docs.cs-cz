---
title: _EFN_GetManagedObjectFieldInfo – funkce
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedObjectFieldInfo
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedObjectFieldInfo
helpviewer_keywords:
- _EFN_GetManagedObjectFieldInfo function [.NET Framework debugging]
ms.assetid: 3b93bcff-62a4-47b2-babc-6bcf4216119a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c6195d9666afa8fba3f77322366e4709634e53bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="efngetmanagedobjectfieldinfo-function"></a>_EFN_GetManagedObjectFieldInfo – funkce
Získá posun od začátku objekt pole a hodnotu pole pomocí ukazatele zadaného objektu a název pole.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT _EFN_GetManagedObjectFieldInfo(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       objAddr,  
    [in]  __out_ecount (mdNameLen) PSTR szFieldName,  
    [out] PULONG64      pValue,  
    [out] PULONG        pOffset  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `Client`  
 [v] Ukazatel na klientské ladění.  
  
 `objAddr`  
 [v] Ukazatel spravovaného objektu.  
  
 szFieldName  
 [v] Ukazatel spravovaného objektu na název pole.  
  
 `pValue`  
 [out] Hodnota pole. Tento parametr může mít hodnotu null.  
  
 `pOffset`  
 [out] Posun od `objAddr` na pole. Tento parametr může mít hodnotu null.  
  
## <a name="remarks"></a>Poznámky  
 Pokud posun 0, je zapsán posunutí.  
  
 Pokud neexistuje žádný spravovaný kód ve vlákně aktuálně v kontextu, funkce vrátí HRESULT SOS_E_NOMANAGEDCODE s hodnotou zařízení 0xa0 a chybový kód 0x1000.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** SOS_Stacktrace.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Globální statické funkce pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
