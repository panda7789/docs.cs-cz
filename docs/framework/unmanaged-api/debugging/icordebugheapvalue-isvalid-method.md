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
ms.openlocfilehash: 95532d6721467b482b1d79d611f8055b606bb4a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugheapvalueisvalid-method"></a>ICorDebugHeapValue::IsValid – metoda
Získá hodnotu, která určuje, zda je objekt reprezentovaný rozhraním tento icordebugheapvalue – platný.  
  
 Tato metoda je zastaralá v rozhraní .NET Framework verze 2.0.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT IsValid (  
    [out] BOOL    *pbValid  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbValid`  
 [out] Ukazatel na logickou hodnotu, která určuje, zda je tato hodnota v haldě platný.  
  
## <a name="remarks"></a>Poznámky  
 Hodnota je neplatná, pokud má bylo uvolněno modulem garbage collector.  
  
 Tato metoda je zastaralá. V rozhraní .NET Framework 2.0, všechny hodnoty jsou platné do [icordebugcontroller::Continue –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) je volána, na kterých časové hodnoty jsou neplatné.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
