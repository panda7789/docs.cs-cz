---
title: EMemoryCriticalLevel – výčet
ms.date: 03/30/2017
api_name:
- EMemoryCriticalLevel
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EMemoryCriticalLevel
helpviewer_keywords:
- EMemoryCriticalLevel enumeration [.NET Framework hosting]
ms.assetid: 2ca8a7a2-7b54-4ba3-8e73-277c7df485f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: def1c04064cc9fc98c108dcdad5c017c0c8e465b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54655527"
---
# <a name="ememorycriticallevel-enumeration"></a>EMemoryCriticalLevel – výčet
Obsahuje hodnoty, které označují dopad selhání při přidělování paměti konkrétní se požaduje, ale není možné spokojeni.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
    eTaskCritical      = 0,  
    eAppDomainCritical = 1,  
    eProcessCritical   = 2  
} EMemoryCriticalLevel;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`eAppDomainCritical`|Označuje, že je velmi důležité pro spuštění spravovaného kódu v doméně, která vyžaduje přidělování přidělení. Pokud nelze přidělit paměť, modul CLR nemůže zaručit, že doménu je stále možné použít. Hostitele Určuje, jaká akce se má provést při přidělení nedokáže splnit. To můžete dát pokyn modulu CLR pro přerušení `AppDomain` automaticky, nebo povolíte jeho běžela voláním metod na [iclrpolicymanager –](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).|  
|`eProcessCritical`|Označuje, že přidělování je zásadní pro spuštění spravovaného kódu v procesu. Tato hodnota se používá během spouštění a při spuštění finalizační metody. Pokud nelze přidělit paměť, modul CLR nelze použít v procesu. Selhání přidělení paměti CLR efektivně zakázána. Všechny následné volání do CLR selhat s HOST_E_CLRNOTAVAILABLE.|  
|`eTaskCritical`|Označuje, že je důležité pro spuštění úlohy, která vyžaduje přidělování přidělení. Pokud nelze přidělit paměť, CLR nemůže zaručit, že mohou být provedeny úlohy. V případě selhání, vydá modul CLR <xref:System.Threading.ThreadAbortException> ve vlákně systému fyzických operace.|  
  
## <a name="remarks"></a>Poznámky  
 Metody přidělení paměti definované v [ihostmemorymanager –](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md) a [ihostmalloc –](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) rozhraní měl parametr tohoto typu. V závislosti na závažnosti k chybě, hostitele můžete rozhodnout, zda požadavek na přidělení selhala okamžitě, nebo počkejte, dokud je možné splnit.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICLRMemoryNotificationCallback – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
- [Výčty pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
