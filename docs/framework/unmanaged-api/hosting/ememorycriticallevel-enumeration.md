---
title: "EMemoryCriticalLevel – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EMemoryCriticalLevel
api_location: mscoree.dll
api_type: COM
f1_keywords: EMemoryCriticalLevel
helpviewer_keywords: EMemoryCriticalLevel enumeration [.NET Framework hosting]
ms.assetid: 2ca8a7a2-7b54-4ba3-8e73-277c7df485f3
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4fb279402b2b677546f775b9a8badfbe2095fe4f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ememorycriticallevel-enumeration"></a>EMemoryCriticalLevel – výčet
Obsahuje hodnoty, které označují dopad selhání při přidělování konkrétní paměti bylo vyzváno, ale nemůže být splněna.  
  
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
|`eAppDomainCritical`|Označuje, že je velmi důležitá pro provádění spravovaného kódu v doméně, která vyžaduje přidělení přidělení. Pokud nelze přidělit paměť, modul CLR nemůže zaručit, že doména je stále možné použít. Hostitel rozhodne, jaká opatření se mají při přidělování nelze uspokojit. Ho můžete určit, aby CLR k přerušení `AppDomain` automaticky, nebo umožněte její běžet voláním metod v [ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md).|  
|`eProcessCritical`|Označuje, že je důležité pro spuštění spravovaného kódu v procesu přidělení. Tato hodnota se používá během spuštění a při spuštění finalizační metody. Pokud nelze přidělit paměť, modul CLR nemůže pracovat v procesu. V případě selhání přidělení vypnutá efektivně modulu CLR. Všechny následující volání do modulu CLR nezdaří s HOST_E_CLRNOTAVAILABLE.|  
|`eTaskCritical`|Označuje, že je důležité pro spuštění úlohy, která vyžaduje přidělení přidělení. Pokud nelze přidělit paměť, modul CLR nemůže zaručit, že úlohu můžete spustit. V případě selhání, vyvolá modulu CLR <xref:System.Threading.ThreadAbortException> ve vlákně systému fyzické operaci.|  
  
## <a name="remarks"></a>Poznámky  
 Přidělení paměti metody definované v [ihostmemorymanager –](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md) a [ihostmalloc –](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) rozhraní přebírají parametr tohoto typu. V závislosti na závažnosti selhání se hostitel může rozhodnout, zda selhání požadavek na přidělení okamžitě, nebo počkejte, dokud ho už může obsloužit.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRMemoryNotificationCallback – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)  
 [Výčty pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
