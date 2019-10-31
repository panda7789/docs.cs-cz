---
title: ICorDebugHeapValue2::CreateHandle – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue2.CreateHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue2::CreateHandle
helpviewer_keywords:
- CreateHandle method [.NET Framework debugging]
- ICorDebugHeapValue2::CreateHandle method [.NET Framework debugging]
ms.assetid: fbc418e8-fa22-420d-84ec-e0e1800db041
topic_type:
- apiref
ms.openlocfilehash: b9eab1274f2d0ad562c0dec6adeddb85c6cfc458
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138381"
---
# <a name="icordebugheapvalue2createhandle-method"></a>ICorDebugHeapValue2::CreateHandle – metoda
Vytvoří popisovač zadaného typu pro hodnotu haldy reprezentované tímto objektem ICorDebugHeapValue2.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,   
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `type`  
 pro Hodnota výčtu CorDebugHandleType –, která určuje typ popisovače, který má být vytvořen.  
  
 `ppHandle`  
 mimo Ukazatel na adresu objektu ICorDebugHandleValue, který představuje nový popisovač pro tuto hodnotu haldy.  
  
## <a name="remarks"></a>Poznámky  
 Popisovač bude vytvořen v doméně aplikace, která je přidružena k hodnotě haldy, a stane se neplatným, pokud se doména aplikace uvolní.  
  
 Více volání této funkce pro stejnou hodnotu haldy vytvoří více popisovačů. Vzhledem k tomu, že obslužné rutiny ovlivňují výkon uvolňování paměti, by měl ladicí program omezit na poměrně malý počet popisovačů (přibližně 256), které jsou aktivní v čase.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
