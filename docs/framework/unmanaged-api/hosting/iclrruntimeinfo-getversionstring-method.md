---
title: ICLRRuntimeInfo::GetVersionString – metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetVersionString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetVersionString
helpviewer_keywords:
- ICLRRuntimeInfo::GetVersionString method [.NET Framework hosting]
- GetVersionString method, ICLRRuntimeInfo interface [.NET Framework hosting]
ms.assetid: 98b097ef-2276-4dd9-8551-b03c972e8179
topic_type:
- apiref
ms.openlocfilehash: ccf48b6aea25bd602b55727c2e5958811702f6bf
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762575"
---
# <a name="iclrruntimeinfogetversionstring-method"></a>ICLRRuntimeInfo::GetVersionString – metoda
Získá informace o verzi modulu CLR (Common Language Runtime) přidružené k danému rozhraní [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) .  
  
 Tato metoda nahrazuje následující funkce:  
  
- [GetRequestedRuntimeInfo –](getrequestedruntimeinfo-function.md)  
  
- [GetRequestedRuntimeVersion –](getrequestedruntimeversion-function.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetVersionString(  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out]  DWORD *pcchBuffer);  
```  
  
## <a name="parameters"></a>Parametry  
 `pwzBuffer`  
 mimo Verze kompilace .NET Framework ve formátu "v*A*. *B*[.* X*] ". *A*, *B*a *X* jsou desítková čísla, která odpovídají hlavní verzi, dílčí verzi a číslo buildu. *X* je volitelné. Pokud není k dispozici *X* , neexistuje žádná koncová tečka.  
  
> [!NOTE]
> Tento parametr se musí shodovat s názvem adresáře pro verzi .NET Framework, jak se zobrazuje v části C:\Windows\Microsoft.NET\Framework.  
  
 Příklady hodnot jsou "v 1.0.3705", "v 1.1.4322", "v 2.0.50727" a "v 4.0". *x*, kde *x* závisí na nainstalovaném čísle sestavení. Všimněte si, že předpona "v" je povinná.  
  
 `pchBuffer`  
 [in, out] Určuje velikost `pwzBuffer` pro zamezení přetečení vyrovnávací paměti. Pokud `pwzBuffer` je `null` , `pchBuffer` vrátí požadovanou velikost pro, `pwzBuffer` aby bylo možné předběžné přidělení.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|E_POINTER|`pwzBuffer`nebo `pchBuffer` má hodnotu null.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MetaHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRRuntimeInfo – rozhraní](iclrruntimeinfo-interface.md)
- [Rozhraní pro hostování](hosting-interfaces.md)
- [Rozhraní pro hostování CLR přidaná do .NET Framework 4 a 4.5](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [Hostování](index.md)
