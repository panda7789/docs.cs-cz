---
title: IMetaDataImport::GetNameFromToken – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetNameFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNameFromToken
helpviewer_keywords:
- GetNameFromToken method [.NET Framework metadata]
- IMetaDataImport::GetNameFromToken method [.NET Framework metadata]
ms.assetid: 32114ecf-8916-4ab2-a201-179c017344f1
topic_type:
- apiref
ms.openlocfilehash: 6ed30f07fcec9c730e1514350c594399f0aa16e5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437271"
---
# <a name="imetadataimportgetnamefromtoken-method"></a>IMetaDataImport::GetNameFromToken – metoda
Získá název UTF-8 objektu, na který odkazuje zadaný token metadat. Tato metoda je zastaralá.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetNameFromToken (  
   [in] mdToken      tk,  
   [out] MDUTF8CSTR  *pszUtf8NamePtr  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `tk`  
 pro Token představující objekt, pro který má být vrácen název.  
  
 `pszUtf8NamePtr`  
 mimo Ukazatel na název objektu UTF-8 v haldě.  
  
## <a name="remarks"></a>Poznámky  
 `GetNameFromToken` je zastaralá. Jako alternativu volejte metodu pro získání vlastností konkrétního typu tokenu, jako je například `GetFieldProps` pro pole nebo `GetMethodProps` pro metodu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** 1,0  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
