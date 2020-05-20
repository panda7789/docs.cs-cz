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
ms.openlocfilehash: dbe4129cf4160a1a9b31bc6f418095ea4b392d57
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616993"
---
# <a name="iclrerrorreportingmanager-interface"></a>ICLRErrorReportingManager – rozhraní
Poskytuje metody, které umožňují hostiteli nakonfigurovat vlastní výpisy zásobníku pro zasílání zpráv o chybách.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[BeginCustomDump – metoda](iclrerrorreportingmanager-begincustomdump-method.md)|Určuje konfiguraci vlastních výpisů paměti zásobníku pro zasílání zpráv o chybách.|  
|[EndCustomDump – metoda](iclrerrorreportingmanager-endcustomdump-method.md)|Vymaže vlastní konfiguraci výpisu zásobníku, která byla nastavena starším voláním `BeginCustomDump` .|  
|[GetBucketParametersForCurrentException – metoda](iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|Získá blok programu Watson pro aktuální výjimku v volajícím vlákně.|  
  
## <a name="remarks"></a>Poznámky  
 `BeginCustomDump`Metoda nastavuje vlastní konfiguraci výpisu zásobníku. `EndCustomDump`Metoda vymaže vlastní konfiguraci výpisu zásobníku a uvolní všechny přidružené stavy. Tato metoda by měla být volána po dokončení vlastního výpisu paměti.  
  
> [!IMPORTANT]
> Selhání volání `EndCustomDump` způsobuje nevrácení paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ECustomDumpItemKind – výčet](ecustomdumpitemkind-enumeration.md)
- [Rozhraní pro hostování](hosting-interfaces.md)
