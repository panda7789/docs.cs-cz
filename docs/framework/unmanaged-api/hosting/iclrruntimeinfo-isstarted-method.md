---
title: ICLRRuntimeInfo::IsStarted – metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsStarted
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsStarted
helpviewer_keywords:
- IsStarted method [.NET Framework hosting]
- ICLRRuntimeInfo::IsStarted method [.NET Framework hosting]
ms.assetid: ef6f2662-323b-4534-aa82-6d1afb7b9309
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 45b1ef75227932449b68366345ded33a2cd96490
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479672"
---
# <a name="iclrruntimeinfoisstarted-method"></a>ICLRRuntimeInfo::IsStarted – metoda
Označuje, zda modul runtime byl spuštěn (to znamená, zda [ICLRRuntimeHost::Start – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) byla volána a proběhlo úspěšně).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT IsStarted(  
        [out] BOOL     *pbStarted,  
        [out] DWORD    *pdwStartupFlags);  
```  
  
## <a name="parameters"></a>Parametry  
 `pbStarted`  
 [out] `true` Pokud tento modul runtime je spuštěna; v opačném případě `false`.  
  
 `pdwStartupFlags`  
 [out] Vrátí příznaky, které byly použity při spuštění modulu runtime.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|E_NOTIMPL|Společné jazykové verzi modulu runtime (CLR) je starší než verze CLR [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda funguje pouze s CLR verze starší než verze CLR [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICLRRuntimeInfo – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
