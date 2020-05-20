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
ms.openlocfilehash: dd1aa4089a981d82ae1403189343694a065a701d
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703660"
---
# <a name="iclrruntimehost-interface"></a>ICLRRuntimeHost – rozhraní
Poskytuje podobné funkce jako rozhraní [ICorRuntimeHost](icorruntimehost-interface.md) , které je k dispozici ve .NET Framework verze 1, s následujícími změnami:  
  
- Přidání metody [SetHostControl –](iclrruntimehost-sethostcontrol-method.md) k nastavení rozhraní pro řízení hostitele.  
  
- Vynechání některých metod, které poskytuje `ICorRuntimeHost` .  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ExecuteApplication – metoda](iclrruntimehost-executeapplication-method.md)|Používá se ve scénářích nasazení ClickOnce založených na manifestech k určení aplikace, která se má aktivovat v nové doméně.|  
|[ExecuteInAppDomain – metoda](iclrruntimehost-executeinappdomain-method.md)|Určuje, <xref:System.AppDomain> ve kterém se má spustit zadaný spravovaný kód.|  
|[ExecuteInDefaultAppDomain – metoda](iclrruntimehost-executeindefaultappdomain-method.md)|Vyvolá zadanou metodu zadaného typu v zadaném sestavení.|  
|[GetCLRControl – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getclrcontrol-method.md)|Načte ukazatel rozhraní typu [ICLRControl](iclrcontrol-interface.md) , který můžou hostitelé použít k přizpůsobení aspektů modulu CLR (Common Language Runtime).|  
|[GetCurrentAppDomainId – metoda](iclrruntimehost-getcurrentappdomainid-method.md)|Získá číselný identifikátor <xref:System.AppDomain> aktuálně prováděného.|  
|[SetHostControl – metoda](iclrruntimehost-sethostcontrol-method.md)|Nastaví rozhraní pro řízení hostitele. `SetHostControl`Před voláním je nutné zavolat `Start` .|  
|[Start – metoda](iclrruntimehost-start-method.md)|Inicializuje modul CLR do procesu.|  
|[Stop – metoda](iclrruntimehost-stop-method.md)|Zastaví provádění kódu modulem runtime.|  
|[UnloadAppDomain – metoda](iclrruntimehost-unloadappdomain-method.md)|Uvolní <xref:System.AppDomain> , který odpovídá zadanému číselnému identifikátoru.|  
  
## <a name="remarks"></a>Poznámky  
 Počínaje .NET Framework 4 použijte rozhraní [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md) k získání ukazatele na rozhraní [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) a pak zavolejte metodu [ICLRRuntimeInfo:: GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) , abyste získali ukazatel na `ICLRRuntimeHost` . V dřívějších verzích .NET Framework hostitel získá ukazatel na `ICLRRuntimeHost` instanci voláním [CorBindToRuntimeEx –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) nebo [CorBindToCurrentRuntime –](corbindtocurrentruntime-function.md). Chcete-li zajistit implementace libovolné technologie, které jsou součástí .NET Framework verze 2,0, je nutné použít `ICLRRuntimeHost` místo `ICorRuntimeHost` .  
  
> [!IMPORTANT]
> Nevolejte metodu [Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) před voláním metody [ExecuteApplication –](iclrruntimehost-executeapplication-method.md) pro aktivaci aplikace založené na manifestu. Pokud `Start` je metoda volána jako první, `ExecuteApplication` volání metody se nezdaří.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [CorBindToCurrentRuntime – funkce](corbindtocurrentruntime-function.md)
- [CorBindToRuntimeEx – funkce](corbindtoruntimeex-function.md)
- [ICLRControl – rozhraní](iclrcontrol-interface.md)
- [ICorRuntimeHost – rozhraní](icorruntimehost-interface.md)
- [Rozhraní pro hostování](hosting-interfaces.md)
- [CLRRuntimeHost – třída typu coclass](clrruntimehost-coclass.md)
