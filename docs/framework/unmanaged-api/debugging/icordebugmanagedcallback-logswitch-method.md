---
title: ICorDebugManagedCallback::LogSwitch – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LogSwitch
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LogSwitch
helpviewer_keywords:
- LogSwitch method [.NET Framework debugging]
- ICorDebugManagedCallback::LogSwitch method [.NET Framework debugging]
ms.assetid: 0ac59d27-783f-4a87-b7a8-baa3ccc54582
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d5284cf6072aa5c1c11cc83355a3e9fa5c96837
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmanagedcallbacklogswitch-method"></a>ICorDebugManagedCallback::LogSwitch – metoda
Ladicí program upozorní, že běžné vlákna modulu runtime (CLR) spravované jazyk volal metodu <xref:System.Diagnostics.Switch> třída k vytvoření, úpravě nebo odstranění přepínač ladění nebo trasování.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT LogSwitch (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] LONG                 lLevel,  
    [in] ULONG                ulReason,  
    [in] WCHAR               *pLogSwitchName,  
    [in] WCHAR               *pParentName);  
```  
  
#### <a name="parameters"></a>Parametry  
 `PAppDomain`  
 [v] Ukazatel na ICorDebugAppDomain objekt, který představuje doménu aplikace obsahující spravované vlákno, které vytvořit, upravit nebo odstranit přepínač ladění nebo trasování.  
  
 `pThread`  
 [v] Ukazatel ICorDebugThread objektu, která představuje spravované vlákno.  
  
 `lLevel`  
 [v] Hodnota, která určuje úroveň závažnosti popisné zprávy, která byla zapsána do protokolu událostí.  
  
 `ulReason`  
 [v] Hodnota [LogSwitchCallReason](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md) výčtu, která určuje operaci provést na přepínači ladění nebo trasování.  
  
 `pLogSwitchName`  
 [v] Ukazatel na název přepínače ladění nebo trasování.  
  
 `pParentName`  
 [v] Ukazatel na název nadřazené přepínače ladění nebo trasování.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugManagedCallback – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
