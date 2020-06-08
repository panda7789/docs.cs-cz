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
ms.openlocfilehash: bb7c3659930f308328cba121c06a88cb6a95eb26
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504157"
---
# <a name="iclrmetahost-interface"></a>ICLRMetaHost – rozhraní
Poskytuje metody, které vracejí konkrétní verzi modulu CLR (Common Language Runtime) na základě jeho čísla verze, vypíše všechny instalované CLRs, vypíše všechny moduly runtime, které jsou načteny v zadaném procesu, zjistí verzi CLR použitou pro zkompilování sestavení, ukončí proces s čistým vypnutím běhového prostředí a dotazuje se na vazbu staršího rozhraní API.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Description|  
|------------|-----------------|  
|[EnumerateInstalledRuntimes – metoda](iclrmetahost-enumerateinstalledruntimes-method.md)|Vrátí výčet obsahující platný ukazatel rozhraní [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) pro každou verzi CLR, která je nainstalována v počítači.|  
|[EnumerateLoadedRuntimes – metoda](iclrmetahost-enumerateloadedruntimes-method.md)|Vrátí výčet obsahující platný ukazatel rozhraní [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) pro každý modul CLR, který je načten v daném procesu. Tato metoda nahrazuje [GetVersionFromProcess –](getversionfromprocess-function.md).|  
|[ExitProcess – metoda](iclrmetahost-exitprocess-method.md)|Pokusí se řádně vypnout všechny načtené běhové moduly a pak proces ukončí. Nahrazuje funkci [CorExitProcess –](corexitprocess-function.md) .|  
|[GetRuntime – metoda](iclrmetahost-getruntime-method.md)|Získá rozhraní [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) , které odpovídá konkrétní verzi CLR. Tato metoda nahrazuje funkci [CorBindToRuntimeEx –](corbindtoruntimeex-function.md) použitou s příznakem [STARTUP_LOADER_SAFEMODE](startup-flags-enumeration.md) .|  
|[GetVersionFromFile – metoda](iclrmetahost-getversionfromfile-method.md)|Získá původní verzi kompilace sestavení .NET Framework (uloženou v metadatech), která má za následek cestu k souboru. Tato metoda nahrazuje [GetFileVersion –](getfileversion-function.md).|  
|[QueryLegacyV2RuntimeBinding – metoda](iclrmetahost-querylegacyv2runtimebinding-method.md)|Vrátí rozhraní, které představuje modul runtime, ke kterému byly navázány starší Zásady aktivace, například pomocí `useLegacyV2RuntimeActivationPolicy` atributu u položky konfiguračního souboru [ \<startup> elementu](../../configure-apps/file-schema/startup/startup-element.md) , přímým použitím starší verze aktivačních rozhraní API nebo voláním metody [ICLRRuntimeInfo:: bindaslegacyv2runtime –](iclrruntimeinfo-bindaslegacyv2runtime-method.md) .|  
|[RequestRuntimeLoadedNotification – metoda](iclrmetahost-requestruntimeloadednotification-method.md)|Garantuje zpětné volání na zadaný ukazatel na funkci při prvním načtení verze CLR, ale ještě nebyla spuštěna. Tato metoda nahrazuje [LockClrVersion –](lockclrversion-function.md)|  
  
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
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro hostování](hosting-interfaces.md)
- [Hosting](index.md)
