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
ms.openlocfilehash: 4a258ce9121a287929ca5bc39c480f1ca2596e78
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437459"
---
# <a name="imetadataimportgetmethodprops-method"></a>IMetaDataImport::GetMethodProps – metoda
Získá metadata přidružená k metodě, na kterou odkazuje zadaný token MethodDef.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
 pro Token MethodDef, který představuje metodu pro vrácení metadat.  
  
 `pClass`  
 mimo Ukazatel na token TypeDef, který představuje typ, který implementuje metodu.  
  
 `szMethod`  
 mimo Ukazatel na vyrovnávací paměť, která má název metody.  
  
 `cchMethod`  
 pro Požadovaná velikost `szMethod`.  
  
 `pchMethod`  
 mimo Ukazatel na velikost v různých znacích `szMethod`, nebo v případě zkrácení, skutečný počet znaků v názvu metody.  
  
 `pdwAttr`  
 mimo Ukazatel na libovolný příznak spojený s metodou.  
  
 `ppvSigBlob`  
 mimo Ukazatel na binární podpis metadat metody.  
  
 `pcbSigBlob`  
 mimo Ukazatel na velikost v bajtech `ppvSigBlob`.  
  
 `pulCodeRVA`  
 mimo Ukazatel na relativní virtuální adresu metody.  
  
 `pdwImplFlags`  
 mimo Ukazatel na libovolný příznak implementace pro metodu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
