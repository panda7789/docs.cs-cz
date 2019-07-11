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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fa6e8665e5e2194eb4a3dffad8e97a69deb202d0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778974"
---
# <a name="imetadataimportgetnamefromtoken-method"></a>IMetaDataImport::GetNameFromToken – metoda
Získá název kódování UTF-8 odkazuje token metadat zadaného objektu. Tato metoda je zastaralá.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetNameFromToken (  
   [in] mdToken      tk,  
   [out] MDUTF8CSTR  *pszUtf8NamePtr  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `tk`  
 [in] Token, který představuje objekt, který chcete vrátit pro název.  
  
 `pszUtf8NamePtr`  
 [out] Ukazatel na název objektu UTF-8 v haldě.  
  
## <a name="remarks"></a>Poznámky  
 `GetNameFromToken` je zastaralý. Jako alternativu volat metodu k získání vlastnosti konkrétního typu, jako například vyžaduje se token `GetFieldProps` pro pole nebo `GetMethodProps` pro metodu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** 1.0  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
