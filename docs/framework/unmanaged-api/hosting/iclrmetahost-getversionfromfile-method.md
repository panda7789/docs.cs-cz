---
title: ICLRMetaHost::GetVersionFromFile – metoda
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.GetVersionFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::GetVersionFromFile
helpviewer_keywords:
- ICLRMetaHost::GetVersionFromFile method [.NET Framework hosting]
- GetVersionFromFile method [.NET Framework hosting]
ms.assetid: 55bb3eb4-f665-42fc-973c-465567570e82
topic_type:
- apiref
ms.openlocfilehash: a237dff63015cda2cf2ca86a64bb4028ec9b6e2c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140927"
---
# <a name="iclrmetahostgetversionfromfile-method"></a>ICLRMetaHost::GetVersionFromFile – metoda
Získá původní verzi .NET Framework kompilace sestavení (uloženou v metadatech), která má za následek cestu k souboru. Tato metoda nahrazuje funkci [GetFileVersion –](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetVersionFromFile (  
    [in] LPCWSTR pwzFilePath,  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBuffer);  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pwzFilePath`  
 pro Úplná cesta k souboru sestavení.  
  
 `pwzbuffer`  
 mimo Verze kompilace .NET Framework uložená v metadatech ve formátu "v*A*. *B*[. *X*] ". *A*, *B*a *X* jsou desítková čísla, která odpovídají hlavní verzi, dílčí verzi a číslo buildu. Délka tohoto řetězce je omezená na MAX_PATH.  
  
> [!NOTE]
> Tento výstup se shoduje s názvem adresáře pro .NET Framework verzi, jak se zobrazuje v části C:\Windows\Microsoft.NET\Framework.  
  
 Příklady hodnot jsou "v 1.0.3705", "v 1.1.4322", "v 2.0.50727" a "v 4.0". *X*, kde *x* závisí na nainstalovaném čísle sestavení. Všimněte si, že je vyžadována předpona "v".  
  
 `pcchBuffer`  
 [in, out] Velikost `pwzbuffer`, aby se předešlo přetečení vyrovnávací paměti.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací následující konkrétní hodnoty HRESULT a také chyby HRESULT, které naznačují selhání metody.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|E_POINTER|`pwzbuffer` nebo `pcchBuffer` je null.|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|Vyrovnávací paměť je příliš malá.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MetaHost. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRMetaHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
