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
ms.openlocfilehash: 9a80336db4a5a8d7cfdebb7eb8d25bcb8f96e87c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437645"
---
# <a name="imetadataimportgetcustomattributeprops-method"></a>IMetaDataImport::GetCustomAttributeProps – metoda
Získá hodnotu vlastního atributu s ohledem na jeho token metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCustomAttributeProps (  
   [in]            mdCustomAttribute   cv,  
   [out, optional] mdToken             *ptkObj,  
   [out, optional] mdToken             *ptkType,  
   [out, optional] void const          **ppBlob,  
   [out, optional] ULONG               *pcbSize  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `cv`  
 pro Token metadat, který představuje vlastní atribut, který má být načten.  
  
 `ptkObj`  
 [out, volitelné] Token metadat představující objekt, který upravuje vlastní atribut. Tato hodnota může být jakýkoli typ tokenu metadat s výjimkou `mdCustomAttribute`.  
  
 `ptkType`  
 [out, volitelné] Token metadat `mdMethodDef` nebo `mdMemberRef` reprezentující <xref:System.Type> vráceného vlastního atributu.  
  
 `ppBlob`  
 [out, volitelné] Ukazatel na pole dat, které je hodnotou vlastního atributu.  
  
 `pcbSize`  
 [out, volitelné] Velikost v bajtech dat vrácených ve formátu *`ppBlob`.  
  
## <a name="remarks"></a>Poznámky  
 Vlastní atribut je uložen jako pole dat, formátu srozumitelného modulem metadat.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
