---
title: ICLRRuntimeHost – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost
helpviewer_keywords:
- ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: cb0c5f65-3791-47bc-b833-2f84f4101ba5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0f159c0b57f2087b608fac8cbc9b9c64ceb063a1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965994"
---
# <a name="iclrruntimehost-interface"></a>ICLRRuntimeHost – rozhraní
Poskytuje podobné funkce jako rozhraní [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) , které je k dispozici ve .NET Framework verze 1, s následujícími změnami:  
  
- Přidání metody [SetHostControl –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md) k nastavení rozhraní pro řízení hostitele.  
  
- Vynechání některých metod, které `ICorRuntimeHost`poskytuje.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ExecuteApplication – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md)|Používá se ve scénářích nasazení ClickOnce založených na manifestech k určení aplikace, která se má aktivovat v nové doméně.|  
|[ExecuteInAppDomain – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeinappdomain-method.md)|Určuje, <xref:System.AppDomain> ve kterém se má spustit zadaný spravovaný kód.|  
|[ExecuteInDefaultAppDomain – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeindefaultappdomain-method.md)|Vyvolá zadanou metodu zadaného typu v zadaném sestavení.|  
|[GetCLRControl – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getclrcontrol-method.md)|Načte ukazatel rozhraní typu [ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) , který můžou hostitelé použít k přizpůsobení aspektů modulu CLR (Common Language Runtime).|  
|[GetCurrentAppDomainId – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)|Získá číselný identifikátor <xref:System.AppDomain> aktuálně prováděného.|  
|[SetHostControl – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)|Nastaví rozhraní pro řízení hostitele. Před voláním `SetHostControl` `Start`je nutné zavolat.|  
|[Start – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)|Inicializuje modul CLR do procesu.|  
|[Stop – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-stop-method.md)|Zastaví provádění kódu modulem runtime.|  
|[UnloadAppDomain – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-unloadappdomain-method.md)|Uvolní <xref:System.AppDomain> , který odpovídá zadanému číselnému identifikátoru.|  
  
## <a name="remarks"></a>Poznámky  
 Počínaje .NET Framework 4 použijte rozhraní [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md) k získání ukazatele na rozhraní [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) a pak zavolejte metodu [ICLRRuntimeInfo:: GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) , abyste získali ukazatel na `ICLRRuntimeHost`. V dřívějších verzích .NET Framework hostitel získá ukazatel na `ICLRRuntimeHost` instanci voláním [CorBindToRuntimeEx –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) nebo [CorBindToCurrentRuntime –](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md). Chcete-li zajistit implementace libovolné technologie, které jsou součástí .NET Framework verze 2,0, je nutné použít `ICLRRuntimeHost` `ICorRuntimeHost`místo.  
  
> [!IMPORTANT]
> Nevolejte metodu [Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) před voláním metody [ExecuteApplication –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md) pro aktivaci aplikace založené na manifestu. `ExecuteApplication` Pokud je `Start` metoda volána jako první, volání metody se nezdaří.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlaviček** MSCorEE. h  
  
 **Knihovna** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [CorBindToCurrentRuntime – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntimeEx – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [ICLRControl – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICorRuntimeHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [CLRRuntimeHost – třída typu coclass](../../../../docs/framework/unmanaged-api/hosting/clrruntimehost-coclass.md)
