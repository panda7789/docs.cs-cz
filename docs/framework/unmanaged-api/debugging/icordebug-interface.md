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
ms.openlocfilehash: 0ca66f001d04bc86b64e0fe2d1cd37559e4fc633
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785121"
---
# <a name="icordebug-interface"></a>ICorDebug – rozhraní
Poskytuje metody, které umožňují vývojářům ladit aplikace v prostředí modulu CLR (Common Language Runtime).  
  
> [!NOTE]
> Ladění ve smíšeném režimu (spravovaný a nativní kód) není podporováno ve Windows 95, Windows 98 nebo Windows Millennium Edition ani na platformách jiných než x86 (například IA64 a AMD64).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[CanLaunchOrAttach – metoda](icordebug-canlaunchorattach-method.md)|Určuje, zda je možné v kontextu aktuálního počítače a konfigurace modulu runtime spustit nový proces nebo připojení k danému procesu.|  
|[CreateProcess – metoda](icordebug-createprocess-method.md)|Spustí proces a jeho primární vlákno pod ovládacím prvkem ladicího programu.|  
|[DebugActiveProcess – metoda](icordebug-debugactiveprocess-method.md)|Připojí ladicí program k existujícímu procesu.|  
|[EnumerateProcesses – metoda](icordebug-enumerateprocesses-method.md)|Získá enumerátor pro procesy, které jsou laděny.|  
|[GetProcess – metoda](icordebug-getprocess-method.md)|Vrátí objekt "ICorDebugProcess" s daným ID procesu.|  
|[Initialize – metoda](icordebug-initialize-method.md)|Inicializuje objekt `ICorDebug`.|  
|[SetManagedHandler – metoda](icordebug-setmanagedhandler-method.md)|Určuje objekt obslužné rutiny události pro spravované události.|  
|[SetUnmanagedHandler – metoda](icordebug-setunmanagedhandler-method.md)|Určuje objekt obslužné rutiny události pro nespravované události.|  
|[Terminate – metoda](icordebug-terminate-method.md)|Ukončí objekt `ICorDebug`.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebug` představuje smyčku zpracování událostí pro proces ladicího programu. Ladicí program musí počkat na zpětné volání [ICorDebugManagedCallback:: ExitProcess –](icordebugmanagedcallback-exitprocess-method.md) ze všech procesů, které jsou laděny před uvolněním tohoto rozhraní.  
  
 Objekt `ICorDebug` je počáteční objekt pro řízení všech dalších spravovaných ladění. V .NET Framework verzích 1,0 a 1,1 byl tento objekt objektem `CoClass` vytvořeným z modelu COM. V .NET Framework verze 2,0 Tento objekt již není objektem `CoClass`. Musí být vytvořen funkcí [CreateDebuggingInterfaceFromVersion –](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) , což je více zohledňuje verze. Tato nová funkce vytváření umožňuje klientům získat konkrétní implementaci `ICorDebug`, která také emuluje konkrétní verzi rozhraní API pro ladění.  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](debugging-interfaces.md)
