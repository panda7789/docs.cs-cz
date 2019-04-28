---
title: ICorDebugCode2 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugCode2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2
helpviewer_keywords:
- ICorDebugCode2 interface [.NET Framework debugging]
ms.assetid: 9321903b-7dea-40d8-ba32-99016c00cc46
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dce3e3e4baeaa351c5ed1d9e5ca2c03631c3fce4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61750108"
---
# <a name="icordebugcode2-interface"></a>ICorDebugCode2 – rozhraní

Poskytuje metody, které rozšiřují možnosti "ICorDebugCode".  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetCodeChunks – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)|Získá bloky kódu, ze kterých je tento objekt kódu sestaven.|  
|[GetCompilerFlags – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcompilerflags-method.md)|Získá příznaky určující podmínky, za kterých byl tento objekt kódu buď kompilován just-in-time (JIT), nebo generován pomocí generátoru nativních bitových kopií (Ngen.exe).|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugCode3 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
