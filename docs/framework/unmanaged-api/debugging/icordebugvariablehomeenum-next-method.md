---
title: 'ICorDebugVariableHomeEnum:: Next – metoda'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHomeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHomeEnum::Next
helpviewer_keywords:
- ICorDebugVariableHomeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: eb9ea96c-5b58-4655-8104-094fc8b393b8
topic_type:
- apiref
ms.openlocfilehash: 980f563d3b11fbfcce48b6d7c05275af520e14f1
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396507"
---
# <a name="icordebugvariablehomeenumnext-method"></a>ICorDebugVariableHomeEnum:: Next – metoda
Získá zadaný počet instancí [ICorDebugVariableHome](icordebugvariablehome-interface.md) , které obsahují informace o místních proměnných a argumentech ve funkci.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] ICorDebugVariableHome *homes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `celt`  
 pro Počet objektů, které mají být načteny.  
  
 `homes`  
 Pole ukazatelů, z nichž každý odkazuje na objekt [ICorDebugVariableHome](icordebugvariablehome-interface.md) , který poskytuje informace o lokální proměnné nebo argumentu funkce.  
  
 `pceltFetched`  
 mimo Počet instancí skutečně vrácených v objektech.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda vrací následující hodnoty.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|`S_OK`|Metoda byla úspěšně dokončena.|  
|`S_FALSE`|Skutečný počet načtených instancí, jak se odráží v `pceltFetched` , je menší než počet požadovaných instancí.|  
  
## <a name="remarks"></a>Poznámky  
 Metoda [ICorDebugVariableHomeEnum:: Next](icordebugvariablehomeenum-next-method.md) načte maximum `celt` objektů začínajících na aktuální pozici čítače výčtu. Když se metoda vrátí, `pceltFetched` obsahuje skutečný počet načtených objektů.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugVariableHomeEnum – rozhraní](icordebugvariablehomeenum-interface.md)
- [ICorDebugVariableHome – rozhraní](icordebugvariablehome-interface.md)
