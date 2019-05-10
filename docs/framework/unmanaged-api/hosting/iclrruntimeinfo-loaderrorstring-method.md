---
title: ICLRRuntimeInfo::LoadErrorString – metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.LoadErrorString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::LoadErrorString
helpviewer_keywords:
- ICLRRuntimeInfo::LoadErrorString method [.NET Framework hosting]
- LoadErrorString method [.NET Framework hosting]
ms.assetid: 52c543ab-9ef5-4ee7-b836-c0ffc35cd45b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dd7bdcf891146a15953b7466e0f6dc680495bd5a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64585062"
---
# <a name="iclrruntimeinfoloaderrorstring-method"></a>ICLRRuntimeInfo::LoadErrorString – metoda
Převede hodnotu HRESULT na příslušnou chybovou zprávu pro zadanou jazykovou verzi.  
  
 Tato metoda nahrazuje následující funkce:  
  
- [LoadStringRC](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
  
- [LoadStringRCEx](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT LoadErrorString(  
     [in] UINT iResourceID,  
     [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
     [in, out]  DWORD *pcchBuffer,  
     [in, lcid] LONG iLocaleID);  
```  
  
## <a name="parameters"></a>Parametry  
 `iResourceID`  
 [in] Hodnota HRESULT pro převod.  
  
 `pwzBuffer`  
 [out] Řetězec zprávy přidružené k dané HRESULT.  
  
 `pcchBuffer`  
 [out v] Velikost `pwzbuffer` , aby přetečení vyrovnávací paměti. Pokud `pwzbuffer` má hodnotu null, `pcchBuffer` poskytuje očekávanou velikost `pwzbuffer` povolit předběžné přidělování.  
  
 `iLocaleID`  
 [in] Identifikátor jazykové verze. Pokud chcete použít výchozí jazykovou verzi, je nutné zadat -1.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|E_POINTER|`pcchBuffer` má hodnotu null.|  
|E_INVALIDARG|`pwzBuffer` má hodnotu null.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRRuntimeInfo – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
