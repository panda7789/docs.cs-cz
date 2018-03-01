---
title: "EClrOperation – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- EClrOperation
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrOperation
helpviewer_keywords:
- EClrOperation enumeration [.NET Framework hosting]
ms.assetid: 5aef6808-5aac-4b2f-a2c7-fee1575c55ed
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 343ff04dba1a02660734beb726f9b895370a10af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="eclroperation-enumeration"></a>EClrOperation – výčet
Popisuje sadu operací, pro které můžete použít hostitele akce zásad.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
    OPR_ThreadAbort,  
    OPR_ThreadRudeAbortInNonCriticalRegion,  
    OPR_ThreadRudeAbortInCriticalRegion,  
    OPR_AppDomainUnload,  
    OPR_AppDomainRudeUnload,  
    OPR_ProcessExit,  
    OPR_FinalizerRun  
} EClrOperation;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`OPR_AppDomainRudeUnload`|Hostitele můžete určit zásady akce, které mají být provedeny, když <xref:System.AppDomain> je odpojeno způsobem řádně (článku neslušní).|  
|`OPR_AppDomainUnload`|Hostitele můžete určit zásady akce, které mají být provedeny, když <xref:System.AppDomain> je odpojen.|  
|`OPR_FinalizerRun`|Hostitele můžete zadat zásady akce prováděné při spuštění finalizační metody.|  
|`OPR_ProcessExit`|Hostitele můžete určit zásady akce, které mají být provedeny, když proces bude ukončen.|  
|`OPR_ThreadAbort`|Hostitele můžete určit zásady akce, které mají být provedeny, když byl přerušen vlákna.|  
|`OPR_ThreadRudeAbortInCriticalRegion`|Hostitele můžete určit zásady akce, které mají být provedeny, když dojde k přerušení článku neslušní vláken v kritické oblasti kódu.|  
|`OPR_ThreadRudeAbortInNonCriticalRegion`|Hostitele můžete určit zásady akce provést, když dojde k přerušení článku neslušní vláken v méně důležité oblasti kódu.|  
  
## <a name="remarks"></a>Poznámky  
 Common language runtime (CLR) spolehlivost infrastructure rozlišuje mezi přerušení a prostředků, ke kterým došlo v kritické oblastech kódu a soubory, ke kterým došlo v oblasti nekritické kódu chyby v přidělení. Tento rozdíl je navržena k umožnění hostitelů nastavit různé zásady v závislosti na tom, kde dojde k chybě v kódu.  
  
 A *kód důležité oblasti* je veškeré místo, kde modulu CLR nemůže zaručit, že přerušení úlohu nebo nedaří dokončit žádost o pro prostředky ovlivní pouze aktuální úlohy. Například pokud úloha je zámek a dostane HRESULT označující selhání při vytváření požadavku přidělení paměti, je nedostatečné jednoduše na tento úkol zajistit stabilitu zrušení <xref:System.AppDomain>, protože <xref:System.AppDomain> může obsahovat jiné Čekání na zámek stejné úlohy. Ukončil aktuální úloha může způsobit, že ty dalších úloh přestane reagovat (nebo zablokování) po neomezenou dobu. V takovém případě musí hostitel znát schopnost uvolnit celý <xref:System.AppDomain> místo nestabilitu potenciální riziko.  
  
 A *nekritické kód oblasti*, na druhé straně je oblast, kde modulu CLR může zaručit, že přerušení nebo selhání ovlivní pouze úlohy, při kterém dojde k chybě.  
  
 Modul CLR také rozlišuje řádně a řádně přerušení (článku neslušní). Obecně platí normální nebo řádně přerušení neustále snaží spustit rutiny zpracování výjimek a finalizační metody před ukončením úlohy, zatímco článku neslušní přerušení díky žádné záruky.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [EClrFailure – výčet](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)  
 [EPolicyAction – výčet](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)  
 [ICLRPolicyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 [IHostPolicyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 [Výčty pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
