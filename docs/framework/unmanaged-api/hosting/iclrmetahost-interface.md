---
title: ICLRMetaHost – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRMetaHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost
helpviewer_keywords:
- ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: c627fcdd-fc4f-4b1c-8e91-df8536f627d8
topic_type:
- apiref
ms.openlocfilehash: 391adc6f9fe55ad7ca527ea416956ab013a27b15
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703720"
---
# <a name="iclrmetahost-interface"></a>ICLRMetaHost – rozhraní
Poskytuje metody, které vracejí konkrétní verzi modulu CLR (Common Language Runtime) na základě jeho čísla verze, vypíše všechny instalované CLRs, vypíše všechny moduly runtime, které jsou načteny v zadaném procesu, zjistí verzi CLR použitou pro zkompilování sestavení, ukončí proces s čistým vypnutím běhového prostředí a dotazuje se na vazbu staršího rozhraní API.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EnumerateInstalledRuntimes – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateinstalledruntimes-method.md)|Vrátí výčet obsahující platný ukazatel rozhraní [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) pro každou verzi CLR, která je nainstalována v počítači.|  
|[EnumerateLoadedRuntimes – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateloadedruntimes-method.md)|Vrátí výčet obsahující platný ukazatel rozhraní [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) pro každý modul CLR, který je načten v daném procesu. Tato metoda nahrazuje [GetVersionFromProcess –](getversionfromprocess-function.md).|  
|[ExitProcess – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md)|Pokusí se řádně vypnout všechny načtené běhové moduly a pak proces ukončí. Nahrazuje funkci [CorExitProcess –](corexitprocess-function.md) .|  
|[GetRuntime – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md)|Získá rozhraní [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) , které odpovídá konkrétní verzi CLR. Tato metoda nahrazuje funkci [CorBindToRuntimeEx –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) použitou s příznakem [STARTUP_LOADER_SAFEMODE](startup-flags-enumeration.md) .|  
|[GetVersionFromFile – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getversionfromfile-method.md)|Získá původní verzi kompilace sestavení .NET Framework (uloženou v metadatech), která má za následek cestu k souboru. Tato metoda nahrazuje [GetFileVersion –](getfileversion-function.md).|  
|[QueryLegacyV2RuntimeBinding – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-querylegacyv2runtimebinding-method.md)|Vrátí rozhraní, které představuje modul runtime, ke kterému byly navázány starší verze zásad aktivace, například pomocí `useLegacyV2RuntimeActivationPolicy` atributu v položce konfiguračního souboru [ \<> po spuštění](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) , přímým použitím starší verze aktivačních rozhraní API nebo voláním metody [ICLRRuntimeInfo:: bindaslegacyv2runtime –](iclrruntimeinfo-bindaslegacyv2runtime-method.md) .|  
|[RequestRuntimeLoadedNotification – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-requestruntimeloadednotification-method.md)|Garantuje zpětné volání na zadaný ukazatel na funkci při prvním načtení verze CLR, ale ještě nebyla spuštěna. Tato metoda nahrazuje [LockClrVersion –](lockclrversion-function.md)|  
  
## <a name="remarks"></a>Poznámky  
 Jediným způsobem, jak získat instanci tohoto rozhraní, je volání funkce [CLRCreateInstance –](clrcreateinstance-function.md) následujícím způsobem:  
  
```cpp  
ICLRMetaHost *pMetaHost = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHost,  
                   IID_ICLRMetaHost, (LPVOID*)&pMetaHost);  
```  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MetaHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Rozhraní pro hostování](hosting-interfaces.md)
- [Hostování](index.md)
