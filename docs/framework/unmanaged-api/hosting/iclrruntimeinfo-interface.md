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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c4789d5cad8bbb4f7dc6f5fcedc56be3bf74703b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54520188"
---
# <a name="iclrruntimeinfo-interface"></a>ICLRRuntimeInfo – rozhraní
Poskytuje metody, které vracejí informace o konkrétní CLR (CLR), včetně verze, adresáře a načíst stav. Toto rozhraní také poskytuje funkce specifické pro modul runtime bez inicializace modulu runtime. Zahrnuje modul runtime relativní [LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) metody, modulů runtime [GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) metoda a poskytuje modul runtime rozhraní prostřednictvím [getinterface –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)metody.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[BindAsLegacyV2Runtime – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md)|Vytvoří vazbu tento modul runtime pro všechny starší verze CLR verze 2 aktivace rozhodnutí o zásadách.|  
|[GetDefaultStartupFlags – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getdefaultstartupflags-method.md)|Získá příznaky CLR při spuštění a konfigurační soubor hostitele.|  
|[GetInterface – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)|Načte modul CLR do aktuální proces a vrátí runtime ukazatele rozhraní, jako například [iclrruntimehost –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [iclrstrongname –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) a [imetadatadispenser –](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md). Tato metoda nahrazuje všechny `CorBindTo*` funkce.|  
|[GetProcAddress – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md)|Získá adresu zadané funkce, která byla exportována z CLR přidružený k tomuto rozhraní. Tato metoda nahrazuje [getrealprocaddress –](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) metody.|  
|[GetRuntimeDirectory – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md)|Načte instalační adresář modulu CLR přidružený k tomuto rozhraní. Tato metoda nahrazuje [getcorsystemdirectory –](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md) metody.|  
|[GetVersionString – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getversionstring-method.md)|Získá common language runtime (CLR) informace o verzi přidružené danou [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní. Tato metoda nahrazuje [getrequestedruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md) a [getrequestedruntimeversion –](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) metody.|  
|[IsLoadable – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-isloadable-method.md)|Určuje, zda modul runtime spojený s tímto rozhraním je možné načíst do aktuální proces zohledněním jiné moduly runtime, který může být již načten do procesu.|  
|[IsLoaded – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-isloaded-method.md)|Určuje, zda modul CLR přidružený [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní je načten do procesu.|  
|[IsStarted – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-isstarted-method.md)|Určuje, zda modul CLR, který je přidružen [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní se spustila.|  
|[LoadErrorString – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loaderrorstring-method.md)|Převede hodnotu HRESULT na příslušnou chybovou zprávu pro zadanou jazykovou verzi. Tato metoda nahrazuje [loadstringrc –](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md) a [loadstringrcex –](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md) metody.|  
|[LoadLibrary – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md)|Načte knihovnu z adresáře rozhraní framework CLR reprezentována [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní. Tato metoda nahrazuje [LoadLibraryShim –](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md) metody.|  
|[SetDefaultStartupFlags – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md)|Nastaví konfigurační soubor spuštění příznaky CLR a hostitele.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
