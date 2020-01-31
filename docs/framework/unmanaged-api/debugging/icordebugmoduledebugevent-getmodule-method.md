---
title: 'ICorDebugModuleDebugEvent:: GetModule – metoda'
ms.date: 03/30/2017
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
ms.openlocfilehash: 4d9eea8fb5c42002763a0ae52a186bf2c1e6d2ee
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792906"
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a>ICorDebugModuleDebugEvent:: GetModule – metoda
Získá sloučený modul, který byl právě načten nebo uvolněn.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppModule`  
 mimo Ukazatel na adresu ICorDebugModule objektu, který reprezentuje sloučený modul, který byl právě načten nebo uvolněn.  
  
## <a name="remarks"></a>Poznámky  
 Můžete zavolat metodu [GetEventKind –](icordebugdebugevent-geteventkind-method.md) a zjistit, zda byl modul načten nebo uvolněn.  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugModuleDebugEvent – rozhraní](icordebugmoduledebugevent-interface.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
