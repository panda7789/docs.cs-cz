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
ms.openlocfilehash: 899d6e74902e47f1f41b849bd5c25048baa175f7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617136"
---
# <a name="getrequestedruntimeversionforclsid-function"></a>GetRequestedRuntimeVersionForCLSID – funkce
Získá příslušné informace o verzi modulu CLR (Common Language Runtime) pro třídu se zadaným parametrem `CLSID` .  
  
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
 pro  `CLSID`Komponenty.  
  
 `pVersion`  
 mimo  Vyrovnávací paměť, která obsahuje řetězec čísla verze po úspěšném dokončení.  
  
 `cchBuffer`  
 pro  Velikost vyrovnávací paměti v různých znacích `pVersion` .  
  
 `dwLength`  
 mimo Délka vrácené vyrovnávací paměti v bajtech.  
  
 `dwResolutionFlags`  
 pro  Jedna z hodnot CLSID_RESOLUTION_FLAGS. Podporovány jsou následující hodnoty:  
  
- CLSID_RESOLUTION_DEFAULT: (0x0) určuje, že se má použít výchozí chování spolupráce.  
  
- CLSID_RESOLUTION_REGISTERED: (0x1) určuje, že by měl být registr prohledáván a musí být použita zásada překrytí.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Funkce byla úspěšně vrácena.|  
|E_INVALIDARG|Jeden z parametrů má neplatný typ nebo formát.|  
|ERROR_INSUFFICIENT_BUFFER|`pVersion`Vyrovnávací paměť není dostatečně velká pro uložení celého řetězce verze.|  
|REGDB_E_CLASSNOTREG|Není zaregistrována žádná třída se zadaným parametrem `CLSID` .|  
|E_POINTER|`dwLength`má hodnotu null nebo `cchBuffer` je dostatečně velká pro uložení řetězce verze, ale `pVersion` má hodnotu null.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Zastaralé funkce hostování CLR](deprecated-clr-hosting-functions.md)
