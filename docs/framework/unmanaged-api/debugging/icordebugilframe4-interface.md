---
title: Rozhraní ICorDebugILFrame4
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame4
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1e739183-3e05-49e5-846f-4075256e41de
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b17c7630160af78fe3163e6962b8fe085af1edc1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206613"
---
# <a name="icordebugilframe4-interface"></a>Rozhraní ICorDebugILFrame4
[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]  
  
 Poskytuje metody, které umožňují přístup k místní proměnné a kód v bloku zásobníku kódu (IL intermediate language). Parametr určuje, zda ladicí program má přístup k proměnné a kód přidaný v profileru ReJIT instrumentace.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EnumerateLocalVariablesEx – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md)|Vrátí seznam hodnot místních proměnných, které jsou k dispozici v rámci aktuální.|  
|[GetCodeEx – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md)|Vrátí kód, na kterém běží tento rámec zásobníku.|  
|[GetLocalVariableEx – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md)|Vrátí hodnotu místní proměnné v rámci IL.|  
  
## <a name="remarks"></a>Poznámky  
 Tyto metody nabízejí funkce kromě toho poskytuje [enumeratelocalvariables –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md), [getcode –](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md), a [getlocalvariable –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) metody. Každá metoda obsahuje `flags` parametr, který určuje, zda jsou viditelná další místní proměnné nebo definované ReJIT požadavkem profileru kód.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Debugging – rozhraní](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
