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
ms.openlocfilehash: a20b79dd5eda9c431511cc49e7e3adaa9486b2aa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59155984"
---
# <a name="iclrerrorreportingmanager-interface"></a>ICLRErrorReportingManager – rozhraní
Poskytuje metody, které umožňují hostiteli nakonfigurovat vlastní výpisy pro hlášení chyb.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[BeginCustomDump – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)|Určuje konfiguraci vlastních výpisy pro hlášení chyb.|  
|[EndCustomDump – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md)|Vymaže konfiguraci vlastní zásobníku s výpisem paměti, která byla nastavena v dřívějším volání `BeginCustomDump`.|  
|[GetBucketParametersForCurrentException – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|Získá Watson kbelíku pro aktuální výjimky na volajícím vlákně.|  
  
## <a name="remarks"></a>Poznámky  
 `BeginCustomDump` Metoda nastaví konfiguraci vlastní zásobníku s výpisem paměti. `EndCustomDump` Metoda vymaže výpisu stavu systému configuration vlastní zásobníku a uvolní všechny přidružený stav. By měla být volána po dokončení vlastní s výpisem paměti.  
  
> [!IMPORTANT]
>  Nepodařilo se zavolat `EndCustomDump` způsobí, že k únik paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ECustomDumpItemKind – výčet](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)
- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
