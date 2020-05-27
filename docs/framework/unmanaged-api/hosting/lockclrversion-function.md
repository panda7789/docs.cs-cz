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
ms.openlocfilehash: 09bcebfdcfea3d5728d404cdb6b5fb170a5432c3
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008492"
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
  
|Návratový kód|Description|  
|-----------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|E_INVALIDARG|Jeden nebo více argumentů má hodnotu null.|  
  
## <a name="remarks"></a>Poznámky  
 Hostitel volá `LockClrVersion` před inicializací modulu CLR. `LockClrVersion`přijímá tři parametry, z nichž všechny jsou zpětná volání typu [FLockClrVersionCallback –](flockclrversioncallback-function-pointer.md). Tento typ je definován následujícím způsobem.  
  
```cpp  
typedef HRESULT ( __stdcall *FLockClrVersionCallback ) ();  
```  
  
 Při inicializaci modulu runtime dojde k následujícím krokům:  
  
1. Hostitel volá [CorBindToRuntimeEx –](corbindtoruntimeex-function.md) nebo jednu z dalších funkcí inicializace modulu runtime. Alternativně může hostitel inicializovat modul runtime pomocí aktivace objektu COM.  
  
2. Modul runtime zavolá funkci určenou `hostCallback` parametrem.  
  
3. Funkce zadaná v `hostCallback` pak provede následující posloupnost volání:  
  
    - Funkce určená `pBeginHostSetup` parametrem.  
  
    - `CorBindToRuntimeEx`(nebo jiná funkce inicializace modulu runtime).  
  
    - [ICLRRuntimeHost:: SetHostControl –](iclrruntimehost-sethostcontrol-method.md).  
  
    - [ICLRRuntimeHost:: Start](iclrruntimehost-start-method.md).  
  
    - Funkce určená `pEndHostSetup` parametrem.  
  
 Všechna volání od `pBeginHostSetup` do `pEndHostSetup` musí být provedena v jednom vlákně nebo vlákně se stejným logickým zásobníkem. Toto vlákno se může lišit od vlákna, na kterém `hostCallback` je volána.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Zastaralé funkce hostování CLR](deprecated-clr-hosting-functions.md)
