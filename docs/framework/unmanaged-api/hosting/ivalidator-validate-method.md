---
title: IValidator::Validate – metoda
ms.date: 03/30/2017
api_name:
- IValidator.Validate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Validate
helpviewer_keywords:
- IValidator::Validate method [.NET Framework hosting]
- Validate method, IValidator interface [.NET Framework hosting]
ms.assetid: 7d68666a-fb73-4455-bebd-908d49a16abc
topic_type:
- apiref
ms.openlocfilehash: 8ae47eac713fbee30ea543538957b12460b8e1fc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123273"
---
# <a name="ivalidatorvalidate-method"></a>IValidator::Validate – metoda
Ověří zadaný přenos přenositelného spustitelného souboru (PE) nebo jazyka MSIL (Microsoft Intermediate Language).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Validate (  
    [in] IVEHandler            *veh,  
    [in] IUnknown              *pAppDomain,  
    [in] unsigned long          ulFlags,  
    [in] unsigned long          ulMaxError,  
    [in] unsigned long          token,  
    [in] LPWSTR                 fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long          ulSize  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `veh`  
 pro Ukazatel na instanci `IVEHandler`, která zpracovává chyby ověřování.  
  
 `pAppDomain`  
 pro Ukazatel na doménu aplikace, ve které je soubor načten.  
  
 `ulFlags`  
 pro Bitová kombinace hodnot [ValidatorFlags –](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) , která označuje ověření, která by měla být provedena.  
  
 `ulMaxError`  
 pro Maximální počet chyb, které mají být povoleny před ukončením ověřování.  
  
 `token`  
 pro Nepoužívá se.  
  
 `fileName`  
 pro Řetězec, který určuje název souboru, který má být ověřen.  
  
 `pe`  
 pro Ukazatel na vyrovnávací paměť, ve které je soubor uložený.  
  
 `ulSize`  
 pro Velikost souboru (v bajtech), který má být ověřen.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** IValidator. idl, IValidator. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
