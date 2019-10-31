---
title: ICLRRuntimeInfo – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo
helpviewer_keywords:
- ICLRRuntimeInfo interface [.NET Framework hosting]
ms.assetid: 287e5ede-b3a7-4ef8-a756-4fca3f285a82
topic_type:
- apiref
ms.openlocfilehash: f6608b03df80fa37ebf5049b53bce46da3e155e0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120358"
---
# <a name="iclrruntimeinfo-interface"></a>ICLRRuntimeInfo – rozhraní
Poskytuje metody, které vracejí informace o konkrétním modulu CLR (Common Language Runtime), včetně verze, adresáře a stavu zatížení. Toto rozhraní také poskytuje funkcionalitu specifickou pro modul runtime bez inicializace modulu runtime. Zahrnuje metodu [LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) relativní pro modul runtime, metodu [GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) specifickou pro modul runtime a rozhraní poskytovaná modulem runtime prostřednictvím metody [GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) .  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[BindAsLegacyV2Runtime – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md)|Vytvoří vazby tohoto modulu runtime pro všechna starší rozhodnutí zásad aktivace CLR verze 2.|  
|[GetDefaultStartupFlags – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getdefaultstartupflags-method.md)|Získá spouštěcí příznaky CLR a konfigurační soubor hostitele.|  
|[GetInterface – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)|Načte CLR do aktuálního procesu a vrátí ukazatele rozhraní Runtime, jako jsou [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) a [IMetaDataDispenser](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md). Tato metoda nahrazuje všechny funkce `CorBindTo*`.|  
|[GetProcAddress – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md)|Získá adresu zadané funkce, která byla exportována z CLR přidruženého k tomuto rozhraní. Tato metoda nahrazuje metodu [GetRealProcAddress –](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) .|  
|[GetRuntimeDirectory – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md)|Získá instalační adresář modulu CLR přidruženého k tomuto rozhraní. Tato metoda nahrazuje metodu [GetCORSystemDirectory –](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md) .|  
|[GetVersionString – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getversionstring-method.md)|Získá informace o verzi modulu CLR (Common Language Runtime) přidružené k danému rozhraní [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) . Tato metoda nahrazuje metody [GetRequestedRuntimeInfo –](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md) a [GetRequestedRuntimeVersion –](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) .|  
|[IsLoadable – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-isloadable-method.md)|Určuje, zda lze modul runtime spojený s tímto rozhraním načíst do aktuálního procesu, přičemž vezme v úvahu jiné moduly runtime, které mohou být do procesu již načteny.|  
|[IsLoaded – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-isloaded-method.md)|Určuje, zda je modul CLR přidružený k rozhraní [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) načten do procesu.|  
|[IsStarted – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-isstarted-method.md)|Určuje, zda byl spuštěn modul CLR, který je přidružen k [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní.|  
|[LoadErrorString – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loaderrorstring-method.md)|Přeloží hodnotu HRESULT do příslušné chybové zprávy pro zadanou jazykovou verzi. Tato metoda nahrazuje metody [LoadStringRC –](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md) a [LoadStringRCEx –](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md) .|  
|[LoadLibrary – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md)|Načte knihovnu z adresáře rozhraní CLR, reprezentovaného rozhraním [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) . Tato metoda nahrazuje metodu [LoadLibraryShim –](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md) .|  
|[SetDefaultStartupFlags – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md)|Nastaví spouštěcí příznaky CLR a konfigurační soubor hostitele.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MetaHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
