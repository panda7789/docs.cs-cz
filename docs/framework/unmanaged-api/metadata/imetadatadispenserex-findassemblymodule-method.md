---
title: "IMetaDataDispenserEx::FindAssemblyModule – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenserEx.FindAssemblyModule
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenserEx::FindAssemblyModule
helpviewer_keywords:
- FindAssemblyModule method [.NET Framework metadata]
- IMetaDataDispenserEx::FindAssemblyModule method [.NET Framework metadata]
ms.assetid: d1fb65e1-7e19-4513-85b1-44f87c294d3e
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 482bc9b9a89d876e7ac09fcb4edcd190adc168f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatadispenserexfindassemblymodule-method"></a>IMetaDataDispenserEx::FindAssemblyModule – metoda
Tato metoda není implementována. Pokud je volána, vrátí E_NOTIMPL.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT FindAssemblyModule(  
    [in]  LPCWSTR  szAppBase,  
    [in]  LPCWSTR  szPrivateBin,  
    [in]  LPCWSTR  szGlobalBin,  
    [in]  LPCWSTR  szAssemblyName,  
    [in]  LPCWSTR  szModuleName,  
    [out] LPCWSTR  szName,  
    [in]  ULONG    cchName,  
    [out] ULONG    *pcName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `szAppBase`  
 [v] Nepoužívá se.  
  
 `szPrivateBin`  
 [v] Nepoužívá se.  
  
 `szGlobalBin`  
 [v] Nepoužívá se.  
  
 `szAssemblyName`  
 [v] Název modulu.  
  
 `szModuleName`  
 [v] Sestavení, která se má najít.  
  
 `szName`  
 [out] Jednoduchý název sestavení.  
  
 `cchName`  
 [v] Velikost v bajtech z `szName`.  
  
 `pcName`  
 [out] Počet znaků, které jsou ve skutečnosti, vrátí se v `szName`.  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataDispenserEx – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [IMetaDataDispenser – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
