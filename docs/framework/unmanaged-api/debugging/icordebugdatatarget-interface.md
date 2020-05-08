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
ms.openlocfilehash: 54272dd18a12715bab58ec1b1a4c1dc00e4bf12b
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976522"
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
 `ICorDebugDataTarget`a jeho metody mají následující vlastnosti:  
  
- Metody volání služby ladění v tomto rozhraní pro přístup k paměti a dalším datům v cílovém procesu.  
  
- Klient ladicího programu musí implementovat toto rozhraní v závislosti na konkrétním cíli (například při živém procesu nebo výpisu paměti).  
  
- `ICorDebugDataTarget` Metody lze vyvolat pouze v rámci metod implementovaných v jiných `ICorDebug*` rozhraních. Tím je zajištěno, že klient ladicího programu má kontrolu nad tím, ve kterém vlákně je vyvoláno, a kdy.  
  
- `ICorDebugDataTarget` Implementace musí vždycky vracet aktuální informace o cíli.  
  
 Při `ICorDebug*` volání rozhraní (a tudíž `ICorDebugDataTarget` metod) by se měl cílový proces zastavit a nijak beze změny. Pokud je cílem živý proces a jeho změny stavu, metoda [ICLRDebugging:: OpenVirtualProcess –](iclrdebugging-openvirtualprocess-method.md) musí být znovu volána, aby poskytovala náhradní instanci ICorDebugProcess.  
  
> [!NOTE]
> Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Debugging – rozhraní](debugging-interfaces.md)
- [Ladění](index.md)
