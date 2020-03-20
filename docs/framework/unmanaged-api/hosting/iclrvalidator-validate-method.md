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
ms.openlocfilehash: 427895ffea94e6c657d775ebdeb8571070a61c6e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178065"
---
# <a name="iclrvalidatorvalidate-method"></a>ICLRValidator::Validate – metoda
Ověří přenosný spustitelný soubor (PE) nebo zprostředkující jazyk společnosti Microsoft (MSIL) v zadaném souboru.  
  
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
 [v] Ukazatel na `IVEHandler` instanci, která zpracovává chyby ověření.  
  
 `ulAppDomainId`  
 [v] Identifikátor pro aktuální <xref:System.AppDomain>.  
  
 `ulFlags`  
 [v] Kombinace hodnot [ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md) označující druh ověření, který by měl být proveden.  
  
 `ulMaxError`  
 [v] Maximální počet chyb, které mají být povoleny před ukončením ověření.  
  
 `token`  
 [v] Nepoužité.  
  
 `fileName`  
 [v] Název souboru, který má být ověřen.  
  
 `pe`  
 [v] Ukazatel na vyrovnávací paměť souboru.  
  
 `ulSize`  
 [v] Velikost souboru, který má být ověřen, v bajtech.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`Validate`úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Běžný jazyk runtime (CLR) nebyl načten do procesu nebo CLR je ve stavu, ve kterém nelze spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Časový čas hovoru byl vypován.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena, zatímco na ní čekalo blokované vlákno nebo vlákno.|  
|E_fail|Došlo k neznámému katastrofickému selhání. Když metoda vrátí E_FAIL CLR již není použitelný v rámci procesu. Následná volání metod hostování vrátí HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** IValidator.idl, IValidator.h  
  
 **Knihovna:** Zahrnuto jako prostředek v souboru MSCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRValidator – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
