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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e7312a50137ab8a5c066d5e140a1742ee1918b44
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776558"
---
# <a name="iclrmetahostquerylegacyv2runtimebinding-method"></a>ICLRMetaHost::QueryLegacyV2RuntimeBinding – metoda
Vrátí rozhraní, která představuje modul runtime, ke kterému zásady aktivace starší verze byl vázán, například pomocí `useLegacyV2RuntimeActivationPolicy` atribut na [ \<spuštění > element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) položka souboru konfigurace s přímým přístupem pomocí Aktivace starší verze rozhraní API, nebo pomocí volání [iclrruntimeinfo::bindaslegacyv2runtime –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT QueryLegacyV2RuntimeBinding (  
    [in] REFIID riid,  
    [out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a>Parametry  
 `riid`  
 [in] Jediná platná hodnota pro tento parametr je Required.Currently `IID_ICLRRuntimeInfo`.  
  
 `ppUnk`  
 [out] Povinné. Po návratu metody obsahuje ukazatel [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní, které představuje modul runtime, který bylo svázáno se zásady aktivace starší verze.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena a vrátí modulu runtime, která byla vázána na starší verzi Aktivace zásady.|  
|S_FALSE|Metoda byla úspěšně dokončena, ale starší verzi modulu runtime nebyl dosud byl svázán.|  
|E_NOINTERFACE|Metoda najít modul runtime, který je vázán na zásady aktivace starší verze, ale `riid` nepodporuje tento modul runtime.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRMetaHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
