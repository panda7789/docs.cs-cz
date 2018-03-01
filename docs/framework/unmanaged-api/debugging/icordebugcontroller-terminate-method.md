---
title: "ICorDebugController::Terminate – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugController.Terminate
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Terminate
helpviewer_keywords:
- Terminate method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Terminate method [.NET Framework debugging]
ms.assetid: 4275af0c-b5a7-4e4c-97c9-7e41f36b2dd8
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2e7647df7a67d8357e72f8f41b0b3f586675aaac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcontrollerterminate-method"></a>ICorDebugController::Terminate – metoda
Ukončí proces uvedený ukončovací kód.  
  
> [!NOTE]
>  Tato metoda je obálka pro Win32 `TerminateProcess` funkce. Proto `Terminate` používá ukončovací kód ve stejném způsobem Win32 `TerminateProcess` funkce používá je.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Terminate (  
    [in] UINT exitCode  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `exitCode`  
 [v] Číselnou hodnotu, která je v něm ukončovací kód. Platné číselné hodnoty jsou definovány v Winbase.h.  
  
## <a name="remarks"></a>Poznámky  
 Po zastavení procesu, při `Terminate` je volána, by měly pokračovat proces, pomocí [icordebugcontroller::Continue –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) metoda tak, aby ladicí program obdržel potvrzení ukončení prostřednictvím [ Icordebugmanagedcallback::exitprocess –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) nebo [icordebugmanagedcallback::exitappdomain –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md) zpětného volání.  
  
> [!NOTE]
>  Tato metoda není implementována podle domény aplikace. To znamená, není implementována v <xref:System.AppDomain> úroveň.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 
