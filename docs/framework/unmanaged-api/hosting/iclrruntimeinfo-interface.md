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
ms.openlocfilehash: 71e2c7f6790f29872c051bb5cea50755068057e9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504040"
---
# <a name="iclrruntimeinfo-interface"></a>ICLRRuntimeInfo – rozhraní
Poskytuje metody, které vracejí informace o konkrétním modulu CLR (Common Language Runtime), včetně verze, adresáře a stavu zatížení. Toto rozhraní také poskytuje funkcionalitu specifickou pro modul runtime bez inicializace modulu runtime. Zahrnuje metodu [LoadLibrary](iclrruntimeinfo-loadlibrary-method.md) relativní pro modul runtime, metodu [GetProcAddress](iclrruntimeinfo-getprocaddress-method.md) specifickou pro modul runtime a rozhraní poskytovaná modulem runtime prostřednictvím metody [GetInterface](iclrruntimeinfo-getinterface-method.md) .  
  
## <a name="methods"></a>Metody  
  
|Metoda|Description|  
|------------|-----------------|  
|[BindAsLegacyV2Runtime – metoda](iclrruntimeinfo-bindaslegacyv2runtime-method.md)|Vytvoří vazby tohoto modulu runtime pro všechna starší rozhodnutí zásad aktivace CLR verze 2.|  
|[GetDefaultStartupFlags – metoda](iclrruntimeinfo-getdefaultstartupflags-method.md)|Získá spouštěcí příznaky CLR a konfigurační soubor hostitele.|  
|[GetInterface – metoda](iclrruntimeinfo-getinterface-method.md)|Načte CLR do aktuálního procesu a vrátí ukazatele rozhraní Runtime, jako jsou [ICLRRuntimeHost](iclrruntimehost-interface.md), [ICLRStrongName](iclrstrongname-interface.md) a [IMetaDataDispenser](../metadata/imetadatadispenser-interface.md). Tato metoda nahrazuje všechny `CorBindTo*` funkce.|  
|[GetProcAddress – metoda](iclrruntimeinfo-getprocaddress-method.md)|Získá adresu zadané funkce, která byla exportována z CLR přidruženého k tomuto rozhraní. Tato metoda nahrazuje metodu [GetRealProcAddress –](getrealprocaddress-function.md) .|  
|[GetRuntimeDirectory – metoda](iclrruntimeinfo-getruntimedirectory-method.md)|Získá instalační adresář modulu CLR přidruženého k tomuto rozhraní. Tato metoda nahrazuje metodu [GetCORSystemDirectory –](getcorsystemdirectory-function.md) .|  
|[GetVersionString – metoda](iclrruntimeinfo-getversionstring-method.md)|Získá informace o verzi modulu CLR (Common Language Runtime) přidružené k danému rozhraní [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) . Tato metoda nahrazuje metody [GetRequestedRuntimeInfo –](getrequestedruntimeinfo-function.md) a [GetRequestedRuntimeVersion –](getrequestedruntimeversion-function.md) .|  
|[IsLoadable – metoda](iclrruntimeinfo-isloadable-method.md)|Určuje, zda lze modul runtime spojený s tímto rozhraním načíst do aktuálního procesu, přičemž vezme v úvahu jiné moduly runtime, které mohou být do procesu již načteny.|  
|[IsLoaded – metoda](iclrruntimeinfo-isloaded-method.md)|Určuje, zda je modul CLR přidružený k rozhraní [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) načten do procesu.|  
|[IsStarted – metoda](iclrruntimeinfo-isstarted-method.md)|Určuje, zda byl spuštěn modul CLR, který je přidružen k [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) rozhraní.|  
|[LoadErrorString – metoda](iclrruntimeinfo-loaderrorstring-method.md)|Přeloží hodnotu HRESULT do příslušné chybové zprávy pro zadanou jazykovou verzi. Tato metoda nahrazuje metody [LoadStringRC –](loadstringrc-function.md) a [LoadStringRCEx –](loadstringrcex-function.md) .|  
|[LoadLibrary – metoda](iclrruntimeinfo-loadlibrary-method.md)|Načte knihovnu z adresáře rozhraní CLR, reprezentovaného rozhraním [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) . Tato metoda nahrazuje metodu [LoadLibraryShim –](loadlibraryshim-function.md) .|  
|[SetDefaultStartupFlags – metoda](iclrruntimeinfo-setdefaultstartupflags-method.md)|Nastaví spouštěcí příznaky CLR a konfigurační soubor hostitele.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MetaHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro hostování](hosting-interfaces.md)
- [Hosting](index.md)
