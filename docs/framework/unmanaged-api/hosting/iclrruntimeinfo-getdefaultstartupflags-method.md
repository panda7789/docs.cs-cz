---
title: "ICLRRuntimeInfo::GetDefaultStartupFlags – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.GetDefaultStartupFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::GetDefaultStartupFlags
helpviewer_keywords:
- ICLRRuntimeInfo::GetDefaultStartupFlags method [.NET Framework hosting]
- GetDefaultStartupFlags method [.NET Framework hosting]
ms.assetid: 35c2173e-3b0b-4b2a-950d-e0a01c6df052
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8b278a791c7e5418322a80bc6478f75791a35af8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimeinfogetdefaultstartupflags-method"></a>ICLRRuntimeInfo::GetDefaultStartupFlags – metoda
Získá spuštění příznaky a hostitele konfigurační soubor, který se použije ke spuštění modulu runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetDefaultStartupFlags(  
     [out]  DWORD *pdwStartupFlags,  
     [out, size_is(*pcchHostConfigFile)] LPWSTR pwzHostConfigFile,  
     [in, out]  DWORD *pcchHostConfigFile);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdwStartupFlags`  
 [out] Ukazatel na příznaky spuštění hostitele, které jsou aktuálně nastavené.  
  
 `pwzHostConfigFile`  
 [out] Ukazatel na cestu k adresáři aktuálního konfiguračního souboru hostitele.  
  
 `pcchHostConfigFile`  
 [ve out] Na vstupu velikost `pwzHostConfigFile`, aby se zabránilo přetečení vyrovnávací paměti. Pokud `pwzHostConfigFile` je null, vrátí metoda požadovaná velikost `pwzHostConfigFile` pro předběžné přidělení.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní HRESULT a také HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vrátí příznak výchozí hodnoty (`STARTUP_CONCURRENT_GC` a `NULL`), nebo hodnoty od předchozího volání [iclrruntimeinfo::setdefaultstartupflags – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md), nebo s hodnotami nastavenými v některé z `CorBind*` metody, pokud je vázána na tento modul runtime.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICLRRuntimeInfo – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
