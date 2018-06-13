---
title: ICLRDataTarget::GetCurrentThreadID – metoda
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetCurrentThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetCurrentThreadID
helpviewer_keywords:
- GetCurrentThreadID method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::GetCurrentThreadID method [.NET Framework debugging]
ms.assetid: dc9a0a6c-d592-4fb7-86ed-62684da3b0e1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03ce49466587d3e214c32e2a5cca89cdd7a72038
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405224"
---
# <a name="iclrdatatargetgetcurrentthreadid-method"></a>ICLRDataTarget::GetCurrentThreadID – metoda
Získá identifikátor pro aktuální vlákno.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetCurrentThreadID (  
    [out] ULONG32    *threadID  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `threadID`  
 [out] Ukazatel na identifikátor operační systém aktuální vlákno pro tento cílový proces.  
  
## <a name="remarks"></a>Poznámky  
 Pokud není žádná aktuální vlákno pro tento cílový proces `GetCurrentThreadID` metoda může selhat.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** ClrData.idl, ClrData.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRDataTarget – rozhraní](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
