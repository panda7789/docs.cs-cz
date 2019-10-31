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
ms.openlocfilehash: 49a60b6b9b076138d8ff1f8a15041e9a6bacfede
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129245"
---
# <a name="iclrerrorreportingmanager-interface"></a>ICLRErrorReportingManager – rozhraní
Poskytuje metody, které umožňují hostiteli nakonfigurovat vlastní výpisy zásobníku pro zasílání zpráv o chybách.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[BeginCustomDump – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)|Určuje konfiguraci vlastních výpisů paměti zásobníku pro zasílání zpráv o chybách.|  
|[EndCustomDump – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md)|Vymaže vlastní konfiguraci výpisu paměti zásobníku, která byla nastavena starším voláním `BeginCustomDump`.|  
|[GetBucketParametersForCurrentException – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|Získá blok programu Watson pro aktuální výjimku v volajícím vlákně.|  
  
## <a name="remarks"></a>Poznámky  
 Metoda `BeginCustomDump` nastaví vlastní konfiguraci výpisu zásobníku. Metoda `EndCustomDump` vymaže vlastní konfiguraci výpisu zásobníku a uvolní všechny přidružené stavy. Tato metoda by měla být volána po dokončení vlastního výpisu paměti.  
  
> [!IMPORTANT]
> Selhání volání `EndCustomDump` způsobuje nevracení paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ECustomDumpItemKind – výčet](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)
- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
