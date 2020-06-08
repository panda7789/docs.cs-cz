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
ms.openlocfilehash: 4c015d77deb4e6ed3d43074f2903e26b687de84f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493562"
---
# <a name="corbindtocurrentruntime-function"></a>CorBindToCurrentRuntime – funkce
Načte modul CLR (Common Language Runtime) do procesu pomocí informací o verzi uložených v souboru XML. Formát souboru XML je modelován po standardní konfigurační soubor aplikace. Další informace o konfiguračních souborech najdete v tématu [Schéma konfiguračního souboru](../../configure-apps/file-schema/index.md).  
  
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
  
 Verze modulu runtime, která má být načtena, je popsána atributem verze v [\<requiredRuntime>](../../configure-apps/file-schema/startup/requiredruntime-element.md) elementu konfiguračního souboru.  
  
 Pokud není zadána žádná verze nebo pokud `<requiredRuntime>` prvek nelze nalézt, je načtena nejnovější verze CLR, která je nainstalována v počítači.  
  
 `rclsid`  
 pro `CLSID`Třída typu coclass, která implementuje rozhraní [ICorRuntimeHost](icorruntimehost-interface.md) nebo [ICLRRuntimeHost](iclrruntimehost-interface.md) . Podporované hodnoty jsou CLSID_CorRuntimeHost nebo CLSID_CLRRuntimeHost.  
  
 `riid`  
 pro `IID`Rozhraní, které požadujete. Podporované hodnoty jsou IID_ICorRuntimeHost nebo IID_ICLRRuntimeHost.  
  
 `ppv`  
 mimo Vrácený ukazatel rozhraní.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [CorBindToRuntime – funkce](corbindtoruntime-function.md)
- [CorBindToRuntimeByCfg – funkce](corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeEx – funkce](corbindtoruntimeex-function.md)
- [CorBindToRuntimeHost – funkce](corbindtoruntimehost-function.md)
- [ICorRuntimeHost – rozhraní](icorruntimehost-interface.md)
- [Zastaralé funkce hostování CLR](deprecated-clr-hosting-functions.md)
