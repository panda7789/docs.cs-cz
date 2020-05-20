---
title: CorBindToRuntimeByCfg – funkce
ms.date: 03/30/2017
api_name:
- CorBindToRuntimeByCfg
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeByCfg
helpviewer_keywords:
- CorBindToRuntimeByCfg function [.NET Framework hosting]
ms.assetid: ded1e492-a782-4185-9c66-709e421c1782
topic_type:
- apiref
ms.openlocfilehash: 9326484c6a9f96d245e3c61a0ac3e3465a8a6dcd
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616642"
---
# <a name="corbindtoruntimebycfg-function"></a>CorBindToRuntimeByCfg – funkce
Načte modul CLR (Common Language Runtime) do procesu pomocí informací o verzi načtených ze souboru XML.  
  
 Tato funkce se už nepoužívá v .NET Framework 4.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CorBindToRuntimeByCfg (  
    [in]  IStream     *pCfgStream,  
    [in]  DWORD        reserved,  
    [in]  DWORD        startupFlags,  
    [in]  REFCLSID     rclsid,  
    [in]  REFIID       riid,
    [out] LPVOID FAR*  ppv  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pCfgStream`  
 pro Ukazatel na `IStream` objekt, který čte soubor XML.  
  
 `reserved`  
 pro Vyhrazeno pro budoucí použití. Jako hodnotu použijte 0 (nula).  
  
 `startupFlags`  
 pro Hodnota výčtu [STARTUP_FLAGS](startup-flags-enumeration.md) , která určuje chování při spuštění modulu CLR.  
  
 `rclsid`  
 pro `CLSID`Třída typu coclass, která implementuje rozhraní [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) nebo [ICLRRuntimeHost](iclrruntimehost-interface.md) . Podporované hodnoty jsou CLSID_CorRuntimeHost nebo CLSID_CLRRuntimeHost.  
  
 `riid`  
 pro `IID` `ICorRuntimeHost` `ICLRRuntimeHost` Rozhraní nebo. Podporované hodnoty jsou IID_ICorRuntimeHost nebo IID_ICLRRuntimeHost.  
  
 `ppv`  
 mimo Ukazatel na adresu vráceného rozhraní.  
  
## <a name="remarks"></a>Poznámky  
 Formát souboru XML je modelován po standardní konfigurační soubor aplikace. Další informace o souborech XML najdete v tématu [Schéma konfiguračního souboru](../../configure-apps/file-schema/index.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [CorBindToCurrentRuntime – funkce](corbindtocurrentruntime-function.md)
- [CorBindToRuntime – funkce](corbindtoruntime-function.md)
- [CorBindToRuntimeEx – funkce](corbindtoruntimeex-function.md)
- [CorBindToRuntimeHost – funkce](corbindtoruntimehost-function.md)
- [ICorRuntimeHost – rozhraní](icorruntimehost-interface.md)
- [Zastaralé funkce hostování CLR](deprecated-clr-hosting-functions.md)
