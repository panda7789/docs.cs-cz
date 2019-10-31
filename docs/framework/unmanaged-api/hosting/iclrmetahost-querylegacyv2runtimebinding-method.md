---
title: ICLRMetaHost::QueryLegacyV2RuntimeBinding – metoda
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.RequestRuntimeLoadedNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::QueryLegacyV2RuntimeBinding
helpviewer_keywords:
- QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
- ICLRMetaHost::QueryLegacyV2RuntimeBinding method [.NET Framework hosting]
ms.assetid: 9929817e-acc9-40b7-960c-598664e04b60
topic_type:
- apiref
ms.openlocfilehash: 90474a61b16d65565889bd69ef75616804d8bc60
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140879"
---
# <a name="iclrmetahostquerylegacyv2runtimebinding-method"></a>ICLRMetaHost::QueryLegacyV2RuntimeBinding – metoda
Vrátí rozhraní, které představuje modul runtime, ke kterému byly navázány zastaralé Zásady aktivace, například pomocí atributu `useLegacyV2RuntimeActivationPolicy` v položce konfiguračního souboru [\<po spuštění >](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) , a to přímým použitím starších aktivačních rozhraní API nebo voláním metody [ICLRRuntimeInfo:: bindaslegacyv2runtime –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT QueryLegacyV2RuntimeBinding (  
    [in] REFIID riid,  
    [out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a>Parametry  
 `riid`  
 pro Požadováno. v současné době je `IID_ICLRRuntimeInfo`jedinou platnou hodnotou tohoto parametru.  
  
 `ppUnk`  
 mimo Požadovanou. Až tato metoda vrátí, obsahuje ukazatel na rozhraní [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) , které představuje modul runtime, který je svázán se staršími zásadami aktivace.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda se úspěšně dokončila a vrátila modul runtime, který se váže k zásadám aktivace starší verze.|  
|S_FALSE|Metoda se úspěšně dokončila, ale starší verze modulu runtime ještě není vázaná.|  
|E_NOINTERFACE|Metoda našla modul runtime, který byl vázán na starší Zásady aktivace, ale `riid` není tímto modulem runtime podporován.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MetaHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRMetaHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
