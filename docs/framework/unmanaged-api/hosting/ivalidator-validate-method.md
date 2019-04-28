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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1fba06360a0c31e0a7fa3e61de9793bad14650fa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765294"
---
# <a name="ivalidatorvalidate-method"></a>IValidator::Validate – metoda
Ověří zadaný (PE portable executable) nebo soubor Microsoft intermediate language (MSIL).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 [in] Ukazatel `IVEHandler` instanci, která zpracovává chyby ověření.  
  
 `pAppDomain`  
 [in] Ukazatel aplikační doménu, ve kterém je soubor načten.  
  
 `ulFlags`  
 [in] Bitová kombinace hodnot [validatorflags –](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) hodnoty určující, které by se měla provést ověření.  
  
 `ulMaxError`  
 [in] Maximální počet chyb, aby před ukončením ověření.  
  
 `token`  
 [in] Nepoužívá se.  
  
 `fileName`  
 [in] Řetězec, který určuje název souboru, který má být ověřen.  
  
 `pe`  
 [in] Ukazatel do vyrovnávací paměti, ve kterém je soubor uložený.  
  
 `ulSize`  
 [in] Velikost v bajtech, soubor, který má být ověřen.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** IValidator.idl, IValidator.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
