---
title: ICLRValidator::FormatEventInfo – metoda
ms.date: 03/30/2017
api_name:
- ICLRValidator.FormatEventInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRValidator::FormatEventInfo
helpviewer_keywords:
- FormatEventInfo method, ICLRValidator interface [.NET Framework hosting]
- ICLRValidator::FormatEventInfo method [.NET Framework hosting]
ms.assetid: 808e1f1d-52f4-47c4-83cc-dcf47d075219
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 40a60bb79c4b1e250ec2d363816d9837c6b51c91
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474199"
---
# <a name="iclrvalidatorformateventinfo-method"></a>ICLRValidator::FormatEventInfo – metoda
Získá podrobnou zprávu o chybě ověření pro zadané.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT FormatEventInfo (  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `hVECode`  
 [in] Hodnota HRESULT, který byl předán obslužná rutina chyb ověření.  
  
 `Context`  
 [in] A `VEContext` instance, která obsahuje kontextové informace o chyby ověření.  
  
 `msg`  
 [out v] Popisná chybová zpráva.  
  
 `ulMaxLength`  
 [in] Maximální délka chybová zpráva.  
  
 `psa`  
 [in] Bezpečné pole další parametry, který se má použít ve zprávě.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`FormatEventInfo` bylo úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající není vlastníkem zámku.|  
|HOST_E_ABANDONED|Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.|  
|E_FAIL|Došlo k neznámé katastrofických selhání. Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu. Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** IValidator.idl, IValidator.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICLRErrorReportingManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
- [ICLRValidator – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)
