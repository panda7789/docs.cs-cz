---
title: ICorDebugType2 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugType2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType2
helpviewer_keywords:
- ICorDebugType2 interface
ms.assetid: 376fb03f-f1ef-4107-baa4-4d9d55884862
topic_type:
- apiref
ms.openlocfilehash: 7b56f0f3ba62efb48ac8d79aad4480b5f22771ba
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73110216"
---
# <a name="icordebugtype2-interface"></a>ICorDebugType2 – rozhraní
Rozšiřuje rozhraní ICorDebugType, aby získal identifikátor typu základního typu nebo komplexního (uživatelsky definovaného) typu.  
  
## <a name="methods"></a>Metody  
  
|Metoda||  
|------------|-|  
|[GetTypeID – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md)|Načte [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) pro tento typ.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní je logickou příponou rozhraní ICorDebugType.  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="example"></a>Příklad  
 Následující fragment kódu ukazuje použití metody [ICorDebugType2:: GetTypeId.](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) .  
  
```cpp  
// (error checking omitted for brevity)  
// given an ICorDebugType *pType  
  
ICorDebugType2 *pType2 = NULL;  
pType->QueryInterface(IID_ICorDebugType2, &pType);  
  
COR_TYPEID id;  
pType2->GetTypeID(&id);  
  
// now we can use existing APIs to get information about this COR_TYPEID  
```  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
