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
ms.openlocfilehash: 2b24c2ca6907dfdb63ad934ec30557c246db174c
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004351"
---
# <a name="imetadataemitdefinenestedtype-method"></a>IMetaDataEmit::DefineNestedType – metoda
Vytvoří podpis metadat definice typu, vrátí `mdTypeDef` token pro daný typ a určí, že definovaný typ je členem typu, na který odkazuje `tdEncloser` parametr.  
  
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
 pro Název typu v kódování Unicode.  
  
 `dwTypeDefFlags`  
 [in] `TypeDef` atribut. Toto je Bitová maska `CorTypeAttr` hodnot.  
  
 `tkExtends`  
 pro Token základní třídy. Toto je buď `mdTypeDef` token, nebo `mdTypeRef` .  
  
 `rtkImplements`[]  
 pro Pole tokenů, které určují rozhraní, které tato třída nebo rozhraní implementuje.  
  
 `tdEncloser`  
 pro Token ohraničujícího typu Poslední prvek pole musí být `mdTokenNil` .  
  
 `ptd`  
 mimo `mdTypeDef`Přiřazený token.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IMetaDataEmit – rozhraní](imetadataemit-interface.md)
- [IMetaDataEmit2 – rozhraní](imetadataemit2-interface.md)
