---
title: "GetRequestedRuntimeInfo – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetRequestedRuntimeInfo
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: GetRequestedRuntimeInfo
helpviewer_keywords: GetRequestedRuntimeInfo function [.NET Framework hosting]
ms.assetid: 0dfd7cdc-c116-4e25-b56a-ac7b0378c942
topic_type: apiref
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cca74a1ff66392608802eacedcd74bb673919e8c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="getrequestedruntimeinfo-function"></a>GetRequestedRuntimeInfo – funkce
Získá informace o modul CLR (CLR) požadoval aplikace verzi a adresáře.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `pExe`  
 [v] Název aplikace.  
  
 `pwszVersion`  
 [v] Řetězec určující číslo verze modulu runtime.  
  
 `pConfigurationFile`  
 [v] Název konfiguračního souboru, který je spojen s `pExe`.  
  
 `startupFlags`  
 [v] Jeden nebo více [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) hodnot výčtu.  
  
 `runtimeInfoFlags`  
 [v] Jeden nebo více [RUNTIME_INFO_FLAGS](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md) hodnot výčtu.  
  
 `pDirectory`  
 [out] Vyrovnávací paměť, která obsahuje cestu k adresáři modulu runtime po úspěšném dokončení.  
  
 `dwDirectory`  
 [v] Délka vyrovnávací paměti adresáře.  
  
 `dwDirectoryLength`  
 [out] Ukazatel na délku řetězce cestu adresáře.  
  
 `pVersion`  
 [out] Vyrovnávací paměť, která obsahuje číslo verze modulu runtime po úspěšném dokončení.  
  
 `cchBuffer`  
 [v] Délka vyrovnávací paměti řetězec verze.  
  
 `dwlength`  
 [out] Ukazatel na délku řetězec verze.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí standardní kódy chyb modelu COM (Component Object), jak jsou definovány v WinError.h, kromě následující hodnoty.  
  
|Návratový kód|Popis|  
|-----------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|ERROR_INSUFFICIENT_BUFFER|Directory vyrovnávací paměť není dostatečně velký pro uložení cesta k adresáři.<br /><br /> - nebo -<br /><br /> Verze vyrovnávací paměť není dostatečně velký pro uložení řetězec verze.|  
  
## <a name="remarks"></a>Poznámky  
 `GetRequestedRuntimeInfo` Metoda vrátí běhu informace o verzi načtena do procesu, který není nutně v počítači nainstalována nejnovější verze.  
  
 V rozhraní .NET Framework verze 2.0, můžete získat informace o nejnovější nainstalované verzi pomocí `GetRequestedRuntimeInfo` metoda následujícím způsobem:  
  
-   Zadejte `pExe`, `pwszVersion`, a `pConfigurationFile` parametry jako hodnotu null.  
  
-   Zadejte příznak RUNTIME_INFO_UPGRADE_VERSION v `RUNTIME_INFO_FLAGS` výčty pro `runtimeInfoFlags` parametr.  
  
 `GetRequestedRuntimeInfo` Metoda nevrátí nejnovější verze CLR v následujících případech:  
  
-   Existuje konfigurační soubor aplikace, která určuje načtení určité verze modulu CLR. Upozorňujeme, že rozhraní .NET Framework se použít konfigurační soubor i v případě, že zadáte hodnotu null pro `pConfigurationFile` parametr.  
  
-   [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) byla volána metoda zadání starší verze CLR.  
  
-   Aktuálně je spuštěna aplikace, který byl sestaven pro starší verze CLR.  
  
 Pro `runtimeInfoFlags` parametr, můžete zadat pouze jeden konstant architekturu systému `RUNTIME_INFO_FLAGS` výčtu současně:  
  
-   RUNTIME_INFO_REQUEST_IA64  
  
-   RUNTIME_INFO_REQUEST_AMD64  
  
-   RUNTIME_INFO_REQUEST_X86  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Getrequestedruntimeversion – funkce](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
 [Getversionfromprocess – funkce](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)  
 [Zastaralé funkce hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
