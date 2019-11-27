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
ms.openlocfilehash: 0542c518b64764ad27aa00b8d595be1191059436
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437457"
---
# <a name="imetadataimportgetmethodsemantics-method"></a>IMetaDataImport::GetMethodSemantics – metoda
Získá příznaky označující vztah mezi metodou, na kterou se odkazuje zadaný token MethodDef, a spárovanými vlastnostmi a událostmi, na které odkazuje zadaný EventProp token.  
  
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
 pro Token MethodDef reprezentující metodu pro získání informací o sémantické roli pro.  
  
 `tkEventProp`  
 pro Token představující spárovánou vlastnost a událost, pro kterou má být získána role metody.  
  
 `pdwSemanticsFlags`  
 mimo Ukazatel na přidružené sémantické příznaky. Tato hodnota je Bitová maska z výčtu [CorMethodSemanticsAttr –](../../../../docs/framework/unmanaged-api/metadata/cormethodsemanticsattr-enumeration.md) .  
  
## <a name="remarks"></a>Poznámky  
 Metoda [IMetaDataEmit::D efineproperty](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineproperty-method.md) nastaví příznaky sémantiky metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
