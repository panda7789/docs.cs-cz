---
title: ICLRErrorReportingManager – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager
helpviewer_keywords:
- ICLRErrorReportingManager interface [.NET Framework hosting]
ms.assetid: ea8af0d5-4133-4472-8a1f-50570d7e85fa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bf9e04ed1d3a68fed120c4c13ad992af1f777244
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="iclrerrorreportingmanager-interface"></a>ICLRErrorReportingManager – rozhraní
Poskytuje metody, které umožňují hostiteli nakonfigurovat vlastní zásobník výpisy pro zasílání zpráv o chybách.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[BeginCustomDump – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)|Určuje konfiguraci výpisy zásobníku vlastní pro zasílání zpráv o chybách.|  
|[EndCustomDump – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md)|Vymaže konfiguraci výpisu vlastní zásobníku, která byla nastavena starší voláním `BeginCustomDump`.|  
|[GetBucketParametersForCurrentException – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|Získá Watson sady pro aktuální výjimky na volající vlákno.|  
  
## <a name="remarks"></a>Poznámky  
 `BeginCustomDump` Metoda nastaví vlastní zásobník výpisu konfiguraci. `EndCustomDump` Metoda bude vymazána konfigurace výpisu vlastní zásobníku a uvolní všechny přidružený stav. By měla být volána po dokončení vlastní výpis.  
  
> [!IMPORTANT]
>  Selhání volání `EndCustomDump` způsobí, že k úniku paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ECustomDumpItemKind – výčet](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)  
 [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
