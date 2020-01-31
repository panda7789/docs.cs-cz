---
title: ICorDebugAppDomain3::GetCachedWinRTTypes – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain3.GetCachedWinRTTypes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypes
helpviewer_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypes method [.NET Framework debugging]
- GetCachedWinRTTypes method, ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 9afd0e04-a403-41e2-9528-a6dcbcdcbd4d
topic_type:
- apiref
ms.openlocfilehash: 55d0b40bbdb5628f60090d9d70f7dccbebe9d58f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785002"
---
# <a name="icordebugappdomain3getcachedwinrttypes-method"></a>ICorDebugAppDomain3::GetCachedWinRTTypes – metoda
Získá enumerátor pro všechny typy prostředí Windows Runtime v mezipaměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCachedWinRTTypes (   
    [out] ICorDebugGuidToTypeEnum **ppGuidToTypeEnum)  
;  
```  
  
## <a name="parameters"></a>Parametry  
 `ppGuidToTypeEnum`  
 mimo Ukazatel na objekt rozhraní [ICorDebugGuidToTypeEnum –](icordebugguidtotypeenum-interface.md) , který může vyčíslit spravované reprezentace prostředí Windows runtimech typů, které jsou aktuálně načteny v doméně aplikace.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** prostředí Windows Runtime  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugAppDomain3 – rozhraní](icordebugappdomain3-interface.md)
