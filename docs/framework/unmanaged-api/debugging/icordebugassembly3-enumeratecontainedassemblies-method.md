---
title: ICorDebugAssembly3::EnumerateContainedAssemblies – metoda
ms.date: 03/30/2017
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
ms.openlocfilehash: aebf499d7d25caef80782cc5661a57048dc5f6a9
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894866"
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
 `S_OK`Pokud je `ICorDebugAssembly3` tento objekt kontejnerem; `S_FALSE`v opačném případě je výčet prázdný.  
  
## <a name="remarks"></a>Poznámky  
 Pro zobrazení výčtu obsažených sestavení jsou vyžadovány symboly. Pokud nejsou k dispozici, metoda vrátí `S_FALSE`hodnotu a není k dispozici žádný platný enumerátor.  
  
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
