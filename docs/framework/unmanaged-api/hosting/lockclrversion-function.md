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
ms.openlocfilehash: 6956d73be0380baef96d94584f007e0683331784
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="lockclrversion-function"></a>LockClrVersion – funkce
Umožňuje na hostiteli a určit, která verze common language runtime (CLR) se použije v procesu před explicitně inicializace modulu CLR.  
  
 Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT LockClrVersion (  
    [in] FLockClrVersionCallback   hostCallback,  
    [in] FLockClrVersionCallback  *pBeginHostSetup,  
    [in] FLockClrVersionCallback  *pEndHostSetup  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `hostCallback`  
 [v] Funkce, která má být volána při inicializaci modulu CLR.  
  
 `pBeginHostSetup`  
 [v] Funkce, která má být voláno hostitelem k informování modulu CLR této inicializace se spouští.  
  
 `pEndHostSetup`  
 [v] Funkce, která má být voláno hostitelem k informování modulu CLR této inicializace je dokončena.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí standardní kódy chyb COM, jak jsou definovány v WinError.h, kromě následující hodnoty.  
  
|Návratový kód|Popis|  
|-----------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|E_INVALIDARG|Jeden nebo více parametrů má hodnotu null.|  
  
## <a name="remarks"></a>Poznámky  
 Volání hostitele `LockClrVersion` před inicializace modulu CLR. `LockClrVersion` přijímá tři parametry, které jsou zpětná volání typu [FLockClrVersionCallback](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md). Tento typ je definován následujícím způsobem.  
  
```  
typedef HRESULT ( __stdcall *FLockClrVersionCallback ) ();  
```  
  
 Při inicializaci modulu runtime dojít k následující kroky:  
  
1.  Volání hostitele [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) nebo jednoho z dalších funkcí inicializace modulu runtime. Alternativně hostitele může provést inicializaci modulu runtime použijte aktivace objektu COM.  
  
2.  Modul runtime volá funkci určeného `hostCallback` parametr.  
  
3.  Funkce určeného `hostCallback` pak provede následující pořadí volání:  
  
    -   Funkce určeného `pBeginHostSetup` parametr.  
  
    -   `CorBindToRuntimeEx` (nebo jinou funkci inicializace modulu runtime).  
  
    -   [Iclrruntimehost::sethostcontrol –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md).  
  
    -   [Iclrruntimehost::Start –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md).  
  
    -   Funkce určeného `pEndHostSetup` parametr.  
  
 Všechna volání z `pBeginHostSetup` k `pEndHostSetup` musí dojít k na jedno vlákno nebo fiber se stejným zásobníkem logické. Tento přístup z více vláken se může lišit od vlákno němž `hostCallback` je volána.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Zastaralé funkce pro hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
