---
title: GetCORSystemDirectory – funkce
ms.date: 03/30/2017
api_name:
- GetCORSystemDirectory
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetCORSystemDirectory
helpviewer_keywords:
- GetCORSystemDirectory function [.NET Framework hosting]
ms.assetid: 3dcd16a7-dafc-4ca8-b5cd-20ffb37db91d
topic_type:
- apiref
ms.openlocfilehash: 63fb505a92683fda21b6e71a6ca891ca35afba1d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136415"
---
# <a name="getcorsystemdirectory-function"></a>GetCORSystemDirectory – funkce
Vrátí instalační adresář modulu CLR (Common Language Runtime), který je načten do procesu. Instalační adresář je plně kvalifikovaný, například "c:\Windows\Microsoft.NET\Framework\v1.0.3705".  
  
 Tato funkce je zastaralá. Je nahrazen metodou [ICLRRuntimeInfo:: GetRuntimeDirectory –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) , která je k dispozici v .NET Framework 4.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCORSystemDirectory (   
    [out] LPWSTR  pbuffer,     
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
## <a name="parameters"></a>Parametry  
 `pbuffer`  
 mimo Vyrovnávací paměť, ve které modul runtime vrátí řetězec, který obsahuje plně kvalifikovaný název instalačního adresáře pro modul runtime, který je načten do procesu. Pokud modul runtime ještě nebyl načten do procesu, vrátí funkce příslušné informace o adresáři pro nejnovější verzi modulu runtime nainstalovaného v počítači.  
  
 `cchBuffer`  
 pro Velikost `pbuffer`v bajtech.  
  
 `dwLength`  
 mimo Počet znaků vrácených v `pbuffer`.  
  
## <a name="remarks"></a>Poznámky  
  
> [!CAUTION]
> Nepoužívejte tuto funkci v procesech, ve kterých je spuštěna verze 4 modulu CLR. Pokud je v počítači nainstalována starší verze modulu CLR, vrátí tato funkce instalační adresář pro danou verzi.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Zastaralé funkce pro hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
