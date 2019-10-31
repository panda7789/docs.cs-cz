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
ms.openlocfilehash: cd1d9e768698115bee22e35699b044e0c3526d2d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136324"
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
 pro Název konfiguračního souboru, který je přidružený k `pExe`.  
  
 `startupFlags`  
 pro Jedna nebo více hodnot výčtu [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) .  
  
 `runtimeInfoFlags`  
 pro Jedna nebo více hodnot výčtu [RUNTIME_INFO_FLAGS](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md) .  
  
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
|ERROR_INSUFFICIENT_BUFFER|Vyrovnávací paměť adresáře není dostatečně velká pro uložení cesty k adresáři.<br /><br /> ani<br /><br /> Vyrovnávací paměť verze není dostatečně velká pro uložení řetězce verze.|  
  
## <a name="remarks"></a>Poznámky  
 Metoda `GetRequestedRuntimeInfo` vrátí běhové informace o verzi načtené do procesu, což nemusí nutně být v počítači nainstalovaná nejnovější verze.  
  
 V .NET Framework verze 2,0 můžete získat informace o nejnovější nainstalované verzi pomocí metody `GetRequestedRuntimeInfo` následujícím způsobem:  
  
- Zadejte parametry `pExe`, `pwszVersion`a `pConfigurationFile` jako null.  
  
- Zadejte příznak RUNTIME_INFO_UPGRADE_VERSION v výčtech `RUNTIME_INFO_FLAGS` pro parametr `runtimeInfoFlags`.  
  
 Metoda `GetRequestedRuntimeInfo` nevrátí nejnovější verzi CLR v následujících případech:  
  
- Existuje konfigurační soubor aplikace, který určuje načtení konkrétní verze CLR. Všimněte si, že .NET Framework použije konfigurační soubor i v případě, že pro parametr `pConfigurationFile` zadáte hodnotu null.  
  
- Metoda [CorBindToRuntimeEx –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) byla volána pro zadání dřívější verze CLR.  
  
- Aplikace, která byla zkompilována pro starší verzi CLR, je aktuálně spuštěna.  
  
 Pro parametr `runtimeInfoFlags` lze současně zadat pouze jednu z konstant architektury `RUNTIME_INFO_FLAGS` výčtu:  
  
- RUNTIME_INFO_REQUEST_IA64  
  
- RUNTIME_INFO_REQUEST_AMD64  
  
- RUNTIME_INFO_REQUEST_X86  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [GetRequestedRuntimeVersion – funkce](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [GetVersionFromProcess – funkce](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [Zastaralé funkce pro hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
