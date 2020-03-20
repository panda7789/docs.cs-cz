---
title: IMetaDataAssemblyImport::GetFileProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetFileProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetFileProps
helpviewer_keywords:
- GetFileProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetFileProps method [.NET Framework metadata]
ms.assetid: c5e6216f-ae3d-4697-9688-66b69c1251ec
topic_type:
- apiref
ms.openlocfilehash: dae4a36537eeac58ffb17ebc1b78d935ec807cd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175977"
---
# <a name="imetadataassemblyimportgetfileprops-method"></a>IMetaDataAssemblyImport::GetFileProps – metoda
Získá vlastnosti souboru se zadaným podpisem metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetFileProps (  
    [in]  mdFile      mdf,
    [out] LPWSTR      szName,
    [in]  ULONG       cchName,
    [out] ULONG       *pchName,
    [out] const void  **ppbHashValue,
    [out] ULONG       *pcbHashValue,
    [out] DWORD       *pdwFileFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `mdf`  
 [v] Token `mdFile` metadat, který představuje soubor, pro který chcete získat vlastnosti.  
  
 `szName`  
 [out] Jednoduchý název souboru.  
  
 `cchName`  
 [v] Velikost , v širokých `szName`znaků, .  
  
 `pchName`  
 [out] Počet širokých znaků skutečně `szName`vrátil v .  
  
 `ppbHashValue`  
 [out] Ukazatel na hodnotu hash. Toto je algoritmus hash pomocí algoritmu SHA-1 souboru.  
  
 `pcbHashValue`  
 [out] Počet širokých znaků ve vrácené hodnotě hash.  
  
 `pdwFileFlags`  
 [out] Ukazatel na příznaky, které popisují metadata použitá v souboru. Hodnota příznaky je kombinací jedné nebo více hodnot [CorFileFlags.](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md)  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataAssemblyImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
