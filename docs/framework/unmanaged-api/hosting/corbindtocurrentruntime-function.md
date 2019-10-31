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
ms.openlocfilehash: 77a0a8f58c11673a1958d837b4c3a21a05754c94
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138322"
---
# <a name="corbindtocurrentruntime-function"></a>CorBindToCurrentRuntime – funkce
Načte modul CLR (Common Language Runtime) do procesu pomocí informací o verzi uložených v souboru XML. Formát souboru XML je modelován po standardní konfigurační soubor aplikace. Další informace o konfiguračních souborech najdete v tématu [Schéma konfiguračního souboru](../../../../docs/framework/configure-apps/file-schema/index.md).  
  
 Tato funkce se už nepoužívá v .NET Framework 4. Viz [načtení modulu CLR (Common Language Runtime) do procesu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/01918c6x(v=vs.100)).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CorBindToCurrentRuntime (  
    [in]  LPCWSTR   pwszFileName,  
    [in]  REFCLSID  rclsid,  
    [in]  REFIID    riid,  
    [out] LPVOID    *ppv  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pwszFileName`  
 pro Název konfiguračního souboru aplikace, který určuje verzi modulu CLR, která má být načtena. Pokud název souboru není plně kvalifikovaný, předpokládá se, že se nachází ve stejném adresáři jako spustitelný soubor, který volání provádí.  
  
 Verze modulu runtime, která má být načtena, je popsána atributem verze v [\<requiredRuntime >](../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) elementu konfiguračního souboru.  
  
 Pokud není zadána žádná verze nebo pokud `<requiredRuntime>` element nebyl nalezen, je načtena nejnovější verze CLR, která je nainstalována v počítači.  
  
 `rclsid`  
 pro `CLSID` třídy coclass, která implementuje rozhraní [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) nebo [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) . Podporované hodnoty jsou CLSID_CorRuntimeHost nebo CLSID_CLRRuntimeHost.  
  
 `riid`  
 pro `IID` rozhraní, které požadujete. Podporované hodnoty jsou IID_ICorRuntimeHost nebo IID_ICLRRuntimeHost.  
  
 `ppv`  
 mimo Vrácený ukazatel rozhraní.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [CorBindToRuntime – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [CorBindToRuntimeByCfg – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeEx – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [CorBindToRuntimeHost – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [ICorRuntimeHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [Zastaralé funkce pro hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
