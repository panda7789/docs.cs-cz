---
title: ICLRValidator::Validate – metoda
ms.date: 03/30/2017
api_name:
- ICLRValidator.Validate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRValidator::Validate
helpviewer_keywords:
- Validate method, ICLRValidator interface [.NET Framework hosting]
- ICLRValidator::Validate method [.NET Framework hosting]
ms.assetid: 0b1b432a-d234-4002-839b-81366c3a8bdc
topic_type:
- apiref
ms.openlocfilehash: 497a115b980bb58a3906fda68d7ff564efe78089
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127832"
---
# <a name="iclrvalidatorvalidate-method"></a>ICLRValidator::Validate – metoda
Ověří přenosných spustitelných souborů (PE) nebo jazyka MSIL (Microsoft Intermediate Language) v zadaném souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Validate (  
    [in] IVEHandler        *veh,  
    [in] unsigned long      ulAppDomainId,  
    [in] unsigned long      ulFlags,  
    [in] unsigned long      ulMaxError,  
    [in] unsigned long      token,  
    [in] LPWSTR             fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long      ulSize  
);      
```  
  
## <a name="parameters"></a>Parametry  
 `veh`  
 pro Ukazatel na instanci `IVEHandler`, která zpracovává chyby ověřování.  
  
 `ulAppDomainId`  
 pro Identifikátor pro aktuální <xref:System.AppDomain>.  
  
 `ulFlags`  
 pro Kombinace hodnot [ValidatorFlags –](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) , které označují druh ověřování, které se má provést.  
  
 `ulMaxError`  
 pro Maximální počet chyb, které mají být povoleny před ukončením ověřování.  
  
 `token`  
 pro Nepoužívané.  
  
 `fileName`  
 pro Název souboru, který se má ověřit  
  
 `pe`  
 pro Ukazatel na vyrovnávací paměť souboru.  
  
 `ulSize`  
 pro Velikost souboru (v bajtech), který má být ověřen.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`Validate` byla úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** IValidator. idl, IValidator. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRValidator – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
