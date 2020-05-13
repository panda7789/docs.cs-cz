---
title: 'ICorDebugModuleDebugEvent:: GetModule – metoda'
ms.date: 03/30/2017
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
ms.openlocfilehash: 1df71ddbf1ee76cc8202d8f9e263b9d95b4aaa09
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213358"
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
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugModuleDebugEvent – rozhraní](icordebugmoduledebugevent-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
