---
title: CorRuntimeHost – třída typu coclass
ms.date: 03/30/2017
api_name:
- CorRuntimeHost Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRuntimeHost
helpviewer_keywords:
- CoRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 5833740b-7d67-44b4-865c-b5bf45e291e3
topic_type:
- apiref
ms.openlocfilehash: 512009e053605e2018f1fcbafa422c1a36ddecc1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136910"
---
# <a name="corruntimehost-coclass"></a>CorRuntimeHost – třída typu coclass
Poskytuje rozhraní pro správu aplikací, které jsou spouštěny modulem CLR (Common Language Runtime).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
coclass CorRuntimeHost {  
    [default] interface ICorRuntimeHost;  
    interface IGCHost;  
    interface ICorConfiguration;  
    interface IValidator;  
    interface IDebuggerInfo;  
};  
```  
  
## <a name="interfaces"></a>Rozhraní  
  
|Rozhraní|Popis|  
|---------------|-----------------|  
|[ICorConfiguration – rozhraní](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)|Poskytuje metody pro konfiguraci modulu CLR (Common Language Runtime).|  
|[ICorRuntimeHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)|Poskytuje metody, které umožňují hostiteli explicitně spustit a zastavit modul CLR (Common Language Runtime), vytvořit a nakonfigurovat domény aplikace, získat přístup k výchozí doméně a vytvořit výčet všech domén spuštěných v procesu.|  
|[IDebuggerInfo – rozhraní](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)|Poskytuje metody pro získání informací o stavu služeb ladění.|  
|[IGCHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)|Poskytuje metody pro získání informací o systému uvolňování paměti a pro řízení některých aspektů uvolňování paměti.|  
|IValidator|Poskytuje metody pro ověřování přenosných spustitelných imagí a podrobné hlášení chyb ověřování.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. idl  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Třídy typu coclass pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
