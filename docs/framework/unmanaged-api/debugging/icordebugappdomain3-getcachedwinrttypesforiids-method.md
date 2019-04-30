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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed1d7ad95b7c8474121994d0f54557c1c36cb531
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61917373"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a>ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs – metoda
Získá enumerátor pro uložené v mezipaměti [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typy v doméně aplikace podle jejich identifikátorů rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetCachedWinRTTypesForIIDs (   
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `cReqTypes`  
 [in] Počet požadovaných typů.  
  
 `iidsToResolve`  
 [in] Ukazatel na pole, které obsahuje rozhraní identifikátory odpovídající spravované reprezentace [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typy, které se mají načíst.  
  
 `ppTypesEnum`  
 [out] Spravované reprezentace ukazatele na adresu objektu rozhraní "icordebugtypeenum –", která umožňuje vytvoření výčtu v mezipaměti [!INCLUDE[wrt](../../../../includes/wrt-md.md)] načíst typy založené na rozhraní identifikátory v `iidsToResolve`.  
  
## <a name="remarks"></a>Poznámky  
 Jestliže metoda selže načíst informace pro konkrétní rozhraní identifikátor, odpovídající položku v kolekci "Icordebugtypeenum –" bude mít typ `ELEMENT_TYPE_END` chyby kvůli problémům s načítání dat, nebo `ELEMENT_TYPE_VOID` pro neznámé rozhraní identifikátory.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugAppDomain3 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
