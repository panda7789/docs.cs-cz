---
title: "Rozhraní ICorDebugProcess6"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 34a10ac2-882c-4797-8369-f120e8e640c7
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9928018b7d4065fbf24b4c39f7ef2d121e66d7ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess6-interface"></a>Rozhraní ICorDebugProcess6
Logicky rozšiřuje rozhraní ICorDebugProcess k povolení funkcí, jako je například dekódování spravované ladění události, které jsou v událostí výjimek na nativní ladění a rozdělení virtuální modulu kódování.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[DecodeEvent – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md)|Dekóduje spravované ladění události, které byly zapouzdřené v datové části události ladění speciálního nativní výjimky.|  
|[EnableVirtualModuleSplitting – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md)|Povolí nebo zakáže virtuální modulu rozdělení.|  
|[GetCode – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getcode-method.md)|Získá informace o spravovaného kódu na adrese konkrétního kódu.|  
|[GetExportStepInfo – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md)|Obsahuje informace o modulu runtime exportované funkce, které umožňují krok prostřednictvím spravovaného kódu.|  
|[MarkDebuggerAttached – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-markdebuggerattached-method.md)|Změní vnitřní stav debugee tak, aby <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> vrátí metoda v knihovně tříd rozhraní .NET Framework `true`.|  
|[ProcessStateChanged – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md)|Upozorní [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) kterém proces běží.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Rozhraní je k dispozici s .NET Native pouze. Probíhá pokus o volání `QueryInterface` načíst ukazatele rozhraní vrátí `E_NOINTERFACE` pro scénáře ICorDebug mimo .NET Native.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
