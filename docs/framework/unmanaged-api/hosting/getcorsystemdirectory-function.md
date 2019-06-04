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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a412bd8410750ec826762e45d70d59c514c61542
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490382"
---
# <a name="getcorsystemdirectory-function"></a>GetCORSystemDirectory – funkce
Vrátí instalační adresář modulu common language runtime (CLR), který je načten do procesu. Instalační adresář je plně kvalifikovaný, například "c:\windows\microsoft.net\framework\v1.0.3705".  
  
 Tato funkce je zastaralá. Je nahrazen technologií [iclrruntimeinfo::getruntimedirectory –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) metodě v rozhraní .NET Framework 4.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetCORSystemDirectory (   
    [out] LPWSTR  pbuffer,     
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
## <a name="parameters"></a>Parametry  
 `pbuffer`  
 [out] Vyrovnávací paměť, ve kterém modul runtime vrátí řetězec, který obsahuje plně kvalifikovaný název v instalačním adresáři pro modul runtime, který je načten do procesu. Pokud modul runtime nebylo načteno do procesu, funkce vrátí informace o příslušné adresáře pro nejnovější verzi modulu runtime nainstalovaného v počítači.  
  
 `cchBuffer`  
 [in] Velikost v bajtech, z `pbuffer`.  
  
 `dwLength`  
 [out] Počet znaků, které jsou vráceny v `pbuffer`.  
  
## <a name="remarks"></a>Poznámky  
  
> [!CAUTION]
>  Nepoužívejte tuto funkci v procesy, které jsou spuštěny modulu CLR verze 4. Pokud v počítači je nainstalovaná starší verzi modulu CLR, tato funkce vrátí instalační adresář pro tuto verzi.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Zastaralé funkce pro hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
