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
ms.openlocfilehash: e7cb1c2070e760258e548d2f45e3b6ed11e046c4
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616317"
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
|`OPR_AppDomainRudeUnload`|Hostitel může určit akce zásad, které se mají provést, když <xref:System.AppDomain> dojde k uvolnění v neúspěšném (hrubé) způsobu.|  
|`OPR_AppDomainUnload`|Hostitel může určit akce zásad, které mají být provedeny při <xref:System.AppDomain> uvolnění.|  
|`OPR_FinalizerRun`|Hostitel může určit akce zásad, které se mají provést při spuštění finalizační metody.|  
|`OPR_ProcessExit`|Hostitel může určit akce zásad, které mají být provedeny při ukončení procesu.|  
|`OPR_ThreadAbort`|Hostitel může určit akce zásad, které se mají provést při přerušení vlákna.|  
|`OPR_ThreadRudeAbortInCriticalRegion`|Hostitel může určit akce zásad, které mají být provedeny, když dojde k přerušení hrubé vlákna v kritické oblasti kódu.|  
|`OPR_ThreadRudeAbortInNonCriticalRegion`|Hostitel může určit akce zásad, které se mají provést, když dojde k přerušení hrubé vlákna v nekritické oblasti kódu.|  
  
## <a name="remarks"></a>Poznámky  
 Infrastruktura spolehlivosti modulu CLR (Common Language Runtime) rozlišuje mezi přerušeními a selháním přidělení prostředků, ke kterým dochází v kritických oblastech kódu a těch, ke kterým dochází v nekritických oblastech kódu. Toto rozlišení je navrženo tak, aby umožňovalo hostitelům nastavit různé zásady v závislosti na tom, kde v kódu dojde k selhání.  
  
 *Kritická oblast kódu* je jakékoli místo, kde CLR nemůže zaručit, že přerušení úlohy nebo selhání dokončení žádosti o prostředky ovlivní pouze aktuální úlohu. Například pokud úloha drží zámek a obdrží HRESULT, která indikuje selhání při vytváření žádosti o přidělení paměti, není nestačí jednoduše tuto úlohu přerušit, aby se zajistila stabilita <xref:System.AppDomain> , protože <xref:System.AppDomain> může obsahovat další úlohy, které čekají na stejný zámek. Pokud chcete opustit aktuální úlohu, může to způsobit, že tyto další úlohy přestanou reagovat. V takovém případě hostitel potřebuje možnost uvolnit celé <xref:System.AppDomain> místo rizikového potenciálního nestability.  
  
 *Nekritická oblast kódu*na druhé straně je oblast, kde CLR může zaručit, že přerušení nebo selhání ovlivní pouze úlohu, na které dojde k chybě.  
  
 CLR také rozlišuje mezi řádnými a neřádnými (hrubé) přerušeními. Obecně platí, že normální nebo plynulé přerušení umožňuje spustit rutiny zpracování výjimek a finalizační metody před přerušením úlohy, zatímco hrubé přerušení neprovede žádné takové záruky.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [EClrFailure – výčet](eclrfailure-enumeration.md)
- [EPolicyAction – výčet](epolicyaction-enumeration.md)
- [ICLRPolicyManager – rozhraní](iclrpolicymanager-interface.md)
- [IHostPolicyManager – rozhraní](ihostpolicymanager-interface.md)
- [Výčty hostování](hosting-enumerations.md)
