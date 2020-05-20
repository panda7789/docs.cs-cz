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
ms.openlocfilehash: fbaf45da0902ded8a2f7bf0d470aaed3b5f531aa
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617123"
---
# <a name="getversionfromprocess-function"></a>GetVersionFromProcess – funkce
Získá číslo verze modulu CLR (Common Language Runtime), který je spojen se zadaným popisovačem procesu.  
  
 Tato funkce se už nepoužívá v .NET Framework 4.  
  
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
 pro Popisovač procesu.  
  
 `pVersion`  
 mimo Vyrovnávací paměť, která obsahuje řetězec čísla verze po úspěšném dokončení metody.  
  
 `cchBuffer`  
 pro Délka vyrovnávací paměti verze.  
  
 `pdwLength`  
 mimo Ukazatel na délku řetězce čísla verze.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí standardní kódy chyb modelu COM (Component Object Model), jak je definováno v WinError. h, kromě následujících hodnot.  
  
|Návratový kód|Popis|  
|-----------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|E_INVALIDARG|`pVersion`má hodnotu null a `cchBuffer` není null nebo naopak.<br /><br /> -nebo-<br /><br /> `hProcess`není platným popisovačem procesu.<br /><br /> -nebo-<br /><br /> Modul CLR není zaveden.|  
|ERROR_INSUFFICIENT_BUFFER|`cchBuffer`má hodnotu null nebo menší než délka řetězce verze.|  
|E_NOTIMPL|Tato metoda není k dispozici v operačním systému Microsoft Windows 95, Microsoft Windows 98 nebo Microsoft Windows Millennium Edition.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [GetRequestedRuntimeInfo – funkce](getrequestedruntimeinfo-function.md)
- [GetRequestedRuntimeVersion – funkce](getrequestedruntimeversion-function.md)
- [Zastaralé funkce hostování CLR](deprecated-clr-hosting-functions.md)
