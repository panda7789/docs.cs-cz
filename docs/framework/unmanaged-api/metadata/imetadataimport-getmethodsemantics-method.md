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
ms.openlocfilehash: 2cfb66203d8f2d69ea188f6913a5ef34dd74791e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503598"
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
 mimo Ukazatel na přidružené sémantické příznaky. Tato hodnota je Bitová maska z výčtu [CorMethodSemanticsAttr –](cormethodsemanticsattr-enumeration.md) .  
  
## <a name="remarks"></a>Poznámky  
 Metoda [IMetaDataEmit::D efineproperty](imetadataemit-defineproperty-method.md) nastaví příznaky sémantiky metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IMetaDataImport – rozhraní](imetadataimport-interface.md)
- [IMetaDataImport2 – rozhraní](imetadataimport2-interface.md)
