---
title: EClrOperation – výčet
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 01b000ed3d75ddb6a7882cb8f03ff2cec64fb9fe
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767874"
---
# <a name="eclroperation-enumeration"></a>EClrOperation – výčet
Popisuje sadu operací, u které můžete použít hostitele akce zásad.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
|`OPR_AppDomainRudeUnload`|Hostitele můžete určit akce zásad, které mají být provedeny, když <xref:System.AppDomain> uvolnění způsobem řádné (pravidla).|  
|`OPR_AppDomainUnload`|Hostitele můžete určit akce zásad, které mají být provedeny, když <xref:System.AppDomain> je uvolněna.|  
|`OPR_FinalizerRun`|Hostitele můžete určit akce zásad, které mají být provedeny, když spuštění finalizační metody.|  
|`OPR_ProcessExit`|Hostitele můžete určit akce zásad, které mají být provedeny při ukončení procesu.|  
|`OPR_ThreadAbort`|Hostitele můžete určit akce zásad, které mají být provedeny, když je přerušeno vlákno.|  
|`OPR_ThreadRudeAbortInCriticalRegion`|Hostitele můžete určit akce zásad, které mají být provedeny, když dojde k přerušení článku neslušní vlákna v důležité oblasti kódu.|  
|`OPR_ThreadRudeAbortInNonCriticalRegion`|Hostitele můžete určit akce zásad má provést, když dojde k přerušení článku neslušní vlákna v méně důležité oblasti kódu.|  
  
## <a name="remarks"></a>Poznámky  
 Common language runtime (CLR) spolehlivost infrastructure rozlišuje mezi přeruší a prostředků, ke kterým dochází v důležité oblasti kódu a těch, ke kterým dochází v méně důležité oblasti kódu chyby v přidělení. Toto rozlišení je navržena k umožnění hostitelů nastavit různé zásady v závislosti na tom, kde dojde k chybě v kódu.  
  
 A *důležité oblasti kódu* je jakýkoli prostor, kde nemůže zaručit CLR dané přeruší úlohu nebo selhání žádost pro prostředky ovlivní pouze aktuální úloha dokončí. Například pokud úloha drží zámek a přijímá HRESULT označující selhání při vytváření požadavku přidělení paměti, je jednoduše k přerušení tento úkol zajistit stabilitu <xref:System.AppDomain>, protože <xref:System.AppDomain> může obsahovat jiné Čekání na zámek stejné úkoly. Pokud chcete opustit aktuální úloha může způsobit tyto úlohy přestane reagovat. V takovém případě hostitele musí být schopné uvolnit celý <xref:System.AppDomain> místo nestabilitu potenciální riziko.  
  
 A *méně důležité oblasti kódu*, na druhé straně je oblast, ve kterém CLR může zaručit, že přerušení nebo selhání ovlivní pouze úlohy, na kterém dojde k chybě.  
  
 CLR také rozlišuje mezi bezproblémové a jiné řádné přerušení (pravidla). Obecně platí normální nebo řádné přerušení snaží spustit před přerušením úlohy, zatímco hrubé přerušení nezaručuje tyto rutiny zpracování výjimek a finalizační metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [EClrFailure – výčet](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [EPolicyAction – výčet](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [ICLRPolicyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [IHostPolicyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [Výčty pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
