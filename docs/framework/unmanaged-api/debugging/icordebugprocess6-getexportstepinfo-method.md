---
title: "ICorDebugProcess6::GetExportStepInfo – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a927e0ac-f110-426d-bbec-9377a29c8f17
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dbb0e1cf904675005522002596476aec996124b6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess6getexportstepinfo-method"></a>ICorDebugProcess6::GetExportStepInfo – metoda
Obsahuje informace o modulu runtime exportované funkce, které umožňují krok prostřednictvím spravovaného kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetExportStepInfo(  
    [in] LPCWSTR pszExportName,   
    [out] CorDebugCodeInvokeKind* pInvokeKind,   
    [out] CorDebugCodeInvokePurpose* pInvokePurpose);  
```  
  
#### <a name="parameters"></a>Parametry  
 pszExportName  
 [v] Název funkce exportu runtime zapsaný v tabulce PE export.  
  
 invokeKind  
 [out] Ukazatel na členem [CorDebugCodeInvokeKind](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md) výčet, který popisuje, jak bude exportované funkce vyvolání spravovaného kódu.  
  
 invokePurpose  
 [out] Ukazatel na členem [CorDebugCodeInvokePurpose](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md) výčet, který popisuje, proč exportované funkce zavolá spravovaného kódu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda může vrátit hodnoty uvedené v následující tabulce.  
  
|Návratová hodnota|Popis|  
|------------------|-----------------|  
|`S_OK`|Volání metody, které bylo úspěšné.|  
|`E_POINTER`|`pInvokeKind`nebo `pInvokePurpose` je **null**.|  
|Další selhání `HRESULT` hodnoty.|Podle potřeby.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Tato metoda je k dispozici s .NET Native jenom.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní ICorDebugProcess6](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [Ladění v rozhraní](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
