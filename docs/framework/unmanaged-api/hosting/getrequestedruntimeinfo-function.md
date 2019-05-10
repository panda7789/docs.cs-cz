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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a440cef9de12c420e7b49b794ed0bcba39e756e8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665063"
---
# <a name="getrequestedruntimeinfo-function"></a>GetRequestedRuntimeInfo – funkce
Získá informace o common language runtime (CLR) požadovaný aplikací verzi a adresář.  
  
 Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 [in] Název aplikace.  
  
 `pwszVersion`  
 [in] Řetězec určující číslo verze modulu runtime.  
  
 `pConfigurationFile`  
 [in] Název konfiguračního souboru, který je přidružen `pExe`.  
  
 `startupFlags`  
 [in] Jeden nebo více následujících [startup_flags –](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) hodnot výčtu.  
  
 `runtimeInfoFlags`  
 [in] Jeden nebo více následujících [runtime_info_flags –](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md) hodnot výčtu.  
  
 `pDirectory`  
 [out] Vyrovnávací paměť, která obsahuje cestu k adresáři modulu runtime po úspěšném dokončení.  
  
 `dwDirectory`  
 [in] Délka vyrovnávací paměti adresáře.  
  
 `dwDirectoryLength`  
 [out] Ukazatel na délku řetězce cestu adresáře.  
  
 `pVersion`  
 [out] Vyrovnávací paměť, která obsahuje číslo verze modulu runtime po úspěšném dokončení.  
  
 `cchBuffer`  
 [in] Délka vyrovnávací paměti pro řetězec verze.  
  
 `dwlength`  
 [out] Ukazatel na délku řetězce verze.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací standardní kódy chyb modelu COM (Component Object), jak je definovaný ve WinError.h, kromě následujících hodnot.  
  
|Návratový kód|Popis|  
|-----------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|ERROR_INSUFFICIENT_BUFFER|Adresář vyrovnávací paměť není dostatečně velký pro uložení cesta k adresáři.<br /><br /> - nebo -<br /><br /> Verze vyrovnávací paměť není dostatečně velký pro uložení řetězce verze.|  
  
## <a name="remarks"></a>Poznámky  
 `GetRequestedRuntimeInfo` Metoda vrátí běhových informací o verzi načten do procesu, což není nutně v počítači nainstalovanou nejnovější verzi.  
  
 V rozhraní .NET Framework verze 2.0, můžete získat informace o nejnovější verze pomocí `GetRequestedRuntimeInfo` metodu následujícím způsobem:  
  
- Zadejte `pExe`, `pwszVersion`, a `pConfigurationFile` parametry jako hodnota null.  
  
- Zadejte příznak RUNTIME_INFO_UPGRADE_VERSION v `RUNTIME_INFO_FLAGS` výčty pro `runtimeInfoFlags` parametru.  
  
 `GetRequestedRuntimeInfo` Metoda nevrací na nejnovější verzi modulu CLR v následujících případech:  
  
- Existuje konfigurační soubor aplikace, která určuje načtení konkrétní verze modulu CLR. Všimněte si, že rozhraní .NET Framework se použít konfigurační soubor i v případě, že zadáte hodnotu null pro `pConfigurationFile` parametru.  
  
- [CorBindToRuntimeEx –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) byla volána metoda zadání starší verzi modulu CLR.  
  
- Aplikace, která byla zkompilována pro starší verzi modulu CLR je právě spuštěna.  
  
 Pro `runtimeInfoFlags` parametr, můžete zadat jenom jednu z konstant architektury `RUNTIME_INFO_FLAGS` výčtu v čase:  
  
- RUNTIME_INFO_REQUEST_IA64  
  
- RUNTIME_INFO_REQUEST_AMD64  
  
- RUNTIME_INFO_REQUEST_X86  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [GetRequestedRuntimeVersion – funkce](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [GetVersionFromProcess – funkce](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [Zastaralé funkce pro hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
