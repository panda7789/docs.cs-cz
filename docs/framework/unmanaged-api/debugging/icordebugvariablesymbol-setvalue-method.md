---
title: ICorDebugVariableSymbol::SetValue – metoda
ms.date: 03/30/2017
ms.assetid: 4609418d-71fa-44bc-9618-4d529d25cabb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1ccdb78e522cb037821135c52bf762707f7de76c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422354"
---
# <a name="icordebugvariablesymbolsetvalue-method"></a>ICorDebugVariableSymbol::SetValue – metoda
Proměnné přiřazuje hodnoty bajtové pole.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetValue(  
   [in] ULONG32 offset,  
   [in] DWORD threadID,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [in, size_is(cbValue)] BYTE pValue[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `offset`  
 [v] Počáteční odsazení v proměnné, pro kterou chcete nastavit hodnotu. Tento parametr je použit při zápisu do pole člena v objektu.  
  
 `threadID`  
 [v] Identifikátor vlákno vlákna, jehož kontext musí být aktualizovány tak, aby odrážely novou hodnotu.  
  
 `cbContext`  
 [v] Velikost v bajtech kontextu přístup z více vláken.  
  
 `context`  
 [v] Vlákno kontext, který používá pro zápis hodnoty.  
  
 `cbValue`  
 [v] Velikost v bajtech `pValue` vyrovnávací paměti.  
  
 `pValue`  
 [v] Vyrovnávací paměť, která obsahuje hodnotu pro nastavení.  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Tato metoda je k dispozici s .NET Native jenom.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugVariableSymbol – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
