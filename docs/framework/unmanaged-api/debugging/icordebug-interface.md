---
title: "ICorDebug – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebug
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug
helpviewer_keywords:
- ICorDebug interface [.NET Framework debugging]
ms.assetid: 33f431d7-ab1a-494d-8af2-20ab15aba194
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0ed0b3a8b42157f6a4fcbc6b4a05a416da736147
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebug-interface"></a>ICorDebug – rozhraní
Poskytuje metody, které umožňují vývojářům ladit aplikace v běžné prostředí runtime (CLR) jazyk.  
  
> [!NOTE]
>  Ladění ve smíšeném režimu (spravovaná a nativní kód) není podporována v systému Windows 95, Windows 98 nebo Windows ME nebo na jiný x86 platformy (například IA64 a AMD64).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CanLaunchOrAttach – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebug-canlaunchorattach-method.md)|Určuje, zda je možné v rámci aktuální konfiguraci počítače a prostředí runtime spouštění nového procesu nebo připojení do daného procesu.|  
|[CreateProcess – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md)|Spustí se proces a jeho primární vlákno pod kontrolou ladicího programu.|  
|[DebugActiveProcess – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md)|Připojí ladicí program pro existující proces.|  
|[EnumerateProcesses – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebug-enumerateprocesses-method.md)|Získá enumerátor pro procesy, které se právě ladí.|  
|[GetProcess – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebug-getprocess-method.md)|Vrátí objekt "ICorDebugProcess" s ID daného procesu.|  
|[Initialize – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md)|Inicializuje `ICorDebug` objektu.|  
|[SetManagedHandler – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)|Určuje objekt obslužné rutiny události pro spravované události.|  
|[SetUnmanagedHandler – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebug-setunmanagedhandler-method.md)|Určuje objekt obslužné rutiny události pro události se nespravované.|  
|[Terminate – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md)|Ukončí `ICorDebug` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebug`představuje smyčky zpracování událostí pro proces ladicího programu. Ladicí program musí počkat [icordebugmanagedcallback::exitprocess –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) zpětného volání ze všech procesů laděné před uvolněním toto rozhraní.  
  
 `ICorDebug` Objektu je objekt počáteční řídit všechny další spravované ladění. V rozhraní .NET Framework verze 1.0 a 1.1, byl tento objekt `CoClass` objekt vytvořený z modelu COM. V rozhraní .NET Framework verze 2.0, tento objekt je už `CoClass` objektu. Musí být vytvořen pomocí [createdebugginginterfacefromversion –](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) funkci, která je zvýšení povědomí pro verzi. Tato nová funkce vytváření umožňuje klientům získat na konkrétní implementace `ICorDebug`, což emuluje také na konkrétní verzi rozhraní API pro ladění.  
  
> [!NOTE]
>  Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
