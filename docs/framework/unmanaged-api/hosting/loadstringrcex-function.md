---
title: LoadStringRCEx – funkce
ms.date: 03/30/2017
api_name:
- LoadStringRCEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- LoadStringRCEx
helpviewer_keywords:
- LoadStringRCEx function [.NET Framework hosting]
ms.assetid: bc789636-ca14-4f07-8f77-9305874d7495
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a0cac77d7bf7611acf6042298bfe6814d8f4352
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768448"
---
# <a name="loadstringrcex-function"></a>LoadStringRCEx – funkce
Převede hodnotu HRESULT na příslušnou chybovou zprávu pro zadanou jazykovou verzi.  
  
 Tato funkce se již nepoužívá v rozhraní .NET Framework 4.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT LoadStringRCEx (  
    [in]  LCID    lcid,   
    [in]  UINT    iResouceID,   
    [out] LPWSTR  szBuffer,   
    [in]  int     iMax,   
    [in]  int     bQuiet,   
    [out] int    *pcwchUsed  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `lcid`  
 [in] Identifikátor jazykové verze. Předejte hodnotu -1 `lcid` používat výchozí jazykovou verzi.  
  
 `iResourceID`  
 [in] HRESULT.  
  
 `szBuffer`  
 [out] Vyrovnávací paměti, který obsahuje chybovou zprávu po úspěšném dokončení.  
  
 `iMax`  
 [in] Velikost vyrovnávací paměti zpráv chyby.  
  
 `bQuiet`  
 [in] Ignorovat.  
  
 `pcwchUsed`  
 [out] Ukazatel na délku chybová zpráva.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací standardní kódy chyb modelu COM, jak je definovaný ve WinError.h, kromě následujících hodnot.  
  
|Návratový kód|Popis|  
|-----------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|E_INVALIDARG|`szBuffer` má hodnotu null, nebo `iMax` je nula (0).|  
  
## <a name="remarks"></a>Poznámky  
 Pokud metoda nedokončí úspěšně, `szBuffer` obsahuje prázdný řetězec.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Globalization.CultureInfo.LCID%2A?displayProperty=nameWithType>
- [LoadStringRC – funkce](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)
- [Zastaralé funkce pro hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
