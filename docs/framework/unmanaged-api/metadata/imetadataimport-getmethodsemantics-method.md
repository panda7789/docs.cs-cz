---
title: IMetaDataImport::GetMethodSemantics – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMethodSemantics
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMethodSemantics
helpviewer_keywords:
- GetMethodSemantics method [.NET Framework metadata]
- IMetaDataImport::GetMethodSemantics method [.NET Framework metadata]
ms.assetid: 5e018eaa-d60e-4a0b-a2c5-8c36bd09d905
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 65bc4bc74e06368e6c7be9b742a8f311ecadc7fc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782323"
---
# <a name="imetadataimportgetmethodsemantics-method"></a>IMetaDataImport::GetMethodSemantics – metoda
Získá příznaky, která označuje vztah mezi metodou odkazuje zadaný token MethodDef a spárované vlastnosti a události odkazuje zadaný EventProp token.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetMethodSemantics (  
   [in]  mdMethodDef   mb,  
   [in]  mdToken       tkEventProp,  
   [out] DWORD         *pdwSemanticsFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `mb`  
 [in] Token MethodDef představující metodu k získání informací o sémantických rolích.  
  
 `tkEventProp`  
 [in] Token představující spárované vlastnosti a události, pro který má být získána metody role.  
  
 `pdwSemanticsFlags`  
 [out] Ukazatel na příznaky přidružené sémantiku. Tato hodnota je bitová maska z [cormethodsemanticsattr –](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) výčtu.  
  
## <a name="remarks"></a>Poznámky  
 [Imetadataemit::defineproperty –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) metoda nastavuje příznaky sémantiku metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
