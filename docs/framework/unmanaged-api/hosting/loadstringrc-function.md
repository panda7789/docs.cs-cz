---
title: LoadStringRC – funkce
ms.date: 03/30/2017
api_name:
- LoadStringRC
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- LoadStringRC
helpviewer_keywords:
- LoadStringRC function [.NET Framework hosting]
ms.assetid: 752e49b4-987c-4c28-a118-1a0c1ed510c5
topic_type:
- apiref
ms.openlocfilehash: 56ae7b7cf3b577bfe41ebd0bdd98e0da68047b44
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176237"
---
# <a name="loadstringrc-function"></a>LoadStringRC – funkce
Převede hodnotu HRESULT na chybovou zprávu pomocí výchozí jazykové verze aktuálního vlákna.  
  
 Tato funkce byla v rozhraní .NET Framework 4 zastaralá.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT LoadStringRC (  
    [in]  UINT    iResourceID,
    [out] LPWSTR  szBuffer,
    [in]  int     iMax,
    [in]  int     bQuiet  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `iResourceID`  
 [v] An HRESULT.  
  
 `szBuffer`  
 [out] Vyrovnávací paměť, která obsahuje chybovou zprávu po úspěšném dokončení.  
  
 `iMax`  
 [v] Velikost vyrovnávací paměti chybové zprávy.  
  
 `bQuiet`  
 [v] Ignorovány.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí standardní kódy chybový model COM (COM), jak je definováno v souboru WinError.h, kromě následujících hodnot.  
  
|Návratový kód|Popis|  
|-----------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|E_invalidarg|`szBuffer`je null `iMax` nebo je nula (0).|  
  
## <a name="remarks"></a>Poznámky  
 Pokud metoda není úspěšně dokončena, `szBuffer` obsahuje prázdný řetězec.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll a Mscorwks.dll. Místo souboru Mscorwks.dll použijte soubor MSCorEE.dll a ujistěte se, že cílíte na správnou verzi rozhraní .NET Framework.  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [LoadStringRCEx – funkce](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)
- [Zastaralé funkce hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
