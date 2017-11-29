---
title: "ICorDebugVariableSymbol::GetValue – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 90abece1-392e-4ade-94a1-30c75b0f7074
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 789bca88ea2f2d87ebfc73275b4a7569fcbe8cc9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablesymbolgetvalue-method"></a>ICorDebugVariableSymbol::GetValue – metoda
Získá hodnotu proměnné jako bajtové pole.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetValue(  
   [in] ULONG32 offset,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [out] ULONG32 *pcbValue,  
   [out, size_is(cbValue), length_is(*pcbValue)] BYTE pValue[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `offset`  
 [v] Počáteční odsazení v proměnné z kterého se mají číst hodnotu. Tento parametr se používá při čtení člen pole v objektu.  
  
 `cbContext`  
 [v] Velikost v bajtech `context` argument.  
  
 `context`  
 [v] Kontext vlákno použít ke čtení hodnota.  
  
 `cbValue`  
 [v] Velikost v bajtech `pValue` vyrovnávací paměti.  
  
 `pcbValue`  
 [out] Počet bajtů ve skutečnosti zapsána do `pValue` vyrovnávací paměti.  
  
 `pValue`  
 [out] Bajtové pole, která obsahuje hodnotu proměnné.  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Tato metoda je k dispozici s .NET Native jenom.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugVariableSymbol rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [Ladění v rozhraní](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
