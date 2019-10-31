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
ms.openlocfilehash: 828e4dc67cb93d0a35879e94b54c9fac6e5bda16
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124087"
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
 mimo Ukazatel na `CORDB_ADDRESS`, který určuje počáteční adresu rámce zásobníku reprezentovaného tímto objektem `ICorDebugFrame`.  
  
 `pEnd`  
 mimo Ukazatel na `CORDB_ADDRESS`, který určuje koncovou adresu rámce zásobníku reprezentovaného tímto objektem `ICorDebugFrame`.  
  
## <a name="remarks"></a>Poznámky  
 Rozsah adres zásobníku je užitečný pro piecing společně prokládaných trasování zásobníku shromážděných z několika ladicích modulů. Číselný rozsah neposkytuje žádné informace o obsahu rámce zásobníku. Má smysl jenom pro porovnání umístění rámce zásobníku.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
