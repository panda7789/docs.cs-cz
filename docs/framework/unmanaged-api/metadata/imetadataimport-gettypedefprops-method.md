---
title: IMetaDataImport::GetTypeDefProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeDefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeDefProps
helpviewer_keywords:
- GetTypeDefProps method [.NET Framework metadata]
- IMetaDataImport::GetTypeDefProps method [.NET Framework metadata]
ms.assetid: 00061a25-ba05-47a7-b984-fd916b06b149
topic_type:
- apiref
ms.openlocfilehash: c9ac624e17223def206e86fd92ee4fd2de7f6082
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436745"
---
# <a name="imetadataimportgettypedefprops-method"></a>IMetaDataImport::GetTypeDefProps – metoda
Vrátí informace o metadatech pro <xref:System.Type> reprezentované zadaným tokenem TypeDef.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetTypeDefProps (  
   [in]  mdTypeDef   td,  
   [out] LPWSTR      szTypeDef,  
   [in]  ULONG       cchTypeDef,  
   [out] ULONG       *pchTypeDef,  
   [out] DWORD       *pdwTypeDefFlags,  
   [out] mdToken     *ptkExtends  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `td`  
 pro Token TypeDef, který představuje typ, pro který se mají vracet metadata.  
  
 `szTypeDef`  
 mimo Vyrovnávací paměť obsahující název typu.  
  
 `cchTypeDef`  
 pro Velikost v různých znacích `szTypeDef`.  
  
 `pchTypeDef`  
 mimo Počet velkých znaků vrácených v `szTypeDef`.  
  
 `pdwTypeDefFlags`  
 mimo Ukazatel na libovolný příznak, který upraví definici typu. Tato hodnota je Bitová maska z výčtu [CorTypeAttr –](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) .  
  
 `ptkExtends`  
 mimo Token metadat TypeDef nebo TypeRef, který představuje základní typ požadovaného typu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
