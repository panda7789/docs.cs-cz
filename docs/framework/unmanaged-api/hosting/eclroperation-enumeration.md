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
ms.openlocfilehash: 6becc44b061ff2baac63437b6a72375d1c3735b2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131166"
---
# <a name="eclroperation-enumeration"></a>EClrOperation – výčet
Popisuje sadu operací, pro které může hostitel použít akce zásad.  
  
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
|`OPR_AppDomainRudeUnload`|Hostitel může určit akce zásad, které se mají provést, když se <xref:System.AppDomain> uvolní způsobem, který nefunguje (hrubé).|  
|`OPR_AppDomainUnload`|Hostitel může určit akce zásad, které se mají provést, když se <xref:System.AppDomain> uvolní.|  
|`OPR_FinalizerRun`|Hostitel může určit akce zásad, které se mají provést při spuštění finalizační metody.|  
|`OPR_ProcessExit`|Hostitel může určit akce zásad, které mají být provedeny při ukončení procesu.|  
|`OPR_ThreadAbort`|Hostitel může určit akce zásad, které se mají provést při přerušení vlákna.|  
|`OPR_ThreadRudeAbortInCriticalRegion`|Hostitel může určit akce zásad, které mají být provedeny, když dojde k přerušení hrubé vlákna v kritické oblasti kódu.|  
|`OPR_ThreadRudeAbortInNonCriticalRegion`|Hostitel může určit akce zásad, které se mají provést, když dojde k přerušení hrubé vlákna v nekritické oblasti kódu.|  
  
## <a name="remarks"></a>Poznámky  
 Infrastruktura spolehlivosti modulu CLR (Common Language Runtime) rozlišuje mezi přerušeními a selháním přidělení prostředků, ke kterým dochází v kritických oblastech kódu a těch, ke kterým dochází v nekritických oblastech kódu. Toto rozlišení je navrženo tak, aby umožňovalo hostitelům nastavit různé zásady v závislosti na tom, kde v kódu dojde k selhání.  
  
 *Kritická oblast kódu* je jakékoli místo, kde CLR nemůže zaručit, že přerušení úlohy nebo selhání dokončení žádosti o prostředky ovlivní pouze aktuální úlohu. Například pokud úloha drží zámek a obdrží HRESULT, která indikuje selhání při vytváření žádosti o přidělení paměti, není nestačí jednoduše tuto úlohu přerušit, aby se zajistila stabilita <xref:System.AppDomain>, protože <xref:System.AppDomain> by mohla obsahovat další úlohy. čeká se na stejný zámek. Pokud chcete opustit aktuální úlohu, může to způsobit, že tyto další úlohy přestanou reagovat. V takovém případě hostitel potřebuje možnost uvolnit celé <xref:System.AppDomain> místo rizika nestability potenciálního potenciálu.  
  
 *Nekritická oblast kódu*na druhé straně je oblast, kde CLR může zaručit, že přerušení nebo selhání ovlivní pouze úlohu, na které dojde k chybě.  
  
 CLR také rozlišuje mezi řádnými a neřádnými (hrubé) přerušeními. Obecně platí, že normální nebo plynulé přerušení umožňuje spustit rutiny zpracování výjimek a finalizační metody před přerušením úlohy, zatímco hrubé přerušení neprovede žádné takové záruky.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [EClrFailure – výčet](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [EPolicyAction – výčet](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [ICLRPolicyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
- [IHostPolicyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)
- [Výčty pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
