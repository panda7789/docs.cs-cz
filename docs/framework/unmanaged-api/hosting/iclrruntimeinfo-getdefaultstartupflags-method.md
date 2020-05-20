---
title: ICLRRuntimeInfo::GetDefaultStartupFlags – metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetDefaultStartupFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetDefaultStartupFlags
helpviewer_keywords:
- ICLRRuntimeInfo::GetDefaultStartupFlags method [.NET Framework hosting]
- GetDefaultStartupFlags method [.NET Framework hosting]
ms.assetid: 35c2173e-3b0b-4b2a-950d-e0a01c6df052
topic_type:
- apiref
ms.openlocfilehash: 8513787f48ae89632816face386bbcda20555dac
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703881"
---
# <a name="iclrruntimeinfogetdefaultstartupflags-method"></a>ICLRRuntimeInfo::GetDefaultStartupFlags – metoda
Získá spouštěcí příznaky a konfigurační soubor hostitele, který se použije ke spuštění modulu runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetDefaultStartupFlags(  
     [out]  DWORD *pdwStartupFlags,  
     [out, size_is(*pcchHostConfigFile)] LPWSTR pwzHostConfigFile,  
     [in, out]  DWORD *pcchHostConfigFile);  
```  
  
## <a name="parameters"></a>Parametry  
 `pdwStartupFlags`  
 mimo Ukazatel na příznaky spouštění hostitele, které jsou aktuálně nastaveny.  
  
 `pwzHostConfigFile`  
 mimo Ukazatel na cestu k adresáři aktuálního konfiguračního souboru hostitele.  
  
 `pcchHostConfigFile`  
 [in, out] V případě vstupu velikost `pwzHostConfigFile` , aby nedošlo k přetečení vyrovnávací paměti. Pokud `pwzHostConfigFile` je null, metoda vrátí požadovanou velikost `pwzHostConfigFile` pro předběžné přidělení.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda vrátí výchozí hodnoty příznaků ( `STARTUP_CONCURRENT_GC` a `NULL` ) nebo hodnoty poskytnuté předchozím voláním [metody ICLRRuntimeInfo:: SetDefaultStartupFlags –](iclrruntimeinfo-setdefaultstartupflags-method.md)nebo hodnoty nastavené pomocí kterékoli z `CorBind*` metod, pokud jsou svázány s tímto modulem runtime.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MetaHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRRuntimeInfo – rozhraní](iclrruntimeinfo-interface.md)
- [Rozhraní pro hostování](hosting-interfaces.md)
- [Hostování](index.md)
