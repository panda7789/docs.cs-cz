---
title: "ICorDebugProcess6::MarkDebuggerAttached – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: bf94f090-5265-4112-8e57-5b4e20e070d0
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f6d219e298e04157ea0670681c7550bd920bd284
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess6markdebuggerattached-method"></a>ICorDebugProcess6::MarkDebuggerAttached – metoda
Změní vnitřní stav debugee tak, aby <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> vrátí metoda v knihovně tříd rozhraní .NET Framework `true`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT MarkDebuggerAttached(  
    BOOL fIsAttached  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fIsAttached`  
 `true`Pokud <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> metoda by měl znamenat, že je připojen ladicí program; `false` jinak.  
  
## <a name="return-value"></a>Návratová hodnota  
 Metoda může vrátit hodnoty uvedené v následující tabulce.  
  
|Návratová hodnota|Popis|  
|------------------|-----------------|  
|`S_OK`|Ladění byla úspěšně aktualizována.|  
|`CORDBG_E_MODULE_NOT_LOADED`|Sestavení, které obsahuje <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> metoda není načten nebo některé jiné chyby, jako je například chybí metadata, znemožňuje ho bude rozpoznán.<br /><br /> Tato chyba je běžné a neškodné. Při spouštění dalších sestavení by měl znovu volejte metodu.|  
|Další selhání `HRESULT` hodnoty.|Ostatní hodnoty pravděpodobně znamenat identifikovala ladicí program nebo kompilátoru součásti.|  
  
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
