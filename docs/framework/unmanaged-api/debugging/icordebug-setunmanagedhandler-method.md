---
title: ICorDebug::SetUnmanagedHandler – metoda
ms.date: 03/30/2017
api_name:
- ICorDebug.SetUnmanagedHandler
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::SetUnmanagerHandler
helpviewer_keywords:
- SetUnmanagedHandler method [.NET Framework debugging]
- ICorDebug::SetUnmanagedHandler method [.NET Framework debugging]
ms.assetid: 6b546be4-f86d-4536-8cfc-1d08e5066eb6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c234b3953130f53d7e6b583cd92670149a70689b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168859"
---
# <a name="icordebugsetunmanagedhandler-method"></a>ICorDebug::SetUnmanagedHandler – metoda
Určuje objekt obslužné rutiny události pro nespravované události.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetUnmanagedHandler (  
    [in] ICorDebugUnmanagedCallback  *pCallback  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pCallback`  
 [in] Ukazatel [icordebugunmanagedcallback –](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md) objekt, který reprezentuje obslužnou rutinu události pro nespravované události.  
  
## <a name="remarks"></a>Poznámky  
 Obslužná rutina události objektu pro nespravované události musí být nastavena po volání [icordebug::Initialize –](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md) a před všechna volání do [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) nebo [icordebug::DebugActiveProcess – ](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md). V zájmu starší verze však není nutné nastavit objekt obslužné rutiny události pro nespravované události, dokud se vyvolá první událost nativní ladění. Konkrétně Pokud `ICorDebug::CreateProcess` nastavil příznak CREATE_SUSPENDED nativní ladění události nelze zpracovat, dokud nebude obnoven hlavního vlákna.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebug – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
