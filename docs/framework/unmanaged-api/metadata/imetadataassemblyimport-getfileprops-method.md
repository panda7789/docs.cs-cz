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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f147fef90d7a9033bdfd07b75e5c33efd2c6881f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataassemblyimportgetfileprops-method"></a>IMetaDataAssemblyImport::GetFileProps – metoda
Získá vlastnosti souboru s podpisem Zadaná metadata.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `mdf`  
 [v] `mdFile` Metadata token, který představuje soubor, pro které chcete získat vlastnosti.  
  
 `szName`  
 [out] Jednoduchý název souboru.  
  
 `cchName`  
 [v] Velikost v široké znaků, z `szName`.  
  
 `pchName`  
 [out] Počet široké znaků ve skutečnosti, vrátí se v `szName`.  
  
 `ppbHashValue`  
 [out] Ukazatel na hodnotu hash. Toto je hodnota hash, pomocí algoritmu SHA-1, souboru.  
  
 `pcbHashValue`  
 [out] Počet široké znaků v hodnotě vrácené hodnoty hash.  
  
 `pdwFileFlags`  
 [out] Ukazatel na příznaky, které popisují metadata použít na soubor. Hodnota příznaky je kombinací jednoho nebo více [CorFileFlags](../../../../docs/framework/unmanaged-api/metadata/corfileflags-enumeration.md) hodnoty.  
  
## <a name="requirements"></a>Požadavky  
 **Platforma:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataAssemblyImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
