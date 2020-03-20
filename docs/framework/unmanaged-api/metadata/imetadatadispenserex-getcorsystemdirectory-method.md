---
title: IMetaDataDispenserEx::GetCORSystemDirectory – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.GetCORSystemDirectory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::GetCORSystemDirectory
helpviewer_keywords:
- IMetaDataDispenserEx::GetCORSystemDirectory method [.NET Framework metadata]
- GetCORSystemDirectory method [.NET Framework metadata]
ms.assetid: d9e0f3b6-e106-4820-bada-5bfba34ce360
topic_type:
- apiref
ms.openlocfilehash: fb673666543bea3df44005ee3b20d311524f51d0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175912"
---
# <a name="imetadatadispenserexgetcorsystemdirectory-method"></a>IMetaDataDispenserEx::GetCORSystemDirectory – metoda
Získá adresář, který obsahuje aktuální clr (COMMON Language Runtime). Tato metoda je podporována pouze pro použití mimoprocesladivé. Pokud je volána z jiné součásti, vrátí E_NOTIMPL.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCORSystemDirectory (  
    [out] LPWSTR      szBuffer,
    [in]  DWORD       cchBuffer,
    [out] DWORD*      pchBuffer  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `szBuffer`  
 [out] Vyrovnávací paměť pro příjem názvu adresáře.  
  
 `cchBuffer`  
 [v] Velikost v bajtů `szBuffer`.  
  
 `pchBuffer`  
 [out] Počet bajtů skutečně vrácených v `szBuffer`.  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataDispenserEx – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [IMetaDataDispenser – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
