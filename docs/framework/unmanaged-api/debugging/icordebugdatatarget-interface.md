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
ms.openlocfilehash: 972c650e0fb3b42e943838b72faf2658f65543ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugdatatarget-interface"></a>ICorDebugDataTarget – rozhraní
Poskytuje rozhraní zpětného volání, které poskytuje přístup ke konkrétnímu cílovému procesu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetPlatform – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)|Poskytuje informace o platformě, včetně architekturu procesoru a operačního systému, na kterém je tento cílový proces běží.|  
|[ReadVirtual – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-readvirtual-method.md)|Získá blok souvislé paměti začínající na zadanou adresu a vrátí ji v poskytnutá vyrovnávací paměť.|  
|[GetThreadContext – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getthreadcontext-method.md)|Požádá o aktuálním kontextu vláken pro zadaný vlákno.|  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugDataTarget` a její metody mají následující vlastnosti:  
  
-   Ladění služeb volat metody pro toto rozhraní pro přístup k paměti a další data v tento cílový proces.  
  
-   Ladicí program klienta musí implementovat toto rozhraní podle potřeby pro konkrétní cíl (například za provozu procesu nebo výpis stavu paměti).  
  
-   `ICorDebugDataTarget` Metody lze uplatnit pouze z v rámci metody implementované v jiných `ICorDebug*` rozhraní. Tím se zajistí, aby ladicí program klienta má kontrolu nad přes které vlákno vyvolání na a kdy.  
  
-   `ICorDebugDataTarget` Implementace musí vracet vždy aktuální informace o cíli.  
  
 Tento Cílový proces by měl být zastaven a nebyl změněn. žádným způsobem při `ICorDebug*` rozhraní (a proto `ICorDebugDataTarget` metody) jsou volána. Pokud je cílový proces za provozu a její změny stavu [iclrdebugging::openvirtualprocess –](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) metoda má být volána znovu k zadejte instanci ICorDebugProcess nahrazení.  
  
> [!NOTE]
>  Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
