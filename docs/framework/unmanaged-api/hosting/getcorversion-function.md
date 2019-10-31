---
title: GetCORVersion – funkce
ms.date: 03/30/2017
api_name:
- GetCORVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetCORVersion
helpviewer_keywords:
- GetCORVersion function [.NET Framework hosting]
ms.assetid: 2f09cd37-bf3a-4cc5-87b0-adc42a7eed31
topic_type:
- apiref
ms.openlocfilehash: 1283abaf6b08af1d842d8fe4469f7f6c15e38ec5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136424"
---
# <a name="getcorversion-function"></a>GetCORVersion – funkce
Vrátí číslo verze modulu CLR (Common Language Runtime), který je spuštěn v aktuálním procesu.  
  
 Tato funkce se už nepoužívá v .NET Framework 4.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCORVersion (  
    [in] LPWSTR  pbuffer,  
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
## <a name="parameters"></a>Parametry  
 `pbuffer`  
 Ukazatel na vyrovnávací paměť, ve které CLR vrátí řetězec určující verzi modulu runtime, který je aktuálně načten do procesu. Vrácený řetězec má stejný tvar jako řetězce předané do [CorBindToRuntimeEx –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), například "v 1.0.1216". Pokud modul runtime ještě nebyl načten do procesu, vrátí funkce příslušné informace o adresáři pro nejnovější verzi modulu runtime nainstalovaného v počítači.  
  
 `cchBuffer`  
 Počet znaků (`WCHAR`ů), které lze uchovávat v `pbuffer`.  
  
 `dwLength`  
 Ukazatel na počet znaků ve skutečnosti vrácených v `pbuffer`. Pokud je `pbuffer` ukazatel s hodnotou null, modul runtime vrátí E_POINTER. Pokud je počet znaků větší než délka `pbuffer`, modul runtime vrátí ERROR_INSUFFICIENT_BUFFER.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Zastaralé funkce pro hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
