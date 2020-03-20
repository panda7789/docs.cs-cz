---
title: GetVersionFromProcess – funkce
ms.date: 03/30/2017
api_name:
- GetVersionFromProcess
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetVersionFromProcess
helpviewer_keywords:
- GetVersionFromProcess function [.NET Framework hosting]
ms.assetid: a9f7f824-64a1-408d-8607-91c7f19d21fe
topic_type:
- apiref
ms.openlocfilehash: a04a0c5e6865c3664d2cb5fb341c3625e35d4d7c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178120"
---
# <a name="getversionfromprocess-function"></a>GetVersionFromProcess – funkce
Získá číslo verze cltime společného jazyka (CLR), který je přidružen k popisovač zadaného procesu.  
  
 Tato funkce byla v rozhraní .NET Framework 4 zastaralá.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetVersionFromProcess (  
    [in]  HANDLE  hProcess,
    [out] LPWSTR  pVersion,
    [in]  DWORD   cchBuffer,
    [out] DWORD  *dwLength  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `hProcess`  
 [v] Popisovač procesu.  
  
 `pVersion`  
 [out] Vyrovnávací paměť, která obsahuje řetězec číslo verze po úspěšném dokončení metody.  
  
 `cchBuffer`  
 [v] Délka vyrovnávací paměti verze.  
  
 `pdwLength`  
 [out] Ukazatel na délku řetězce čísla verze.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí standardní kódy chybový model COM (COM), jak je definováno v souboru WinError.h, kromě následujících hodnot.  
  
|Návratový kód|Popis|  
|-----------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|E_invalidarg|`pVersion`je null `cchBuffer` a není null nebo naopak.<br /><br /> -nebo-<br /><br /> `hProcess`není platný popisovač procesu.<br /><br /> -nebo-<br /><br /> CLR není načten.|  
|ERROR_INSUFFICIENT_BUFFER|`cchBuffer`je null nebo menší než délka řetězce verze.|  
|E_NOTIMPL|Tato metoda není k dispozici v operačních systémech Microsoft Windows 95, Microsoft Windows 98 nebo Microsoft Windows Millennium Edition.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Soubor MSCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [GetRequestedRuntimeInfo – funkce](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)
- [GetRequestedRuntimeVersion – funkce](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [Zastaralé funkce hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
