---
title: ICorDebugModule::EnableClassLoadCallbacks – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.EnableClassLoadCallbacks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::EnableClassLoadCallbacks
helpviewer_keywords:
- ICorDebugModule::EnableClassLoadCallbacks method [.NET Framework debugging]
- EnableClassLoadCallbacks method [.NET Framework debugging]
ms.assetid: 78dad5e4-8e2e-400f-bec3-92ff0205cd82
topic_type:
- apiref
ms.openlocfilehash: d552b694787b5d9f0d5adc399eda6f75df93c385
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793023"
---
# <a name="icordebugmoduleenableclassloadcallbacks-method"></a>ICorDebugModule::EnableClassLoadCallbacks – metoda
Určuje, zda jsou pro tento modul volána zpětná volání [ICorDebugManagedCallback:: LoadClass –](icordebugmanagedcallback-loadclass-method.md) a [ICorDebugManagedCallback:: UnloadClass –](icordebugmanagedcallback-unloadclass-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnableClassLoadCallbacks(  
    [in] BOOL bClassLoadCallbacks  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `bClassLoadCallbacks`  
 pro Nastavte tuto hodnotu na `true`, pokud chcete povolit modul CLR (Common Language Runtime) pro volání metod `ICorDebugManagedCallback::LoadClass` a `ICorDebugManagedCallback::UnloadClass`, když dojde k jejich přidruženým událostem.  
  
 Výchozí hodnota je `false` pro jiné než dynamické moduly. Hodnota je vždy `true` pro dynamické moduly a nelze ji změnit.  
  
## <a name="remarks"></a>Poznámky  
 Zpětná volání `ICorDebugManagedCallback::LoadClass` a `ICorDebugManagedCallback::UnloadClass` jsou vždy povolena pro dynamické moduly a nelze je zakázat.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
