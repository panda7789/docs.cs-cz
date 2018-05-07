---
title: ICorDebugType2 rozhraní
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 038598e6fa8c0f7d47a161783d21f03b3c87af0c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugtype2-interface"></a>ICorDebugType2 rozhraní
Rozšiřuje rozhraní ICorDebugType načíst identifikátor typu základní typ nebo komplexní typ (definovaný uživatelem).  
  
## <a name="methods"></a>Metody  
  
|Metoda||  
|------------|-|  
|[GetTypeID – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md)|Získá [cor_typeid –](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) pro tento typ.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní je logické rozšíření rozhraní ICorDebugType.  
  
> [!NOTE]
>  Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.  
  
## <a name="example"></a>Příklad  
 Následující fragment kódu ukazuje použití [ICorDebugType2::GetTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) metoda.  
  
```  
// (error checking omitted for brevity)  
// given an ICorDebugType *pType  
  
ICorDebugType2 *pType2 = NULL;  
pType->QueryInterface(IID_ICorDebugType2, &pType);  
  
COR_TYPEID id;  
pType2->GetTypeID(&id);  
  
// now we can use existing APIs to get information about this COR_TYPEID  
```  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
