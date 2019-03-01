---
title: ICorDebugAppDomain – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain
api_location:
- corguids.lib
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain
helpviewer_keywords:
- ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: be7ae711-1217-4a44-be40-166e29641b77
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db2052bafb259f07370f007f699f6858c532b11d
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973753"
---
# <a name="icordebugappdomain-interface"></a>ICorDebugAppDomain – rozhraní

Poskytuje metody pro ladění domén aplikace. Toto rozhraní je podtřídou třídy icordebugcontroller –.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Attach – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-attach-method.md)|Ladicí program připojí k doméně aplikace.|  
|[EnumerateAssemblies – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|Získá enumerátor pro sestavení v doméně aplikace.|  
|[EnumerateBreakpoints – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratebreakpoints-method.md)|Získá enumerátor pro všechny zarážky aktivní v doméně aplikace.|  
|[EnumerateSteppers – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratesteppers-method.md)|Získá enumerátor pro všechny aktivní prvky krokování v doméně aplikace.|  
|[GetId – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getid-method.md)|Získá jedinečné ID domény aplikace.|  
|[GetModuleFromMetaDataInterface – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getmodulefrommetadatainterface-method.md)|Získá objekt icordebugmodule – rozhraní daná metadata.|  
|[GetName – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getname-method.md)|Získá název domény aplikace.|  
|[GetObject – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getobject-method.md)|Získá ukazatel rozhraní common language runtime (CLR) aplikační doménu.|  
|[GetProcess – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getprocess-method.md)|Získá proces obsahující domény aplikace.|  
|[IsAttached – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-isattached-method.md)|Určuje, zda ladicí program je připojen k doméně aplikace.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
