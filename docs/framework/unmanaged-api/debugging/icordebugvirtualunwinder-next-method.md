---
title: ICorDebugVirtualUnwinder::Next – metoda
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a4bacbd9ef11f6f6cb6d9952290c00f1b8ce50aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423426"
---
# <a name="icordebugvirtualunwindernext-method"></a>ICorDebugVirtualUnwinder::Next – metoda
Přejde k kontextu volajícího.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Next();  
```  
  
#### <a name="parameters"></a>Parametry  
 Žádné  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK` Pokud došlo k chybě unwind úspěšně, nebo `CORDBG_S_AT_END_OF_STACK` Pokud unwind nemůže být dokončena, protože nejsou k dispozici žádné další rámce.  
  
 Pokud dojde při selhání je vrácen HRESULT ICorDebug rozhraní API vrátí `CORDBG_E_DATA_TARGET_ERROR`.  
  
## <a name="remarks"></a>Poznámky  
 Walkera zásobníku se ujistěte, že umožňuje postup směrem vpřed, takže to nakonec volání `Next` vrátí dojde při selhání HRESULT nebo `CORDBG_S_AT_END_OF_STACK`. Vrácení `S_OK` po neomezenou dobu může způsobit nekonečné smyčce.  
  
> [!NOTE]
>  Tato metoda je k dispozici s .NET Native jenom.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugMemoryBuffer – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
