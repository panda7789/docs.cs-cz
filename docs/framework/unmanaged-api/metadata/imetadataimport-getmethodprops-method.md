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
ms.openlocfilehash: 4037ca42c5a66f075e949cd2035c1e7db510bb8e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448905"
---
# <a name="imetadataimportgetmethodprops-method"></a>IMetaDataImport::GetMethodProps – metoda
Získá metadata přidružená metoda odkazuje zadaný MethodDef token.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `mb`  
 [v] MethodDef token, který představuje metodu vrátit metadata pro.  
  
 `pClass`  
 [out] Ukazatel na TypeDef token, který představuje typ, který implementuje metodu.  
  
 `szMethod`  
 [out] Ukazatel na vyrovnávací paměť, která má název metody.  
  
 `cchMethod`  
 [v] Požadovaná velikost `szMethod`.  
  
 `pchMethod`  
 [out] Ukazatel na velikost v široké znaky `szMethod`, nebo v případě zkrácení, skutečný počet široké znaky v názvu metody.  
  
 `pdwAttr`  
 [out] Ukazatel na žádné příznaky přidružené k metodě.  
  
 `ppvSigBlob`  
 [out] Ukazatel na binární metadata podpis metody.  
  
 `pcbSigBlob`  
 [out] Ukazatel na velikost v bajtech `ppvSigBlob`.  
  
 `pulCodeRVA`  
 [out] Ukazatel na adresu relativní virtuální metody.  
  
 `pdwImplFlags`  
 [out] Ukazatel na žádné příznaky implementace pro metodu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** zahrnuty jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
