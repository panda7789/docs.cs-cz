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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f4b4ac1a37c2b3506216499ed0c9f8194949b768
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081889"
---
# <a name="getrequestedruntimeversionforclsid-function"></a>GetRequestedRuntimeVersionForCLSID – funkce
Získá odpovídající common language runtime (CLR) informace o verzi pro třídu se zadaným `CLSID`.  
  
 Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 [in]  `CLSID` Komponenty.  
  
 `pVersion`  
 [out]  Vyrovnávací paměť, která obsahuje řetězec, číslo verze po úspěšném dokončení.  
  
 `cchBuffer`  
 [in]  Velikost v širokých znaků, z `pVersion` vyrovnávací paměti.  
  
 `dwLength`  
 [out] Délka v bajtech, vrácený vyrovnávací paměti.  
  
 `dwResolutionFlags`  
 [in]  Jedna z hodnot clsid_resolution_flags –. Podporovány jsou následující hodnoty:  
  
-   CLSID_RESOLUTION_DEFAULT: (0x0) určuje, že má být použito výchozí chování spolupráce.  
  
-   CLSID_RESOLUTION_REGISTERED: (0x1) určuje, že registru vyhledávat a překrytí tato zásada použít.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Funkci bylo úspěšně vráceno.|  
|E_INVALIDARG|Jeden z parametrů má neplatný typ nebo formát.|  
|ERROR_INSUFFICIENT_BUFFER|`pVersion` Vyrovnávací paměť není dostatečně velký pro umístění celého řetězci verze.|  
|REGDB_E_CLASSNOTREG|Neexistuje žádná třída zaregistrován se zadaným `CLSID`.|  
|E_POINTER|`dwLength` má hodnotu null, nebo `cchBuffer` je dostatečně velký pro uložení řetězce verze, ale `pVersion` má hodnotu null.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Zastaralé funkce hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
