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
ms.openlocfilehash: 137b2e30916cb1934d4389c5668bfb7eb5066064
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617227"
---
# <a name="getcorsystemdirectory-function"></a>GetCORSystemDirectory – funkce
Vrátí instalační adresář modulu CLR (Common Language Runtime), který je načten do procesu. Instalační adresář je plně kvalifikovaný, například "c:\Windows\Microsoft.NET\Framework\v1.0.3705".  
  
 Tato funkce je zastaralá. Je nahrazen metodou [ICLRRuntimeInfo:: GetRuntimeDirectory –](iclrruntimeinfo-getruntimedirectory-method.md) , která je k dispozici v .NET Framework 4.  
  
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
 pro Velikost v bajtech `pbuffer` .  
  
 `dwLength`  
 mimo Počet znaků vrácených v `pbuffer` .  
  
## <a name="remarks"></a>Poznámky  
  
> [!CAUTION]
> Nepoužívejte tuto funkci v procesech, ve kterých je spuštěna verze 4 modulu CLR. Pokud je v počítači nainstalována starší verze modulu CLR, vrátí tato funkce instalační adresář pro danou verzi.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Zastaralé funkce hostování CLR](deprecated-clr-hosting-functions.md)
