---
title: Rozhraní ICorDebugAssembly3
ms.date: 03/30/2017
ms.assetid: 17fc5d76-75a9-4933-83f0-594de7f973f3
ms.openlocfilehash: 67707092c80b0e07aa284336c426aba09ff991af
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894817"
---
# <a name="icordebugassembly3-interface"></a>Rozhraní ICorDebugAssembly3
Logicky rozšiřuje rozhraní ICorDebugAssembly, aby poskytovala podporu pro sestavení kontejneru a jejich obsažená sestavení.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EnumerateContainedAssemblies – metoda](icordebugassembly3-enumeratecontainedassemblies-method.md)|Získá enumerátor pro sestavení obsažená v tomto sestavení.|  
|[GetContainerAssembly – metoda](icordebugassembly3-getcontainerassembly-method.md)|Vrátí sestavení kontejneru tohoto `ICorDebugAssembly3` objektu.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
> Rozhraní je k dispozici pouze s .NET Native. Pokus o volání metody `QueryInterface` načtení ukazatele rozhraní `E_NOINTERFACE` pro ICorDebug scénáře mimo .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
- [Ladění](index.md)
