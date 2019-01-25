---
title: ICorDebugModuleDebugEvent::GetModule – metoda
ms.date: 03/30/2017
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1ad20bdee5fee83b62d5da7f52c607835055616f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672328"
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a>ICorDebugModuleDebugEvent::GetModule – metoda
Získá sloučené modul, který byl právě nenačetl nebo je uvolněna.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppModule`  
 [out] Ukazatel na adresu icordebugmodule – objekt, který představuje sloučené modul, který byl právě načteny nebo uvolněny.  
  
## <a name="remarks"></a>Poznámky  
 Můžete volat [GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) metodou ke zjištění, zda byl modul načten nebo byla uvolněna.  
  
> [!NOTE]
>  Tato metoda je pouze k dispozici s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICorDebugModuleDebugEvent – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
