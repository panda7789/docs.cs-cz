---
title: ICorDebugAssembly3::EnumerateContainedAssemblies – metoda
ms.date: 03/30/2017
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
ms.openlocfilehash: 032f32a08efa92cea682b0e2fc974dc607a9dca4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133939"
---
# <a name="icordebugassembly3enumeratecontainedassemblies-method"></a>ICorDebugAssembly3::EnumerateContainedAssemblies – metoda
Získá enumerátor pro sestavení obsažená v tomto sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumerateContainedAssemblies(  
    ICorDebugAssemblyEnum **ppAssemblies  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppAssemblies`  
 mimo Ukazatel na adresu objektu rozhraní ICorDebugAssemblyEnum, který je enumerátorem.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK`, pokud je tento objekt `ICorDebugAssembly3` kontejnerem; v opačném případě `S_FALSE`a výčet je prázdný.  
  
## <a name="remarks"></a>Poznámky  
 Pro zobrazení výčtu obsažených sestavení jsou vyžadovány symboly. Pokud nejsou k dispozici, metoda vrátí `S_FALSE`a není k dispozici žádný platný enumerátor.  
  
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
