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
ms.openlocfilehash: fe378307ce2bda6e1a267e46433ead70a0e2299e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616515"
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
|[ICorConfiguration – rozhraní](icorconfiguration-interface.md)|Poskytuje metody pro konfiguraci modulu CLR (Common Language Runtime).|  
|[ICorRuntimeHost – rozhraní](icorruntimehost-interface.md)|Poskytuje metody, které umožňují hostiteli explicitně spustit a zastavit modul CLR (Common Language Runtime), vytvořit a nakonfigurovat domény aplikace, získat přístup k výchozí doméně a vytvořit výčet všech domén spuštěných v procesu.|  
|[IDebuggerInfo – rozhraní](idebuggerinfo-interface.md)|Poskytuje metody pro získání informací o stavu služeb ladění.|  
|[IGCHost – rozhraní](igchost-interface.md)|Poskytuje metody pro získání informací o systému uvolňování paměti a pro řízení některých aspektů uvolňování paměti.|  
|IValidator|Poskytuje metody pro ověřování přenosných spustitelných imagí a podrobné hlášení chyb ověřování.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. idl  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Třídy typu coclass hostování](hosting-coclasses.md)
