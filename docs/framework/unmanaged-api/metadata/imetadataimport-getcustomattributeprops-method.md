---
title: IMetaDataImport::GetCustomAttributeProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetCustomAttributeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetCustomAttributeProps
helpviewer_keywords:
- GetCustomAttributeProps method [.NET Framework metadata]
- IMetaDataImport::GetCustomAttributeProps method [.NET Framework metadata]
ms.assetid: 6eefb243-a281-41c1-bcdc-7e17513bc446
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8a4ed21b6f9fd067f3357e07c5fda07d25ce868d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="imetadataimportgetcustomattributeprops-method"></a>IMetaDataImport::GetCustomAttributeProps – metoda
Získá hodnotu atributu vlastní zadaný token jeho metadata.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetCustomAttributeProps (  
   [in]            mdCustomAttribute   cv,  
   [out, optional] mdToken             *ptkObj,  
   [out, optional] mdToken             *ptkType,  
   [out, optional] void const          **ppBlob,  
   [out, optional] ULONG               *pcbSize  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cv`  
 [v] Metadata token, který představuje vlastní atribut mají být načteny.  
  
 `ptkObj`  
 [na víc systémů, volitelné] Metadata token představující objektu, která upraví vlastních atributů. Tato hodnota může být jakýkoli typ metadat token s výjimkou `mdCustomAttribute`.  
  
 `ptkType`  
 [na víc systémů, volitelné] `mdMethodDef` Nebo `mdMemberRef` metadata token reprezentující <xref:System.Type> vrácený vlastního atributu.  
  
 `ppBlob`  
 [na víc systémů, volitelné] Ukazatel na pole dat, která je hodnota vlastního atributu.  
  
 `pcbSize`  
 [na víc systémů, volitelné] Velikost v bajtech data v *`ppBlob`.  
  
## <a name="remarks"></a>Poznámky  
 Vlastní atribut se ukládají jako pole dat, formátu, který se rozumí modul metadat.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** zahrnuty jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
