---
title: "IValidator::Validate – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IValidator.Validate
api_location: mscoree.dll
api_type: COM
f1_keywords: Validate
helpviewer_keywords:
- IValidator::Validate method [.NET Framework hosting]
- Validate method, IValidator interface [.NET Framework hosting]
ms.assetid: 7d68666a-fb73-4455-bebd-908d49a16abc
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 722c6acc7e152a78ba28bc2730b2fdc7e0c45eb0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ivalidatorvalidate-method"></a>IValidator::Validate – metoda
Ověří zadaný přenosné spustitelný soubor (PE) nebo soubor Microsoft (MSIL intermediate language).  
  
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
  
#### <a name="parameters"></a>Parametry  
 `veh`  
 [v] Ukazatel na `IVEHandler` instanci, která zpracovává chyby ověření.  
  
 `pAppDomain`  
 [v] Ukazatel na doménu aplikace, ve kterém je načíst soubor.  
  
 `ulFlags`  
 [v] Bitovou kombinaci [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) hodnoty, označující objasňuje ověření, která má být provedena.  
  
 `ulMaxError`  
 [v] Maximální počet chyb umožňující před ukončením ověření.  
  
 `token`  
 [v] Nepoužívá se.  
  
 `fileName`  
 [v] Řetězec, který určuje název souboru, který má být ověřen.  
  
 `pe`  
 [v] Ukazatel na vyrovnávací paměť, ve kterém je soubor uložený.  
  
 `ulSize`  
 [v] Velikost v bajtech, soubor, který má být ověřen.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** IValidator.idl, IValidator.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 
