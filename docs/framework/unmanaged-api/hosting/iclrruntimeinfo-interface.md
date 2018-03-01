---
title: "ICLRRuntimeInfo – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 11976e8c147b2c5cab2dd67946b561d703028c8a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimeinfo-interface"></a>ICLRRuntimeInfo – rozhraní
Poskytuje metody, které vracejí informace o konkrétní modul common language runtime (CLR), včetně verze, adresář a stavové zatížení. Toto rozhraní také poskytuje funkce specifické pro modul runtime bez inicializace modulu runtime. Zahrnuje modul runtime relativní [LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) metoda, modul runtime modulů [GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md) metoda a zadaný modul runtime rozhraní prostřednictvím [getinterface –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)metoda.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[BindAsLegacyV2Runtime – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md)|Vytvoří vazbu tento modul runtime pro všechny starší verze CLR verze 2 aktivace rozhodnutí o zásadách.|  
|[GetDefaultStartupFlags – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getdefaultstartupflags-method.md)|Získá CLR spuštění příznaky a hostitele konfigurační soubor.|  
|[GetInterface – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)|Načte modul CLR do aktuální proces a vrátí runtime ukazatele rozhraní, jako například [iclrruntimehost –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md), [iclrstrongname –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) a [imetadatadispenser –](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md). Tato metoda nahrazuje všechny `CorBindTo*` funkce.|  
|[GetProcAddress – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md)|Získá adresu určenou funkci, která byla exportována z modulu CLR související s tímto rozhraním. Tato metoda nahrazuje [getrealprocaddress –](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) metoda.|  
|[GetRuntimeDirectory – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md)|Získá instalační adresář modulu CLR související s tímto rozhraním. Tato metoda nahrazuje [getcorsystemdirectory –](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md) metoda.|  
|[GetVersionString – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getversionstring-method.md)|Získá běžné language runtime (CLR) informace o verzi přidružené dané [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní. Tato metoda nahrazuje [getrequestedruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md) a [getrequestedruntimeversion –](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) metody.|  
|[IsLoadable – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-isloadable-method.md)|Určuje, zda modul runtime přidružené toto rozhraní je možné načíst do aktuální proces, vezme v úvahu další moduly runtime, který může být již načtena do procesu.|  
|[IsLoaded – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-isloaded-method.md)|Určuje, zda modul CLR přidružený [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní je načten do procesu.|  
|[IsStarted – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-isstarted-method.md)|Určuje, zda modul CLR, je přidružen [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní byla spuštěna.|  
|[LoadErrorString – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loaderrorstring-method.md)|Změní hodnotu HRESULT na příslušná chybová zpráva pro zadanou jazykovou verzi. Tato metoda nahrazuje [loadstringrc –](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md) a [loadstringrcex –](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md) metody.|  
|[LoadLibrary – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md)|Načte knihovnu z adresáře framework CLR reprezentována [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní. Tato metoda nahrazuje [LoadLibraryShim](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md) metoda.|  
|[SetDefaultStartupFlags – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md)|Nastaví příznaky spuštění CLR a hostitele konfigurační soubor.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
