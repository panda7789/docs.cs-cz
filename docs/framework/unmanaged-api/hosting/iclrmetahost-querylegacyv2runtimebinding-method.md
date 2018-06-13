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
ms.openlocfilehash: 1664c47e580730fb0000465f9010e024c64fec2b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432941"
---
# <a name="iclrmetahostquerylegacyv2runtimebinding-method"></a>ICLRMetaHost::QueryLegacyV2RuntimeBinding – metoda
Vrátí rozhraní, které představuje runtime, do které starší verze aktivace zásad byla svázána, například pomocí `useLegacyV2RuntimeActivationPolicy` atributu u [ \<spuštění > element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) souboru položka konfigurace, pomocí přímých Aktivace starší verze rozhraní API nebo voláním [iclrruntimeinfo::bindaslegacyv2runtime –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md) metoda.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT QueryLegacyV2RuntimeBinding (  
    [in] REFIID riid,  
    [out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
#### <a name="parameters"></a>Parametry  
 `riid`  
 [v] Jedinou platnou hodnotou tohoto parametru je Required.Currently `IID_ICLRRuntimeInfo`.  
  
 `ppUnk`  
 [out] Vyžaduje se. Když tato metoda vrací výsledek, obsahuje odkazy [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní, které představuje modul runtime, který bylo svázáno se starší verze aktivace zásad.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní hodnoty HRESULT a také HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena a vrátí modul runtime, který byl spojen starší verze aktivace zásad.|  
|S_FALSE|Metoda byla úspěšně dokončena, ale starší verze modulu runtime nebyl ještě svázány.|  
|E_NOINTERFACE|Metoda nalezena modul runtime, který byl spojen starší verze aktivace zásad, ale `riid` nepodporuje tento modul runtime.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRMetaHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
