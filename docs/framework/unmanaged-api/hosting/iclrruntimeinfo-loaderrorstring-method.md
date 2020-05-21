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
ms.openlocfilehash: da6efae38cd70a68feea56b12e86be23fde7f0cb
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762185"
---
# <a name="iclrruntimeinfoloaderrorstring-method"></a>ICLRRuntimeInfo::LoadErrorString – metoda
Přeloží hodnotu HRESULT do příslušné chybové zprávy pro zadanou jazykovou verzi.  
  
 Tato metoda nahrazuje následující funkce:  
  
- [LoadStringRC –](loadstringrc-function.md)  
  
- [LoadStringRCEx –](loadstringrcex-function.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT LoadErrorString(  
     [in] UINT iResourceID,  
     [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
     [in, out]  DWORD *pcchBuffer,  
     [in, lcid] LONG iLocaleID);  
```  
  
## <a name="parameters"></a>Parametry  
 `iResourceID`  
 pro Hodnota HRESULT pro překlad.  
  
 `pwzBuffer`  
 mimo Řetězec zprávy přidružený k danému HRESULT.  
  
 `pcchBuffer`  
 [in, out] Velikost, `pwzbuffer` která se má vyhnout přetečení vyrovnávací paměti. Pokud `pwzbuffer` má hodnotu null, `pcchBuffer` poskytuje očekávanou velikost pro povolení předběžného `pwzbuffer` přidělení.  
  
 `iLocaleID`  
 pro Identifikátor jazykové verze. Chcete-li použít výchozí jazykovou verzi, je nutné zadat-1.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|E_POINTER|`pcchBuffer`má hodnotu null.|  
|E_INVALIDARG|`pwzBuffer`má hodnotu null.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MetaHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRRuntimeInfo – rozhraní](iclrruntimeinfo-interface.md)
- [Rozhraní pro hostování](hosting-interfaces.md)
- [Hostování](index.md)
