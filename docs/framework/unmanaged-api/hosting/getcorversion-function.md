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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4bd398a5b214ac0046d5fe1965f70eef2eedaa6b
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490396"
---
# <a name="getcorversion-function"></a>GetCORVersion – funkce
Vrátí číslo verze common language runtime (CLR), na kterém běží v aktuálním procesu.  
  
 Tato funkce se již nepoužívá v rozhraní .NET Framework 4.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetCORVersion (  
    [in] LPWSTR  pbuffer,  
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
## <a name="parameters"></a>Parametry  
 `pbuffer`  
 Ukazatel do vyrovnávací paměti, ve kterém CLR vrátí řetězec určující verzi modulu runtime, který je aktuálně načtená do procesu. Vrácený řetězec má stejného formuláře jako řetězce předané [CorBindToRuntimeEx –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), například "v1.0.1216". Pokud modul runtime nebylo načteno do procesu, funkce vrátí informace o příslušné adresáře pro nejnovější verzi modulu runtime nainstalovaného v počítači.  
  
 `cchBuffer`  
 Počet znaků (`WCHAR`s), která se můžou uchovávat v `pbuffer`.  
  
 `dwLength`  
 Ukazatel na počet skutečně vrácených v znaků `pbuffer`. Pokud `pbuffer` je ukazatel s hodnotou null, vrátí E_POINTER modulu runtime. Pokud je větší počet znaků, které pak délka `pbuffer` , modul runtime vrátí ERROR_INSUFFICIENT_BUFFER.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Zastaralé funkce pro hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
