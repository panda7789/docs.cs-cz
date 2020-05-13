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
ms.openlocfilehash: cacdccf5c27cd1d115134d49e754b4ace2870b72
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205159"
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
 mimo Ukazatel na `CORDB_ADDRESS` , který určuje počáteční adresu rámce zásobníku reprezentované tímto `ICorDebugFrame` objektem.  
  
 `pEnd`  
 mimo Ukazatel na `CORDB_ADDRESS` , který určuje koncovou adresu rámce zásobníku reprezentované tímto `ICorDebugFrame` objektem.  
  
## <a name="remarks"></a>Poznámky  
 Rozsah adres zásobníku je užitečný pro piecing společně prokládaných trasování zásobníku shromážděných z několika ladicích modulů. Číselný rozsah neposkytuje žádné informace o obsahu rámce zásobníku. Má smysl jenom pro porovnání umístění rámce zásobníku.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
