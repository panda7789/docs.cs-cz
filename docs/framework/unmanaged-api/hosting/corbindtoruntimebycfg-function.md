---
title: "CorBindToRuntimeByCfg – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorBindToRuntimeByCfg
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: CorBindToRuntimeByCfg
helpviewer_keywords: CorBindToRuntimeByCfg function [.NET Framework hosting]
ms.assetid: ded1e492-a782-4185-9c66-709e421c1782
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bbf5a486246d1fb596c08f1510e6d5d89b03df62
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="corbindtoruntimebycfg-function"></a>CorBindToRuntimeByCfg – funkce
Načte modul CLR (CLR) do procesu pomocí informací o verzi, která je pro čtení ze souboru XML.  
  
 Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CorBindToRuntimeByCfg (  
    [in]  IStream     *pCfgStream,  
    [in]  DWORD        reserved,  
    [in]  DWORD        startupFlags,  
    [in]  REFCLSID     rclsid,  
    [in]  REFIID       riid,   
    [out] LPVOID FAR*  ppv  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pCfgStream`  
 [v] Ukazatel na `IStream` objekt, který načte soubor XML.  
  
 `reserved`  
 [v] Vyhrazeno pro budoucí použití. Jako hodnotu, použijte hodnotu 0 (nula).  
  
 `startupFlags`  
 [v] Hodnota [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) výčtu, která určuje chování při spouštění modulu CLR.  
  
 `rclsid`  
 [v] `CLSID` Coclass, který implementuje buď [icorruntimehost –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) nebo [iclrruntimehost –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) rozhraní. Podporované hodnoty jsou CLSID_CorRuntimeHost nebo CLSID_CLRRuntimeHost.  
  
 `riid`  
 [v] `IID` Buď `ICorRuntimeHost` nebo `ICLRRuntimeHost` rozhraní. Podporované hodnoty jsou IID_ICorRuntimeHost nebo IID_ICLRRuntimeHost.  
  
 `ppv`  
 [out] Ukazatel na adresu vrácený rozhraní.  
  
## <a name="remarks"></a>Poznámky  
 Formát souboru XML je Modelováno podle konfiguračního souboru standardní aplikace. Další informace o souborech XML, najdete v části [schéma konfiguračního souboru](../../../../docs/framework/configure-apps/file-schema/index.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Corbindtocurrentruntime – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [Corbindtoruntime – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 [CorBindToRuntimeEx – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [Corbindtoruntimehost – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 [Icorruntimehost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [Zastaralé funkce hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
