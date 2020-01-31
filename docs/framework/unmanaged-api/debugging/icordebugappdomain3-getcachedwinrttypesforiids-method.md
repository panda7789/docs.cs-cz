---
title: ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain3.GetCachedWinRTTypesForIIDs
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs
helpviewer_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs method, [.NET Framework debugging]
- GetCachedWinRTTypesForIIDs method, ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 23682ca0-1bcf-48e6-996e-69f7ba337682
topic_type:
- apiref
ms.openlocfilehash: 8b259636a8bd28abd3bba12c4a05dda3c13557e1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784893"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a>ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs – metoda
Načte enumerátor pro prostředí Windows Runtime typy v mezipaměti aplikace na základě jejich identifikátorů rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCachedWinRTTypesForIIDs (   
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `cReqTypes`  
 pro Počet požadovaných typů.  
  
 `iidsToResolve`  
 pro Ukazatel na pole, které obsahuje identifikátory rozhraní odpovídající spravovaným reprezentacím typů prostředí Windows Runtime, které mají být načteny.  
  
 `ppTypesEnum`  
 mimo Ukazatel na adresu objektu rozhraní "ICorDebugTypeEnum", která umožňuje vyhodnotit výčet spravovaných reprezentace typů prostředí Windows Runtime uložených v mezipaměti, na základě identifikátorů rozhraní v `iidsToResolve`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud metoda nepovede načíst informace pro konkrétní identifikátor rozhraní, odpovídající položka v kolekci "ICorDebugTypeEnum" bude mít typ `ELEMENT_TYPE_END` chyby z důvodu problémů načítání dat, nebo `ELEMENT_TYPE_VOID` pro neznámé identifikátory rozhraní.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** prostředí Windows Runtime  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugAppDomain3 – rozhraní](icordebugappdomain3-interface.md)
