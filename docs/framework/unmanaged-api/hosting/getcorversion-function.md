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
ms.openlocfilehash: 23d68e8e4bbd87779e3b49f0c40f5a5ab9f5124f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617214"
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
 Ukazatel na vyrovnávací paměť, ve které CLR vrátí řetězec určující verzi modulu runtime, který je aktuálně načten do procesu. Vrácený řetězec má stejný tvar jako řetězce předané do [CorBindToRuntimeEx –](corbindtoruntimeex-function.md), například "v 1.0.1216". Pokud modul runtime ještě nebyl načten do procesu, vrátí funkce příslušné informace o adresáři pro nejnovější verzi modulu runtime nainstalovaného v počítači.  
  
 `cchBuffer`  
 Počet znaků `WCHAR` , které lze uchovávat v `pbuffer` .  
  
 `dwLength`  
 Ukazatel na počet skutečně vrácených znaků `pbuffer` . Pokud `pbuffer` je ukazatel s hodnotou null, modul runtime vrátí E_POINTER. Pokud je počet znaků větší než délka `pbuffer` , modul runtime vrátí ERROR_INSUFFICIENT_BUFFER.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Zastaralé funkce hostování CLR](deprecated-clr-hosting-functions.md)
