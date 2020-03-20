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
ms.openlocfilehash: 3b8fd9876563bace52a6088747d1ca4ed26ea872
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175808"
---
# <a name="imetadataemitdefinenestedtype-method"></a>IMetaDataEmit::DefineNestedType – metoda
Vytvoří podpis metadat definice typu, vrátí `mdTypeDef` token pro tento typ a určuje, že definovaný typ je `tdEncloser` členem typu, na který parametr odkazuje.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineNestedType (
    [in]  LPCWSTR     szTypeDef,  
    [in]  DWORD       dwTypeDefFlags,
    [in]  mdToken     tkExtends,
    [in]  mdToken     rtkImplements[],
    [in]  mdTypeDef   tdEncloser,
    [out] mdTypeDef   *ptd  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `szTypeDef`  
 [v] Název typu v Unicode.  
  
 `dwTypeDefFlags`  
 [v] `TypeDef` atributy. Toto je bitová maska `CorTypeAttr` hodnot.  
  
 `tkExtends`  
 [v] Token základní třídy. Toto je `mdTypeDef` buď `mdTypeRef` token nebo.  
  
 `rtkImplements`[]  
 [v] Pole tokenů, které určují rozhraní, které tato třída nebo rozhraní implementuje.  
  
 `tdEncloser`  
 [v] Token ohraničujícího typu. Poslední prvek pole musí `mdTokenNil`být .  
  
 `ptd`  
 [out] Přiřazen `mdTypeDef` token.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
