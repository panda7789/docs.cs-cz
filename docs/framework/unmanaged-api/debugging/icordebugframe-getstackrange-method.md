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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c9f58e66286f5e3e169507efd2f87ce10e9d323b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754854"
---
# <a name="icordebugframegetstackrange-method"></a>ICorDebugFrame::GetStackRange – metoda
Získá absolutní adresu rozsahu tohoto rámce zásobníku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,   
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pStart`  
 [out] Ukazatel `CORDB_ADDRESS` určující počáteční adresu zásobníku představovaného tímto rozhraním `ICorDebugFrame` objektu.  
  
 `pEnd`  
 [out] Ukazatel `CORDB_ADDRESS` , který určuje koncovou adresu zásobníku představovaného tímto rozhraním `ICorDebugFrame` objektu.  
  
## <a name="remarks"></a>Poznámky  
 Rozsah adres zásobníku je užitečné pro piecing společně trasování zásobníků shromážděných z více ladicí moduly. Číselný rozsah poskytuje žádné informace o obsahu tohoto rámce zásobníku. To má smysl pouze pro porovnání umístění rámce zásobníku.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
