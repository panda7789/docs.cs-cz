---
title: GetRequestedRuntimeVersion – funkce
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeVersion
helpviewer_keywords:
- GetRequestedRuntimeVersion function [.NET Framework hosting]
ms.assetid: 82f596a4-483d-4509-b0c5-a84c53c3da1b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 977f63b58ccbc709fb9383acf64686fc92808da4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="getrequestedruntimeversion-function"></a>GetRequestedRuntimeVersion – funkce
Získá číslo verze common language runtime (CLR) potřebný pro zadanou aplikaci. Pokud není nainstalovaná této verze, získá nejnovější verzi, který se nainstaloval před požadovanou verzi.  
  
 Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetRequestedRuntimeVersion (  
    [in]  LPWSTR  pExe,   
    [out] LPWSTR  pVersion,   
    [in]  DWORD   cchBuffer,   
    [out] DWORD  *pdwLength  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pExe`  
 [v] Název aplikace.  
  
 `pVersion`  
 [out] Vyrovnávací paměť, která obsahuje řetězec číslo verze po úspěšném dokončení.  
  
 `cchBuffer`  
 [v] Délka vyrovnávací paměti verze.  
  
 `pdwLength`  
 [out] Ukazatel na délku řetězce číslo verze.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí standardní kódy chyb modelu COM (Component Object), jak jsou definovány v WinError.h, kromě následující hodnoty.  
  
|Návratový kód|Popis|  
|-----------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|ERROR_INSUFFICIENT_BUFFER|Verze vyrovnávací paměť není dostatečně velký pro uložení řetězec verze.|  
|E_POINTER|`pdwLength` má hodnotu null.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [GetRequestedRuntimeInfo – funkce](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
 [GetVersionFromProcess – funkce](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)  
 [Zastaralé funkce pro hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
