---
title: IMetaDataDispenserEx::FindAssemblyModule – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.FindAssemblyModule
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::FindAssemblyModule
helpviewer_keywords:
- FindAssemblyModule method [.NET Framework metadata]
- IMetaDataDispenserEx::FindAssemblyModule method [.NET Framework metadata]
ms.assetid: d1fb65e1-7e19-4513-85b1-44f87c294d3e
topic_type:
- apiref
ms.openlocfilehash: e73c95d8c720ed3263d6a66c48bdb5b5582eb686
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442189"
---
# <a name="imetadatadispenserexfindassemblymodule-method"></a>IMetaDataDispenserEx::FindAssemblyModule – metoda
Tato metoda není implementována. Při volání Vrátí E_NOTIMPL.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
  
## <a name="parameters"></a>Parametry  
 `szAppBase`  
 pro Nepoužívá se.  
  
 `szPrivateBin`  
 pro Nepoužívá se.  
  
 `szGlobalBin`  
 pro Nepoužívá se.  
  
 `szAssemblyName`  
 pro Název modulu.  
  
 `szModuleName`  
 pro Sestavení, které má být nalezeno.  
  
 `szName`  
 mimo Jednoduchý název sestavení.  
  
 `cchName`  
 pro Velikost `szName`v bajtech.  
  
 `pcName`  
 mimo Počet znaků, které jsou ve skutečnosti vráceny v `szName`.  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataDispenserEx – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataDispenser – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
