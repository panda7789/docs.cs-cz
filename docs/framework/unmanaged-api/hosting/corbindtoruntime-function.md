---
title: CorBindToRuntime – funkce
ms.date: 03/30/2017
api_name:
- CorBindToRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntime
helpviewer_keywords:
- CorBindToRuntime function [.NET Framework hosting]
ms.assetid: 799740aa-46ec-4532-95da-6444565b4971
topic_type:
- apiref
ms.openlocfilehash: 2db9d26ef2dec150977c468b16334a7cb4b3d49c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176510"
---
# <a name="corbindtoruntime-function"></a>CorBindToRuntime – funkce
Umožňuje nespravovaným hostitelům načíst běžný jazyk runtime (CLR) do procesu.  
  
 Tato funkce byla v rozhraní .NET Framework 4 zastaralá.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CorBindToRuntime (  
    [in]  LPCWSTR     pwszVersion,
    [in]  LPCWSTR     pwszBuildFlavor,
    [in]  REFCLSID    rclsid,
    [in]  REFIID      riid,
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pwszVersion`  
 [v] Řetězec popisující verzi CLR, kterou chcete načíst.  
  
 Číslo verze v rozhraní .NET Framework se skládá ze čtyř částí oddělených tečkami: *major.minor.build.revision*. Řetězec předán `pwszVersion` jako musí začínat znak "v" následuje první tři části číslo verze (například "v1.0.1529").  
  
 Některé verze clr jsou nainstalovány s prohlášením zásad, které určuje kompatibilitu s předchozími verzemi CLR. Ve výchozím nastavení překrytí `pwszVersion` při spuštění vyhodnocuje příkazy zásad a načte nejnovější verzi běhu, který je kompatibilní s požadovanou verzí. Hostitel může vynutit překrytí přeskočit vyhodnocení zásad a `pwszVersion` načíst přesnou `flags` verzi zadanou v souboru předáním hodnoty parametru, `STARTUP_LOADER_SAFEMODE` jak je popsáno níže.  
  
 Pokud volající určuje hodnotu null pro `pwszVersion`, je načtena nejnovější verze runtime. Předávání null dává hostiteli žádnou kontrolu nad tím, která verze runtime je načtena. Ačkoli tento přístup může být vhodné v některých scénářích, důrazně doporučujeme, aby hostitel dodat konkrétní verzi načíst.  
  
 `pwszBuildFlavor`  
 [v] Řetězec, který určuje, zda má být server nebo sestavení pracovní stanice CLR načíst. Platné hodnoty `svr` `wks`jsou a . Sestavení serveru je optimalizováno tak, aby využívalo více procesorů pro uvolňování paměti, a sestavení pracovní stanice je optimalizováno pro klientské aplikace spuštěné v počítači s jedním procesorem.  
  
 Pokud `pwszBuildFlavor` je nastavena na hodnotu null, sestavení pracovní stanice je načten. Při spuštění na počítači s jedním procesorem je sestavení `pwszBuildFlavor` pracovní `svr`stanice vždy načteno, i když je nastaveno na . Však `pwszBuildFlavor` pokud je `svr` nastavena a souběžné uvolňování paměti `flags` je zadán (viz popis parametru), sestavení serveru je načten.  
  
 `rclsid`  
 [v] Coclass, `CLSID` která implementuje buď [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) nebo [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) rozhraní. Podporované hodnoty jsou CLSID_CorRuntimeHost nebo CLSID_CLRRuntimeHost.  
  
 `riid`  
 [v] Požadované `IID` rozhraní od `rclsid`aplikace . Podporované hodnoty jsou IID_ICorRuntimeHost nebo IID_ICLRRuntimeHost.  
  
 `ppv`  
 [out] Vrácený ukazatel `riid`rozhraní na .  
  
## <a name="remarks"></a>Poznámky  
 Pokud `pwszVersion` určuje verzi runtime, která `CorBindToRuntimeEx` neexistuje, vrátí hodnotu HRESULT CLR_E_SHIM_RUNTIMELOAD.  
  
## <a name="execution-context-and-flow-of-windows-identity"></a>Kontext spuštění a tok identity systému Windows  
 Ve verzi 1 CLR <xref:System.Security.Principal.WindowsIdentity> objekt netokuje přes asynchronní body, jako jsou nová vlákna, fondy vláken nebo zpětná volání časovače. Ve verzi 2.0 CLR <xref:System.Threading.ExecutionContext> objekt zabalí některé informace o aktuálně spuštěném vlákně a nateče přes libovolný asynchronní bod, ale ne přes hranice domény aplikace. Podobně <xref:System.Security.Principal.WindowsIdentity> objekt také toky přes všechny asynchronní bod. Proto aktuální zosobnění ve vlákně, pokud existuje, toky příliš.  
  
 Tok můžete změnit dvěma způsoby:  
  
1. Úpravou <xref:System.Threading.ExecutionContext> nastavení potlačit tok na základě vlákno (viz <xref:System.Threading.ExecutionContext.SuppressFlow%2A> <xref:System.Security.SecurityContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> , a metody).  
  
2. Změnou výchozího režimu procesu na režim <xref:System.Security.Principal.WindowsIdentity> kompatibility verze 1, kde objekt neprobíhá <xref:System.Threading.ExecutionContext> přes žádný asynchronní bod, bez ohledu na nastavení v aktuálním vlákně. Způsob změny výchozího režimu závisí na tom, zda k načtení příkazu CLR načtete spravované spustitelné nebo nespravované hostitelské rozhraní:  
  
    1. U spravovaných spustitelných `enabled` souborů je nutné nastavit atribut [ \<staršího prvku ImpersonationPolicy>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) na `true`.  
  
    2. Pro nespravované hostitelské rozhraní `STARTUP_LEGACY_IMPERSONATION` nastavte příznak `flags` v parametru při volání `CorBindToRuntimeEx` funkce.  
  
     Režim kompatibility verze 1 se vztahuje na celý proces a na všechny aplikační domény v procesu.  
  
## <a name="remarks"></a>Poznámky  
 [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) `CorBindToRuntime` a provést stejnou operaci, ale `CorBindToRuntimeEx` funkce umožňuje nastavit příznaky určit chování CLR.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Soubor MSCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [CorBindToCurrentRuntime – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntimeByCfg – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeEx – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [CorBindToRuntimeHost – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [ICorRuntimeHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [Zastaralé funkce hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
