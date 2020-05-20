---
title: GetRequestedRuntimeVersion – funkce
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeVersion
helpviewer_keywords:
- GetRequestedRuntimeVersion function [.NET Framework hosting]
ms.assetid: 82f596a4-483d-4509-b0c5-a84c53c3da1b
topic_type:
- apiref
ms.openlocfilehash: b7a38d28b55842e9358bd9c7019b84c529526613
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617162"
---
# <a name="getrequestedruntimeversion-function"></a>GetRequestedRuntimeVersion – funkce
Získá číslo verze modulu CLR (Common Language Runtime), který požaduje Zadaná aplikace. Pokud tato verze není nainstalovaná, získá nejnovější verzi, která je nainstalovaná před požadovanou verzí.  
  
 Tato funkce se už nepoužívá v .NET Framework 4.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetRequestedRuntimeVersion (  
    [in]  LPWSTR  pExe,
    [out] LPWSTR  pVersion,
    [in]  DWORD   cchBuffer,
    [out] DWORD  *pdwLength  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pExe`  
 pro Název aplikace  
  
 `pVersion`  
 mimo Vyrovnávací paměť, která obsahuje řetězec čísla verze po úspěšném dokončení.  
  
 `cchBuffer`  
 pro Délka vyrovnávací paměti verze.  
  
 `pdwLength`  
 mimo Ukazatel na délku řetězce čísla verze.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí standardní kódy chyb modelu COM (Component Object Model), jak je definováno v WinError. h, kromě následujících hodnot.  
  
|Návratový kód|Popis|  
|-----------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|ERROR_INSUFFICIENT_BUFFER|Vyrovnávací paměť verze není dostatečně velká pro uložení řetězce verze.|  
|E_POINTER|`pdwLength`má hodnotu null.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [GetRequestedRuntimeInfo – funkce](getrequestedruntimeinfo-function.md)
- [GetVersionFromProcess – funkce](getversionfromprocess-function.md)
- [Zastaralé funkce hostování CLR](deprecated-clr-hosting-functions.md)
