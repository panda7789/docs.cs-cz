---
title: IMetaDataImport::GetMethodProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMethodProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMethodProps
helpviewer_keywords:
- GetMethodProps method [.NET Framework metadata]
- IMetaDataImport::GetMethodProps method [.NET Framework metadata]
ms.assetid: e0667ef7-1d31-4c89-a2d3-d426f023f8d2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 57604d80d40130ca147c026852b7bcd23f8f90bc
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496453"
---
# <a name="imetadataimportgetmethodprops-method"></a>IMetaDataImport::GetMethodProps – metoda
Získá token budou metadata spojená s metodou odkazuje zadaný MethodDef.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetMethodProps (  
    [in]  mdMethodDef         mb,  
    [out] mdTypeDef           *pClass,  
    [out] LPWSTR              szMethod,  
    [in]  ULONG               cchMethod,  
    [out] ULONG               *pchMethod,  
    [out] DWORD               *pdwAttr,  
    [out] PCCOR_SIGNATURE     *ppvSigBlob,  
    [out] ULONG               *pcbSigBlob,  
    [out] ULONG               *pulCodeRVA,  
    [out] DWORD               *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `mb`  
 [in] Token MethodDef, který představuje metodu vrátit metadata pro.  
  
 `pClass`  
 [out] Ukazatel, který představuje typ, který implementuje metodu token TypeDef.  
  
 `szMethod`  
 [out] Ukazatel do vyrovnávací paměti, který má název metody.  
  
 `cchMethod`  
 [in] Požadovaná velikost `szMethod`.  
  
 `pchMethod`  
 [out] Ukazatel na velikost v širokých znaků `szMethod`, nebo v případě zkrácení, skutečný počet širokých znaků v názvu metody.  
  
 `pdwAttr`  
 [out] Ukazatel na libovolný příznaky spojené s metodou.  
  
 `ppvSigBlob`  
 [out] Ukazatel na binární metadat podpis metody.  
  
 `pcbSigBlob`  
 [out] Ukazatel na velikost v bajtech `ppvSigBlob`.  
  
 `pulCodeRVA`  
 [out] Ukazatel na relativní virtuální adresu metody.  
  
 `pdwImplFlags`  
 [out] Ukazatel na libovolný příznaky implementace metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
