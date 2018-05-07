---
title: CorBindToCurrentRuntime – funkce
ms.date: 03/30/2017
api_name:
- CorBindToCurrentRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- HeaderDef
f1_keywords:
- CorBindToCurrentRuntime
helpviewer_keywords:
- CorBindToCurrentRuntime function [.NET Framework hosting]
ms.assetid: 6105c13e-d9cd-44d2-a95a-924e042830c7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3667ac5a19664507b767ee6c5421a5e93f6cdfe0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="corbindtocurrentruntime-function"></a>CorBindToCurrentRuntime – funkce
Načte modul CLR (CLR) do procesu pomocí verze informace uložené v souboru XML. Formát souboru XML je Modelováno podle konfiguračního souboru standardní aplikace. Další informace o konfiguračních souborech najdete v tématu [schéma konfiguračního souboru](../../../../docs/framework/configure-apps/file-schema/index.md).  
  
 Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. V tématu [načítání modul Common Language Runtime do procesu](http://msdn.microsoft.com/library/1e2d6dc1-6aab-43e2-bbc0-aae40756d24f).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CorBindToCurrentRuntime (  
    [in]  LPCWSTR   pwszFileName,  
    [in]  REFCLSID  rclsid,  
    [in]  REFIID    riid,  
    [out] LPVOID    *ppv  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pwszFileName`  
 [v] Název konfiguračního souboru aplikace, který určuje verzi modulu CLR načíst. Pokud název souboru není úplná, předpokládá se, že se ve stejném adresáři jako spustitelný soubor, a to voláním.  
  
 Verze runtime, který má být načten je popsán atribut verze v [ \<requiredRuntime >](../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) element konfiguračního souboru.  
  
 Pokud není určená verze, nebo pokud `<requiredRuntime>` element nebyl nalezen, je-li načíst nejnovější verzi modulu CLR, který je nainstalován na počítači.  
  
 `rclsid`  
 [v] `CLSID` Coclass, který implementuje buď [icorruntimehost –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) nebo [iclrruntimehost –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) rozhraní. Podporované hodnoty jsou CLSID_CorRuntimeHost nebo CLSID_CLRRuntimeHost.  
  
 `riid`  
 [v] `IID` Rozhraní jste požádali. Podporované hodnoty jsou IID_ICorRuntimeHost nebo IID_ICLRRuntimeHost.  
  
 `ppv`  
 [out] Ukazatel vrácený rozhraní.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [CorBindToRuntime – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 [CorBindToRuntimeByCfg – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 [CorBindToRuntimeEx – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [CorBindToRuntimeHost – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 [ICorRuntimeHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [Zastaralé funkce pro hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
