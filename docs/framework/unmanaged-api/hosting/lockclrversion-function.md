---
title: LockClrVersion – funkce
ms.date: 03/30/2017
api_name:
- LockClrVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- LockClrVersion
helpviewer_keywords:
- LockClrVersion function [.NET Framework hosting]
ms.assetid: 1318ee37-c43b-40eb-bbe8-88fc46453d74
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f3b263efa95936190ed771e811a84886b11be75b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57465746"
---
# <a name="lockclrversion-function"></a>LockClrVersion – funkce
Umožňuje hostiteli zjistit, která verze modulu common language runtime (CLR) se použije v rámci procesu před explicitní inicializací modulu CLR.  
  
 Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT LockClrVersion (  
    [in] FLockClrVersionCallback   hostCallback,  
    [in] FLockClrVersionCallback  *pBeginHostSetup,  
    [in] FLockClrVersionCallback  *pEndHostSetup  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `hostCallback`  
 [in] Funkce, které jsou volány při inicializaci modulu CLR.  
  
 `pBeginHostSetup`  
 [in] Spouští se funkce má být volána hostitele tak, aby modul CLR informovat, že inicializace.  
  
 `pEndHostSetup`  
 [in] Funkce, která se dřív říkalo hostitelem informovat CLR, že inicializace je dokončena.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací standardní kódy chyb modelu COM, jak je definovaný ve WinError.h, kromě následujících hodnot.  
  
|Návratový kód|Popis|  
|-----------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|E_INVALIDARG|Jeden nebo více parametrů má hodnotu null.|  
  
## <a name="remarks"></a>Poznámky  
 Volání hostitele `LockClrVersion` před inicializací modulu CLR. `LockClrVersion` přijímá tři parametry, které jsou zpětná volání typu [FLockClrVersionCallback](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md). Tento typ je definován následujícím způsobem.  
  
```  
typedef HRESULT ( __stdcall *FLockClrVersionCallback ) ();  
```  
  
 Při inicializaci modulu runtime dojde k následujícím krokům:  
  
1.  Volání hostitele [CorBindToRuntimeEx –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) nebo jeden z jiné funkce inicializace modulu runtime. Alternativně může hostitele inicializovat modul runtime pomocí aktivace objektu COM.  
  
2.  Modul runtime volá funkci určené `hostCallback` parametru.  
  
3.  Funkce určené `hostCallback` pak provede následující posloupnost volání:  
  
    -   Určené funkce `pBeginHostSetup` parametru.  
  
    -   `CorBindToRuntimeEx` (nebo jinou funkci inicializace modulu runtime).  
  
    -   [ICLRRuntimeHost::SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md).  
  
    -   [ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md).  
  
    -   Určené funkce `pEndHostSetup` parametru.  
  
 Všechna volání z `pBeginHostSetup` k `pEndHostSetup` musí vyskytovat na jednoho vlákna nebo vlákénka se stejným zásobníkem logické. Toto vlákno může lišit od vlákna, na kterém `hostCallback` je volána.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [Zastaralé funkce pro hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
