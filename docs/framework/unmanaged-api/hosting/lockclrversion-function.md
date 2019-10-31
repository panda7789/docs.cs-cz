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
ms.openlocfilehash: 216852f8f051440b2814619b843a1f25013e4042
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133775"
---
# <a name="lockclrversion-function"></a>LockClrVersion – funkce
Umožňuje hostiteli určit, která verze modulu CLR (Common Language Runtime) bude použita v rámci procesu před explicitní inicializací modulu CLR.  
  
 Tato funkce se už nepoužívá v .NET Framework 4.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT LockClrVersion (  
    [in] FLockClrVersionCallback   hostCallback,  
    [in] FLockClrVersionCallback  *pBeginHostSetup,  
    [in] FLockClrVersionCallback  *pEndHostSetup  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `hostCallback`  
 pro Funkce, která má být volána modulem CLR při inicializaci.  
  
 `pBeginHostSetup`  
 pro Funkce, která má být volána hostitelem pro informování modulu CLR, který spouští inicializaci.  
  
 `pEndHostSetup`  
 pro Funkce, která má být volána hostitelem pro informování CLR o dokončení inicializace.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací standardní chybové kódy modelu COM, jak jsou definovány v WinError. h, kromě následujících hodnot.  
  
|Návratový kód|Popis|  
|-----------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|E_INVALIDARG|Jeden nebo více argumentů má hodnotu null.|  
  
## <a name="remarks"></a>Poznámky  
 Hostitel volá `LockClrVersion` před inicializací modulu CLR. `LockClrVersion` používá tři parametry, z nichž všechny jsou zpětná volání typu [FLockClrVersionCallback –](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md). Tento typ je definován následujícím způsobem.  
  
```cpp  
typedef HRESULT ( __stdcall *FLockClrVersionCallback ) ();  
```  
  
 Při inicializaci modulu runtime dojde k následujícím krokům:  
  
1. Hostitel volá [CorBindToRuntimeEx –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) nebo jednu z dalších funkcí inicializace modulu runtime. Alternativně může hostitel inicializovat modul runtime pomocí aktivace objektu COM.  
  
2. Modul runtime zavolá funkci určenou parametrem `hostCallback`.  
  
3. Funkce určená `hostCallback` pak provede následující posloupnost volání:  
  
    - Funkce určená parametrem `pBeginHostSetup`.  
  
    - `CorBindToRuntimeEx` (nebo jiná funkce inicializace modulu runtime).  
  
    - [ICLRRuntimeHost:: SetHostControl –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md).  
  
    - [ICLRRuntimeHost:: Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md).  
  
    - Funkce určená parametrem `pEndHostSetup`.  
  
 Všechna volání z `pBeginHostSetup` k `pEndHostSetup` musí nastat v jednom vlákně nebo vlákně se stejným logickým zásobníkem. Toto vlákno se může lišit od vlákna, na kterém je volána `hostCallback`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Zastaralé funkce pro hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
