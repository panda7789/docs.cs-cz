---
title: GetRequestedRuntimeInfo – funkce
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeInfo
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeInfo
helpviewer_keywords:
- GetRequestedRuntimeInfo function [.NET Framework hosting]
ms.assetid: 0dfd7cdc-c116-4e25-b56a-ac7b0378c942
topic_type:
- apiref
ms.openlocfilehash: 0efda458d51677fcd16140cd0f0a835b76c20173
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617175"
---
# <a name="getrequestedruntimeinfo-function"></a>GetRequestedRuntimeInfo – funkce
Získá informace o verzi a adresáři modulu CLR (Common Language Runtime), který požaduje aplikace.  
  
 Tato funkce se už nepoužívá v .NET Framework 4.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetRequestedRuntimeInfo (  
    [in]  LPCWSTR  pExe,
    [in]  LPCWSTR  pwszVersion,
    [in]  LPCWSTR  pConfigurationFile,
    [in]  DWORD    startupFlags,
    [in]  DWORD    runtimeInfoFlags,
    [out] LPWSTR   pDirectory,
    [in]  DWORD    dwDirectory,
    [out] DWORD   *dwDirectoryLength,
    [out] LPWSTR   pVersion,
    [in]  DWORD    cchBuffer,
    [out] DWORD   *dwlength  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pExe`  
 pro Název aplikace  
  
 `pwszVersion`  
 pro Řetězec určující číslo verze modulu runtime.  
  
 `pConfigurationFile`  
 pro Název konfiguračního souboru, ke kterému je přidružen `pExe` .  
  
 `startupFlags`  
 pro Jedna nebo více hodnot [STARTUP_FLAGS](startup-flags-enumeration.md) výčtu.  
  
 `runtimeInfoFlags`  
 pro Jedna nebo více hodnot [RUNTIME_INFO_FLAGS](runtime-info-flags-enumeration.md) výčtu.  
  
 `pDirectory`  
 mimo Vyrovnávací paměť, která obsahuje cestu k adresáři modulu runtime po úspěšném dokončení.  
  
 `dwDirectory`  
 pro Délka vyrovnávací paměti adresáře.  
  
 `dwDirectoryLength`  
 mimo Ukazatel na délku řetězce cesty k adresáři.  
  
 `pVersion`  
 mimo Vyrovnávací paměť obsahující číslo verze modulu runtime po úspěšném dokončení.  
  
 `cchBuffer`  
 pro Délka vyrovnávací paměti pro řetězec verze.  
  
 `dwlength`  
 mimo Ukazatel na délku řetězce verze.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí standardní kódy chyb modelu COM (Component Object Model), jak je definováno v WinError. h, kromě následujících hodnot.  
  
|Návratový kód|Popis|  
|-----------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|ERROR_INSUFFICIENT_BUFFER|Vyrovnávací paměť adresáře není dostatečně velká pro uložení cesty k adresáři.<br /><br /> - nebo -<br /><br /> Vyrovnávací paměť verze není dostatečně velká pro uložení řetězce verze.|  
  
## <a name="remarks"></a>Poznámky  
 `GetRequestedRuntimeInfo`Metoda vrátí běhové informace o verzi načtené do procesu, což není nutně nejnovější verze nainstalovaná v počítači.  
  
 V .NET Framework verze 2,0 můžete získat informace o nejnovější nainstalované verzi pomocí `GetRequestedRuntimeInfo` metody následujícím způsobem:  
  
- Zadejte `pExe` parametry, `pwszVersion` a `pConfigurationFile` jako hodnotu null.  
  
- Zadejte příznak RUNTIME_INFO_UPGRADE_VERSION v `RUNTIME_INFO_FLAGS` výčtech pro `runtimeInfoFlags` parametr.  
  
 `GetRequestedRuntimeInfo`Metoda nevrátí nejnovější verzi CLR v následujících případech:  
  
- Existuje konfigurační soubor aplikace, který určuje načtení konkrétní verze CLR. Všimněte si, že .NET Framework bude používat konfigurační soubor i v případě, že pro parametr zadáte hodnotu null `pConfigurationFile` .  
  
- Metoda [CorBindToRuntimeEx –](corbindtoruntimeex-function.md) byla volána pro zadání dřívější verze CLR.  
  
- Aplikace, která byla zkompilována pro starší verzi CLR, je aktuálně spuštěna.  
  
 Pro `runtimeInfoFlags` parametr můžete zadat pouze jednu z konstant architektury `RUNTIME_INFO_FLAGS` výčtu v daném čase:  
  
- RUNTIME_INFO_REQUEST_IA64  
  
- RUNTIME_INFO_REQUEST_AMD64  
  
- RUNTIME_INFO_REQUEST_X86  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [GetRequestedRuntimeVersion – funkce](getrequestedruntimeversion-function.md)
- [GetVersionFromProcess – funkce](getversionfromprocess-function.md)
- [Zastaralé funkce hostování CLR](deprecated-clr-hosting-functions.md)
