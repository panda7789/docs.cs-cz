---
title: IMetaDataEmit::DefineNestedType – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineNestedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineNestedType
helpviewer_keywords:
- IMetaDataEmit::DefineNestedType method [.NET Framework metadata]
- DefineNestedType method [.NET Framework metadata]
ms.assetid: 1e994de6-4628-459c-b967-b34be1e9fe4f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a0d105679a749b8c87099af871bdb42874d440b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447000"
---
# <a name="imetadataemitdefinenestedtype-method"></a>IMetaDataEmit::DefineNestedType – metoda
Vytvoří metadata podpis definice typu, vrátí `mdTypeDef` token pro tento typ a určuje, že je definovaný typ člena typu odkazuje `tdEncloser` parametr.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT DefineNestedType (   
    [in]  LPCWSTR     szTypeDef,  
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[],   
    [in]  mdTypeDef   tdEncloser,   
    [out] mdTypeDef   *ptd  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `szTypeDef`  
 [v] Název typu ve formátu Unicode.  
  
 `dwTypeDefFlags`  
 [v] `TypeDef` atributy. Toto je bitová maska s `CorTypeAttr` hodnoty.  
  
 `tkExtends`  
 [v] Token základní třídy. To znamená buď `mdTypeDef` nebo `mdTypeRef` tokenu.  
  
 `rtkImplements`[]  
 [v] Pole tokeny, které určují, rozhraní, která implementuje této třídě nebo rozhraní.  
  
 `tdEncloser`  
 [v] Token nadřazených typů. Musí být posledním prvkem pole `mdTokenNil`.  
  
 `ptd`  
 [out] `mdTypeDef` Token přiřazený.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
