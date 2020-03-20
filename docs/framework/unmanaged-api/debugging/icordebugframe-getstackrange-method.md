---
title: ICorDebugFrame::GetStackRange – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetStackRange
helpviewer_keywords:
- GetStackRange method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetStackRange method [.NET Framework debugging]
ms.assetid: fab037cb-fda6-40fb-9367-921e435dd5a0
topic_type:
- apiref
ms.openlocfilehash: 7a35ce025360e0ec8b7085d68e54548026b7c7fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178899"
---
# <a name="icordebugframegetstackrange-method"></a>ICorDebugFrame::GetStackRange – metoda
Získá absolutní rozsah adres tohoto rámce zásobníku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pStart`  
 [out] Ukazatel `CORDB_ADDRESS` na, který určuje počáteční adresu rámce zásobníku `ICorDebugFrame` reprezentovaného tímto objektem.  
  
 `pEnd`  
 [out] Ukazatel na `CORDB_ADDRESS` a, který určuje koncovou adresu rámce `ICorDebugFrame` zásobníku reprezentovaného tímto objektem.  
  
## <a name="remarks"></a>Poznámky  
 Rozsah adres zásobníku je užitečné pro skládání společně prokládané trasování zásobníku shromážděné z více ladicích modulů. Číselný rozsah neposkytuje žádné informace o obsahu rámce zásobníku. Je smysluplné pouze pro porovnání umístění rámce zásobníku.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
