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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 878941f7af71fa5e3de8e38c4a68a66cb964983d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223157"
---
# <a name="icordebugtype2-interface"></a>ICorDebugType2 – rozhraní
Rozšiřuje rozhraní ICorDebugType načtete identifikátor typu základního typu nebo komplexní typ (definovaný uživatelem).  
  
## <a name="methods"></a>Metody  
  
|Metoda||  
|------------|-|  
|[GetTypeID – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md)|Získá [cor_typeid –](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) u tohoto typu.|  
  
## <a name="remarks"></a>Poznámky  
 Toto rozhraní je logickým rozšířením icordebugtype – rozhraní.  
  
> [!NOTE]
>  Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.  
  
## <a name="example"></a>Příklad  
 Následující fragment kódu ukazuje použití metody [ICorDebugType2::GetTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) metody.  
  
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
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Debugging – rozhraní](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
