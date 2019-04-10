---
title: Rozhraní ICorDebugAssembly3
ms.date: 03/30/2017
ms.assetid: 17fc5d76-75a9-4933-83f0-594de7f973f3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eecb135e034c3565e805ea776115579488b2a4d5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59210305"
---
# <a name="icordebugassembly3-interface"></a>Rozhraní ICorDebugAssembly3
Logicky rozšiřuje icordebugassembly – rozhraní a poskytuje podporu pro sestavení kontejneru a jejich obsažené sestavení.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EnumerateContainedAssemblies – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-enumeratecontainedassemblies-method.md)|Získá enumerátor pro sestaveních obsažených v tomto sestavení.|  
|[GetContainerAssembly – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-getcontainerassembly-method.md)|Vrátí kontejner sestavení tohoto `ICorDebugAssembly3` objektu.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Rozhraní je pouze k dispozici s .NET Native. Pokus o volání `QueryInterface` načíst ukazatel rozhraní vrátí `E_NOINTERFACE` pro scénáře ICorDebug mimo .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Debugging – rozhraní](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
