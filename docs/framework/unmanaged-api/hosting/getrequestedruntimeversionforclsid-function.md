---
title: GetRequestedRuntimeVersionForCLSID – funkce
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeVersionForCLSID
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeVersionForCLSID
helpviewer_keywords:
- GetRequestedRuntimeVersionForCLSID function [.NET Framework hosting]
ms.assetid: 5bb12f9a-0612-434b-b4ed-2db636a20bec
topic_type:
- apiref
ms.openlocfilehash: 6132e94544b30486b70ecfec49c1ddd5e3c0f50b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178106"
---
# <a name="getrequestedruntimeversionforclsid-function"></a>GetRequestedRuntimeVersionForCLSID – funkce
Získá příslušné informace o verzi clr (COMMON Language Runtime) pro třídu se zadanou `CLSID`.  
  
 Tato funkce byla v rozhraní .NET Framework 4 zastaralá.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetRequestedRuntimeVersionForCLSID (  
    [in]  REFCLSID   rclsid,
    [out]  LPWSTR     pVersion,
    [in]  DWORD      cchBuffer,
    [out] DWORD*     dwLength,
    [in]  CLSID_RESOLUTION_FLAGS dwResolutionFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `rclsid`  
 [v]  Součást. `CLSID`  
  
 `pVersion`  
 [out]  Vyrovnávací paměť, která obsahuje řetězec číslo verze po úspěšném dokončení.  
  
 `cchBuffer`  
 [v]  Velikost, v širokých znaků `pVersion` vyrovnávací paměti.  
  
 `dwLength`  
 [out] Délka vrácené vyrovnávací paměti v bajtech.  
  
 `dwResolutionFlags`  
 [v]  Jedna z CLSID_RESOLUTION_FLAGS hodnot. Podporovány jsou následující hodnoty:  
  
- CLSID_RESOLUTION_DEFAULT: (0x0) Určuje, že má být použito výchozí chování interop.  
  
- CLSID_RESOLUTION_REGISTERED: (0x1) Určuje, že registr by měl být prohledán a měl by být použit a použity zásady překrytí.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Funkce byla úspěšně vrácena.|  
|E_invalidarg|Jeden z parametrů má neplatný typ nebo formát.|  
|ERROR_INSUFFICIENT_BUFFER|Vyrovnávací `pVersion` paměť není dostatečně velká pro uložení celého řetězce verze.|  
|REGDB_E_CLASSNOTREG|Neexistuje žádná třída registrovaná `CLSID`s zadanou .|  
|E_POINTER|`dwLength`je null `cchBuffer` nebo je dostatečně velký pro `pVersion` uložení řetězce verze, ale je null.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Zastaralé funkce hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
