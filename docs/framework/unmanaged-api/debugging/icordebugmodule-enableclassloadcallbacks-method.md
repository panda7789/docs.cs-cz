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
ms.openlocfilehash: 1ca3adf30ad633fcfb10a4b43a435698d2899597
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213527"
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
 pro Nastavte tuto hodnotu, chcete-li `true` Povolit modulu CLR (Common Language Runtime) volat `ICorDebugManagedCallback::LoadClass` metody a, `ICorDebugManagedCallback::UnloadClass` když dojde k jejich přidruženým událostem.  
  
 Výchozí hodnota je `false` pro jiné než dynamické moduly. Hodnota je vždy `true` pro dynamické moduly a nelze ji změnit.  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugManagedCallback::LoadClass` `ICorDebugManagedCallback::UnloadClass` Zpětná volání a jsou vždy povolena pro dynamické moduly a nelze je zakázat.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také
