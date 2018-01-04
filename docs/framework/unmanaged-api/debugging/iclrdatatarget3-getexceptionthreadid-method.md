---
title: "ICLRDataTarget3::GetExceptionThreadID – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICLRDataTarget3.GetExceptionThreadID
api_location: mscordbi.dll
api_type: COM
ms.assetid: 307d6ac7-4a86-45f3-999d-6b47004a68f2
topic_type: apiref
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0f8b2e7c764eb5d7694633be7fb095b3d19be6e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatarget3getexceptionthreadid-method"></a>ICLRDataTarget3::GetExceptionThreadID – metoda
Voláno rozhraním běžné jazyk služby modulu runtime (CLR) data přístup získat ID podprocesu, která vrátila výjimku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetExceptionThreadID(  
    [out] ULONG32* threadID  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `threadID`  
 [out] ID podprocesu, která vrátila výjimku.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrácená hodnota je `S_OK` na úspěch nebo neúspěch `HRESULT` kód při selhání. `HRESULT` Kódy může zahrnovat, avšak nejsou omezeny na následující:  
  
|Návratový kód|Popis|  
|-----------------|-----------------|  
|`S_OK`|Metoda byla úspěšná.|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|Nelze najít ID platný vlákna výjimku.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je implementována zapisovačem ladění aplikace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** ClrData.idl, ClrData.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRDataTarget3 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 [GetExceptionContextRecord – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)  
 [GetExceptionRecord – metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)
