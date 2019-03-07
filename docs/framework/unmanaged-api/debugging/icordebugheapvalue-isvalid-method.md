---
title: ICorDebugHeapValue::IsValid – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue.IsValid
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue::IsValid
helpviewer_keywords:
- IsValid method [.NET Framework debugging]
- ICorDebugHeapValue::IsValid method [.NET Framework debugging]
ms.assetid: 68e20e62-203d-46d8-bb91-8d3c61cfacc3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e1edb1d25a62a9a689c397339740e563d986c8b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478762"
---
# <a name="icordebugheapvalueisvalid-method"></a>ICorDebugHeapValue::IsValid – metoda
Získá hodnotu určující, zda objekt reprezentovaný rozhraním tento ICorDebugHeapValue je platný.  
  
 Tato metoda je zastaralá v rozhraní .NET Framework verze 2.0.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT IsValid (  
    [out] BOOL    *pbValid  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pbValid`  
 [out] Ukazatel na logickou hodnotu určující, zda je platný tuto hodnotu na haldě.  
  
## <a name="remarks"></a>Poznámky  
 Hodnota není platná, pokud byl uvolněn systémem uvolňování.  
  
 Tato metoda je zastaralá. V rozhraní .NET Framework 2.0, jsou všechny hodnoty platné až do [icordebugcontroller::Continue –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) je volán, na kterém jsou neplatné hodnoty.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
