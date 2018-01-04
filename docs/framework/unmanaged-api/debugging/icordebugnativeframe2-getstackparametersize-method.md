---
title: "ICorDebugNativeFrame2::GetStackParameterSize – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame2.GetStackParameterSize Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame2::GetStackParameterSize
helpviewer_keywords:
- ICorDebugNativeFrame2::GetStackParameterSize method [.NET Framework debugging]
- GetStackParameterSize method [.NET Framework debugging]
ms.assetid: f6a449c8-a941-43ba-9a90-c98b29ae3c36
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fa7e67c252f2ece16c072e22d0333e085fbc4f65
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframe2getstackparametersize-method"></a>ICorDebugNativeFrame2::GetStackParameterSize – metoda
Vrátí celková velikost všech parametrů v zásobníku na x86 operační systémy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetStackParameterSize([out] ULONG32 * pSize)  
```  
  
#### <a name="parameters"></a>Parametry  
 `pSize`  
 [out] Ukazatel na celková velikost všech parametrů v zásobníku.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Velikost zásobníku byl byla úspěšně vrácena.|  
|S_FALSE|`GetStackParameterSize`na platformě není x86 byla volána.|  
|E_FAIL|`The size of the parameters could not be returned`.|  
|E_INVALIDARG|`pSize`Je `null`.|  
  
## <a name="exceptions"></a>Výjimky  
  
## <a name="remarks"></a>Poznámky  
 [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) metody neměnit ukazatel zásobníku pro parametry, které se instaluje v zásobníku. Místo toho můžete použít hodnoty vrácené `GetStackParameterSize` upravit ukazatel zásobníku počáteční hodnoty nativní unwinder, který upravit parametry.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugNativeFrame2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
