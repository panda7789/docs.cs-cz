---
title: "LoadLibraryShim – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LoadLibraryShim
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: LoadLibraryShim
helpviewer_keywords: LoadLibraryShim function [.NET Framework hosting]
ms.assetid: 30931874-4d0e-4df1-b3d1-e425b50655d1
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c56f5a3576c505fd7b7d514e3f2d038e7f8f3ecc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="loadlibraryshim-function"></a>LoadLibraryShim – funkce
Načte zadaný verzi knihovny DLL, která je součástí Distribuovatelný balíček .NET Framework.  
  
 Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. Použití [iclrruntimeinfo::LoadLibrary –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md) metoda místo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT LoadLibraryShim (  
    [in]  LPCWSTR  szDllName,  
    [in]  LPCWSTR  szVersion,  
          LPVOID   pvReserved,  
    [out] HMODULE *phModDll  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `szDllName`  
 [v] Byl ukončen nula řetězec, který představuje název knihovnu DLL, která má být načten z knihovny rozhraní .NET Framework.  
  
 `szVersion`  
 [v] Byl ukončen nula řetězec, který představuje verzi knihovny DLL pro načtení. Pokud `szVersion` je null, verze, vybraný pro načítání je nejnovější verze zadané knihovny DLL, která je nižší než verze 4. To znamená, jsou ignorovány všechny verze rovna nebo větší než verze 4, pokud `szVersion` má hodnotu null, a pokud je nainstalována žádná verze a nižší než verze 4, nepodaří načíst knihovnu DLL. To je potřeba zajistit, že instalace [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] nemá vliv na existující aplikace nebo součásti. Naleznete v příspěvku [vnitroprocesovou SxS a migrace rychlý Start](http://go.microsoft.com/fwlink/?LinkId=200329) v blogu týmu CLR.  
  
 `pvReserved`  
 Vyhrazeno pro budoucí použití.  
  
 `phModDll`  
 [out] Ukazatel na popisovač modulu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí standardní kódy chyb modelu COM (Component Object), jak jsou definovány v WinError.h, kromě následující hodnoty.  
  
|Návratový kód|Popis|  
|-----------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|CLR_E_SHIM_RUNTIMELOAD|Načítání `szDllName` vyžaduje načítání nelze načíst modul CLR (CLR) a potřebnou verzi modulu CLR.|  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce slouží k načtení knihovny DLL, které jsou součástí Distribuovatelný balíček .NET Framework. Nenačítá uživatelem generovaný knihovny DLL.  
  
> [!NOTE]
>  Od verze rozhraní .NET Framework verze 2.0, načítání knihovna Fusion.dll způsobí, že CLR má být načten. Je to proto, že funkce v knihovně Fusion.dll jsou nyní obálky, jejíž implementace poskytované modulem runtime.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Zastaralé funkce hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
