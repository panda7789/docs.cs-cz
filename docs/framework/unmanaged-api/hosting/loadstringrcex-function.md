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
ms.openlocfilehash: a300c2679ef11a84edb2ab89c8dea96e445c9ee3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177985"
---
# <a name="loadstringrcex-function"></a>LoadStringRCEx – funkce
Převede hodnotu HRESULT na příslušnou chybovou zprávu pro zadanou jazykovou verzi.  
  
 Tato funkce byla v rozhraní .NET Framework 4 zastaralá.  
  
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
 [v] Identifikátor jazykové verze. Pass -1 `lcid` pro použití výchozí jazykové verze.  
  
 `iResourceID`  
 [v] An HRESULT.  
  
 `szBuffer`  
 [out] Vyrovnávací paměť, která obsahuje chybovou zprávu po úspěšném dokončení.  
  
 `iMax`  
 [v] Velikost vyrovnávací paměti chybové zprávy.  
  
 `bQuiet`  
 [v] Ignorovány.  
  
 `pcwchUsed`  
 [out] Ukazatel na délku chybové zprávy.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí standardní kódy chyb COM, jak je definováno v souboru WinError.h, kromě následujících hodnot.  
  
|Návratový kód|Popis|  
|-----------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|E_invalidarg|`szBuffer`je null `iMax` nebo je nula (0).|  
  
## <a name="remarks"></a>Poznámky  
 Pokud metoda není úspěšně dokončena, `szBuffer` obsahuje prázdný řetězec.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Soubor MSCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Globalization.CultureInfo.LCID%2A?displayProperty=nameWithType>
- [LoadStringRC – funkce](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)
- [Zastaralé funkce hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
