---
title: "ICLRRuntimeHost – rozhraní"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 247c50eb88f3b1814fd5342ded4ed3c98d4b60a6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimehost-interface"></a>ICLRRuntimeHost – rozhraní
Poskytuje funkce, které jsou podobné jako [icorruntimehost –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) rozhraní, které jsou uvedeny v rozhraní .NET Framework verze 1, s následujícími změnami:  
  
-   Přidání [sethostcontrol –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md) metodu a nastavit rozhraní Řízení hostitele.  
  
-   Vynechání některé metody poskytované `ICorRuntimeHost`.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ExecuteApplication – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md)|Používá ve scénářích nasazení na základě manifest ClickOnce pro zadání aplikací, které chcete aktivovat. v nové doméně.|  
|[ExecuteInAppDomain – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeinappdomain-method.md)|Určuje <xref:System.AppDomain> ve kterém se má provést zadanou spravovaného kódu.|  
|[ExecuteInDefaultAppDomain – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeindefaultappdomain-method.md)|Vyvolá zadanou metodu zadaného typu v zadaném sestavení.|  
|[GetCLRControl – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getclrcontrol-method.md)|Získá ukazatele rozhraní typu [iclrcontrol –](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) , hostitelů můžete přizpůsobit aspekty common language runtime (CLR).|  
|[GetCurrentAppDomainId – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)|Získá identifikátor číselné <xref:System.AppDomain> , právě probíhá.|  
|[SetHostControl – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)|Nastaví rozhraní Řízení hostitele. Je třeba volat `SetHostControl` před voláním `Start`.|  
|[Start – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)|Inicializuje modulu CLR do procesu.|  
|[Stop – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-stop-method.md)|Ukončí provádění kódu modulem runtime.|  
|[UnloadAppDomain – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-unloadappdomain-method.md)|Uvolní <xref:System.AppDomain> , který odpovídá zadané identifikační číslo.|  
  
## <a name="remarks"></a>Poznámky  
 Počínaje [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], použijte [iclrmetahost –](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md) rozhraní získání ukazatele na [iclrruntimeinfo –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) rozhraní a pak zavolají [iclrruntimeinfo::getinterface –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) Metoda získání ukazatele na `ICLRRuntimeHost`. V dřívějších verzích rozhraní .NET Framework hostitele získá ukazatel na `ICLRRuntimeHost` instance voláním [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) nebo [corbindtocurrentruntime –](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md). Chcete-li poskytovat implementace některé technologie, které jsou uvedeny v rozhraní .NET Framework verze 2.0, je nutné použít `ICLRRuntimeHost` místo `ICorRuntimeHost`.  
  
> [!IMPORTANT]
>  Nevolejte [spustit](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) metoda před voláním [executeapplication –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md) metoda aktivace na základě manifest aplikace. Pokud `Start` metoda je volána nejprve `ExecuteApplication` volání metody, které se nezdaří.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [CorBindToCurrentRuntime – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [CorBindToRuntimeEx – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [ICLRControl – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [ICorRuntimeHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [CLRRuntimeHost – třída typu coclass](../../../../docs/framework/unmanaged-api/hosting/clrruntimehost-coclass.md)
