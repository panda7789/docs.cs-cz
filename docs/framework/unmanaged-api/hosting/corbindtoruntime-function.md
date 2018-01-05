---
title: "CorBindToRuntime – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorBindToRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: CorBindToRuntime
helpviewer_keywords: CorBindToRuntime function [.NET Framework hosting]
ms.assetid: 799740aa-46ec-4532-95da-6444565b4971
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6e6ce976961eedaa58ad265a133c15b2f27a8985
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corbindtoruntime-function"></a>CorBindToRuntime – funkce
Umožňuje nespravované hostitelé načíst modul CLR (CLR) do procesu.  
  
 Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CorBindToRuntime (  
    [in]  LPCWSTR     pwszVersion,   
    [in]  LPCWSTR     pwszBuildFlavor,   
    [in]  REFCLSID    rclsid,   
    [in]  REFIID      riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pwszVersion`  
 [v] Řetězec popisující verzi modulu CLR, které se má zatížení.  
  
 Číslo verze v rozhraní .NET Framework se skládá ze čtyř částí, které jsou odděleny tečkami: *major.minor.build.revision*. Řetězec předány jako `pwszVersion` musí začínat znak "v" následované první tři části číslo verze (například "v1.0.1529").  
  
 Některé verze modulu CLR jsou nainstalovány s prohlášení o zásadách, která určuje kompatibility s předchozími verzemi modulu CLR. Ve výchozím nastavení, vyhodnotí shim spuštění `pwszVersion` proti příkazy zásad a zatížením nejnovější verzi modulu runtime, je kompatibilní s požadovanou verzí. Hostitel může vynutit shim přeskočit vyhodnocení zásad a načíst přesné verze zadaná v `pwszVersion` předáním hodnotu `STARTUP_LOADER_SAFEMODE` pro `flags` parametr, jak je popsáno níže.  
  
 Pokud má volající Určuje hodnotu null pro `pwszVersion`, je-li načíst nejnovější verzi modulu runtime. Předání hodnotou null dává hostitele žádnou kontrolu nad niž je načíst verzi modulu runtime. I když tento přístup může být vhodné v některých scénářích, důrazně doporučujeme, aby hostitel zadat konkrétní verzi načíst.  
  
 `pwszBuildFlavor`  
 [v] Řetězec, který určuje, jestli zatížení serveru nebo pracovní stanice sestavení CLR. Platné hodnoty jsou `svr` a `wks`. Sestavení serveru je optimalizovaná tak, aby využít výhod více procesorů pro kolekce a sestavení pracovní stanici je optimalizovaná pro klientské aplikace spuštěné na počítač s jedním procesorem.  
  
 Pokud `pwszBuildFlavor` je nastaven na hodnotu null, je načíst sestavení pracovní stanice. Při spuštění na počítač s jedním procesorem, je vždy načteno sestavení pracovní stanice, i když `pwszBuildFlavor` je nastaven na `svr`. Ale pokud `pwszBuildFlavor` je nastaven na `svr` a je zadána souběžné uvolňování (naleznete v popisu `flags` parametr), je načíst sestavení serveru.  
  
 `rclsid`  
 [v] `CLSID` Coclass, který implementuje buď [icorruntimehost –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) nebo [iclrruntimehost –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) rozhraní. Podporované hodnoty jsou CLSID_CorRuntimeHost nebo CLSID_CLRRuntimeHost.  
  
 `riid`  
 [v] `IID` Požadované rozhraní z `rclsid`. Podporované hodnoty jsou IID_ICorRuntimeHost nebo IID_ICLRRuntimeHost.  
  
 `ppv`  
 [out] Vrácený rozhraní ukazatel na `riid`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud `pwszVersion` Určuje verzi modulu runtime, který ještě neexistuje, `CorBindToRuntimeEx` vrátí hodnotu HRESULT CLR_E_SHIM_RUNTIMELOAD.  
  
## <a name="execution-context-and-flow-of-windows-identity"></a>Kontext spuštění a toku identitu systému Windows  
 Ve verzi modulu CLR, 1 <xref:System.Security.Principal.WindowsIdentity> objekt nepostupuje napříč asynchronní bodů například Nová vlákna, fondy vláken nebo zpětná volání časovače. Ve verzi 2.0 modulu CLR <xref:System.Threading.ExecutionContext> objekt zabalí některé informace o aktuálně spuštěném vlákno a jeho toků mezi kdykoli asynchronní, ale není napříč hranicemi domény aplikace. Podobně <xref:System.Security.Principal.WindowsIdentity> objekt také přeteče kdykoli asynchronní. Proto aktuální zosobnění na vlákno, pokud existuje, toky příliš.  
  
 Chcete-li změnit toku dvěma způsoby:  
  
1.  Změnou <xref:System.Threading.ExecutionContext> nastavení potlačit toku na základě vlákna (najdete v článku <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, a <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> metody).  
  
2.  Změnou výchozí režim proces na režim kompatibility verze 1, kde <xref:System.Security.Principal.WindowsIdentity> bez ohledu na to není tok objektů mezi kdykoli asynchronní <xref:System.Threading.ExecutionContext> nastavení na aktuální vlákno. Jak změnit výchozí režim, závisí na ať už používáte spravované spustitelný soubor nebo nespravované rozhraní hostingu načíst modul CLR:  
  
    1.  Pro spravované spustitelné soubory, je potřeba nastavit `enabled` atribut [ \<legacyimpersonationpolicy – >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element `true`.  
  
    2.  Nespravované rozhraní hostování, nastavit `STARTUP_LEGACY_IMPERSONATION` příznak v `flags` parametr při volání metody `CorBindToRuntimeEx` funkce.  
  
     Režim kompatibility verze 1 platí pro celý proces a všechny domény aplikace v procesu.  
  
## <a name="remarks"></a>Poznámky  
 [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) a `CorBindToRuntime` provádět stejné operace, ale `CorBindToRuntimeEx` funkce vám umožní nastavit příznaky určit způsob chování modulu CLR.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [CorBindToCurrentRuntime – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [CorBindToRuntimeByCfg – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 [CorBindToRuntimeEx – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [CorBindToRuntimeHost – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 [ICorRuntimeHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [Zastaralé funkce pro hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
