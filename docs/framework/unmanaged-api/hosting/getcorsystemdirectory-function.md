---
title: "GetCORSystemDirectory – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetCORSystemDirectory
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: GetCORSystemDirectory
helpviewer_keywords: GetCORSystemDirectory function [.NET Framework hosting]
ms.assetid: 3dcd16a7-dafc-4ca8-b5cd-20ffb37db91d
topic_type: apiref
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 802e9a7bd4e6caedd657a8e8cf0132d75b4cbc2e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="getcorsystemdirectory-function"></a>GetCORSystemDirectory – funkce
Vrátí instalační adresář common language runtime (CLR), který je načten do procesu. Instalační adresář je plně kvalifikovaný, například "c:\windows\microsoft.net\framework\v1.0.3705".  
  
 Tato funkce je zastaralý. Je nahrazena [iclrruntimeinfo::getruntimedirectory –](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) metody, které jsou součástí [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetCORSystemDirectory (   
    [out] LPWSTR  pbuffer,     
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
#### <a name="parameters"></a>Parametry  
 `pbuffer`  
 [out] Vyrovnávací paměť, ve kterém modulu runtime vrátí řetězec, který obsahuje plně kvalifikovaný název instalační adresář pro modul runtime, který je načten do procesu. Pokud modul runtime dosud nebyla načtena do procesu, funkce vrátí informace příslušný adresář na nejnovější verzi modulu runtime v počítači nainstalována.  
  
 `cchBuffer`  
 [v] Velikost v bajtech z `pbuffer`.  
  
 `dwLength`  
 [out] Počet znaků, vrátí se v `pbuffer`.  
  
## <a name="remarks"></a>Poznámky  
  
> [!CAUTION]
>  Nepoužívejte tuto funkci v procesy, které používají 4 verzi modulu CLR. Pokud v počítači je nainstalovaná starší verze modulu CLR, vrátí tato funkce instalační adresář pro tuto verzi.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Zastaralé funkce hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
