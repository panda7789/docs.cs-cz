---
title: "ICorDebugStepper::SetInterceptMask – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.SetInterceptMask
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::SetInterceptMask
helpviewer_keywords:
- SetInterceptMask method [.NET Framework debugging]
- ICorDebugStepper::SetInterceptMask method [.NET Framework debugging]
ms.assetid: 6245e2ae-5cc2-43ff-8cc1-71953d12113a
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3ef03b63c4af79c01ba9962fcc6f106b3141b576
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsteppersetinterceptmask-method"></a>ICorDebugStepper::SetInterceptMask – metoda
Nastaví hodnotu, která určuje typy kód, který se stupeň do.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetInterceptMask (  
    [in] CorDebugIntercept    mask  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `mask`  
 [v] Kombinace hodnot CorDebugIntercept – výčet, který určuje typy kódu.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je nastaven bit pro interceptoru, krokovače dokončí, když je došlo k danému typu brání kódu. Pokud je bit není zaškrtnuto, bude přeskočen intercepting kódu.  
  
 `SetInterceptMask` Metoda může mít nepředpokládaného interakce s [icordebugstepper::setunmappedstopmask –](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) (z uživatele hlediska). Například pokud jenom viditelné (to znamená,-vnitřní) část kód inicializace třídy chybí informace o mapování a STOP_NO_MAPPING_INFO není nastavený (najdete v článku [icordebugstepper::setunmappedstopmask –](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) metoda a CorDebugUnmappedStop – výčet), bude krokovače krok přes inicializaci třídy. Ve výchozím nastavení pouze INTERCEPT_NONE hodnotu `CorDebugIntercept` se použije výčet.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
