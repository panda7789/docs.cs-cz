---
title: ICorDebugAssembly3::GetContainerAssembly – metoda
ms.date: 03/30/2017
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
ms.openlocfilehash: 068a08d70f2443edfe0970ec1ffb8cba9953c6b9
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894852"
---
# <a name="icordebugassembly3getcontainerassembly-method"></a>ICorDebugAssembly3::GetContainerAssembly – metoda
Vrátí sestavení kontejneru tohoto `ICorDebugAssembly3` objektu.  
  
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
 `S_OK`Pokud je volání metody úspěšné; `S_FALSE`v opačném případě `ppAssembly` je **hodnota null**.  
  
## <a name="remarks"></a>Poznámky  
 Pokud bylo toto sestavení sloučeno s ostatními v rámci jednoho sestavení kontejneru, vrátí tato metoda sestavení kontejneru. Další informace a terminologii naleznete v tématu [ICorDebugProcess6:: EnableVirtualModuleSplitting](icordebugprocess6-enablevirtualmodulesplitting-method.md) .  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Rozhraní ICorDebugAssembly3](icordebugassembly3-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
