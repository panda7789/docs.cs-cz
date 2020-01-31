---
title: ICorDebugModule3 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugModule3
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule3
helpviewer_keywords:
- ICorDebugModule3 interface [.NET Framework debugging]
ms.assetid: 0b69f945-263a-4e11-8512-89d27f6ea296
topic_type:
- apiref
ms.openlocfilehash: 33acc4d9a0819c43d17c362fcbea2e7636521fd3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792937"
---
# <a name="icordebugmodule3-interface"></a>ICorDebugModule3 – rozhraní
Vytvoří čtečku symbolů pro dynamický modul.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
interface ICorDebugModule3 : IUnknown  
{  
    HRESULT CreateReaderForInMemorySymbols  
      (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **  ppObj  
      );  
};  
```  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ICorDebugModule3::CreateReaderForInMemorySymbols – metoda](icordebugmodule3-createreaderforinmemorysymbols-method.md)|Vytvoří čtečku symbolů (obvykle [rozhraní ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)) pro dynamický modul.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní logicky rozšiřuje rozhraní "ICorDebugModule" a "ICorDebugModule2".  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** 4,5, 4, 3,5 SP1
  
## <a name="see-also"></a>Viz také:

- [ICorDebugRemoteTarget – rozhraní](icordebugremotetarget-interface.md)
- [ICorDebug – rozhraní](icordebug-interface.md)

- [Rozhraní pro ladění](debugging-interfaces.md)
