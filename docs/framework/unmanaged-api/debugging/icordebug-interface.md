---
title: ICorDebug – rozhraní
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 05c95d47d57525aa2aebe16d536b771042600000
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54509724"
---
# <a name="icordebug-interface"></a>ICorDebug – rozhraní
Poskytuje metody, které umožňují vývojářům ladit aplikace v prostředí common language runtime (CLR).  
  
> [!NOTE]
>  Ladění ve smíšeném režimu (spravovaný a nativní kód) není podporováno ve Windows 95, Windows 98 nebo Windows ME, nebo na platformách x x86 (například IA64 a AMD64).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CanLaunchOrAttach – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebug-canlaunchorattach-method.md)|Určuje, zda je možné v rámci kontextu aktuální konfiguraci počítače a modul runtime spustí nový proces nebo připojení k daného procesu.|  
|[CreateProcess – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md)|Spustí proces a jeho primární vlákno pod kontrolu ladicího programu.|  
|[DebugActiveProcess – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md)|Připojí ladicí program k existujícímu procesu.|  
|[EnumerateProcesses – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebug-enumerateprocesses-method.md)|Získá enumerátor pro procesy, které jsou právě laděny.|  
|[GetProcess – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebug-getprocess-method.md)|Vrátí objekt "ICorDebugProcess" s ID daného procesu.|  
|[Initialize – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md)|Inicializuje `ICorDebug` objektu.|  
|[SetManagedHandler – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)|Určuje objekt obslužné rutiny události pro spravované události.|  
|[SetUnmanagedHandler – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebug-setunmanagedhandler-method.md)|Určuje objekt obslužné rutiny události pro nespravované události.|  
|[Terminate – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md)|Ukončuje `ICorDebug` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebug` představuje do smyčky zpracování události pro ladicí program procesu. Ladicí program musí čekat [icordebugmanagedcallback::exitprocess –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) zpětného volání ze všech procesů, který se právě ladí před uvolněním toto rozhraní.  
  
 `ICorDebug` Objekt je počáteční objekt řídit všechny další spravované ladění. V rozhraní .NET Framework verze 1.0 a 1.1, byl tento objekt `CoClass` objekt vytvořený z modelu COM. V rozhraní .NET Framework verze 2.0, tento objekt je již `CoClass` objektu. Musí být vytvořeny podle [createdebugginginterfacefromversion –](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) funkce, což je více podporující verze. Tato nová funkce vytváření umožňuje klientům získat konkrétní implementaci `ICorDebug`, což emuluje také konkrétní verzi rozhraní API pro ladění.  
  
> [!NOTE]
>  Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
