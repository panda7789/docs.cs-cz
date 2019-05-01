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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 480fc27bd41f7ca559ceee379b7f6f81c94da0ba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61989193"
---
# <a name="icordebugdatatarget-interface"></a>ICorDebugDataTarget – rozhraní
Poskytuje rozhraní zpětného volání, které poskytuje přístup ke konkrétnímu cílovému procesu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetPlatform – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)|Poskytuje informace o platformě, včetně architektury procesoru a operačního systému, na kterém je spuštěný Cílový proces.|  
|[ReadVirtual – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-readvirtual-method.md)|Získá blok souvislé paměti začínající na zadané adrese a vrátí jej v poskytnutá vyrovnávací paměť.|  
|[GetThreadContext – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getthreadcontext-method.md)|Požádá o kontext aktuálního vlákna pro zadaný podproces.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugDataTarget` a její metody mají následující vlastnosti:  
  
- Ladění služby volají metody na tomto rozhraní pro přístup k paměti a další data v cílovém procesu.  
  
- Klient ladicího programu musí implementovat toto rozhraní podle potřeby pro konkrétní cíl (například živý proces nebo výpis stavu paměti).  
  
- `ICorDebugDataTarget` Metody lze volat pouze z v rámci metody implementované v ostatních `ICorDebug*` rozhraní. Tím se zajistí, že klient ladicího programu má řídit, přes které vlákno je vyvolána na a kdy.  
  
- `ICorDebugDataTarget` Implementace musí vracet vždycky aktuální informace o cíli.  
  
 Cílový proces by měl být zastaven a nebyl změněn. žádným způsobem při `ICorDebug*` rozhraní (a tedy `ICorDebugDataTarget` metody) jsou volány. Pokud je cílem živý proces a jeho změn stavu [iclrdebugging::openvirtualprocess –](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) musí být znovu volána k poskytnutí instance ICorDebugProcess nahrazení.  
  
> [!NOTE]
>  Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
