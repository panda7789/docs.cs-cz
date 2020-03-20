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
ms.openlocfilehash: db721e1ef774c87de0fa7da178463d832a3da756
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178157"
---
# <a name="getrequestedruntimeinfo-function"></a>GetRequestedRuntimeInfo – funkce
Získá informace o verzi a adresáři o clr (CLR) jazyka požadované aplikací.  
  
 Tato funkce byla v rozhraní .NET Framework 4 zastaralá.  
  
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
 [v] Název aplikace.  
  
 `pwszVersion`  
 [v] Řetězec určující číslo verze za běhu.  
  
 `pConfigurationFile`  
 [v] Název konfiguračního souboru, který je přidružen k programu `pExe`.  
  
 `startupFlags`  
 [v] Jedna nebo více [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) hodnoty výčtu.  
  
 `runtimeInfoFlags`  
 [v] Jedna nebo více [hodnot RUNTIME_INFO_FLAGS](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md) výčtu.  
  
 `pDirectory`  
 [out] Vyrovnávací paměť, která obsahuje cestu k adresáři do běhu po úspěšném dokončení.  
  
 `dwDirectory`  
 [v] Délka vyrovnávací paměti adresáře.  
  
 `dwDirectoryLength`  
 [out] Ukazatel na délku řetězce cesty k adresáři.  
  
 `pVersion`  
 [out] Vyrovnávací paměť, která obsahuje číslo verze za běhu po úspěšném dokončení.  
  
 `cchBuffer`  
 [v] Délka vyrovnávací paměti řetězce verze.  
  
 `dwlength`  
 [out] Ukazatel na délku řetězce verze.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí standardní kódy chybový model COM (COM), jak je definováno v souboru WinError.h, kromě následujících hodnot.  
  
|Návratový kód|Popis|  
|-----------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|ERROR_INSUFFICIENT_BUFFER|Vyrovnávací paměť adresáře není dostatečně velká pro uložení cesty k adresáři.<br /><br /> - nebo -<br /><br /> Vyrovnávací paměť verze není dostatečně velká pro uložení řetězce verze.|  
  
## <a name="remarks"></a>Poznámky  
 Metoda `GetRequestedRuntimeInfo` vrátí informace za běhu o verzi načtené do procesu, což nemusí být nutně nejnovější verze nainstalovaná v počítači.  
  
 V rozhraní .NET Framework verze 2.0 můžete získat informace o `GetRequestedRuntimeInfo` nejnovější nainstalované verzi pomocí metody následujícím způsobem:  
  
- Zadejte `pExe` `pwszVersion`parametry `pConfigurationFile` , a parametry jako null.  
  
- Zadejte příznak RUNTIME_INFO_UPGRADE_VERSION `RUNTIME_INFO_FLAGS` ve výčtech `runtimeInfoFlags` parametru.  
  
 Metoda `GetRequestedRuntimeInfo` nevrací nejnovější verzi CLR za následujících okolností:  
  
- Existuje konfigurační soubor aplikace, který určuje načtení konkrétní verze CLR. Všimněte si, že rozhraní .NET Framework použije konfigurační soubor i v případě, že pro parametr zadáte hodnotu `pConfigurationFile` null.  
  
- Metoda [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) byla volána určující starší verzi CLR.  
  
- Aplikace, která byla zkompilována pro starší verzi CLR, je aktuálně spuštěna.  
  
 Pro `runtimeInfoFlags` parametr můžete zadat pouze jednu konstantu `RUNTIME_INFO_FLAGS` architektury výčtu současně:  
  
- RUNTIME_INFO_REQUEST_IA64  
  
- RUNTIME_INFO_REQUEST_AMD64  
  
- RUNTIME_INFO_REQUEST_X86  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Soubor MSCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [GetRequestedRuntimeVersion – funkce](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [GetVersionFromProcess – funkce](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [Zastaralé funkce hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
