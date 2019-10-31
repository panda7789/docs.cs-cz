---
title: ICorDebugAssembly3::GetContainerAssembly – metoda
ms.date: 03/30/2017
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
ms.openlocfilehash: 39f8dd042ea785258dfe5c048ebc348852be6892
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095396"
---
# <a name="icordebugassembly3getcontainerassembly-method"></a>ICorDebugAssembly3::GetContainerAssembly – metoda
Vrátí sestavení kontejneru tohoto objektu `ICorDebugAssembly3`.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetContainerAssembly(  
    ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppAssembly`  
 Ukazatel na adresu objektu ICorDebugAssembly, který představuje sestavení kontejneru, nebo **hodnotu null** , pokud volání metody se nezdařilo.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK`, pokud je volání metody úspěšné; v opačném případě jsou `S_FALSE`a `ppAssembly` **null**.  
  
## <a name="remarks"></a>Poznámky  
 Pokud bylo toto sestavení sloučeno s ostatními v rámci jednoho sestavení kontejneru, vrátí tato metoda sestavení kontejneru. Další informace a terminologii naleznete v tématu [ICorDebugProcess6:: EnableVirtualModuleSplitting](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md) .  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugAssembly3 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
