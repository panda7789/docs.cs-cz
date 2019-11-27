---
title: IMetaDataImport::GetScopeProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetScopeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetScopeProps
helpviewer_keywords:
- IMetaDataImport::GetScopeProps method [.NET Framework metadata]
- GetScopeProps method [.NET Framework metadata]
ms.assetid: c8ba42d2-d9fa-43cb-bbc0-f33e1e592cb6
topic_type:
- apiref
ms.openlocfilehash: af1c3d599c5280e584ffb842c96c70a7c3d4ed08
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436873"
---
# <a name="imetadataimportgetscopeprops-method"></a>IMetaDataImport::GetScopeProps – metoda
Získá název a volitelně identifikátor verze sestavení nebo modulu v aktuálním oboru metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetScopeProps (  
   [out] LPWSTR           szName,  
   [in]  ULONG            cchName,  
   [out] ULONG            *pchName,  
   [out, optional] GUID   *pmvid  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `szName`  
 mimo Vyrovnávací paměť pro název sestavení nebo modulu.  
  
 `cchName`  
 pro Velikost v různých znacích `szName`.  
  
 `pchName`  
 mimo Počet velkých znaků vrácených v `szName`.  
  
 `pmvid`  
 [out, volitelné] Ukazatel na identifikátor GUID, který jedinečně identifikuje verzi sestavení nebo modulu.  
  
## <a name="remarks"></a>Poznámky  
 Metoda [IMetaDataEmit:: SetModuleProps –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) slouží k nastavení těchto vlastností.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
