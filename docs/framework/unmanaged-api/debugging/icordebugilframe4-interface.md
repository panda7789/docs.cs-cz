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
ms.openlocfilehash: 010d73309ae21f9a593f72533691bdd95fbd4132
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130853"
---
# <a name="icordebugilframe4-interface"></a>Rozhraní ICorDebugILFrame4
[Podporované v .NET Framework 4.5.2 a novějších verzích]  
  
 Poskytuje metody, které umožňují přístup k místním proměnným a kódu v bloku rozhraní IL (Intermediate Language). Parametr určuje, jestli má ladicí program přístup k proměnným a kódu přidanému v profileru ReJIT instrumentace.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EnumerateLocalVariablesEx – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md)|Vrátí seznam místních proměnných dostupných v aktuálním rámci.|  
|[GetCodeEx – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md)|Vrátí kód, na kterém je spuštěn tento rámec zásobníku.|  
|[GetLocalVariableEx – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md)|Vrátí hodnotu lokální proměnné v rámci rámce IL.|  
  
## <a name="remarks"></a>Poznámky  
 Tyto metody nabízejí funkce kromě těch, které poskytují metody [EnumerateLocalVariables –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md), [GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-getcode-method.md)a [GetLocalVariable –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md) . Každá metoda zahrnuje `flags` parametr, který určuje, zda jsou viditelné další lokální proměnné nebo kód definované žádostí ReJIT profileru.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
