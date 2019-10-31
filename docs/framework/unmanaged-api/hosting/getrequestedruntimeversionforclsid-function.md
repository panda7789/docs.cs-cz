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
ms.openlocfilehash: ce0c6307defd93dcf63ac4e9051fc798041475f3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127057"
---
# <a name="getrequestedruntimeversionforclsid-function"></a>GetRequestedRuntimeVersionForCLSID – funkce
Získá příslušné informace o verzi modulu CLR (Common Language Runtime) pro třídu se zadaným `CLSID`.  
  
 Tato funkce se už nepoužívá v .NET Framework 4.  
  
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
 pro  `CLSID` součásti.  
  
 `pVersion`  
 mimo  Vyrovnávací paměť, která obsahuje řetězec čísla verze po úspěšném dokončení.  
  
 `cchBuffer`  
 pro  Velikost `pVersion` vyrovnávací paměti v různých znacích.  
  
 `dwLength`  
 mimo Délka vrácené vyrovnávací paměti v bajtech.  
  
 `dwResolutionFlags`  
 pro  Jedna z hodnot CLSID_RESOLUTION_FLAGS Podporovány jsou následující hodnoty:  
  
- CLSID_RESOLUTION_DEFAULT: (0x0) určuje, že se má použít výchozí chování spolupráce.  
  
- CLSID_RESOLUTION_REGISTERED: (0x1) určuje, že by měl být použit registr a měla by být použita zásada překrytí.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Funkce byla úspěšně vrácena.|  
|E_INVALIDARG|Jeden z parametrů má neplatný typ nebo formát.|  
|ERROR_INSUFFICIENT_BUFFER|Vyrovnávací paměť `pVersion` není dostatečně velká pro uložení celého řetězce verze.|  
|REGDB_E_CLASSNOTREG|Není zaregistrována žádná třída se zadaným `CLSID`.|  
|E_POINTER|`dwLength` má hodnotu null nebo je `cchBuffer` dostatečně velká pro uložení řetězce verze, ale `pVersion` má hodnotu null.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Zastaralé funkce pro hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
