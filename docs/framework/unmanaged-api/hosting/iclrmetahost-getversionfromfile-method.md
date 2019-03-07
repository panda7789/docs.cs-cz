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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1c8f5ea20d00d692e0eea0cba93ec4e73038e8a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497441"
---
# <a name="iclrmetahostgetversionfromfile-method"></a>ICLRMetaHost::GetVersionFromFile – metoda
Získá sestavení původní verzi rozhraní .NET Framework kompilace (uložené v metadatech) zadané cesty k souboru. Tato metoda nahrazuje [getfileversion –](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md) funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetVersionFromFile (  
    [in] LPCWSTR pwzFilePath,  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBuffer);  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pwzFilePath`  
 [in] Cesta k souboru dokončení sestavení.  
  
 `pwzbuffer`  
 [out] Kompilace verzi rozhraní .NET Framework uložena v metadatech ve formátu "v*A*. *B*[. *X*] ". *A*, *B*, a *X* jsou desetinná čísla, která odpovídá hlavní verze, podverze a číslo sestavení. Délka tohoto řetězce je omezená na MAX_PATH.  
  
> [!NOTE]
>  Tento výstup odpovídá názvu adresáře pro verzi rozhraní .NET Framework, jak se zobrazí v části C:\Windows\Microsoft.NET\Framework.  
  
 Příklad hodnoty jsou "v1.0.3705", "v1.1.4322", "v2.0.50727" a "v4.0. *X*", kde *X* závisí na číslo sestavení nainstalována. Mějte na paměti, že předpona "v" je povinný.  
  
 `pcchBuffer`  
 [out v] Velikost `pwzbuffer` , aby přetečení vyrovnávací paměti.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí následující konkrétní HRESULT, stejně jako hodnota HRESULT chyby, které označují selhání metoda.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|E_POINTER|`pwzbuffer` nebo `pcchBuffer` má hodnotu null.|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|Vyrovnávací paměť je příliš malá.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICLRMetaHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)
- [Hostování](../../../../docs/framework/unmanaged-api/hosting/index.md)
