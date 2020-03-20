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
ms.openlocfilehash: f8e92ec4f813e8810273a1514298d0739a3d2406
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179065"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a>ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs – metoda
Získá čítač výčtu pro typy prostředí Windows Runtime uložené v mezipaměti v doméně aplikace na základě jejich identifikátorů rozhraní.  
  
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
 [v] Počet požadovaných typů.  
  
 `iidsToResolve`  
 [v] Ukazatel na pole, které obsahuje identifikátory rozhraní odpovídající spravovaným reprezentacím typů prostředí Windows Runtime, které mají být načteny.  
  
 `ppTypesEnum`  
 [out] Ukazatel na adresu objektu rozhraní ICorDebugTypeEnum, který umožňuje výčet spravovaných reprezentací načtených v prostředí Windows Runtime v mezipaměti na základě identifikátorů rozhraní v `iidsToResolve`aplikaci .  
  
## <a name="remarks"></a>Poznámky  
 Pokud se metodě nepodaří načíst informace pro konkrétní identifikátor rozhraní, odpovídající položka v kolekci `ELEMENT_TYPE_END` "ICorDebugTypeEnum" `ELEMENT_TYPE_VOID` bude mít typ chyb z důvodu problémů s načítáním dat nebo pro neznámé identifikátory rozhraní.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Windows Runtime  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugAppDomain3 – rozhraní](icordebugappdomain3-interface.md)
