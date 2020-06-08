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
ms.openlocfilehash: 320cfae93f8aae94f9315e8e20ed6cf7f9cced7c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491313"
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
 [out, volitelné] Token metadat představující objekt, který upravuje vlastní atribut. Tato hodnota může být jakýkoli typ tokenu metadat s výjimkou `mdCustomAttribute` .  
  
 `ptkType`  
 [out, volitelné] `mdMethodDef` `mdMemberRef` Token metadat nebo představující <xref:System.Type> vrácený vlastní atribut  
  
 `ppBlob`  
 [out, volitelné] Ukazatel na pole dat, které je hodnotou vlastního atributu.  
  
 `pcbSize`  
 [out, volitelné] Velikost v bajtech dat vrácených v * `ppBlob` .  
  
## <a name="remarks"></a>Poznámky  
 Vlastní atribut je uložen jako pole dat, formátu srozumitelného modulem metadat.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](imetadataimport2-interface.md)
