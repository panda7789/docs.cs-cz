---
title: ICorDebugDataTarget – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget
helpviewer_keywords:
- ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: df5f05be-bed7-4f3c-bc89-dbb435d79a0b
topic_type:
- apiref
ms.openlocfilehash: 9029d53872108bc1953fd22c584b6e01a6f3c7ab
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788859"
---
# <a name="icordebugdatatarget-interface"></a>ICorDebugDataTarget – rozhraní
Poskytuje rozhraní zpětného volání, které poskytuje přístup ke konkrétnímu cílovému procesu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetPlatform – metoda](icordebugdatatarget-getplatform-method.md)|Obsahuje informace o platformě, včetně architektury procesoru a operačního systému, na kterých je spuštěn cílový proces.|  
|[ReadVirtual – metoda](icordebugdatatarget-readvirtual-method.md)|Načte blok souvislé paměti začínající na zadané adrese a vrátí ji do zadané vyrovnávací paměti.|  
|[GetThreadContext – metoda](icordebugdatatarget-getthreadcontext-method.md)|Vyžádá aktuální kontext vlákna pro zadané vlákno.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugDataTarget` a jeho metody mají následující vlastnosti:  
  
- Metody volání služby ladění v tomto rozhraní pro přístup k paměti a dalším datům v cílovém procesu.  
  
- Klient ladicího programu musí implementovat toto rozhraní v závislosti na konkrétním cíli (například při živém procesu nebo výpisu paměti).  
  
- Metody `ICorDebugDataTarget` lze vyvolat pouze v rámci metod implementovaných v jiných rozhraních `ICorDebug*`. Tím je zajištěno, že klient ladicího programu má kontrolu nad tím, ve kterém vlákně je vyvoláno, a kdy.  
  
- Implementace `ICorDebugDataTarget` musí vždycky vracet aktuální informace o cíli.  
  
 Při `ICorDebug*` rozhraních (a proto `ICorDebugDataTarget` metody) by se měl cílový proces zastavit a žádným způsobem beze změny. Pokud je cílem živý proces a jeho změny stavu, metoda [ICLRDebugging:: OpenVirtualProcess –](iclrdebugging-openvirtualprocess-method.md) musí být znovu volána, aby poskytovala náhradní instanci ICorDebugProcess.  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](debugging-interfaces.md)
- [Ladění](index.md)
